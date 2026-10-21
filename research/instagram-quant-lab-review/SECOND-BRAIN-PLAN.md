# Second Brain for the Lab: Plan

Extracted from REPORT.md (Part 1). Full evidence for every component is in REPORT.md.


## What you're describing, in the terms people use for it

What you want has standard names, and searching with them finds the real projects instead of Instagram funnels:

| Your words | Common terms |
|---|---|
| "a second brain that remembers everything" | **personal knowledge management (PKM)**, **knowledge base**, **"LLM wiki"** (Karpathy's pattern) |
| "AI that remembers across sessions / projects" | **persistent agent memory**, **long-term memory for LLM agents** (episodic = what happened, semantic = facts and knowledge) |
| "every VM, AI and project can use it" | a **shared memory server** exposed over **MCP (Model Context Protocol)** or an HTTP API, on a private network (e.g. **Tailscale**) |
| "it finds the right thing when needed" | **retrieval / RAG** (keyword BM25 + vector embeddings + reranking), sometimes a **knowledge graph** |
| "it cleans itself up and gets smarter" | **consolidation** (a scheduled job that summarizes, dedupes and promotes lessons), sometimes called a "dream" or "sleep" cycle |

**Is it possible?** Yes. Several mature open-source projects already do most of it, and they run fully self-hosted. The honest limits:
- **It doesn't learn.** No model "learns" in the brain sense. The system stores text, finds the relevant pieces, and hands them to whichever AI you're using at that moment.
- **It only knows what you capture.** It works exactly as well as what gets captured and how well it's organized. Most of the work is *capture discipline + good structure*, not clever AI.
- **"Remembers everything" is marketing.** What's real is "stores what you or your agents write down, and retrieves it well."

## The architecture (one brain, many clients)

```
                ┌────────────────────────── LAB SERVER (system of record) ──────────────────────────┐
  INGEST        │                                                                                     │
  PDFs/papers ─▶│ MinerU / Indra ──▶  brain/ (git repo of Markdown)  ◀── claude-obsidian (curated wiki)│
  web/YouTube ─▶│ Agent-Reach*         projects/ research/ strategies/ graveyard/ journal/ agents/   │
  sessions    ─▶│ hooks (session end)          │                                                     │
                │                              ▼ indexed by                                          │
                │                  GBrain  (Postgres + pgvector, local embeddings via Ollama)         │
                │                     │  HTTP MCP + OAuth, per-agent tokens                           │
                │  (optional) Hindsight ── automatic agent memory (recall/retain hooks), MCP per bank  │
                │  Nightly: consolidation (SkillOpt-Sleep, review-gated) + backups (git push, pg_dump)│
                │  Separate: market-data DB (OpenBB / yfinance / EDGAR / FRED → Postgres or DuckDB)   │
                └───────────────────────────────▲─────────────────────────────────────────────────────┘
                                                │  Tailscale (private network only)
       ┌──────────────────┬─────────────────────┼──────────────────────┬────────────────────┐
   VM: research       VM: backtests        VM: GPU / models       your laptop/phone     future tools
   Claude Code        Codex / agents       Kronos, fine-tunes     Obsidian (read/edit)  anything MCP
   (CLAUDE.md + MCP)  (MCP token)          (MCP token)            Claude Desktop
```
\* Agent-Reach installs by having your agent follow a remote file. Read it before using it (see V10).

### Layer 1: System of record. A git repo of Markdown files on the lab server
- **Why plain files:** every tool can read them, they outlive any app, git gives history and backups, and Obsidian gives you a human view.
- **Folder layout,** combined from the sound conventions found across the videos:
  - `projects/<name>/README.md, STATUS.md, progress.md, decisions.md` per project *(DYYaA1LKtoO)*
  - `agents/<name>/PROMPT.md, handovers/<date>.md, KNOWLEDGE.md` plus evals the agent **can't edit** *(DenJITWMbi2)*
  - `research/` for papers converted to Markdown, plus one "research card" per idea (source, rules, your test result) *(V22, V23)*
  - `strategies/` and **`graveyard/`** (every killed strategy with the reason it died), plus `experiments/` with one record per run: hypothesis, code hash, data window, costs, metrics, verdict, lesson *(V15, V18, V30)*
  - `journal/` for your trade journal and daily notes (fills imported from the IBKR API, not typed by hand) *(V26, V27)*
- **Curated research wiki:** use **claude-obsidian** (MIT; its tests passed when run here) for cited, linked research pages. It writes safely, with locked, all-or-nothing writes. It has **no network server**, which is why Layer 3 exists.

### Layer 2: Ingest (getting things in)
- **Documents:** **MinerU** (Apache-2.0 + terms that only matter at big-company scale) converts PDFs, Office files and scans to Markdown with tables and formulas. Version 4 adds a watched-folder document library. **Run `mineru telemetry disable` and don't use `--remote`.**
- **Light OCR on any VM:** **Indra** (CPU-only; its weights license is free for personal use).
- **Code and repos:** **Understand-Anything** (MIT) turns a repo or wiki into a knowledge-graph file you can commit to git *(V14)*.
- **Your AI sessions:** a Claude Code **Stop/SessionEnd hook** writes a short handover note into `projects/<name>/progress.md`. This is the single most valuable automation.
- **Market data is not memory.** Keep it in its own database: OpenBB, yfinance, SEC EDGAR via `edgartools`, FRED via `fredapi`, Dukascopy/HistData for FX *(DegcLifkzmE, V17, DeloQPzgbtw)*. The brain stores *what you learned* from data, not the data itself.

### Layer 3: The memory server every VM and agent connects to
**Recommendation: start with GBrain.** It's the best fit for "my lab's knowledge, shared by every machine."
- **GBrain** (`garrytan/gbrain`, MIT):
  - **What it does:** indexes your Markdown git repo into Postgres + pgvector, or a built-in embedded Postgres for small setups. It serves it over **HTTP MCP with OAuth**, with **per-agent tokens** and read/write scopes. It has a built-in command to expose it over **Tailscale only**.
  - **Search:** keyword search works with no API keys. For semantic search, **switch embeddings to local (Ollama or llama.cpp)**. The default once enabled is a paid service (Voyage) that would receive your text.
  - **Caveat:** pre-1.0 and changing very fast. Pin a version, and back up the database as well as the git repo.
- **Hindsight** (`vectorize-io/hindsight`, MIT, v1.0), an optional second layer:
  - **What it does:** automatic **agent memory**. Its Claude Code and Codex plugins recall relevant memories before each prompt and save new ones after each response, into separate "banks" (per agent, project or desk). It uses Postgres + pgvector and local embeddings by default.
  - **Costs:** **auth is off by default** (turn it on before other VMs connect). Every save calls an AI model, which can be a local model or your Claude subscription. Enable its secret/PII redaction.
  - **When to add it:** if, after a few weeks, you want agents to remember *what they did* without you writing notes. Running both doubles maintenance, so start with one.
- **Alternatives verified to exist** (not inspected in depth): **mem0**, **Letta**, **basic-memory**. **everything-claude-code's Memory Vault** is file-based, with a local MCP per machine *(V10)*.
- **Not self-hostable (avoid for this):** **Open Glean**, which secretly depends on the creator's paid service. Also any "memory" that is a SaaS (Astral, TradeZella, Replit).

### Layer 4: Connecting every VM and agent
- **On each VM:** register the brain once (`claude mcp add …` with that VM's token; Codex, OpenCode and Cursor are supported the same way).
- **A global `~/.claude/CLAUDE.md`** on each VM that says, in plain words:
  - "Before starting, query the brain for this project's STATUS and relevant decisions."
  - "Record decisions in decisions.md."
  - "Log every experiment to experiments/."
- **Hooks:**
  - SessionStart injects the project's STATUS.md.
  - Stop/SessionEnd writes a handover.
  - Keep both small, so they don't burn tokens silently (V14's plugin is an example of a hook that does).
- **Workflow add-ons that become *users* of the brain:** **superpowers**, Anthropic's **skills**, **BMAD**, **SuperClaude** *(DeRgmkvIkP4, V04)*.

### Layer 5: Consolidation (the "gets smarter" part, done honestly)
- **A nightly job:**
  1. Summarize the day's handovers into each project's STATUS.md.
  2. Dedupe notes.
  3. Promote repeated lessons into `KNOWLEDGE.md`.
  4. Flag stale pages (claude-obsidian's lint does this).
- **SkillOpt-Sleep** (Microsoft, MIT, a preview feature) mines your past Claude Code/Codex sessions and *proposes* improved skills and memory notes. Keep it **review-gated**: don't auto-adopt. It sends session excerpts to whichever AI you configure.
- **The self-improving research loop:** the autoresearch / RD-Agent pattern (V15, V30) writes every attempt, kept or discarded, into `experiments/` and `graveyard/`. That's how your quant agents stop re-testing dead ideas.

### Layer 6: Security and durability (non-negotiable)
- **Network:** everything on **Tailscale only**. Never expose the brain publicly; GBrain has a `--funnel` option that does exactly that, so don't use it.
- **Access:** one token per agent or VM, with scopes. Read-only for agents that don't need to write.
- **Keep data local:** local embeddings and local models wherever possible, so your notes never leave the lab. Turn on redaction, and **never put API keys, broker credentials or passwords in notes.**
- **Backups:** `git push` of the brain repo to a private remote, plus a nightly `pg_dump`. Test a restore once.

## Rollout plan

| Phase | What | Effort | Done when |
|---|---|---|---|
| 1 | Create the `brain/` git repo with the folder layout above; global CLAUDE.md on one VM; session-end handover hook | an evening | every Claude Code session leaves a handover note |
| 2 | Install **GBrain** on the lab server (embedded Postgres to start), local embeddings via Ollama, expose over Tailscale; connect 2 VMs with separate tokens | 1–2 days | an agent on VM B answers "what did we decide on project X?" from notes written on VM A |
| 3 | **MinerU** ingest for papers; **claude-obsidian** for the cited research wiki; research-card and experiment-record templates | 1–2 days | papers dropped in a folder appear as searchable Markdown |
| 4 | Nightly consolidation + backups; move GBrain to full Postgres when notes grow | a day | a restore test passes; STATUS pages update overnight |
| 5 (optional) | **Hindsight** for automatic agent memory; SkillOpt-Sleep proposals reviewed weekly | 1–2 days | agents recall past work without manual notes |

**What I'd need from you to make this exact:**
- the lab server's OS, CPU/RAM/GPU
- which VMs exist and what runs on each
- whether Tailscale (or another VPN) is already in place
- whether you're open to a local embedding model on the server

**Caveat:** the GBrain and Hindsight assessments come from reading their code and docs, not from running them. Retrieval quality and the vendors' benchmark claims are unverified. Phase 2 is the pilot that proves it on your own notes.

---

