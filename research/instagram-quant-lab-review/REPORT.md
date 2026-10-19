# Instagram Saves → Quant Lab & Second Brain: Reviewed, Ranked, Planned

**65 items reviewed** in two batches, compiled 2026-10-19:
- **Batch 1 (35):** Instagram links fetched through a mirror. That's 20 videos and 13 carousels/images, plus 2 posts only partly retrievable.
- **Batch 2 (30):** videos downloaded on the user's phone and shared via Dropbox. There are no captions for these, so each creator was identified from on-screen watermarks.

**How every item was checked**
- **Videos:** every one was transcribed, including Portuguese and Hindi with translation. Every frame and slide was viewed, with crops of small text.
- **Repos:** every repo named was confirmed with git and shallow-cloned, and its LICENSE, README and commit history were read.
- **Products:** checked by web search.
- **Nothing was executed.** The one exception is claude-obsidian's own test suite, which passed.
- **Not verifiable here:** star counts (the GitHub API is blocked in the review sandbox) and anything sent only through "comment X for the DM" funnels.

**How this document is organized**
1. **Part 1, Second-brain plan:** what you're describing, whether it's possible (yes), which pieces are real, how they fit together, and what to install first.
2. **Part 2, Everything worth using:** all subjects (quant, data, AI tooling, dev tooling) ranked across both batches.
3. **Part 3, Patterns, red flags, and what to skip.**
4. **Part 4, Full entries:** batch 2 (V01–V30), then batch 1. Each entry also has a "Second-brain relevance" section.

---

# Part 1: The second brain for the lab

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

# Part 2: Everything worth using (all subjects, both batches)

### Tier 1: free, open source, high value for the lab

| What | Category | License | From |
|---|---|---|---|
| **NautilusTrader**: backtest-to-live engine (IBKR, crypto) | Quant engine | LGPL-3.0 | DcD1vwCtGGX, DegcLifkzmE |
| **skfolio**: portfolio optimization + walk-forward/purged CV | Quant | BSD-3 | DcD1vwCtGGX |
| **OpenBB**: financial data platform with an MCP server | Data | Apache-2.0 | DegcLifkzmE |
| **Free data sources:** Dukascopy, HistData (10+ yrs of 1-min FX), Hyperliquid SDK, Polymarket client, `cot_reports`; yfinance, `edgartools` (SEC), `fredapi` (FRED) | Data | MIT / Apache-2.0 | DeloQPzgbtw, DemXvfSjwCM, V17 |
| **TradingAgents**: multi-agent LLM research desk, paper-backed | AI quant | Apache-2.0 | DegkHS3GRHJ |
| **trading-research-agents** (Bijective Labs): multi-agent crypto desk with a sandbox, auditors, decision journal and MCP; alpha | AI quant | MIT | V19 |
| **Kronos**: open forecasting model for OHLCV; small versions run on CPU | AI quant | MIT | DcD1vwCtGGX, V11, V29 |
| **Vibe-Trading**: LLM research workspace with 462 prebuilt alpha factors | AI quant | MIT | DcD1vwCtGGX |
| **GBrain / Hindsight**: shared memory servers (see Part 1) | Second brain | MIT | Dem60yJDELo, DeCKnW0DAGc |
| **claude-obsidian**: cited research wiki for Claude Code | Second brain | MIT | Defw9ggACu1 |
| **MinerU**: PDF/Office → Markdown with tables and formulas | Ingest | Apache-2.0 + terms | DeCKnW0DAGc |
| **Understand-Anything**: codebase/wiki → knowledge graph plus dashboard | Dev / memory | MIT | V14 |
| **everything-claude-code**: large agent/skill collection plus a Markdown Memory Vault | Claude tooling | MIT | V10 |
| **superpowers**, **Anthropic skills**, **BMAD-METHOD**, **SuperClaude** | Claude tooling | MIT / Apache-2.0* | DeRgmkvIkP4, V04 |
| **SkillOpt**: improves skill files against held-out tests; nightly session mining | Claude tooling | MIT | DbEK3bustQ7 |

\* Anthropic's Word/PDF/PowerPoint/Excel skills are source-available, not open source.

### Tier 2: real and useful, with caveats
- **autoresearch** (Karpathy, MIT) and **RD-Agent** (Microsoft, MIT): unattended keep-or-discard research loops, ideal templates for a strategy-research agent. *(V30, V15)*
- **OpenAlice** (AGPL, beta) for an approval-gated trading assistant. **qanat** (MIT, beta) for point-in-time data over MCP. *(DatpvftE-Iq, DeUE0tQPmgX)*
- **Soup** (Apache-2.0): fine-tune 7–8B models on a small GPU. The video's memory claims are inflated. *(V05)*
- **Indra OCR** (weights have a revenue cap). **OpenChamber** and **OpenRig** (remote agent UI, agent teams). **QF-Lib** backtester. *(DeosAIWFZN2, DenP7kUD3Az, DeCKnW0DAGc, Dd4JGF1lIhA)*
- **Backtesting tools:**
  - **backtesting.py:** AGPL.
  - **vectorbt:** Apache + Commons Clause, which bars reselling it.
  - **smart-money-concepts:** MIT; detects ICT-style zones so those claims can be tested.

  *(V22, V20)*
- **TensorTrade:** RL sandbox only; it loses money after fees in its own results. *(DemfalkFKqU)*
- **awesome-claude-code** (license forbids commercial use and modified copies), **awesome-harness-engineering** (CC0), **Agent-Reach** (read its remote install file first). *(V10)*
- Also verified real: `microsoft/qlib`, `QuantConnect/Lean`, `virattt/ai-hedge-fund`. *(Dd2iE-vjl1-)*

### Tier 3: ideas and references worth keeping
- **Research pipeline:** idea → rules → code → backtest → out-of-sample → Monte Carlo → walk-forward → **deflated Sharpe** → paper → live, plus a **graveyard** of killed strategies. *(Dd4QRzpFM00, V18)*
- **Free papers:**
  - SSRN
  - *151 Trading Strategies* (Kakushadze & Serur)
  - Jegadeesh & Titman momentum
  - the Zarattini/Barbon/Aziz opening-range-breakout paper

  *(V01, V21, V23)*
- **Rules recovered from videos, testable with free tools and realistic costs:**
  - Internal Bar Strength (IBS)
  - 9 EMA + VWAP
  - EURUSD "midday sell"
  - Gartley 222
  - ICT rejection block
  - gold stop-and-reverse straddle (martingale-like, so be careful)

  *(V01, DekhFIbgQTO, DemxOm_AS9a, DejYce1ADfB, V20, V09)*
- **Rebuildable on free tools:**
  - mini "Bloomberg" (yfinance + EDGAR + FRED + FinBERT)
  - self-healing data pipeline (Dagster + dbt + DuckDB)
  - rule-based signal scanner with Slack alerts
  - peer groups by revenue rather than SIC code
  - OI-build-up scanner from free NSE data

  *(V17, V07, DenSGzckhBw, DeUE0tQPmgX, V27)*
- **Claude Code structure cheat sheet** (with corrections) and the agent folder pattern. *(DdtaUOCNmNs, DenJITWMbi2)*

---

# Part 3: Patterns, red flags, what to skip

1. **About 40 of 65 items end in "comment X and I'll DM you."** Every funnel we could trace led to a public repo (now named in this report) or a paid course, newsletter, signal group, prop-firm affiliate link or SaaS. You never need to comment.
2. **The tools are often better than the posts about them.** Repo-spotlight accounts got the facts wrong: an OCR tool sold as an LLM runner, a game port sold as "AI memory," and "200,000 users" that was really "200,000 lines of code."
3. **No trading result shown in any of the 65 items survived scrutiny.** Recurring tricks:
   - a "best day" bigger than the whole month
   - a 56% win rate on 71 trades, statistically a coin flip
   - "90% win rate" that was a spreadsheet's "not empty" counter
   - reshuffling the same trades to claim a "93% pass rate"
   - a 3-day backtest
   - a drawdown that breaks the prop firm's own limit
   - "$10 → $4k" on a dashboard that starts at $45,000
   - stock rallies presented as bot backtests
   - "8 million tests" with the holdout used to pick winners

   Every strategy here is a hypothesis to test with costs and out-of-sample data, never a result.
4. **"AI second brain" videos are mostly animation or prompts.** The working versions are the open-source servers in Part 1.
5. **Skip:**
   - **AI hype:** "AI Omarchy" (twice), "6 AIs 1 brain," the Bloomberg-clone/meme-bot clips.
   - **Copy-trading:** "Casino" copy-trading.
   - **Closed bots:** Range Sniper / Sniper Range Bot.
   - **Generic prompts:** fake "Buffett system" and "learn anything" prompts.
   - **Lists with no detail:** strategy-name grids.
   - **Paid platforms:** "10 platforms → $10k/mo."
   - **Misdescribed or joke posts:** the game-port "memory layer," the comedy skit.

---

# Part 4: Full entries

## Batch 2: downloaded videos (V01–V30), ordered by usefulness

---

## V10 | Five trending agent-harness repos: Everything Claude Code (ECC), awesome-claude-code, Archify, Agent Reach, awesome-harness-engineering
- **Source:** Dropbox video V10 (VID_20261018_120735_355.mp4)
- **Account:** @qendresahhoti (watermark, end card) · **Type:** video (128s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – All five repos are real, MIT/CC0 (one CC BY-NC-ND), and active as of this week. Two of them (ECC, awesome-harness-engineering) directly cover memory and harness patterns for the lab's Claude Code setup.

**What it says:** "Five GitHub repositories the AI builder community cannot stop talking about." She scrolls each GitHub README on screen. Her framing at the end: none of them make the model smarter, they organise what's around it (the harness). Her CTA is "comment REPO and I'll send the link", with a note summarising all five that is visible in the last frames.

1. **Everything Claude Code (ECC):** "battle-tested Claude Code setups, agents, skills, hooks, rules, memory that survives across sessions; installs as a plugin with one command". Her advice: steal 2–3 configs and don't adopt everything. On screen:
   - "ECC is MIT-licensed open source… 68 agents, 286 skills, 94 legacy command shims"
   - "plan → test → implement → review → verify → remember → improve"
   - Install via `npx ecc-universal setup` / `npx ecc-universal install --guided`, or `git clone https://github.com/affaan-m/ECC.git`
   - A "Do not stack install methods" warning
2. **Awesome Claude Code:** a curated list of skills, slash commands and guides. On screen: the table of contents (Memory & Context Persistence, Agent Orchestration, Ralph Wiggum, …), "A Field Guide to Claude Fable 5", andrej-karpathy-skills, and an Anthropic section.
3. **Archify:** "one command installs it as a skill; ask your agent to map the repository and it turns the codebase into an interactive architecture diagram… one HTML file". On screen:
   - "#1 Repository Of The Day"
   - "Archify is a Node.js rendering and validation system… typed JSON IR… compiles into HTML/SVG"
   - `npx skills add tt-a1i/archify -g`
   - MIT, version 2.17.0-dev.1
4. **Agent Reach:** "gives your coding agent real internet access – Twitter, Reddit, YouTube, GitHub, 16 platforms through one installer… installs and health-checks tools rather than some magic universal API". On screen: the platform table (Web, YouTube, RSS, Exa search, GitHub, Twitter/X, Bilibili, Reddit, Facebook, Instagram, Xiaohongshu, LinkedIn, V2EX, Snowball, Xiaoyuzhou podcast) and the cookie/proxy caveats.
5. **Awesome Harness Engineering:** "a curated list for… memory, evals, verification, orchestration". Her advice: pick one pattern a week and build it. On screen:
   - CC0, 4k stars, 496 forks, last commit "today", "Join linux.do"
   - The templates folder (AGENTS.md, HARNESS_CHECKLIST.md, IMPLEMENT.md, PLAN.md), with the AGENTS.md tool-permission template opened

**What's actually behind it:**
- **ECC:** https://github.com/affaan-m/everything-claude-code (alias affaan-m/ECC resolves to the same HEAD)
  - MIT (© 2026 Affaan Mustafa)
  - VERSION 2.2.3, last commit 2026-10-15, PR numbers above #3500
  - Now 71 agents and 311 skill dirs (the video's 68/286 is slightly old)
  - Ships hooks (`hooks/memory-persistence`, session summaries, "instincts" continuous learning), rules, an AgentShield scanner and a Python dashboard
  - **Memory Vault:** `ecc memory init/search/read/handoff/doctor` stores portable `ecc.memory.v1` Markdown under `.ecc/memory/` (project/team) and `~/.ecc/memory/` (user), plus an optional `ecc-memory-mcp` server. The code is in `scripts/memory.js` and is covered by tests.
- **Awesome Claude Code:** https://github.com/hesreallyhim/awesome-claude-code
  - **CC BY-NC-ND 4.0** (not MIT: no commercial use or derivatives of the list itself)
  - Last commit 2026-10-19; the README is generated from a CSV by a Python script
- **Archify:** https://github.com/tt-a1i/archify
  - MIT
  - Last commit 2026-10-19, now stable v3.2.0 (the video showed 2.17-dev)
  - Node.js; README badge claims 130K+ installs on skills.sh
  - Site archify.si (free and open source; the README notes that third-party paid services exist)
  - Turns a codebase or description into an interactive HTML/SVG diagram through a typed JSON IR
  - Has sponsors (Apinebula, EverMind/Raven, Kimi Work)
- **Agent Reach:** https://github.com/Panniantong/Agent-Reach
  - MIT
  - Last commit 2026-10-08, Python 3.10+, README primarily in Chinese with an English version
  - A router and installer over third-party tools: Jina Reader, yt-dlp, Exa via mcporter (MCP), gh CLI, OpenCLI with existing Chrome sessions, rdt-cli, xiaohongshu-mcp, twitter CLI with cookies
  - `agent-reach doctor` health check
  - "All free; only a server proxy (~$1/month) may cost"
  - Install is "tell your agent: install from raw.githubusercontent.com/.../install.md". That means having your agent follow a remote instruction file, which is a supply-chain and prompt-injection exposure. Read it first.
- **Awesome Harness Engineering:** https://github.com/ai-boost/awesome-harness-engineering
  - CC0
  - Last commit 2026-10-18
  - Contents: foundations essays (OpenAI harness engineering, Anthropic "Building Effective Agents" and long-running harness design, LangChain "Anatomy of an Agent Harness", Martin Fowler), memory and context sections (OpenViking, codebase-memory-mcp, OpenWiki, PRO-LONG, agentic-stack, ByteRover paper), and copyable templates

**Verification:**
- Viewed all 16 contact sheets and cropped the Archify, harness and end-note frames (work2/V10/).
- `git ls-remote` on all five repos, plus shallow clones into scratchpad/repos/:
  - everything-claude-code, awesome-claude-code, archify, Agent-Reach, awesome-harness-engineering
- Read the LICENSE files, README sections and `git log -1`, and listed directories.
- Identified the harness list's owner by web search, confirmed by the linux.do badge, the CC0 license and the templates folder matching the video.
- Did not run anything. Live star counts were not verified (the GitHub API is blocked).

**Claims vs reality:**
- "ECC: memory that survives across sessions, one-command plugin install": **true.** There are hooks plus a Markdown Memory Vault and an optional MCP server. "Battle-tested" is marketing; it is a huge, fast-moving config pack (300+ skills), and the README itself warns against stacking install methods. Her advice to cherry-pick is correct.
- "Biggest repo in the space is a harness, not a model wrapper": fair as framing.
- "Awesome Claude Code is constantly updated": **true** (commit today). Note the restrictive license.
- "Archify turns a codebase into an interactive diagram, one HTML file": **true** per the README and the examples. Output quality depends on the agent's understanding.
- "Agent Reach: 16 platforms, one installer": roughly true. She correctly notes it's an installer/router, not a universal API. Several platforms need your own cookies or logins, which is a ToS and account risk.
- "Awesome harness engineering: 4k stars": shown on screen; not independently verified.

**Agenda:** Engagement funnel: "comment REPO" to receive a DM with a link to her notes page. No paid product is visible. Some listed repos carry sponsors.

**Lab use:**
- **ECC:**
  - Don't bulk-install into the lab's Claude Code. Clone it and copy selected `agents/`, `skills/`, `hooks/` and `rules/` into `~/.claude/`.
  - Needs Node ≥18 for the `ecc` runtime (`npm i -g ecc-universal@2.2.3`) if you want the Memory Vault CLI/MCP.
  - Effort: a few hours to curate.
- **awesome-claude-code / awesome-harness-engineering:** reading lists. Use the harness templates (AGENTS.md, PLAN.md, HARNESS_CHECKLIST.md) for lab projects. Effort: an hour.
- **Archify:** `npx skills add tt-a1i/archify -g`; useful for mapping unfamiliar quant repos (Lean, nautilus_trader, qlib). Node only, no GPU.
- **Agent Reach:** run in a sandboxed VM if at all. Free tools; Exa through MCP is free per the README; cookies stay local. Use it for research agents that pull YouTube transcripts and Reddit or X sentiment. Effort: half a day, plus maintenance as platforms block access.
- No paid APIs are required for any of the five.

**Second-brain relevance:** MEDIUM–HIGH –
- **ECC's Memory Vault** is a genuine, self-hostable layer for agent context injection and cross-harness handoff: plain Markdown files, a CLI, and an optional stdio MCP server, shared across Claude Code, Codex, Hermes, OpenClaw and Kimi. Sharing is file-based (project, team or user scope). It is not a networked multi-VM service: to share across VMs you would git-sync `.ecc/memory/` or run the MCP server per machine. It has no vector search or knowledge graph.
- **Awesome-harness-engineering's "Memory & State"** section is a good map of real options, such as OpenViking and codebase-memory-mcp.
- **Agent Reach** covers the capture/ingest side (web, YouTube, RSS into the agent).
- For a true shared lab brain, garrytan/gbrain (verified in batch 1: Markdown/git source of truth, Postgres+pgvector, HTTP MCP with OAuth and per-agent tokens) is still the stronger multi-VM candidate. ECC's vault format could feed it.

---

## V04 | "7 free Claude Code upgrades, part 1": Anthropic's skills repo, Superpowers, BMAD-METHOD and SuperClaude
- **Source:** Dropbox video V04 (VID_20261018_115838_680.mp4)
- **Account:** @gusvandee (Gus Van Dender, "AI for Business Growth", business consultant, link primelive.ai; profile card shown at the end) · **Type:** video (106s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – all four repos are real, free, actively maintained and install straight into Claude Code on the lab server. Superpowers and Anthropic's skills are the most useful.

**What it says:** "There are actually seven free upgrades that I believe every Claude Code user should need." He covers four, each with a scrolling GitHub screenshot:
1. **Anthropic's Skills** (anthropics/skills): "an official playbook for docs, spreadsheets, design... built and maintained by the actual team behind Claude."
2. **superpowers** (obra/superpowers): "the most starred Claude repo"; "it's gonna plan first, write the tests and then review its own work... way fewer bugs and you can ship it right away."
3. **BMAD-METHOD** (bmad-code-org/BMAD-METHOD): builds a PM/architect/developer "team inside of Claude Code", so "your ideas go from concept to shipped feature completely on its own... no more interaction needed. Of course you want to double check."
4. **SuperClaude** (SuperClaude-Org/SuperClaude_Framework): "like picking a character class in a video game"; "expert personas and ready-to-use commands." The screenshot shows "30 slash commands, 20 agents, 7 modes, 8 MCP servers."

He ends with "three to go in part two, hit follow." Part 2 is not in this video.

**What's actually behind it:**
- **anthropics/skills** – https://github.com/anthropics/skills. Most skills are Apache-2.0; the docx/pdf/pptx/xlsx skills are source-available, not open source (stated in the README). Last commit 2026-10-09. It has 19 skills, including docx, xlsx, pdf, pptx, mcp-builder, skill-creator, frontend-design and webapp-testing. Official Anthropic repo.
- **obra/superpowers** – https://github.com/obra/superpowers. MIT, © Jesse Vincent. Verified in batch 1; existing clone last commit 2026-10-09. A skills library (brainstorm, plan, TDD, systematic debugging, code review, subagent-driven development) for Claude Code, Codex, Cursor, Gemini CLI, OpenCode and others.
- **bmad-code-org/BMAD-METHOD** – https://github.com/bmad-code-org/BMAD-METHOD. MIT, © 2025 BMad Code, LLC (plus a TRADEMARK.md). Last commit 2026-10-18. Stable v6.12 installs with `npx bmad-method install`; v7 is in alpha via `npx skills add bmad-code-org/BMAD-METHOD --skill '*'`. Needs Node and uv. It provides persona skills (analyst, PM, architect, PO, dev, UX, QA), PRD/architecture/story workflows, code review, retrospective, and `bmad-project-context` (maintains an AGENTS.md block).
- **SuperClaude-Org/SuperClaude_Framework** – https://github.com/SuperClaude-Org/SuperClaude_Framework. MIT, © 2024 SuperClaude Framework Contributors. Last commit 2026-09-27. Install with `pipx install superclaude`. It is a "meta-programming configuration framework": `/sc:*` slash commands, agent persona prompts, behavioural modes and optional MCP-server installers (Tavily, Context7, Serena and others). The README says it is not affiliated with Anthropic.

**Verification:** Viewed all 14 contact sheets. Shallow-cloned anthropics/skills, BMAD-METHOD and SuperClaude_Framework into `scratchpad/repos/`; read the licences, READMEs and skill lists and checked `git log`. Reused the batch-1 superpowers clone. I did not check star counts ("most starred Claude repo" is not verified) and ran no code.

**Claims vs reality:**
- Anthropic's skills are "official... built by the team behind Claude": true, with the licence caveat that the document skills are source-available only.
- Superpowers "plans first, writes the tests, reviews its own work": true as a methodology the skills push the agent into. "Way fewer bugs, ship right away" is opinion; you still have to review the result.
- BMAD "concept to shipped feature completely on its own, no interaction needed": overstated. BMAD is a structured, conversational workflow (brief → PRD → architecture → stories → dev), and several skills require user approval for each write. He contradicts himself with "of course you want to double check."
- SuperClaude "expert personas": accurate, but these are prompt files plus commands. Several features depend on optional third-party MCP servers, some of which need API keys (e.g. Tavily, 21st.dev Magic).
- "Free": all four are free to use; Claude Code itself still needs a subscription or API key.

**Agenda:** Follower growth ("hit follow for part 2") for a consultant who sells AI-for-business services via primelive.ai. There is no paid product in the video itself.

**Lab use:**
- Superpowers: install it as a Claude Code plugin (`/plugin` marketplace or as the README describes). This is the best default for code quality in the quant repos. Effort: 5 minutes.
- Anthropic skills: add via the plugin marketplace or copy the folders you need into `~/.claude/skills/` (xlsx/pdf for research reports, mcp-builder for wrapping lab data services as MCP servers). Effort: minutes.
- BMAD: worth it only for larger greenfield projects (e.g. a new backtesting service). Install with `npx bmad-method install` (Node 20+, uv). It overlaps heavily with Superpowers, so pick one primary workflow.
- SuperClaude: `pipx install superclaude`. It is optional and overlaps with the above; its many injected instructions use context tokens. Try it in a sandbox project first.
- None needs a GPU. Avoid stacking all four on one project.

**Second-brain relevance:** LOW – These are agent-workflow layers, not memory systems. Small pieces touch memory: BMAD's `bmad-project-context` maintains a verified AGENTS.md block (agent context injection, per repo), and SuperClaude can install the Serena MCP for per-project "session persistence & memory" and mentions a built-in "ReflexionMemory" for error learning. All of this is per-project and local, with no cross-VM sharing. Treat these as consumers of a second brain: point them at a shared memory MCP server (e.g. hindsight or gbrain, verified in batch 1) rather than relying on their per-repo files.

---

## V19 | Bijective Labs "trading-research-agents": MIT-licensed multi-agent crypto-perps desk (screener, 4 analysts, validators, risk manager, 2 auditors) with deterministic cost/risk gates
- **Source:** Dropbox video V19 (VID_20261018_121445_824.mp4)
- **Account:** @seb.ai (watermark on every frame and end card) · **Type:** video (44s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – a real, very actively maintained, MIT-licensed Python package (pip/uv installable, Linux-tested, MCP server included) with an unusually honest design: LLMs only give opinions, the system computes every number, prices costs and enforces limits.

**What it says:** Overlay: "SOMEONE RELEASED AN ENTIRE AI TRADING TEAM FOR FREE". "Someone just built a team of 10 AI pro trading agents that work 24/7 for you… a free GitHub project for AI agents on a trading desk like a real hedge fund." He scrolls the README of **Bijective / trading-research-agents** ("Autonomous trading agents with deterministic execution. The agents propose; the system decides."; MIT license tab, Release 0.7.x visible) and its "What you see, in order" section (console, the screen pass over BTCUSDT, ETHUSDT, SOLUSDT, NEARUSDT, XRPUSDT, DOGEUSDT, MAGICUSDT, FILUSDT, SUIUSDT; one cycle per instrument; the result table; "Between cycles"). Roles narrated: a screening agent picks coins, four analyst agents each make a case, validators poke holes, a risk manager can kill any trade, two auditors check everything afterwards, "and it also runs 24/7". Overlays: "SAVE THIS VIDEO", "Comment AUDIT and I'll send you the repo and the setup guide."

**What's actually behind it:**
- **trading-research-agents** – https://github.com/BijectiveLabs/trading-research-agents (also resolves as bijectivelabs/…) · **MIT** (© 2026 Bijective Labs) · PyPI `trading-research-agents`, version **0.8.0** released 2026-10-18 (last commit that day; history in the clone goes back to at least 2026-09-12) · status badge "alpha". ~405 files, ~61.6k lines of Python under `src/trading_research_agents/` (agents, chain, data, execution, ledger, llm, mcp, records, store, strategy, trading…), 82 test files, CI, Dockerfile, docker-compose, docs at docs.bijectivelabs.dev, MCP registry name `io.github.BijectiveLabs/trading-research-agents`.
- What it does: a "desk" folder with `strategy.toml`; `tra run` (one decision on live data in a **sandbox**, nothing sent), `tra run --every 15m`, `tra watch`, `tra audit`, `tra ledger show` ("every idea that died, and what killed it"), `tra backtest`, `tra paper`, `tra live`, `tra mcp serve` (read-only gates as MCP tools). Venues via **ccxt** (Bybit default, OKX; others "through the same path"), USDT perpetuals; also lists spot, stock perps, tokenized stocks and prediction markets as built.
- Agents: market screener; four analysts; up to three validators (pro/contra/neutral, claims without a cited figure are discarded); risk manager that can only cut/pause/halt; technology and quant auditors that read records and propose changes but cannot change anything. Max 11 roles, so "10 agents" is about right.
- LLM providers: Groq (free tier, default `openai/gpt-oss-120b`), Gemini, Anthropic (`claude-opus-5-5`), OpenAI, DeepSeek, xAI, OpenRouter.

**Verification:** Viewed all 5 contact sheets; read repo name and README sections from frames. `git ls-remote` (both owner spellings) and shallow clone to `scratchpad/repos/trading-research-agents`; read LICENSE, NOTICE, pyproject (v0.8.0), README (install, guarantees, venues, live tier), `git log`, directory structure. Did **not** run anything. Not verified: real-order behaviour, PyPI release contents vs repo, star count, and who is behind Bijective Labs.

**Claims vs reality:**
- "Entire AI trading team for free": true – MIT and free; you pay only for an LLM key (Groq free tier works) and exchange fees.
- "10 AI pro trading agents… like a real hedge fund": the roles exist; "pro" and "hedge fund" are marketing. The README itself says models are only used for opinions; sizing, pricing and limits are deterministic code.
- "Works 24/7 for you": `--every 15m` loops exist, but the default is a sandbox that sends nothing; venue mode needs a signed "mandate" and is only run end to end by the authors on Bybit/OKX **practice/demo** accounts. The README says step 3 (real money) "has not been run by us".
- Implied profitability: none claimed by the repo. The README shows its example strategy core's one-day replay at **net −294.19 bps** and says "a backtest that only shows good news is one nobody should believe". There is no evidence the agents have an edge; the default targets refuse trades whose edge is under 2x round-trip cost.
- "Comment AUDIT for the setup guide": the README already contains a 6-step setup guide.

**Agenda:** "Comment AUDIT" DM funnel for engagement and list-building on a project he did not build. The repo is legitimate; the creator adds nothing beyond reading it.

**Lab use:**
- Install in an isolated venv on the lab server: `uv tool install 'trading-research-agents[ccxt,anthropic,data]'` (or the `openai`/Groq extra), then `tra init my-desk --profile autonomous --agent groq`, put the key in `.env`, `tra check`, `tra run`. Python ≥3.11, no GPU. Keep it in sandbox/paper mode; review the code before any venue mode.
- Valuable as a reference design even if you never trade with it: deterministic cost gate (fees, spread, impact, funding, slippage priced before an order), conviction ladder sizing, fail-closed kill switch, a "kill ledger" of rejected ideas, append-only decision records, and an MCP server exposing the gates.
- Effort: an hour to install and run in sandbox; days to adapt a strategy core. Data via ccxt (free public endpoints). Compare with TradingAgents (verified in batch 1), which is more of an LLM-debate research demo and has no comparable cost/risk gates.

**Second-brain relevance:** LOW – Not a memory system, but it has a good **decision-journal** layer: every cycle's snapshot, briefs, agent answers, intent, venue reply and every refusal are kept on disk with reasons, plus a ledger of killed ideas and auditors that read those records. It is self-hostable, and `tra mcp serve` exposes read-only tools over MCP, so other agents could query its gates/records. For a lab-wide brain, ship those records (they are files) into the shared store (gbrain or hindsight from batch 1) rather than treating this as the memory layer.

---

## V14 | Understand-Anything: open-source Claude Code plugin that turns a codebase into an interactive knowledge graph and dashboard
- **Source:** Dropbox video V14 (VID_20261018_121201_672.mp4)
- **Account:** @charlieautomates · **Type:** video (67s, no audio track; burned-in captions read frame by frame at 4 fps)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – a real, MIT-licensed, very active plugin that works with Claude Code and many other agents. It is useful for understanding the many repos you are cloning into the lab, and it can also graph a Markdown wiki.

**What it says:** The banner reads "#1 REPO TODAY (NOBODY'S TALKING ABOUT IT)". The captions, reconstructed: "This free tool can turn any Claude project into a brain that anybody [can] understand. It is quite literally the number one repo of the day with over 200,000 people currently using it to turn their code bases into an interactive knowledge base that can help you learn what the heck is going on. This is by far the most underrated tool of 2026 so far, because most of us are building applications with Claude Code and have no idea how they're even built. Understand Anything will demystify the entire codebase for you and even give you a guided tour about the infrastructure itself. You can click any component inside of the graph to see what's actually going on behind the scenes. To install it yourself, there are two steps: grab this command on the repo, give it to Claude and click enter. After Claude adds it, we install it with this command, hand it to Claude, click enter. Then all you do is type in /understand-anything [:understand], then drag the project in that you wanna brain for, and just like that you're gonna have a local dashboard set up like this so you can start to understand what's going on. If you want to try this out for yourself… just comment CLAUDE."

The screen shows:
- The GitHub README: "Understand Anything — Turn any codebase, knowledge base, or docs into an interactive knowledge graph…", "An open-source project from Egonex, Originally created by Lum1104", a "GitHub Trending #1 Repository Of The Day" badge, an MIT license badge, and the line "You just joined a new team. The codebase is 200,000 lines of code."
- Quick Start: `/plugin marketplace add Egonex-AI/Understand-Anything`, `/plugin install understand-anything`, `/understand`.
- Claude Code v2.1.201 (Opus 4.8 1M context, Claude Max) running `/understand-anything:understand`.
- His VS Code workspace "Charlieautomates/apps" (ai-slop-landing, carousel-dashboard, Casegate V2, ccstrategic-main, charlie-command-center, charlie-os-dashboard with a `.understand-anything` folder).
- The dashboard for "charlie-os-dashboard": layer graph (Project Configuration, API Routes, Data Layer, Middleware & Session Auth, Service & Integration Layer, UI Pages), a "Project Tour" with 13 steps, and file nodes (workflows.ts, hermes.ts) with summaries.

**What's actually behind it:**
- https://github.com/Egonex-AI/Understand-Anything (the old URL https://github.com/Lum1104/Understand-Anything resolves to the same HEAD `f2d0164`, so the repo was transferred)
  - License: MIT (© 2026 Yuxiang Lin; © 2026 Infinite Universe, Inc.).
  - Status: very active. Last commit 2026-10-12, PR numbers above #720. TypeScript/pnpm monorepo: `understand-anything-plugin/` with packages core, dashboard, viewer, plus tree-sitter WASM. About 34 MB checkout. The star count is not visible in the video; third-party listings say about 15k–21k+ (unverified).
  - What it does:
    - Tree-sitter extracts structure deterministically (imports, definitions, calls). LLM agents (project-scanner, file-analyzer, architecture-analyzer, tour-builder, graph-reviewer, plus domain-analyzer and article-analyzer) add summaries, layers, business-domain flows and guided tours.
    - The output is `.ua/knowledge-graph.json`, shown in a local Vite/React dashboard.
    - Commands: `/understand`, `/understand-dashboard`, `/understand-chat`, `/understand-diff`, `/understand-explain`, `/understand-onboard`, `/understand-domain`, `/understand-knowledge <wiki>` (Karpathy-style LLM wiki → force-directed graph), and `/understand-figma`.
    - Incremental re-runs and a `--auto-update` post-commit hook.
    - Installers for Codex, OpenCode, Gemini CLI, Cursor, Copilot, Hermes, Cline, Kiro and others.
    - A standalone viewer: `npx …/understand-anything-viewer.tgz <project>` needs no LLM.

**Verification:**
- Read all eight contact sheets, plus a 4 fps caption-band montage (268 frames) to recover the full captions.
- Ran `git ls-remote` on both URLs (same HEAD) and a shallow clone into `scratchpad/repos/Understand-Anything`.
- Read the LICENSE and the README (install, pipeline, sharing, viewer) and checked git log dates.
- Inspected `hooks/hooks.json` and grepped for telemetry/analytics (none found in the plugin source) and for an MCP server (none). Not executed.
- Could not verify: the star count, the "#1 repo of the day" badge date, or "200,000 people using it".

**Claims vs reality:**
- "Free tool": **true** (MIT). But `/understand` burns LLM tokens; the README warns the first run "can consume a significant number of tokens on large projects". It is free only if you have a subscription or a local model (Ollama is supported).
- "#1 repo of the day": the README shows a GitHub-Trending #1 badge. That is plausible for some day, not necessarily the day of the video.
- "Over 200,000 people currently using it": **unsupported.** It looks like a mix-up with the README's "codebase is 200,000 lines of code".
- "Turn any Claude project into a brain": it builds a **code-structure knowledge graph** plus summaries. It is a code-understanding map, not a persistent agent memory.
- "Two steps to install": **true** for Claude Code (marketplace add, plugin install, `/understand`).
- "Nobody's talking about it": marketing. Better Stack made a walkthrough video, and it is listed on many directories.

**Agenda:** A "comment CLAUDE" DM funnel for an automation-content brand (his workspace shows a carousel-dashboard and "ai-slop-landing" projects). The repo itself is legitimate. The homepage links to Egonex.ai ("An AI that gets to know you"), the company now backing the project, which has its own commercial angle.

**Lab use:**
- Install in Claude Code: `/plugin marketplace add Egonex-AI/Understand-Anything`, then `/plugin install understand-anything`, then `/understand` inside a repo, then `/understand-dashboard`.
  - For other agents: clone the repo and run `install.sh <platform>`. Pipe-to-bash installs are offered, but read the script first.
- Needs: Node ≥ 18 and pnpm (for the dashboard), plus LLM tokens. No GPU, unless you point it at a local model.
- Great for onboarding into the big quant repos you clone (NautilusTrader, Qlib, OpenBB, Vibe-Trading). Use `/understand src/<subdir>` on huge monorepos to limit token spend. Commit `.ua/` (minus `intermediate/` and `diff-overlay.json`) so other machines can view the graph without re-running.
- Watch out: the SessionStart hook tells Claude to re-analyse a stale graph without asking ("Do not ask the user for confirmation"). This only happens when `autoUpdate` is true, but it means silent token spend, so leave auto-update off on big repos.
- Effort: 30 minutes to install and try on one repo.
- Open-source alternatives or complements:
  - Aider's repo-map (tree-sitter, no LLM cost)
  - code-graph MCP servers
  - CodeQL or Sourcegraph for deterministic code navigation

**Second-brain relevance:** MEDIUM
- Layers covered: **capture/ingest** (code and also Markdown wikis via `/understand-knowledge`), **storage** (one JSON knowledge-graph file per project in `.ua/`, git-committable), **retrieval** (fuzzy and semantic search in the dashboard, `/understand-chat`) and **consolidation** (LLM summaries, tours, domain flows).
- It is fully self-hostable and local.
- Cross-machine sharing works only through git (commit `.ua/`), and the read-only viewer can be served on the LAN.
- It has **no MCP server or network API**, so other agents and VMs can't query it live. It is a per-repo code atlas, not a lab-wide memory.
- Use it as a feeder: export the graph JSON into your real second-brain store, such as GBrain (verified batch 1; Postgres/pgvector plus HTTP MCP, built for multi-agent use) or a Karpathy-style Markdown wiki that `/understand-knowledge` can then visualise.

---

## V18 | "3PO / Threepio": a personal, self-built "self-learning AI quant" dashboard (local web app over an Obsidian-style vault of papers, a strategy factory, robustness gates and a risk gate), shown as a teaser with a "comment QUANT" funnel
- **Source:** Dropbox video V18 (VID_20261018_121341_182.mp4)
- **Account:** @astongilltrading (watermark on every frame and end card) · **Type:** video (82s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – nothing is downloadable, but the architecture on screen (research vault → strategy generator → OOS / Monte Carlo / walk-forward / deflated-Sharpe gates → paper → portfolio with a risk gate) is a sound blueprint for exactly the kind of lab the user is building, and the screens are unusually honest about results.

**What it says:** "I just finished coding an AI quant and it's self-learning." **3PO** "trains himself on quantitative trading". The "brain vault" is a particle/constellation graph: "every single dot is a research paper or a book he's actually read, and the lines are where the ideas connect". Running ~24 hours, he "goes online, finds papers and books… downloads them, reads them and cites them": **393 research items**. These feed a **Strategy Factory** that creates strategies; a **Strategy Star Map** shows tested strategies and correlations. Strategies go through "out-of-sample data, a screening, Monte Carlo tests, a walk-forward test, deflated Sharpe test" and, if they pass, a **demo account**. A **Portfolio** page swaps out underperformers, and a **Risk Gate** keeps everything within limits. A synthetic voice answers "3PO, say hi" (an ElevenLabs "Voices" tab is open). "I'm going to make a whole video about this… comment QUANT below and I'll send you a link."

On-screen details (crops of 1-fps frames):
- App runs at **localhost:5173** (a Vite dev server); browser tabs "Threepio — The Millennium F…", arXiv **2606.27462v1** ("The Decision Geometry of Covariance Estimation for the Global Minimum-Variance Portfolio under Heavy Tails", X. Fonseca), another arXiv tab "…FinM…", "Voices | ElevenLabs", "Settings – Microphone".
- Status bar: "CORE ONLINE · GATE ARMED · **LIVE OFF** · INCIDENTS 0 · MODE BACKTEST".
- **Knowledge base:** 393 research items, **839 vault notes**, 244 graveyard, 784 backtests. "Vault notes by folder": 00 Inbox, 05 Claude, 06 Strategies, 07 Backtests, 08 Trade Logs, 10 Strategy Graveyard, 11 Research Library, 13 Daily Brain…, 14 Portfolio Mgmt, 30 Knowledge. "Research by source": mostly arXiv (q-fin) and GitHub. Note "Grouping is by folder / source / tier / strategy-family – real structure, not a semantic topic map".
- Node tooltips: "2026-07-06 Multivariate volatility models [PS…]" (Research Library), "MOM 15m thr1 1R cut15-30 Mon-Thu" and "ORB 30m 1.5R cut12-00" (Strategy Graveyard), "2026-07-09 Portfolio Report".
- **Strategy Factory** ("breed · screen · gauntlet · bury or promote"): Generation 8, **survivors 6, buried 208**, "top screen P&L $9,312". Families: ORB breakout 82, gap fill 42, momentum ignition 60, ORB breakout 15. A "Lifecycle" page: "promotions past paper require a human"; "The Burial – every kill on record" with 244 buried; a kill ledger mostly "killed by deflated sharpe" or "killed by screen" (e.g. "GAP fade 5-40pt stop10 1.5R… KILLED BY SCREEN").
- **Portfolio HQ:** banner "**LABELED SYNTHETIC – SYNTHETIC PORTFOLIO – fewer than two strategies hold paper… screened over recorded training data (vectorbt, costs on, same harness as A3)**"; combined drawdown **−$2,188** vs a ruin line, combined equity over 253 common days; a correlation web "awaiting first data".
- **Risk Gate:** "fails closed – every order path passes through"; gate radar "eight rules · live verdicts"; active limits (max contracts, max trades per day, daily loss limit, trading window, news blackout minutes before/after, max pairwise correlation 0.7, max simultaneous positions, max combined drawdown); a verdict feed of paper orders (ORB 30m Breakout, entry/exit brackets) dated 05–06/07/2026.

**What's actually behind it:**
- No repo, product or URL is named. It is the creator's own local app (Vite front end on :5173), apparently driven by Claude (a "05 Claude" vault folder) over an Obsidian-style folder vault, backtesting with **vectorbt** (named in the banner), voice via **ElevenLabs** (paid TTS).
- The methods named are all real and standard: out-of-sample testing, Monte Carlo resampling, walk-forward analysis, and the **Deflated Sharpe Ratio** (Bailey & López de Prado, 2014), which corrects for the number of trials. Using DSR as the kill criterion across 200+ generated strategies is the right instinct.
- The strategies themselves are intraday futures-style setups (opening-range breakout, gap fill/fade, momentum ignition), with R-multiple exits and time cutoffs.

**Verification:** Viewed all 11 contact sheets; cropped/upscaled frames of the factory, knowledge base, lifecycle, portfolio banner, risk gate and browser tabs. Fetched arXiv 2606.27462 to identify the open paper. Web search for "astongilltrading" found nothing (results were about an unrelated "Mike Aston" course). The app, its code, its data sources and the "self-learning" loop could not be inspected; nothing to clone.

**Claims vs reality:**
- "Self-learning AI quant": in practice an LLM-driven research pipeline (fetch papers → write notes → generate strategy variants → backtest → filter). It does not learn weights; "learning" = growing a notes vault and a graveyard of rejected strategies. That is fine, but it is not a self-improving trader.
- "Every dot is a paper or book he's actually read": 393 items in 24 h means automated download + LLM summarisation. "Read" = summarised; quality of those summaries is unknown. The dashboard itself says the grouping is by folder/tag, "not a semantic topic map", so the "connections" are structural links, not discovered ideas.
- "Strategy factory creates strategies using what he learned": the visible strategies are standard ORB/gap/momentum templates with parameter sweeps; 208 of 214 buried. The 6 survivors' "top screen P&L $9,312" is an in-sample screen figure.
- "Passes OOS, Monte Carlo, walk-forward, deflated Sharpe → demo account": consistent with the screens (paper orders on the risk-gate feed, "LIVE OFF"). No live or paper P&L is shown.
- "Manages a portfolio of profitable strategies": the screen itself says the portfolio is **SYNTHETIC** because fewer than two strategies are on paper, built from recorded training data, and it shows a **−$2,188** combined drawdown. So no profitable portfolio exists yet. Credit to the app for labelling it honestly; the voice-over overstates it.

**Agenda:** "Comment QUANT for more info" DM funnel; "I'll make a whole video about this". Likely building toward a course, community or paid access. Nothing for sale is shown in the clip.

**Lab use:** Rebuild the architecture with open-source parts on the lab server:
- **Research ingest:** arXiv API (q-fin) + Semantic Scholar/OpenAlex for metadata; PDF → markdown with **MinerU** (verified in batch 1); Claude Code writes one note per paper into a markdown vault (claude-obsidian conventions, verified in batch 1).
- **Strategy factory:** templated strategies (ORB, gap, momentum) generated as parameter grids; backtest with **vectorbt** (free open-source version) or NautilusTrader (verified in batch 1) with costs on; log every trial.
- **Gates:** hold-out OOS, walk-forward, Monte Carlo trade resampling, Deflated Sharpe / PBO with the number of trials counted honestly (e.g. via `skfolio`/own code; mlfinlab-style functions are easy to write).
- **Lifecycle + risk gate:** a small state machine (candidate → screened → paper → human-approved live) and a fail-closed pre-trade check (max contracts, daily loss, news blackout, correlation cap) – exactly as shown.
- Dependencies: Python, an LLM API key (Claude) for summarising papers, intraday futures data (paid unless you use free crypto data). No GPU required. Effort: 1–2 weeks for an MVP without the sci-fi UI.

**Second-brain relevance:** MEDIUM – The "brain vault" is a concrete example of a quant-specific second brain: capture/ingest (auto-downloaded papers), storage as **markdown notes in numbered folders** (Inbox, Claude, Strategies, Backtests, Trade Logs, Graveyard, Research Library, Daily Brain, Portfolio, Knowledge) with counts and links, and a dashboard over it. It appears self-hosted (localhost) but single-user and single-app; there is no sign of network/MCP access for other agents or VMs, and retrieval is folder/tag-based, not semantic. The folder taxonomy and the "graveyard of every killed strategy with its reason" are worth copying. To make it shareable across VMs and agents, put the same markdown vault in git and index it with **gbrain** (garrytan/gbrain, MIT, verified in batch 1, Postgres+pgvector, MCP) or **hindsight** (vectorize-io/hindsight, MIT, verified in batch 1, network API + Claude Code plugin), with claude-obsidian (AgriciDaniel/claude-obsidian, MIT) as the note-writing conventions.

---

## V15 | "Strategy that rewrites itself": Claude Code backtest–critique–rewrite loop with a failed/ archive and read-only risk limits
- **Source:** Dropbox video V15 (VID_20261018_121215_646.mp4)
- **Account:** @jack_gpt_ · **Type:** video (55s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – a sensible agent-loop design (plain English → code → 5-year backtest → second agent diagnoses losing trades → rewrite → archive failures → hard-locked risk file → unseen holdout) that you can build in an afternoon with Claude Code. Nothing is published, and the loop is an overfitting machine unless you guard the holdout.

**What it says:** "There's a trading setup where AI rewrites its own strategy every time it loses money and you never write a line of code yourself… including the one thing you never let AI touch." The steps:
1. Describe the idea in plain English; Claude turns it into code.
2. Test it against five years of market data.
3. If the result is red, a second agent finds the exact losing trades and rewrites the entry and exit (not the whole strategy), then re-tests.
4. Every failed strategy gets saved, "so the next version can see what went wrong and doesn't make the same mistake twice."
5. Never hand over risk: the stop loss and max drawdown are hard-coded before real money "so the agent can't talk itself out of them."

He says "I've been trading for over 10 years". The ending reads "This isn't financial advice… Comment QUANT and I'll send you the full workflow and setup guide."

The animated illustrations show:
- A "Welcome to Claude Code!" terminal in `~/quant` with the prompt `> buy when it's trending up`
- `Write(strategy.py)` producing `from risk import *` / `def entry(c): return c > trend(c)` / `def exit(c): return c < prev(c)`
- `Bash(python backtest.py)` over a "5 years" span
- "Agent 2" with a magnifier over red losing-trade bands
- `Update(strategy.py)` diff: `- return c > trend(c)` / `+ return vol > avg(vol)`; `- return c < prev(c)` / `+ return c < low(c)`
- Versions v1→v2→v3 with a `failed/` folder holding v1 and v2 thumbnails
- `risk.py` with `STOP_LOSS = set_by_you()` and `MAX_DRAWDOWN = set_by_you()` behind a lock icon
- `Update(risk.py)` → "Error: risk.py is read-only"
- A final "Unseen" shaded segment at the end of the chart (out-of-sample)
- "Not financial advice", then a "QUANT" comment box with a reply from "Jack: Full workflow / Setup guide"

**What's actually behind it:**
- **No repo, product or tool name** apart from Claude Code. The visuals are motion-graphics illustrations, not a real session (code is pseudo-code, e.g. `trend(c)`).
- Real open-source projects that implement this loop properly:
  - https://github.com/microsoft/RD-Agent
    - License: MIT. v1.0.0 released 2026-09-23.
    - **RD-Agent(Q)**: a multi-agent factor/model propose → implement → backtest (Qlib) → feedback loop with an experiment-history "knowledge" store. NeurIPS 2025 paper arXiv:2505.15155. `rdagent fin_quant`. Needs an LLM API and Docker.
  - https://github.com/HKUDS/Vibe-Trading (verified in batch 1, MIT): a "self-improving trading agent" with backtests and persistent memory.

**Verification:** I viewed all seven contact sheets and read the code and diff overlays. I ran `git ls-remote` and a shallow clone of microsoft/RD-Agent (MIT; README describes the quant self-loop) to name a real implementation. Vibe-Trading was reused from batch 1. The "full workflow and setup guide" behind the DM could not be seen. The "10 years trading" claim is unverifiable.

**Claims vs reality:**
- "AI rewrites its own strategy every time it loses money": the mechanism is real and buildable. But rewriting entries and exits specifically around the losing trades of the same backtest is **in-sample curve fitting**. Each iteration raises the backtest score and lowers the odds it holds out of sample (multiple-testing bias).
- "Tests against five years of data before you risk a cent": good. But five years on one market is one regime sample, and fees and slippage are not mentioned.
- "Failed strategies get saved so it doesn't repeat mistakes": a good practice (an experiment log). It also makes overfitting worse if the agent learns to dodge specific historical trades. The failures must record why they failed (hypothesis, metric, regime), not just which trades lost.
- "Risk is hard-coded and the agent can't touch it": **the best part.** A file marked read-only in a prompt is not a guarantee, though. Enforce it with Claude Code permission deny rules (`Edit(risk.py)`), OS file permissions (`chmod 444`, a different owner), or a pre-tool-use hook, and enforce limits again in the execution layer or broker (max position, daily loss kill switch).
- The "Unseen" segment at the end is the right instinct (a holdout). But each time you look at it and iterate, it stops being unseen. Lock a final test period and touch it once.
- "You never write a line of code": true for the generation step. You still need to read the code to catch look-ahead (e.g. `low(c)` using the current bar's low for an exit decided on that bar).

**Agenda:** A "comment QUANT" DM funnel ("full workflow and setup guide"), from an AI and trading education account. Likely list building toward a paid community or course. The content is better than average: it pushes testing and risk locks rather than P&L screenshots.

**Lab use:**
- Build it yourself in Claude Code:
  - `~/quant/` with `data/` (5+ years of bars), `backtest.py` (vectorbt, backtesting.py or NautilusTrader, with commissions and slippage), `strategy.py`, a read-only `risk.py`, and `experiments/` (one folder per version: code, params, metrics, equity curve, a "why it failed" note).
  - A `CLAUDE.md` describing the loop.
  - A second subagent ("critic") that reads the trade log and proposes **one** hypothesis-level change per iteration.
- Guards:
  - `.claude/settings.json` deny rules for `Edit(risk.py)` and `Edit(data/**)`.
  - Train / validation / locked-test split, or walk-forward and CPCV (skfolio has CombinatorialPurgedCV).
  - Count iterations and apply a deflated-Sharpe or other multiple-testing haircut.
  - Cap the iteration count.
- Dependencies: Python, pandas, a backtest library, Claude Code (subscription). No GPU.
- Effort: about 1 day for the loop, plus ongoing.
- Off-the-shelf OSS: microsoft/RD-Agent (Qlib-based, heavier, best for cross-sectional factor research) or Vibe-Trading.

**Second-brain relevance:** MEDIUM
- The `failed/` archive is a concrete, useful memory pattern: an **experiment memory** that feeds past failures back into the agent's context so it doesn't repeat them (capture → markdown or JSON storage → retrieval at prompt time). As shown, it is just a local folder plus prompt instructions: self-hostable but single-project, with no cross-agent sharing.
- To make it lab-wide, store each experiment as a structured record (hypothesis, code hash, data window, metrics, verdict, lesson) in a shared store that every agent can query over MCP. Options: GBrain (verified batch 1; Postgres/pgvector, HTTP MCP) or MLflow tracking server for metrics plus a Markdown lessons page.
- RD-Agent's built-in experiment-history knowledge base is the open-source reference implementation of this idea.

---

## V30 | Karpathy's "autoresearch" keep/discard agent loop (700 experiments, 20 improvements), retold as "4 guardrails", with a misattributed "Karpathy 12-page guide", to sell an AI challenge
- **Source:** Dropbox video V30 (VID_20261018_121741_880.mp4)
- **Account:** @itsmariahbrunner (watermark) · **Type:** video (78s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – the real thing (karpathy/autoresearch, MIT, ~1k lines) is a clean pattern for unattended agent experimentation that can be adapted to strategy or feature research on the lab server. The video's framing is partly wrong, and in a quant setting the loop must be guarded against backtest overfitting.

**What it says:** "Andrej Karpathy, one of the people who first started OpenAI, just dropped a 12 page guide on building self-improving AI systems." In one experiment "he built an AI system and then walked away for two days and it ran 700 experiments and found 20 real improvements. And then it kept making itself better without a human touching it."

Four reasons, each with an overlay:
- **"01 outcome, not rules":** "it could judge its own work… every change had a score… if it got better it stayed, if it didn't it got thrown away".
- **"02 Undo Button":** every change was reversible.
- **"03 Tiny Steps":** one small improvement at a time, "not one giant prompt".
- **"04 Strict Boundaries":** it could only change one part of the system.

Close: "The future of AI isn't just giving it more freedom, it's giving it better guardrails. Comment GUARDRAILS… free agent guardrails template… my AI challenge. Cohort 3 starts on August 10th… link in bio, or comment CHALLENGE."

On screen:
- An X post by **0xMarioNawfal (@RoundtableSpace)**: "ANDREJ KARPATHY JUST RELEASED A 12-PAGE GUIDE ON BUILDING SELF-IMPROVING MULTI-AGENT GRAPHS". The document cover reads "The Complete Playbook – Andrej Karpathy – From 1 Loop to 1,000 Agents – The Graph Engineering Manual – Synthesized from Karpathy's autoresearch, AgentHub, Sequoia AI Ascent 2026 talk, and Anthropic's Knowledge Graph Construction Cookbook – **Independently compiled, July 2026 – not affiliated with Andrej Karpathy and Anthropic – and not endorsed**". Its diagram shows entity types Person / Object / Agency-Group / Text.
- A Fortune headline, March 17 2026, by Jeremy Kahn: "'The Karpathy Loop': Former OpenAI researcher's autonomous agents ran 700 experiments in 2 days—and gave a glimpse of where AI is heading".
- Excerpts from the playbook PDF:
  - "VIII. Decision Framework – A. Six Selection Questions – 1. Can success be verified? If not, do not begin with autonomy. Define a test, rubric, source requirement, or human decision."
  - "TABLE VI Production Checklist": Objective / Metric / Reversibility, each with "Ask yourself" and "Failure if missing".
  - "Autoresearch… exposes a small single-GPU training setup and asks an agent to make one change at a time… core code as roughly 630 lines… about 700 experiments in two days, retaining approximately 20 useful optimizations [1], [10]".
  - "4) The environment is bounded. The repository narrows the action space."
- Stock UI clips of OpenAI Codex and a Claude-style coding-agent screen ("acme/order-service", "Opus 4.5").
- Her "GUARDRAILS" lead-magnet page (source link "Fortune: Andrej Karpathy's autonomous agent loop"; "THE AGENT GUARDRAILS").
- Her sales site "Build AI systems that run your work, business, and life" ("Round 1 and Round 2 filled up fast", "20+ specialized agents", "Cohort 3 starts August 10th").

**What's actually behind it:**
- **https://github.com/karpathy/autoresearch**
  - License: MIT (README). Last commit 2026-03-25 (merged PRs).
  - Contents: `prepare.py` (389 lines, fixed data/tokenizer/eval), `train.py` (630 lines, the only file the agent edits), `program.md` (agent instructions).
  - How the loop works: the agent creates a git branch, edits `train.py`, commits, runs a fixed 5-minute training job, and reads `val_bpb`. If it is better it keeps the commit; otherwise `git reset`. It logs every run to `results.tsv` (commit, val_bpb, memory, keep/discard/crash, description) and repeats indefinitely. There is also a "simplicity criterion" for weighing complexity against gain.
  - Requires a single NVIDIA GPU (tested on H100); forks exist for macOS/MLX, Windows and AMD.
- **Fortune, 2026-03-17 (Jeremy Kahn)**: confirms the agent ran ~700 experiments over two days and found ~20 optimisations, which gave about an 11% training speed-up when applied to a larger small model. A Fortune listing subtitle says the agent **did not improve its own code**; it improved a model's training script.
- **"12-page guide"**: a third-party compilation. The cover itself says "not affiliated with Andrej Karpathy… and not endorsed". It was amplified by 0xMarioNawfal's post with a false headline.
- **learnaiwithmariah.com/challenge**: "The AI Challenge · Round 3", about $247 with a 7-day refund, plus a separate $49/mo community. Price is from a web search of the checkout page and is undated.

**Verification:**
- Viewed all 10 contact sheets.
- Cropped the X post and guide cover, the playbook excerpts and the guardrails landing page.
- `git ls-remote` and a shallow clone of karpathy/autoresearch into scratchpad/repos/autoresearch. Read the README (license MIT, design choices, platform support) and `program.md` (git commit/reset loop, results.tsv). Line counts checked. Not executed.
- Web search confirmed the Fortune article and the challenge pricing.
- Could not read the full 12-page PDF or her guardrails template (behind the comment funnel).

**Claims vs reality:**
- "Karpathy just dropped a 12-page guide": **false attribution.** The PDF is an independent compilation that explicitly disclaims affiliation and endorsement. The real primary sources are the autoresearch repo and Karpathy's posts.
- "700 experiments, 20 real improvements in two days": true (Fortune and the playbook both cite it).
- "It kept making itself better without a human touching it": misleading. The agent tuned a separate small LLM's `train.py` against a fixed metric. It did not modify itself, and a human wrote and iterates on `program.md`.
- The four "rules" are an accurate paraphrase of autoresearch's design: a single verifiable metric (val_bpb), git-based revert, one change per 5-minute run, and only `train.py` editable. These are sound and well-known agent-safety practices, not secrets.
- "Self-improving multi-agent graphs" (X headline): not what autoresearch is. It is a single agent in a single loop.

**Agenda:**
- "Comment GUARDRAILS" lead magnet.
- "Comment CHALLENGE" / link in bio for a paid cohort course (about $247, Cohort 3) and a $49/mo community.
- She borrows Karpathy's name and a viral misattributed post for reach.

**Lab use:**
- Adapt the autoresearch pattern to the quant lab (1–3 days):
  - Give Claude Code (headless, `claude -p` in a loop or a tmux session) a `program.md` and one editable file, e.g. `features.py` or `strategy.py`.
  - Keep a frozen `evaluate.py` that runs a walk-forward backtest with costs and prints one metric.
  - Use git branch + commit + reset for undo, a fixed per-run time budget, and an append-only `results.tsv`.
- Quant-specific guardrails that the video omits:
  - An agent running 700 backtest variants is a multiple-testing machine. Hold out a final untouched test period the agent never sees.
  - Score with the deflated Sharpe ratio or a penalised metric. Log the trial count. Re-validate kept changes on CPCV (skfolio).
  - Run in a container with no network or broker credentials.
- Running Karpathy's original needs a CUDA GPU (H100-class ideal; smaller GPUs need the README's down-scaling tips or a fork). The quant adaptation needs only CPU, plus your LLM subscription or API costs.
- The paid challenge is unnecessary: the repo plus its `program.md` is the whole method.

**Second-brain relevance:** LOW –
- What it covers: two small memory layers. An append-only experiment log (`results.tsv` plus git history of kept and discarded changes) acts as consolidation/provenance, and `program.md` is agent context injection, a lightweight "skill" file.
- Hosting: both are plain files, so they are self-hostable and shareable across VMs via git.
- What it is not: a memory system. There is no search, no cross-project index and no multi-agent API.
- How to use it: write every autonomous run's `results.tsv` and its summary into the lab's second brain (e.g. GBrain or Hindsight, verified in batch 1, over MCP), so future agents can query "what has already been tried and failed" before proposing experiments. That is the part that turns this loop into compounding memory.
- The "knowledge graph" cover diagram (Person/Object/Agency/Text) comes from the compiled playbook, not from Karpathy, and nothing in the video implements it.

---

## V17 | "Build a mini Bloomberg Terminal for free": yfinance + SEC EDGAR + FRED + Yahoo headlines scored by FinBERT, wired together by Replit Agent into an "Atlas Research Terminal"
- **Source:** Dropbox video V17 (VID_20261018_121317_593.mp4)
- **Account:** @chrispathway (watermark on every frame and end card; Replit greets the user as "Christian") · **Type:** video (44s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – the four free data sources are exactly the right baseline stack for a personal research terminal and are all verifiable open-source/public data; the Replit part is optional and replaceable by Claude Code on your own server.

**What it says:** "A Bloomberg Terminal costs around $30,000 per year, but you can build your own mini version with completely free data." Four parts: 1. **Market data** (price, volume, charts) with the Python library **yfinance**; 2. **Fundamentals** (earnings, balance sheets) from the SEC's **EDGAR** database (the transcript mishears it as "AdGuard"; the screen shows the EDGAR full-text search page); 3. **Macro data** (rates, inflation) from **FRED** (screen shows the FRED CPI series); 4. **News**: Yahoo Finance headlines plus the open-source model **FinBERT** for sentiment (screen shows the Hugging Face page **ProsusAI/finbert**, 1.27k likes, ~4.3M downloads last month, license tag cc-by-nc-sa-4.0, arXiv 1908.10063). "Wiring all of that together takes forever", so he described it to **Replit** and it built the terminal. On-screen: Replit Agent says "I'll build Atlas Terminal as a web app with FastAPI, PostgreSQL caching, and the six tabs in your brief. I'll preserve the real-data-only rule, show source failures explicitly, and report the metric tests and yfinance cross-check before deployment. SEC requests will also need a real contact email for their required User-Agent header." The result: "ATLAS RESEARCH TERMINAL", amber-on-black Bloomberg style, command line "AAPL MKTS> AAPL FA <GO>", tabs **F1 MKTS, F2 QUOTE, F3 FA, F4 RISK, F5 NEWS, F6 ECO**, a "SNAP CACHED / DELAYED" status, a universe watchlist with a correlation heatmap, fundamentals bar chart, news list and an AAPL price chart (340.97). Ends: "Comment TERMINAL and I'll send you the link to Replit with a guide."

**What's actually behind it:**
- **yfinance** – https://github.com/ranaroussi/yfinance · Apache-2.0 · cloned, last commit 2026-10-18. Unofficial scraper of Yahoo Finance; free, but rate-limited, sometimes breaks, and Yahoo's terms restrict use to personal purposes.
- **SEC EDGAR** – https://www.sec.gov/edgar · free public filings and XBRL "companyfacts" JSON API; requires a descriptive User-Agent with contact email (Replit's message is correct). Good Python wrapper: **edgartools** https://github.com/dgunning/edgartools · MIT · cloned, last commit 2026-10-18.
- **FRED** – https://fred.stlouisfed.org · free API key; Python wrapper `fredapi` (https://github.com/mortada/fredapi, repo exists) or `pandas-datareader`.
- **FinBERT** – code at https://github.com/ProsusAI/finBERT · Apache-2.0 · cloned, last commit 2026-10-12. Model weights at https://huggingface.co/ProsusAI/finbert, tagged **cc-by-nc-sa-4.0 (non-commercial)** per the HF API (1,280 likes, ~4.1M downloads, modified 2026-10-12). BERT fine-tuned on Financial PhraseBank (Araci 2019, arXiv 1908.10063); 3-class positive/negative/neutral. Runs on CPU.
- **Replit Agent** – https://replit.com · closed, paid SaaS (free tier limited; Agent usage is billed by effort/credits). It generated a FastAPI + PostgreSQL app; the code is not public.
- **Bloomberg Terminal price** – roughly $25–32k per seat per year; "$30,000" is a fair round number.

**Verification:** Viewed all 6 contact sheets; cropped the HF page, the Replit prompt screen, the Replit Agent plan text and the finished terminal header/tabs. `git ls-remote` + shallow clone of yfinance, edgartools and ProsusAI/finBERT (licenses read); `ls-remote` of fredapi; Hugging Face API for the FinBERT license and stats. Web search on @chrispathway found a CreatorDB profile (Germany-based, ~308K followers, AI/finance/student content, claims ETH Zurich statistics master's), not independently verified. The Replit app and its "guide" were not accessible, so data quality, metrics and the "six tabs" logic are unverified.

**Claims vs reality:**
- "Build your own mini Bloomberg with completely free data": true for a *mini* version for personal research. Missing vs Bloomberg: real-time/tick data, bonds/FX/options depth, news wire speed, chat, analytics depth, data licensing for redistribution.
- "Fundamentals straight from EDGAR": true, and better than Yahoo's fundamentals, but XBRL tags are messy; standardising them is the real work (edgartools helps).
- "FinBERT gives you the sentiment score": true; it is a 2019 model, decent on headlines, weak on nuance, and its predictive value for returns is small and decays fast. Licence of the weights is non-commercial.
- "Replit built my own terminal": plausible from the screens (a real-looking working app), but you are renting it on Replit; for a self-hosted lab, Claude Code can build the same thing locally.

**Agenda:** "Comment TERMINAL" DM funnel to a Replit link + guide; very likely a Replit sponsorship/affiliate (Replit referral links pay creators). Otherwise the content is honest and educational.

**Lab use:**
- Build it on the lab server with Claude Code instead of Replit: `pip install yfinance edgartools fredapi transformers torch fastapi sqlalchemy psycopg` (or DuckDB/Parquet instead of Postgres). FinBERT via `transformers.pipeline("text-classification", model="ProsusAI/finbert")` on CPU (~440 MB).
- A cron job pulls daily OHLCV (yfinance), quarterly facts (EDGAR companyfacts), macro series (FRED), and headlines; store in DuckDB/Postgres; a FastAPI or Streamlit front end gives MKTS/QUOTE/FA/RISK/NEWS/ECO tabs. Effort: 1–3 days for a solid MVP.
- Ready-made open-source alternative: **OpenBB** (verified in batch 1, https://github.com/OpenBB-finance/OpenBB, Apache-2.0 per its LICENSE, last commit 2026-10-17) already wraps yfinance, SEC, FRED and news providers behind one Python API.
- No GPU needed; the only key is a free FRED API key.

**Second-brain relevance:** LOW – It is a data warehouse, not a memory system: capture/ingest of market, filings, macro and news into one Postgres DB. That said, the same pattern (scheduled ingest → one shared database → API) is how a lab-wide market-data layer should look, and exposing it through an MCP server or FastAPI would let every agent/VM query the same data. Not a substitute for notes/agent memory (see batch-1 options: gbrain, hindsight, claude-obsidian).

---

## V05 | Soup (soup-cli): an open-source one-YAML LLM fine-tuning CLI whose "layer streaming" LoRA-trains an 8B model in about 3.3 GB of VRAM
- **Source:** Dropbox video V05 (VID_20261018_115919_700.mp4)
- **Account:** @forcceee_ (watermark and end card) · **Type:** video (69s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – a real, Apache-2.0, very actively developed tool that lets a small GPU fine-tune 7–8B models. It is useful if the lab ever fine-tunes models on its own text or data, though it is not core to quant research.

**What it says:** A narrator (with stock footage of data centres, keyboards and a Guy Fawkes mask) says "a solo dev from Kazakhstan, Alpamys Makazhan" built "Soup" (the transcript mishears it as "SUP"). Fine-tuning "used to require expensive cloud GPUs, custom scripts and days of debugging"; Soup does it "with one YAML config and one command" (`soup train`). It handles batch size, memory and LoRA adapters. "The secret is layer streaming": an 8B Llama "normally needs 16 gigs of VRAM", and Soup "cuts that to 3.3 gigs by loading one layer at a time." "Someone ran it on a 4 GB laptop GPU... 119 tokens per second. It blew up on Hacker News. It's fully open source."

On-screen text: the Soup site ("Featured on Product Hunt 103", "678 stars", "83.8k downloads", "v0.73.0", "Apache-2.0 License", "Python 3.10 to 3.12", "No vendor lock-in", `pip install "soup-cli[train]"`, `soup init`), a YAML config (`base: meta-llama/Llama-3.1-8B-`, `task: sft`, `# backend: unsloth # 2-5x faster`, `data: train: ./data/train.jsonl, format: alpaca, val_split: 0.1`), `soup migrate --from unsloth notebook.ipynb --dry-run` output (base `unsloth/Meta-Llama-3.1-8B`, `quantization: 4bit`), a VRAM bar "Llama-3.1-8B-Instruct, LoRA, batch 1, seq 512 · RTX 3050 Laptop, 4 GB VRAM · Peak 3.32 GB. It stops short of 4.00", "119.6 tok/s · GPU utilisation 100% · 3.60 GB RAM store, page locked", release-note text ("streamed: 119.6 tok/s... 3.32 GB on an H100", "models above ~165 MiB per layer... gradient checkpointing could not see it, so... gradients were wrong. Repaired and gated", "real 72B (320/320...)"), and the GitHub README.

**What's actually behind it:**
- **Soup**: https://github.com/MakazhanAlpamys/Soup, PyPI `soup-cli`. **Apache-2.0** licence. The repo exists (`git ls-remote` OK). Last commit 2026-10-19, so it is extremely active, with many outside contributors. It is a substantial codebase (about 1,590 Python files: `src/`, `tests/`, `benchmarks/`, `docs/`, `examples/`, Dockerfile). It wraps Hugging Face / PEFT-style training (SFT, DPO, GRPO, KTO, ORPO, SimPO per web sources) behind a YAML config. It can migrate Unsloth notebooks, has an optional Unsloth backend, and adds "layer streaming": the NF4-quantised base weights stay in pinned system RAM and are fed to the GPU one decoder layer at a time.
- The README's own wording of the headline benchmark: "Measured on an RTX 3050 Laptop 4 GB: Llama-3.1-8B-Instruct + NF4 at 119.6 tok/s at 952 MHz, 3.32 GB peak (pre-repair) — bit-exact against a normal resident run, and reproduced independently on an H100 at 113.00 tok/s in the same 3.32 GB." Both figures pre-date the v0.73.0 correctness repair (cost −4.8% at 32B); a post-repair 3050 run reads 208.6 tok/s at 2.40 GB with a different clock, which the README says is "not directly comparable".
- Author: GitHub user MakazhanAlpamys (Alpamys Makazhan). A Peerlist project page and a Product Hunt launch exist (web search).

**Verification:** Viewed all 9 contact sheets and cropped the release-note frame. `git ls-remote` and a shallow clone into `scratchpad/repos/Soup`; read the LICENSE (Apache 2.0), README benchmark section and `git log`. Web search confirmed PyPI `soup-cli`, Product Hunt and the author. I did **not** verify the Hacker News claim or current star and download counts (on screen: 678 stars, 83.8k downloads; a web source says about 1.1k stars and 84k downloads at v0.73.0). No code was run.

**Claims vs reality:**
- "One YAML config and one command": true (`soup init` → `soup train`).
- "8B normally needs 16 GB of VRAM; Soup cuts it to 3.3 GB": misleading comparison. 16 GB is roughly bf16 *inference* weights. QLoRA fine-tuning of an 8B model in 4-bit already fits in about 6–8 GB with standard tools (Unsloth, bitsandbytes). Soup's streaming takes it to about 3.3 GB, which is a real but smaller gain than implied.
- "Someone ran it on a 4 GB laptop GPU and hit 119 tok/s": matches the README (RTX 3050 Laptop 4 GB). Note this is *training* throughput at batch 1 / seq 512, which is slow: a small dataset is fine, a large one will take a long time. The H100 reaching only 113 tok/s in the same setup shows the speed is limited by streaming over PCIe, not by the GPU.
- "Fine-tuning used to require days of debugging and most people gave up": exaggerated. Unsloth, Axolotl, LLaMA-Factory and TRL already offer config-driven fine-tuning.
- "Solo dev": originally yes; the repo now credits many contributors.
- "Fully open source": true (Apache-2.0).
- The release notes themselves admit a past gradient-correctness bug in layer streaming for large models (now "repaired and gated"), so pin versions and validate results.

**Agenda:** Tech-news engagement content with stock footage and no link or funnel in the clip. It is a free promotion of an open-source project.

**Lab use:**
- Install: `pip install "soup-cli[train]"` in its own venv (Python 3.10–3.12), then `soup init --template chat` and `soup train`. Data in JSONL (alpaca/chat format).
- Hardware: an NVIDIA GPU with CUDA. Layer streaming makes 4–8 GB cards usable for 7–8B LoRA; it needs enough system RAM for the quantised base (about 3.6 GB for 8B). No paid API is needed, but gated base models (Llama) need a Hugging Face token.
- Quant-lab uses: fine-tune a small model on your own research notes, trade logs or financial text (e.g. classifying news or filings), or distil an agent's outputs. Effort: an afternoon to set up, plus dataset preparation.
- Alternatives: Unsloth (Apache-2.0, fastest on a single GPU), LLaMA-Factory, Axolotl, Hugging Face TRL.

**Second-brain relevance:** LOW – Fine-tuning is a way to bake knowledge into model weights. That is the wrong tool for a personal memory that must be updated daily, inspected and shared, and retrieval over a store is far better for that job. It could later play a consolidation role: periodically distilling the brain's notes into a small local model that runs on a lab GPU and is served to all VMs (e.g. via vLLM or Ollama). It is self-hostable, but it is not a memory layer.

---

## V01 | Claude reads "151 Trading Strategies" (Kakushadze & Serur) and an Internal Bar Strength index-CFD strategy is backtested in "Algo Trading Hub": +92% in 10 years, sold through a "comment strategy" funnel
- **Source:** Dropbox video V01 (VID_20261018_115708_667.mp4)
- **Account:** @italian_founder (watermark on every frame and end card) · **Type:** video (36s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** MEDIUM – the paper is a well-known free reference and the IBS strategy is simple to rebuild in Python, but the backtest platform is unverified and the shown result is weak once you read the numbers.

**What it says:** The creator searches SSRN for "trading strategy" sorted by downloads and opens "151 Trading Strategies" (the screen shows about 240k downloads; he says "more than 200,000"). He asks Claude Code in a terminal to read the 361-page PDF and list which strategies can be built "on ATH", and Claude returns a table of about 9–10 buildable now (price vs MA, two/three MAs, pivot points, Donchian, internal bar strength, trend following, absolute momentum + 200-day filter, index volatility targeting) plus some needing more work (pairs, cluster mean reversion, dual momentum, rotation, carry). He pastes one spec, "Internal Bar Strength (IBS) Index Basket", into an "AI Assistant" panel of a web app called Algo Trading Hub and shows the report: "over 90% in the last 10 years... all costs are included". He ends with "comment strategy and I'll send you access to this."

On-screen spec (read from crops): four index CFDs (US100, US30, US500, JP225) traded independently; one check per day at a fixed local time on 5-minute bars; buy at market when IBS is below 0.10 (US100), 0.20 (US30), 0.20 (US500), 0.30 (JP225); exit when IBS is above 0.50 at a later daily check; no stop-loss, take-profit or time limit; ATR(20) sizing so one ATR equals 1,000 account currency.

On-screen report: Oct 5 2016 – Oct 6 2026, 100,000 USD deposit, M1 bar-by-bar, 1:100 leverage, hedged, 100 pts slippage. Net profit +92,110.08 (+92.11%), max drawdown 33,744 (33.1%), win rate 59.2% (784/1,324), profit factor 1.23, Sharpe 0.41, recovery factor 2.73, 1,324 trades, commission 0.00, **swap −92,749.19**. Cost model: "IC Markets (EU) Raw (mine)" per symbol, no commission, swap charged, slippage 100 pts (33 pts on one), leverage 1:20.

**What's actually behind it:**
- **151 Trading Strategies**, Zura Kakushadze & Juan Andrés Serur, SSRN abstract 3247865 (https://papers.ssrn.com/abstract=3247865), also a Palgrave Macmillan book (2018, ISBN 978-3-030-02791-9). It is a real, widely cited catalogue of 150+ strategies across stocks, options, ETFs, futures, FX, crypto and more, with formulas and some backtest-free source code. The SSRN PDF is a free download. It is descriptive and pedagogical; it does not contain performance claims.
- **Internal Bar Strength (IBS)**: IBS = (Close − Low) / (High − Low). It is a well-known short-term mean-reversion signal for equity indices and ETFs (section 4.4 in the paper's ETF chapter, as Claude's table shows).
- **"Algo Trading Hub" (ATH)**: a web backtester with an AI assistant, MT5-style metrics ("deposit load", "recovery factor", hedged mode) and broker-specific cost profiles. Two web searches found no product by that name. It appears in the creator's own bookmark bar, and the paper sits in his folder `C:/Sources/SocialMedia/marketing/Strategies/`, which suggests he runs or markets it. Pricing, owner and licence are unknown.
- **Claude Code**: used as a PDF reader and spec writer. That part is real and reproducible.

**Verification:** Viewed all 5 contact sheets, then cropped full-resolution frames of the SSRN results page, the Claude terminal prompt and answer, the strategy table, the AI-assistant spec and the report header, metrics and cost model. Web search confirmed the paper (SSRN 3247865 / Palgrave 2018). Two web searches for "Algo Trading Hub" found nothing, so the platform is **unverified**. The SSRN download figure on screen is blurry (about 240k) and I did not check it live.

**Claims vs reality:**
- "Paper with 151 strategies, more than 200,000 downloads": true in substance. It is one of SSRN's most downloaded finance papers.
- "Claude found 9 I could actually test and trade": that is Claude's judgement of which strategies fit *this platform's* features, not a finding about the strategies themselves.
- "Over 90% in the last 10 years": the number is real on screen but it is a weak result. +92% over 10 years is about 6.7% a year, with a 33% maximum drawdown and a Sharpe of 0.41, using 1:100 leverage. Buying and holding the S&P 500 over Oct 2016–Oct 2026 returned far more, at a similar or smaller drawdown.
- "All costs are included": swap, spread and slippage are modelled, and swap alone (−92.7k) wiped out half the gross profit. This is a strong argument for trading the same signal on ETFs or futures rather than CFDs. Commission is 0 because the broker profile charges none on index CFDs.
- Overfitting risk: the per-index entry thresholds (0.10/0.20/0.20/0.30) look tuned. Only one in-sample run ("Revision #1/#2") is shown, with no out-of-sample or walk-forward test.
- The equity curve is shown without a benchmark.

**Agenda:** "Comment strategy and I'll send you access": a DM funnel to the Algo Trading Hub platform, which the creator appears to promote or own. The paper is used as bait.

**Lab use:**
- Download the free paper PDF from SSRN 3247865 and keep it as a strategy catalogue. Asking Claude to extract "testable with my data" lists from it is a good, cheap workflow.
- Rebuild IBS in Python in 1–2 hours. Use daily OHLC for SPY/QQQ/DIA/EWJ (or index futures) from your existing data source, set `ibs = (c - l) / (h - l)`, enter below X and exit above 0.5. Run it in vectorbt, backtrader or NautilusTrader (verified in batch 1). Test thresholds walk-forward, add realistic ETF costs, and compare against buy-and-hold.
- No GPU or paid API needed. Do not pay for ATH; open-source backtesters cover this.

**Second-brain relevance:** LOW – The only memory-adjacent idea is the workflow of having an agent ingest a long PDF and turn it into a structured, reusable table. That is capture/consolidation done by hand in one chat; nothing is stored or shared. For a lab brain, store such extracted tables as markdown notes in a shared knowledge store (e.g. the gbrain/hindsight options from batch 1) so every agent can reuse them.

---

## V21 | Cross-sectional momentum (Jegadeesh & Titman 1993) pitched as "the most profitable strategy nobody has read"
- **Source:** Dropbox video V21 (VID_20261018_121520_695.mp4)
- **Account:** @js.financials_ (watermark on every frame and end card) · **Type:** video (55s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** MEDIUM – the strategy is real and one of the best-documented anomalies, and it can be rebuilt for free, but the clip adds nothing beyond the paper title, and its paper card shows the wrong paper.

**What it says:** A talking head in front of a trading desk says "the most profitable strategy of the last 30 years is in a free paper from 1993, almost nobody's read it": Jegadeesh and Titman 1993. Stocks that went up over the last year keep rising for months, so you buy the winners, sell the losers and rebalance monthly. He says it has been "tested in every asset class, every country, two centuries of data, still works", and funds "running hundreds of billions" are built on it. It hasn't been arbitraged away because "it crashes every decade", costs kill the naive version, and most people can't hold a strategy that "loses often and small before it wins big". "The alpha is public… the skill isn't." The close is "follow this page because I try to teach the skill". On screen there are only burned-in captions and one JSTOR card overlay at 0:04–0:06. That card reads "Profitability of Momentum Strategies: An Evaluation of Alternative Explanations", Narasimhan Jegadeesh and Sheridan Titman, *The Journal of Finance* Vol. 56, No. 2 (Apr. 2001), pp. 699–720, Wiley, jstor.org/stable/222579. A crop confirmed the text.

**What's actually behind it:**
- **Jegadeesh & Titman (1993)**, "Returns to Buying Winners and Selling Losers: Implications for Stock Market Efficiency", *Journal of Finance* 48(1), 65–91. This is the paper he names. It forms portfolios on past 3–12-month returns, holds them 3–12 months, and earned about 1% a month in 1965–1989 US stocks. Part of the gain reverses in years 2–3. Published in JF/JSTOR (paywalled); copies circulate freely.
- **The paper shown on screen is a different one**: the authors' 2001 follow-up (JF 56(2)), which confirms momentum continued out of sample in the 1990s. It is a good companion read, but it is not the 1993 paper.
- Supporting literature behind his claims (general knowledge, not shown in the clip):
  - Asness, Moskowitz & Pedersen (2013), "Value and Momentum Everywhere": momentum across asset classes and countries.
  - Geczy & Samonov (2016), "Two Centuries of Price-Return Momentum".
  - Daniel & Moskowitz (2016), "Momentum Crashes" (e.g. 2009). Crashes occur after market rebounds, mostly in the short leg.
- Free data for studying it: Kenneth French Data Library (UMD momentum factor, monthly and daily, from 1926).

**Verification:** Viewed all 7 contact sheets and cropped the JSTOR card (`work2/V21/paper.png`). Read the transcript. Web search confirmed the 1993 citation and its Wharton-Jacobs Levy Prize. The 2001 paper's details were read off the frame. The other literature is from general knowledge, not re-fetched. No code or repo is named.

**Claims vs reality:**
- "Most profitable strategy of the last 30 years": hyperbole. Momentum is a strong, persistent premium, but post-publication returns are smaller (McLean & Pontiff decay). US long-short momentum had long flat or negative stretches, e.g. 2009 and roughly 2009–2020 weak.
- "Almost nobody's read it": false. It is one of the most cited papers in finance, and momentum is a standard factor (Carhart 4-factor, MSCI and AQR momentum indexes/funds).
- "Tested in every asset class, every country, two centuries": broadly supported by the literature above.
- "Crashes every decade, costs kill the naive version": true and the honest part of the clip. Naive monthly-rebalanced long-short in small caps has high turnover and shorting costs.
- "Buy the winners, sell the losers, rebalance monthly": accurate as a sketch. It omits the standard skip-month (12-1 formation) to avoid short-term reversal.
- Paper card: wrong paper, and labelled "free" while it is on JSTOR.

**Agenda:** Follower growth ("follow this page… I teach the skill"). No link, course or product is shown in this clip.

**Lab use:**
- Rebuild a 12-1 cross-sectional momentum backtest in Python.
- Sanity-check against the French UMD factor (`pandas-datareader` `famafrench` source, free) before trusting any self-built version.
- The universe must be point-in-time. yfinance S&P 500 constituents today give survivorship bias; use CRSP if available, otherwise test on ETFs and futures (time-series momentum) where survivorship matters less.
- Add the skip month, volatility scaling (Barroso & Santa-Clara 2015 "Momentum has its moments") to blunt crashes, and realistic costs.
- Tools already verified in batch 1: skfolio (BSD-3) for portfolio construction, qlib (MIT) for an alpha-research pipeline with point-in-time data, nautilus_trader (LGPL-3) if it is ever traded.
- CPU only, no paid APIs. Effort: 1–2 days for a solid factor replication plus a crash analysis.

**Second-brain relevance:** NONE – A pure strategy clip with no memory, knowledge-base or agent-context content. The only link is that the paper citations (1993 JF, 2001 JF, Daniel & Moskowitz 2016) belong in the lab's research-notes store as reference entries.

---

## V23 | "Trading bot in 12 seconds": paste an SSRN paper (Zarattini/Barbon/Aziz ORB "Stocks in Play") into Astral (heyastral.ai), a paid AI backtesting terminal
- **Source:** Dropbox video V23 (VID_20261018_121614_492.mp4)
- **Account:** @lucas_lalk (watermark and end card) · **Type:** video (22s)
- **Category:** PAID / CLOSED – USABLE
- **Lab value:** MEDIUM – the paper is a genuine, rebuildable reference (ORB on "Stocks in Play"), and "paper → LLM → backtest" is a sound workflow. The advertised tool, though, is a closed $30/month SaaS, and the one-shot result shown is unverifiable.

**What it says:**
- Title card: "how to build a trading bot in 12 seconds". Go to the site "where people publish their actual strategies from colleges and firms": the screen shows papers.ssrn.com Advanced Search for "day trading strategy", 10,000 results.
- Results visible:
  - "A Profitable Day Trading Strategy For The U.S. Equity Market" (Swiss Finance Institute Research Paper 24-98; Carlo Zarattini, Andrea Barbon, Andrew Aziz; Concretum Research Lugano / University of St. Gallen & SFI / Peak Capital Trading and Bear Bull Traders)
  - "Can Day Trading Really Be Profitable?" (Zarattini, Aziz)
  - "Day Trading: Adapting to Change"
  - "Noise Trading and Volatility: Evidence from Day Trading and Message Boards"
- He opens the PDF (tab "4729284.pdf", a results table and the Conclusion), copies the entire paper, and pastes it into Astral (`heyastral.ai/terminal/session-…`, tab "Astral | Terminal", SPY 1H chart, panel "Run a backtest") with "build me this trading strategy:".
- "Typically your results will not be good but sometimes you get results like this":
  - Earnings +$98,594.21, total return 98.59%, annual return 28.97%
  - Max drawdown −8.44%, Sharpe 2.22, Sortino 3.63, Calmar 3.43
  - Win rate 35.60%, expectancy 0.29%, completed positions 1,747
- "and it's actually insane."

**What's actually behind it:**
- **Paper:** Zarattini, Barbon & Aziz (2024), SSRN 4729284, https://papers.ssrn.com/sol3/papers.cfm?abstract_id=4729284 (also SFI RP 24-98, St. Gallen repository; revised May 2024). Free to download.
  - It studies the 5-minute Opening Range Breakout restricted to "Stocks in Play" (unusual relative volume, usually news), on 7,000+ US stocks, 2016–2023.
  - It reports that the top-20 Stocks-in-Play portfolio returned over 1,600% net with Sharpe 2.81, versus 198% for the S&P 500.
  - It is the authors' own backtest. They run commercial trading/education businesses (Concretum, Peak Capital / Bear Bull Traders), and no independent replication was found.
- **Astral**, https://heyastral.ai : a closed "trading workspace".
  - You describe a strategy in chat, inspect the generated code, backtest (up to 40,000 bars), paper trade, set alerts and connect a broker.
  - It also exposes an MCP connection for ChatGPT/Claude.
  - Paid only: $9 the first month, then $30/month, no free tier. Operator not named on the site; data provider not disclosed.

**Verification:**
- Viewed all 3 contact sheets. Cropped the URL bar, the pasted-paper text and the stats panel (`work2/V23/`). Read the transcript.
- Web search confirmed the paper (SSRN id, authors, headline results).
- WebFetch of heyastral.ai gave the product description and pricing. A web search found no independent reviews of Astral.
- Could not see the generated code or the backtest settings (universe, timeframe, costs).

**Claims vs reality:**
- "Build a trading bot in 12 seconds": the result is a backtest in a paid SaaS, not a deployable bot. He admits results are "typically not good" and shows a cherry-picked success.
- "Paste the paper and it builds the strategy": the paper's edge depends on a cross-sectional, point-in-time Stocks-in-Play screen over 7,000 stocks with 5-minute bars and relative-volume ranking. A chat session on a single SPY 1H chart cannot reproduce that. Whatever Astral backtested is at best a single-ticker ORB approximation. The 35.6% win rate does look ORB-like.
- Stats (Sharpe 2.22, −8.44% drawdown): no cost assumptions, period or out-of-sample split shown. Untrustworthy as presented, and re-rolling until "sometimes you get results like this" is selection bias (multiple testing).
- SSRN as "actual strategies from colleges and firms": SSRN is a preprint server. Papers are not peer-reviewed and are often marketing for the authors' firms (as here).

**Agenda:** Engagement and follower farming. Likely promotion or affiliate for Astral (the only product shown; a link is not visible in the clip). No price disclosed.

**Lab use:**
- Worth doing: rebuild the paper yourself.
- Data: 5-minute bars for a broad US universe plus daily relative volume.
  - Free option: Alpaca's free IEX feed (partial volume) for prototyping.
  - Proper options: Polygon/Massive or Databento (paid), or Interactive Brokers historical bars.
- Start with the paper's simpler companion: the ORB on QQQ/TQQQ in "Can Day Trading Really Be Profitable?" (Zarattini & Aziz, 2023). It is single-ticker and easy to replicate with free data.
- Engines: nautilus_trader (LGPL-3, verified batch 1) for an event-driven intraday sim with fees; backtesting.py (AGPL-3) or vectorbt for quick vectorized tests.
- Claude Code can do the paper-to-code step locally for free: feed it the PDF (MinerU, verified batch 1, for PDF→Markdown) and require a spec + test plan before code.
- Effort: about 1 day for the QQQ ORB; 1–2 weeks for the full Stocks-in-Play universe, which is mostly data plumbing.

**Second-brain relevance:** LOW – The useful pattern is "paper → structured strategy spec → code → backtest result", stored together so agents can recall what was already tried. That is a capture-and-consolidation idea, not a memory system. Astral itself is closed SaaS. Its MCP endpoint lets Claude call it, but your strategy history then lives on their servers, not self-hosted. Do this in-lab instead: PDFs → MinerU Markdown → a git-tracked research notes repo indexed by a self-hosted memory server (GBrain or Hindsight, verified in batch 1).

---

## V11 | Kronos (unnamed in the video): open-source OHLCV forecasting foundation model, pitched as "AI that predicts prices" (Portuguese)
- **Source:** Dropbox video V11 (VID_20261018_120851_194.mp4)
- **Account:** @nathdalat · **Type:** video (43s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – the model behind the video is real, MIT-licensed and runs on CPU. It is a forecasting-feature experiment, not a price oracle, and the video never names it.

**What it says:** In Portuguese, a woman says Claude "killed the trader market" (*"O Cloud matou o mercado de Trader"*) because an open-source model trained on market movements can "literally predict the estimated trajectory of prices". She says companies charge **$24,000 a year** for this (the on-screen graphic is a "TERMINAL PROFISSIONAL" card reading "$24.000 POR ANO", meaning a Bloomberg-style terminal). On screen, a "LAB DE PESQUISA / FEITO POR PESQUISADORES" graphic says it was made by researchers, followed by "OPEN SOURCE / GRÁTIS PARA TODOS". She says it has "30 mil estrelas" (30k stars); the on-screen GitHub counter animates from 6K to **24K**. Then "TREINADO EM 00→10→26→41→**45 BOLSAS GLOBAIS**" (trained on 45 global exchanges) and "TREINADO EM CANDLES". A price chart grows a green "PREVISÃO" fan with "FAIXA" (range) and "CAMINHO PROVÁVEL" (probable path) labels, set against a red dashed "PALPITE" (guess). It ends with "COMENTE BOLSA" and a "GUIA DE USO" card (a "DM" funnel). The background music credit reads "Ted D'souza, Rest of the Soul • Classical Cello Experience". No repo name, URL or code appears anywhere in the video.

**What's actually behind it:**
- https://github.com/shiyu-coder/Kronos (verified in batch 1, local clone re-checked)
  - License: MIT.
  - Status: last commit 2026-04-13 (a merged batch-dimension training fix); about six months quiet. Paper arXiv:2508.02739 (AAAI 2026). Weights on Hugging Face: `NeoQuasar/Kronos-mini` (4.1M), `-small` (24.7M), `-base` (102.3M).
  - What it does: a decoder-only foundation model over tokenized OHLCV K-lines. It produces probabilistic multi-step forecasts by sampling paths, which is the "range plus probable path" fan in the video.
  - The README states "trained on data from over **45 global exchanges**", which matches the video's number exactly. That is how I identified the model.

**Verification:** I viewed all six contact sheets and read the overlays. I matched "45 bolsas globais", "treinado em candles", "open source / researchers" and the forecast fan to the Kronos README (line 47: "over 45 global exchanges"). Clone and license were verified in batch 1, and I re-checked the local clone's git log. The star count is not verifiable here because the GitHub API is blocked; the video itself contradicts its own number (spoken 30k, on screen 24k). I could not see what the "BOLSA" DM contains.

**Claims vs reality:**
- "Claude killed the trader market": **false and confused.** Kronos is not made by Anthropic or Claude; it comes from academic authors (Tsinghua-affiliated). It "killed" nothing.
- "Predicts the trajectory of prices": it outputs probabilistic forecasts. In the authors' own tests, forecasting edge shows up as modest IC and RankIC improvements on A-shares, not reliable direction calls. The README itself says the finetune pipeline is a demo, "not a production-ready quantitative trading system".
- "Companies charge $24,000/year for this": **false comparison.** A Bloomberg terminal sells data, news and execution, not a forecasting model. Kronos replaces none of it, and you still need your own data.
- "30k stars" / "24K": unverified, and the video contradicts itself. The order of magnitude is plausible.
- "Free for anyone to download and use": **true** (MIT license, public weights).

**Agenda:** A "comment BOLSA" DM funnel for a "guia de uso" (usage guide). It is an engagement and lead-capture account. The video withholds the repo name so that viewers have to comment.

**Lab use:**
- Entry point: `git clone https://github.com/shiyu-coder/Kronos`, `pip install -r requirements.txt` (PyTorch), then `KronosTokenizer.from_pretrained("NeoQuasar/Kronos-Tokenizer-base")` and `Kronos.from_pretrained("NeoQuasar/Kronos-small")` with `KronosPredictor`.
- Hardware and cost: CPU is enough for mini and small; a GPU helps for base and finetuning. No paid API.
- Effort: about 1 day to get forecasts on your own bars. Another 1–2 days to benchmark honestly against naive baselines (random walk, EWMA, ARIMA) with walk-forward splits and to measure IC, hit rate and calibration of the forecast bands.
- How to use it: as a feature generator (expected return, forecast dispersion) fed into a normal backtest (e.g. NautilusTrader or a vectorized backtest), never as a stand-alone signal.

**Second-brain relevance:** NONE – a forecasting model with no memory, knowledge-storage or agent-context component. The only memory-related lesson is to log Kronos experiments (config, data window, metrics) into whatever experiment journal your second brain uses.

---

## V29 | Kronos, the open-source (MIT) foundation model for OHLCV candlesticks, shown as "open-source AI model for the stock market"
- **Source:** Dropbox video V29 (VID_20261018_121716_856.mp4)
- **Account:** @baljeet.ai (watermark) · **Type:** video (34s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – Kronos is real, MIT-licensed, pip-installable and runs on CPU (mini/small). It is a legitimate forecasting-feature experiment for the lab, but the video adds nothing beyond the README, and a pretrained K-line model is not a proven trading edge.

**What it says:** Spoken in Hindi; the background transcript failed after 4 s, so I re-transcribed and translated it myself with faster-whisper.
- "This is an open source model for financial markets, trained on the data of 45 global exchanges. This model is called Kronos… it can understand the different kinds of candlesticks easily… it can see market trends."
- "If you want to see a live demo you can go here… you can see different variants… their parameters… their context window. It is quite simple to use: install Python, clone it and run this command."
- "If you want the direct link, follow and comment."

On screen, the overlay reads "Open-Source AI Models for Stock Market". He scrolls the GitHub README (MIT license tab):
- Kronos logo, "the first open-source foundation model for financial candlesticks (K-lines), trained on data from over 45 global exchanges"
- News: 2025.11.10 accepted by AAAI 2026; 2025.08.17 fine-tuning scripts; 2025.08.02 paper on arXiv
- Tokenizer / causal-transformer diagram
- "Live Demo" (BTC/USDT 24-hour forecast)
- Model Zoo table: Kronos-mini (Tokenizer-2k, context 2048, 4.1M) ✅; Kronos-small (Tokenizer-base, 512, 24.7M) ✅; Kronos-base (512, 102.3M) ✅; Kronos-large (512, 499.2M) ❌ not open
- "Getting Started: Install Python 3.10+, then `pip install -r requirements.txt`" and "Making Forecasts"

**What's actually behind it:**
- https://github.com/shiyu-coder/Kronos :
  - License: MIT.
  - Latest commit 2026-04-13 ("Merge pull request #243 … fix/batch-dimension-training"), so about 6 months quiet but not abandoned.
  - Paper arXiv:2508.02739, AAAI 2026.
  - Weights on Hugging Face as NeoQuasar/Kronos-mini, -small and -base, with tokenizers NeoQuasar/Kronos-Tokenizer-2k and -base. Kronos-large is not released.
  - Repo contents: `model/`, `examples/`, `finetune/` (Qlib A-share pipeline), `finetune_csv/`, `webui/`, `tests/`.
- What it does: a BSQ tokenizer turns OHLCV bars into discrete tokens, and a decoder-only transformer autoregressively forecasts future bars (probabilistic, sampled). `KronosPredictor` handles normalisation and truncation to max context (512 for small/base).

**Verification:** Viewed all 5 contact sheets; the README is legible in the frames. Re-transcribed the Hindi audio. Reused the batch 1 shallow clone at scratchpad/repos/Kronos: re-read the LICENSE (MIT), the README model table and context notes, and the git log (last commit 2026-04-13, consistent with batch 1 entry DcD1vwCtGGX). Not executed. Every on-screen detail matches the repo.

**Claims vs reality:**
- "Open-source model for financial markets trained on 45 global exchanges": true per the README and paper.
- "Can understand candlesticks and see trends": overstated. It produces statistical forecasts of next bars. The authors' own backtests are on Chinese A-shares, and the finetune pipeline is labelled a demonstration, not a production trading system. Its forecast skill on your market must be measured against naive baselines (random walk, last value, simple AR) on strict out-of-sample data.
- "Quite simple to use": fair. pip requirements plus a few lines; CPU is fine for mini/small inference.
- Variants and context window: correctly shown, but note that the largest model is not open.

**Agenda:** "Follow and comment for the direct link" DM funnel and follower growth for an AI-tools account. Nothing is sold in the clip.

**Lab use:**
- Entry point: `git clone https://github.com/shiyu-coder/Kronos`, then in a venv `pip install -r requirements.txt` (PyTorch, CPU OK) and `Kronos.from_pretrained("NeoQuasar/Kronos-small")` + `KronosTokenizer.from_pretrained("NeoQuasar/Kronos-Tokenizer-base")` → `KronosPredictor(...).predict(df, x_timestamp, y_timestamp, pred_len)`.
- A GPU helps for Kronos-base and for fine-tuning (`finetune_csv/` lets you finetune on your own CSV bars).
- Use it as one forecast feature or a regime signal. Evaluate with walk-forward splits, include costs, and compare to baselines before using it in any strategy.
- Effort: half a day to run inference on your data; 2–5 days for a proper evaluation and finetune.
- No paid APIs. Data from your own lab feeds (OpenBB, broker, crypto exchanges).

**Second-brain relevance:** NONE – A forecasting model, not a memory or knowledge layer. The only link is bookkeeping: model versions, finetune runs and evaluation results should be logged into the lab's experiment memory so agents can see what has already been tried with Kronos.

---

## V07 | "Self-improving AI trading agent, day 5": a medallion data-pipeline dashboard with chaos/auto-heal, no code shown
- **Source:** Dropbox video V07 (VID_20261018_120450_301.mp4)
- **Account:** @fidetolabs (on-screen tag and end card) · **Type:** video (18s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** LOW–MEDIUM – a nice reference layout for a self-healing market-data pipeline, but closed and undocumented. Nothing in it is "self-improving AI".

**What it says:** There is no speech; the audio is music ("Dezko • Ascend"). The title reads "Day 5: Building A Self-Improving AI Trading Agent". The subtitle reads "Data pipeline from external data sources to multiple trading signals which can do self-recovering". The screen recording shows a dark web dashboard branded **FDTL**:
- **Tabs:** Research / Backtest / Volatility / **Pipeline**.
- **Pipeline layers:** SOURCES → BRONZE → SILVER → GOLD → MARTS.
- **Nodes:**
  - Sources: Market ticks, Broker OMS, Instrument reference, Custody positions, News & filings
  - Bronze: raw_market_ticks, raw_order_events, raw_reference_delta, raw_position_files
  - Silver: bars_1m, executions, instrument_dim, positions_daily
  - Gold: fct_price_daily, fct_fill_quality, fct_pnl_attrib
  - Marts: Execution quality, Risk & exposure, Alpha research
- **Run control:** Speed 1.0x, "CHAOS 2.4/min", and PAUSE / BREAK NODE / HEAL ALL buttons, plus an "auto-recovery (retry & backfill)" checkbox.
- **Health panel:** 24/24 healthy, about 40–43k rows/s.
- **Node panel:** each node shows its lag, its SLA, and its state (OK, DEGRADED with "join ran partial – one parent was late", or BACKFILL / RETRY 1/3). The executions node is labelled "dbt · incremental · dedup · sla 2m". Sample rows show an AAPL BUY with slippage in bps.
- The user clicks "BREAK NODE" and later "HEAL ALL" to show recovery.

**What's actually behind it:**
- **FDTL / fidetolabs:** no public repo, product page or paper was found (web search returned nothing for "fidetolabs").
- The dashboard is almost certainly a **simulation**:
  - There is a "chaos" injection slider and a "break node" button.
  - The rows are synthetic (AAPL fills at 233.x on "2026-08-25").
  - The layout is the standard **medallion architecture** (bronze/silver/gold) from Databricks/dbt practice.
- **"Self-recovering"** here means retry and backfill on a failed DAG node, which is standard orchestrator behaviour (Dagster, Airflow, Prefect). It is not AI self-improvement.

**Verification:**
- Read every UI label from 2x crops (work2/V07/d3.png, d8.png, d12.png).
- Searched the web for "fidetolabs": no results.
- Nothing could be cloned. Unverified: whether any real data or AI component exists.

**Claims vs reality:**
- "Self-improving AI trading agent": nothing on screen is AI or self-improving. It is a data-pipeline monitor with retry/backfill. ("Day 5" of a build-in-public series; the AI part may come later.)
- "Self-recovering pipeline": plausible as described (retry + backfill + partial joins flagged DEGRADED). It is standard data-engineering practice, not novel.
- Throughput figures (40k rows/s) come from a simulated stream and mean nothing.

**Agenda:** A build-in-public series for audience growth, probably leading to a product or a lab brand later. No call to action is shown in this clip.

**Lab use:**
- **Idea worth stealing:** a medallion layout for the lab's market data:
  - raw ticks/bars → cleaned bars → features/facts → marts (backtest inputs, execution-quality and PnL-attribution tables)
  - per-node SLA and lag monitoring
  - automatic retry and backfill
- **Open-source stack:**
  - Dagster (asset graph, freshness SLAs, retries, backfills, built-in lineage UI) or Prefect
  - dbt-core (or SQLMesh) on DuckDB/Postgres for the silver and gold models
  - Parquet storage
  - All of it runs on CPU with no paid APIs.
- **Effort:** 1–2 days for a small Dagster + DuckDB pipeline over existing data sources; 1–2 weeks to add proper freshness checks and backfills.
- **Paid/closed alternative:** none needed. The pictured tool isn't available anyway.

**Second-brain relevance:** LOW – The relevant layers are capture/ingest and lineage. A medallion pipeline with an orchestrator such as Dagster is a sound backbone for *ingesting* lab data (and could feed a knowledge store), but it is not memory or retrieval itself. Dagster is self-hostable and exposes a GraphQL/web API, so several VMs could trigger or read it. It provides no agent-context layer.

---

## V22 | TradingView's community "open-source" scripts library as a free source of strategies (demo: a buy-the-dip pyramiding script with a flattering backtest)
- **Source:** Dropbox video V22 (VID_20261018_121557_716.mp4)
- **Account:** @tctradinglab (watermark throughout; "TC Trading" follow card at end) · **Type:** video (98s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** LOW – the tip is real and old (TradingView's public script library is a huge, free idea mine), but the example strategy is a textbook overfit dip-buyer, and Pine code is not directly usable in a Python lab.

**What it says:**
- The "TradingView unlimited strategy hack": tradingview.com → Community → Indicators and strategies, filter "Open-source only" and type Strategies. That gives a "massive backlog" of indicators and strategies "many people are actually paying money for".
- He opens "Systematic Deviation Harvester". The tab URL is roughly `tradingview.com/script/Y1P36Tth-Systematic-Deviation-Harvester/`, an "Open-source script, updated 2 hours ago" by Capitalist_Zach, shown on SPY 1D NYSE Arca.
- The strategy report shows:
  - Total P&L +$354,973.94 (+35.50%), max drawdown $89,130.08 (7.74%)
  - Profitable trades about 85% (121/142), profit factor 5.1
- He adds it to his own chart on ETHUSD 1D (Coinbase), May 22, 2016 – Jul 25, 2026, $1M capital, Paper Trading. The report there shows:
  - Total P&L +$1,471,355.36 (+147.14%), max drawdown $352,194.70 (14.70%)
  - Profitable trades 87.75% (222/253)
- He opens the source code (`{}` icon). Visible header:
  - `//@version=6`, `strategy("Systematic Deviation Harvester", overlay=false, pyramiding=100, precision=2)`
  - Inputs: "Drawdown Thresholds" with Minor Drop 5%, Major Drop 10%, "Enable Dynamic Scaling" (α3 pyramid) off by default, Rally Reset 2%
  - "True Compounding Sizing": Minor/Major Drop Buy as % of equity
  - "Unified Compounding Exit" with a compounding profit target and a trailing offset
- He says you can "plug this into AI" or edit it. He notes, to his credit, that "just because the back test looks this good doesn't mean that it actually trades this way". He then says that with "the TradingView subscription" you get an endless stream of strategies.

**What's actually behind it:**
- TradingView Community Scripts, https://www.tradingview.com/scripts/ : free to browse and read open-source code with a free account. No subscription is needed to view source. Paid plans raise the per-chart indicator limits, alerts and intraday history. Open-source scripts carry the author's license header (typically MPL-2.0 by default) plus TradingView House Rules on reuse and attribution.
- "Systematic Deviation Harvester" (Capitalist_Zach): a long-only, buy-the-dip, averaging-down script.
  - It buys a % of equity when price falls 5% from a tracked peak, more at 10%, and optionally a third pyramid tier.
  - It sells at a compounding profit target or trailing offset, with pyramiding up to 100 entries.
  - The URL slug was too blurred to read reliably. Both a WebFetch of the guessed URL (404) and a web search failed to find it. The script may be renamed or removed, or the slug may be misread. Unverified.
- Pine Script runs only inside TradingView. Python equivalents:
  - PyneCore, https://github.com/PyneSys/pynecore (Apache-2.0, last commit 2026-10-18): runs Pine-style code in Python with TradingView-matching semantics. Converting existing .pine files needs the separate PyneComp service (API key; paid tiers, 3 free conversions through their Discord bot). Rewriting a small script by hand or with Claude is free.
  - backtesting.py, https://github.com/kernc/backtesting.py (AGPL-3.0, last commit 2026-08-05)
  - vectorbt, https://github.com/polakowo/vectorbt (Apache-2.0 + Commons Clause, last commit 2026-10-18, PRO version upsold)

**Verification:**
- Viewed all 13 contact sheets. Cropped the strategy report, the source code header, the trades stats and the ETH key stats (`work2/V22/`). Read the transcript.
- WebFetch of the script URL returned 404, and a web search did not find it.
- Shallow-cloned pynecore, backtesting.py and vectorbt into `repos/` (LICENSE, README and git log read; nothing executed).
- TradingView plan details are from general knowledge, not re-checked.

**Claims vs reality:**
- "Strategies people pay for are here for free": partly true. Many paid "signal" products are repackaged public indicators. But public scripts are mostly unvetted, and many are curve-fit.
- "You need the TradingView subscription": false for viewing or copying source. A free account works.
- The showcased backtest is the classic averaging-down profile, and the numbers undercut it:
  - 85–88% win rates come from buying dips with pyramiding=100 and % of equity compounding. Losses are deferred, not avoided (martingale-like exposure in a crash).
  - On ETH, +147% over 2016–2026 is a tiny fraction of simply holding ETH (about $12–14 in May 2016), with a 14.7% drawdown on a highly scaled position.
  - SPY +35.5% (window not visible) likewise looks below buy-and-hold.
  - Commission and slippage settings were not shown; TradingView's default is 0.
  - "Updated 2 hours ago" means no live track record.
- He does say the backtest may not reflect live trading. That is fair but buried.

**Agenda:** Follower farming ("follow for more TradingView tips") and implicit TradingView promotion (plausibly affiliate-linked, not shown). No course in this clip.

**Lab use:**
- Use the TradingView library only as an idea source. Port any interesting logic to Python, or run Pine-style code with PyneCore (pip `pynecore`, Python ≥3.11, stdlib only).
- Then test it properly: buy-and-hold benchmark, costs, walk-forward, and a trial count for deflated Sharpe.
- For this specific script, the lab test is simple: compare to buy-and-hold and measure max gross exposure. Expect it to fail.
- CPU only. Effort: 1–3 hours to port and evaluate a small script.

**Second-brain relevance:** LOW – Only as a capture source. Interesting public scripts (URL, author, logic summary, your own evaluation result) are good "research card" entries to ingest into the lab's notes or memory store, so the same overfit ideas are not re-tested. No storage, retrieval or agent-memory component; TradingView is a closed SaaS.

---

## V25 | Claude Code → Pine Script ORB ("School Run Strategy") on MES → TradingView alert → TradersPost → Goat Funded Futures prop evaluation (affiliate funnel)
- **Source:** Dropbox video V25 (VID_20261018_121630_251.mp4)
- **Account:** @erickjablonski (watermark and end card; the TradersPost UI shows "Erick Jablonski") · **Type:** video (95s)
- **Category:** PAID / CLOSED – USABLE
- **Lab value:** LOW – an honest-looking walkthrough of a real (but paid, closed) automation chain. The strategy's own backtest shows it would breach the prop account's drawdown rule, and the endgame is a prop-firm affiliate code.

**What it says:**
- Step 1, Claude Code (desktop app, "Sonnet 4.6 · Medium", session "Build ORB day trading bot for ES futures"). Prompt: "can you help me code a day trading bot for an ORB strategy that utilizes the first 30min range of New york stock market open on ES futures?" Claude replies with clarifying questions:
  - Broker: Interactive Brokers via `ib_insync`, Tradovate or NinjaTrader
  - Paper or live
  - Risk parameters: stop at the opposite side of the range, a fixed 10-tick stop, or target as 1R/1.5R/2R
  - Entry filter: strict breakout or a retest
- His project folder `Claude Code\srs_bot` holds:
  - Python: `.env.example`, `backtest_sliding_orb.py`, `candle_builder.py`, `config.py`, `main.py`, `requirements.txt`, `risk_manager.py`, `srs_strategy.py`, `tradovate_client.py`
  - Pine: `sliding_orb*.pine`, `SRS_Option1_ATR.pine`, `SRS_Option2_Range.pine`, `srs_pullback.pine`, `SRS_Strategy.pine` (6/29/2026)
  - Results: `sliding_orb_summary.csv`, `sliding_orb_trades.csv`
- Step 2: paste the Pine file into TradingView (free account) → Pine Editor → Create new → Strategy → Add to chart. The chart shows "SRS — School Run Strategy" on Micro E-mini S&P 500 (MES1!) 15m, with 4-contract long/short boxes.
- Strategy report, Jan 2, 2025 – Jul 23, 2026, $50K:
  - Total P&L +$7,700 (+15.40%)
  - Max drawdown $7,390 (13.39%)
  - Profitable trades 78.27% (299/382), profit factor 1.16
- Step 3, TradersPost: connect a broker (prop-firm list includes BluSky, Lucid, Apex, Tradeify, Topstep, My Funded Futures, Take Profit Trader, FundedNext, TopOneFutures, Blue Guardian, GoatFunded, TradeDay, Legends, Alpha Futures, Purdia Capital).
- He uses Goat Funded Futures, "listed on PropFirmMatch":
  - Listing: 4.4 from 24 reviews, HK, CEO Edoardo Dalla Torre, created Nov 2024
  - Checkout: "$69 FOR 50K ACCOUNT", "Get 50% OFF by applying code SUMMER50"
- TradersPost shows the GoatFunded account under **"Paper Accounts"** at $50,051.40 with Day's P&L +$207.40 (0.42%). Strategy "SRS – take both sides on any ticker", auto-submit enabled, "Your Starter Plan".
- Step 4: a TradingView alert (MES1! crossing 7,433.75; notifications App, Toasts, Webhook) linked to TradersPost. Trades list: MESU2026 buys and sells, 7/17–7/23/2026.
- The Tradovate prop dashboard shows:
  - Account GFTEFLEXERICK59011, "FLEX 50K · Phase 1", ACTIVE
  - Balance $50,051.40, today's starting balance $50,000
  - "Maximum drawdown (4%) $2,051.40 left"
- Close: "comment bot and I'll send you a link to Goat Funded Futures with the max discount."

**What's actually behind it:**
- Claude Code (Anthropic, paid subscription or API). It did the real work, including a Python Tradovate client and a backtester, which he does not dwell on.
- TradingView Pine Script strategy tester (free tier sufficient for this). Closed.
- TradersPost, https://traderspost.io : webhook-to-broker automation SaaS.
  - Free tier is manual submission only. Paid live auto-submit is about $49/$99/$199/$299 a month per third-party reviews; the official page shows Starter at $41.65/month billed yearly.
  - Its Tradovate integration is labelled beta.
- Goat Funded Futures: futures prop firm (Hong Kong, founded around mid/late 2024) offering Tradovate, NinjaTrader and Quantower.
  - Third-party payout trackers disagree widely (about $1–2M tracked versus a self-claimed $23M+).
  - Trustpilot-based score is around 2.8/5 on one aggregator versus 4.3–4.4 on PropFirmMatch.
  - Whether it explicitly permits fully automated execution was not confirmed. Some firms that integrate with TradersPost ban bots.
- PropFirmMatch: prop-firm comparison and affiliate site.
- "School Run" is a known ORB-style day-trading setup popularised by Tom Hougaard (general knowledge).

**Verification:**
- Viewed all 12 contact sheets. Cropped the key-stats panel and the project file list (`work2/V25/`). Read the transcript.
- Web searches on TradersPost pricing and Goat Funded Futures (reviews, payouts, platform support). Firm details and ratings come from affiliate-heavy review sites; treat them as indicative.
- His repo or code is not public; nothing to clone. The PyneCore and backtesting.py alternatives were shallow-cloned (see V22).

**Claims vs reality:**
- "Build your own Claude Code day-trading bot": real in principle. Claude scaffolded a sensible project, and asked good questions about the broker, stop/target rules and the entry filter.
- "Confirm the strategy is profitable" from the TradingView report: the report itself shows the problem.
  - Profit factor 1.16 over 382 trades is about $20 per trade on 4 MES contracts, roughly one MES point. That is thin enough for commissions and slippage (cost settings not shown) to erase it.
  - **The $7,390 max drawdown is about 3.6× the eval's 4% (about $2,000) max-drawdown allowance.** Run as-is, it would have failed this prop evaluation more than once in the backtest window.
  - A 78% win rate with PF 1.16 means many small wins and occasional large losses.
- "I made $207 on it today": a single day on a **Phase 1 evaluation**, which TradersPost lists as a paper account (prop evals are simulated). The account is up only $51.40 overall. Not evidence of an edge.
- "They're legit… $69": reviews are mixed. The $69 is a discounted eval fee; evaluation fees are the prop firm's main revenue, and most buyers fail.

**Agenda:** Affiliate funnel. "Comment bot" leads to a DM with a Goat Funded Futures discount link (plus PropFirmMatch and possibly TradersPost referrals). Follower growth.

**Lab use:**
- Build the same ORB in Python, entirely free and self-hosted, as Claude did for him:
  - Data: CME futures 1-minute bars from Databento (paid, cheap per GB), or IBKR historical data with an account. Free: Yahoo `ES=F` intraday covers only about 60 days.
  - Engine: nautilus_trader (LGPL-3, verified batch 1) for realistic futures fills and fees; backtesting.py (AGPL-3) for quick tests.
  - Execution, if ever: `ib_async` (successor to the archived ib_insync) or nautilus' IB adapter. That drops the TradersPost subscription.
- If you test for a prop account, model the firm's trailing or static drawdown rule as a hard constraint in the backtest; this strategy fails it.
- Effort: 1–2 days for an honest ES/MES ORB study with costs and walk-forward.

**Second-brain relevance:** LOW – Shows Claude Code working in a per-project folder (`srs_bot`) that accumulates code, variants (`SRS_Option1_ATR`, `Option2_Range`, `pullback`) and results CSVs. That is an implicit, local, unindexed project memory. The lesson for the lab: put each strategy project in git, log each variant and its backtest stats to an `experiments.md` or database, and let agents retrieve them (e.g. via a self-hosted memory MCP such as Hindsight or GBrain, verified in batch 1). TradersPost, TradingView and the prop firm are closed SaaS with no memory role.

---

## V27 | Hindi promo for OrderBlock (order-block.com), a paid Indian F&O "liquidity + order block" scanner, plus one cherry-picked EICHERMOT option trade
- **Source:** Dropbox video V27 (VID_20261018_121654_813.mp4)
- **Account:** @shubhamtradingcoach (watermark; the Sensibull profile on screen shows @shubham_dg1297) · **Type:** video (117s)
- **Category:** PAID / CLOSED – USABLE
- **Lab value:** LOW – a closed, paid (₹7,999/yr) dashboard for Indian F&O stocks only. The underlying idea (sector breadth + OI build-up ranking + intraday supply/demand zones) can be rebuilt in Python, but nothing here is open or testable.

**What it says:** The video is in Hindi. The background transcript caught only the first 14 s and the outro, so I re-transcribed the 12–107 s section myself with faster-whisper (translate mode, VAD off) from the already-installed tools. It opens: "salute to the person who made this website… it may look confusing but it is not confusing at all."
- His step-by-step method: first check "which direction and which sector has the most liquidity". The dashboard shows the top 20 stocks being bought and the top 20 being sold, and within those the top 3 each side. "Click the top stock and find where the order block is."
- He shows the morning order block around 10 o'clock on EICHERMOT: "I took an entry with 3 lots in which 30,000 capital was used." He exited when momentum faded and it started falling back.
- "This is my order book, and this is my verified PNL, the link is in my bio, and today a winning streak of 9 days is complete." Then: find where liquidity is, find the order block "where smart money is already trading", and "capture a small move from a small capital".
- He ends with "like, share and follow".

On screen:
- **order-block.com/app/orderblock**, "Order Block · OrderBlock": a breadth chart of NSE F&O stocks ("BULLISH 172 / BEARISH 41", "IT +2.87%", "OTHERS −2.84%"), sector list (IT, LOGISTICS, CEMENT, FMCG, NBFC, INSURANCE, METAL, POWER, PSU BANK, BANK, PHARMA, NEW-AGE, CHEM, TELECOM, REALTY, DEFENCE, AUTO, CAP GOODS, CONSUMER, CAP MKTS, OIL & GAS).
- Bullish and bearish stock tiles: EICHERMOT +4.17%, TVSMOTOR, INOXWIND +6.76%, ANANDRATHI −4.68%, MPHASIS, COFORGE, LICI, COLPAL, SUZLON, TATAELXSI, DMART, FORTIS, JUBLFOOD, KFINTECH, HINDPETRO and others. Each is tagged "LONG BUILD-UP" or "SHORT BUILD-UP".
- The EICHERMOT detail card: ₹7,050.00; RANK p99.8 · #1/172; OI +13.4% · LONG BUILD-UP; CONV 97 ★★★★★; Δ +90.3K above VWAP; VWAP 7,011.24; OB 7,003.50–7,010.00; Z/S1 7,015.10 / 7,001.45; R1/R2 7,055 / 7,078; R:R 1:4.6; RULE "PICK · BULLISH #1".
- A TradingView chart (in.tradingview.com, Eicher Motors 5m, NSE) annotated "CAPITAL USED – 30K, LOT SIZE – 3 LOTS", ENTRY, EXIT and ORDER BLOCK zone.
- Upstox order book: BUY 300 EICHERMOT 27 Oct 7100 CE @ 99.50 (10:05:08). SELL 200 @ 116.50 and SELL 100 @ 118.05 (11:53:17).
- Sensibull "Verified by Sensibull" page: Taken @ 9 Oct 2026 4:55 PM, Total P&L +5,255; "395 Days P&L Verified", 139 followers, "Positions from Upstox". The daily list shows Oct 9 +5,255, Oct 8 +8,220, Oct 7 +4,422, Oct 6 +6,840, Oct 5 +3,905, Oct 1 +5,175, Sep 30 +6,809, Sep 29 +10,985.
- A "Link In Bio" overlay.

**What's actually behind it:**
- **OrderBlock**, https://order-block.com :
  - Run by "Options Oracle" (Gujarat, India).
  - One plan at ₹7,999 / 12 months ("6 Months + 6 Free", struck-through ₹28,999).
  - Features: bullish/bearish boards ranking the top 20 F&O stocks, order-block charts with support/resistance and liquidity levels, "Market X-Ray" of all F&O stocks by sector, community, videos and a trading journal. Browser-based with Google sign-in.
  - It describes itself as analytics, not advice. Closed source, no API mentioned.
- **Sensibull**: Indian options platform; "verified P&L" pulls positions from the broker (here Upstox).
- **Upstox**: Indian discount broker.
- "Order block" and "smart money" are ICT/SMC retail-trading vocabulary (a supply/demand zone where the last opposite candle precedes an impulsive move). There is no standardised, testable definition.

**Verification:**
- Viewed all 15 contact sheets.
- Cropped the EICHERMOT detail card, the Upstox order list and the Sensibull P&L page.
- Re-transcribed the Hindi audio (translation is machine output; meaning is clear but wording is approximate).
- Fetched order-block.com for owner and pricing.
- Checked the trade arithmetic: 300 × 99.50 = ₹29,850 in; 200 × 116.50 + 100 × 118.05 = ₹35,105 out; gross ₹5,255. This matches the Sensibull figure exactly, so the single trade is internally consistent.
- Could not verify: whether @shubhamtradingcoach is affiliated with or paid by OrderBlock; his full P&L history including losing days; the lot size used.

**Claims vs reality:**
- "The site shows where liquidity is and the top stocks": the boards rank stocks by price change, OI build-up and VWAP position. That is useful breadth context, but it is a relabelled momentum/OI screen, not a view of "smart money".
- "Find the order block and trade there": shown entirely in hindsight. The card he uses ("RANK #1/172", +4.17%, CONV 97) is the end-of-move state. Whether EICHERMOT was #1 at 10:05 when he entered is not shown. This is classic look-ahead in presentation.
- "Verified P&L, 9-day winning streak": the Sensibull page is real broker-sourced data and shows several consecutive green days of ₹3.9k–11k. But a run of wins on a chosen screen says nothing about expectancy. Losing days, drawdown, charges (STT, brokerage, GST) and total capital are not shown. The ₹5,255 is gross.
- "Small capital, small move is enough": buying near-the-money weekly/monthly calls is a high-variance, theta-negative trade. One +17.6% premium gain in two hours on a +4% stock day is a best case, not a system.

**Agenda:** Promotes OrderBlock (paid) and the creator's "link in bio" (verified P&L page, likely leading to his paid group or affiliate). It is also an Instagram engagement play ("like, share, follow"). The relationship to the tool is undisclosed.

**Lab use:**
- Not usable directly: closed, India-only, no API, paid.
- **Rebuildable idea (2–4 days):**
  - Pull NSE F&O bhavcopy and OI data (free NSE archives; or broker APIs such as Upstox/Kite/Dhan for intraday).
  - Compute per-stock price change × OI change classification: long build-up = price↑ OI↑, short build-up = price↓ OI↑, short covering, long unwinding. Add VWAP distance and a sector-breadth aggregate.
  - Rank daily, then backtest a rule (e.g. buy the top-ranked long-build-up stock's ATM call at a 10:00 pullback to VWAP or the opening range, with a fixed exit). Charge real option costs.
  - Tools: pandas, vectorbt or NautilusTrader, free NSE data. No GPU or paid APIs needed beyond an optional broker data feed.
- Define "order block" mechanically (e.g. the last opposite candle before a move of more than k·ATR) so it can be tested out of sample. Expect the edge to shrink sharply once costs and real-time ranking are used.

**Second-brain relevance:** NONE – Nothing about memory or knowledge storage. The only loose link is the idea of a broker-sourced, timestamped trade log (Sensibull "verified P&L"). A lab version of that (fills imported from the broker API into Postgres) belongs in the second brain's trading-journal layer, but this video offers no tool for it.

---

## V09 | "Robô Phoenix": MT5 gold EA that straddles price with stop orders, trails, and flips with a larger position (DM funnel)
- **Source:** Dropbox video V09 (VID_20261018_120708_721.mp4)
- **Account:** @seurobotrader (watermark, end card) · **Type:** video (72s, Portuguese)
- **Category:** PAID / CLOSED – USABLE (as an idea it is REBUILDABLE; the product itself is a funnel)
- **Lab value:** LOW – the logic is a textbook breakout straddle with stop-and-reverse and position scaling. Easy to rebuild and test; the product itself proves nothing.

**What it says:** Narration in Portuguese, translated:
- "This robot doesn't try to guess where the market goes; it waits for the market to decide first."
- It places one stop order above price and one below. If price breaks up it buys; if down, it sells. Then it trails the stop.
- If the market "changes its mind" and breaks the other way, "it flips: closes the previous position and follows the new direction **with a bigger position**".
- Ending: "Comment **Fênix** and I'll send it to you by Direct."

**On-screen:**
- A MetaTrader 5 chart of **GOLD M1** (prices around 4,430–4,540) filmed off a monitor.
- A custom **"PHOENIX – Driver · Control · Precision"** panel showing server time, trade type (No position / Long / Short), asset GOLD, current/daily/monthly result, daily/monthly/total drawdown, position price and contracts.
- "Buy stop" and "Sell stop" boxes on the chart, with SL/PL labels.
- Caption overlays: "Espera o mercado decidir", "Rompeu ➡️ Entrou", "Mas e se o mercado inverter?", "Ele muda de lado".
- The server clock jumps hours between cuts, which suggests the **Strategy Tester visual mode** or heavy editing rather than live trading.
- **Numbers shown (USD):**
  - Monthly result goes from 0 to 20.87, 38.92, 49.34, 59.75, then down to 46.20 (daily −13.55), then 66.96 and finally 98.20.
  - Repeated drawdown figure: 13.51–13.55.
  - Contracts appear tiny (likely 0.01 lot).

**What's actually behind it:**
- A closed-source MQL5 Expert Advisor sold or distributed by @seurobotrader through Instagram DMs.
- No MQL5 Market listing under this name and seller was found. Search found unrelated "Phoenix" EAs on mql5.com (e.g. "Averaging Phoenix" XAUUSD grid EA, "Super Fenix").
- The strategy is generic: an **OCO breakout straddle + trailing stop + stop-and-reverse with increased size** (a martingale-flavoured reversal).

**Verification:**
- Viewed all 9 contact sheets and read the panel from a crop (work2/V09/p71.png).
- Web searched "Robô Phoenix seurobotrader": no product page.
- Could not verify price, track record, broker or whether any trades were live.

**Claims vs reality:**
- "Doesn't predict, just reacts": true of any breakout system, and not an edge in itself. Straddles on M1 gold get whipsawed in ranges, and the clip itself shows a −13.55 daily drawdown episode.
- "Flips with a bigger position": this is scaling after a loss (martingale-like). It makes equity curves look smooth until a choppy session triggers repeated flips. Risk grows geometrically if there is no cap. The clip does not show the multiplier or a cap.
- **Results shown:** about $98 per month on a micro lot, with no account size, no spread/commission/swap details, and no out-of-sample period. Gold spread on M1 is a major cost for stop-entry systems because the stop fills at the ask/bid plus slippage, and Strategy Tester modelling ("every tick based on real ticks" vs generated) matters a lot.
- It is cherry-picked footage of mostly winning flips.

**Agenda:** A classic Brazilian "robô" funnel: comment a keyword, receive a DM, then likely a paid EA, a subscription, or a broker affiliate (IB) signup. Nothing is free or open.

**Lab use:**
- **Rebuild in an hour or two** in Python on XAUUSD data:
  - Dukascopy tick/M1 data via dukascopy-node, already cloned in batch 1 (scratchpad/repos/dukascopy-node).
  - Backtest with backtesting.py, vectorbt or NautilusTrader (verified in batch 1).
  - Logic: at bar t, place a buy-stop at high+k and a sell-stop at low−k (OCO); trailing ATR stop; on opposite-stop trigger, reverse with size × m (cap the count).
- Test m=1 vs m>1 with realistic spreads (gold 15–30 cents) and slippage, then do walk-forward.
- **Expectation:** with m>1 the tails get fat; with m=1 it's a plain breakout system whose edge on M1 gold after costs is doubtful.
- **Dependencies:** CPU only, free data. **Effort:** half a day.

**Second-brain relevance:** NONE – A trading EA promo with no memory or knowledge component.

---

## V26 | "10 trading platforms that will make you 10k/mo": a list of mainstream paid tools, scanners, brokers and one crypto memecoin terminal
- **Source:** Dropbox video V26 (VID_20261018_121641_987.mp4)
- **Account:** @tess.markets (watermark on screen) · **Type:** video (16s)
- **Category:** USELESS / REPACKAGED
- **Lab value:** LOW – a screenshot-bait list of well-known, mostly paid retail products. Only Interactive Brokers (API) and, to a lesser degree, MetaTrader 5 and Finviz/Koyfin data are useful to a Python lab.

**What it says:** A woman with a mic says "I'm a full time day trader, and I'm telling you right now the platforms that you should be using to trade are where no one else is looking. Here are 10 trading platforms that aren't Robinhood or TradingView. Screenshot this list and save it for later." A static on-screen note titled "TRADING PLATFORMS THAT WILL MAKE YOU 10k/mo" lists:
1. ClickTrade (Click.Trade)
2. TrendSpider (trendspider.com)
3. Trade Ideas (trade-ideas.com)
4. Interactive Brokers (interactivebrokers.com)
5. TradeZella (tradezella.com)
6. Finviz (finviz.com)
7. Unusual Whales (unusualwhales.com)
8. Metatrader 5 (metatrader5.com)
9. Benzinga Pro (benzinga.com)
10. Koyfin (koyfin.com)

Nothing else is said or shown. There is no explanation of how any tool is used.

**What's actually behind it:**
- **Click.trade**, https://click.trade : a closed-source crypto trading terminal ("the execution layer for on-chain finance"). It offers spot trading on Solana/BNB/Base/Robinhood Chain, perps up to 40x on 280+ markets, Polymarket-backed prediction markets, a "Click Monitor" for on-chain flows and launches, and a Chrome wallet. It is non-custodial. The site names no company or team, lists no fees, advertises "spot cashback up to 60%", tiered referral earnings, and an early-access waitlist. In practice it is a memecoin/perps terminal with a referral programme. It is the only unusual item on the list, and it sits at #1.
- **TrendSpider**: paid charting with automated trendlines, scanners and no-code strategy backtests. Closed source, subscription.
- **Trade Ideas**: paid US equity scanner with "Holly" AI signals. Closed, among the more expensive retail tools.
- **Interactive Brokers**: a regulated broker with a full API (TWS/IB Gateway, Client Portal Web API). It is the only item that plugs directly into Python (ib_async, NautilusTrader adapter, Lean).
- **TradeZella**: paid trading journal and analytics SaaS.
- **Finviz**: free stock screener and heatmaps. Finviz Elite (paid) adds real-time data, backtests and exports.
- **Unusual Whales**: options-flow, dark-pool and congressional-trade data. Paid subscription; it also sells an API.
- **MetaTrader 5** (MetaQuotes): free platform supplied through brokers, mostly forex/CFD. The official `MetaTrader5` Python package exists but is Windows-only.
- **Benzinga Pro**: paid real-time news squawk and newsfeed.
- **Koyfin**: freemium fundamentals and charting dashboard.

**Verification:** Viewed both contact sheets; the list is large and legible, so no crop was needed. Read the 4-line transcript. Fetched click.trade to identify it. The other nine are well-known products; their descriptions are from general knowledge and current prices were not re-checked. I could not tell from the video whether the URLs are affiliate links (none of the shown URLs carry referral codes, but there is no caption to check).

**Claims vs reality:**
- "Platforms that will make you 10k/mo": no tool makes money. Most are information or charting subscriptions that cost money every month.
- "Where no one else is looking": false. TrendSpider, Trade Ideas, IBKR, Finviz, Unusual Whales, MT5, Benzinga and Koyfin are among the most widely marketed retail trading products.
- "I'm a full-time day trader": unverifiable. No P&L or trades are shown.
- The list mixes categories without saying so: one broker, one forex platform, one journal, scanners, news, data, and a leveraged crypto terminal.

**Agenda:** Save/screenshot engagement bait. Leading with a referral-cashback crypto perps terminal suggests affiliate or sponsor interest, but this cannot be confirmed without the caption.

**Lab use:**
- **Interactive Brokers:** the one real fit. Use `ib_async` (open source) or the NautilusTrader / QuantConnect Lean IBKR adapters on the server with IB Gateway in Docker. You need an account; market-data subscriptions are paid. Effort: 1–2 days for a paper-trading pipeline.
- **Finviz / Koyfin:** manual idea screening only. Scraping Finviz breaks its terms; for a lab use OpenBB (verified in batch 1) plus free data sources instead.
- **Open-source alternatives to the paid items:**
  - Scanners/backtests (TrendSpider, Trade Ideas): pandas + vectorbt / backtesting.py / NautilusTrader on your own data.
  - Journal (TradeZella): a SQLite/Postgres trades table with a notebook or Streamlit dashboard.
  - News (Benzinga Pro): RSS + SEC EDGAR full-text feeds into the lab.
  - Fundamentals/charts (Koyfin): OpenBB.
- **Skip Click.trade.** An anonymous, closed, high-leverage memecoin terminal with referral cashback is not lab infrastructure.

**Second-brain relevance:** LOW – Only TradeZella touches memory (a hosted trade journal: capture of trades and notes). It is paid SaaS, not self-hostable, and not reachable by your agents except through exports. The lab version is a self-hosted trades/journal table (Postgres or SQLite) that the second brain indexes alongside research notes, exposed to agents through the same MCP or API layer as the rest of your memory.

---

## V06 | Order-flow futures bot shown as a NinjaTrader backtest equity curve, with no details
- **Source:** Dropbox video V06 (VID_20261018_115950_519.mp4)
- **Account:** @orderflox.algo (watermark, end card) · **Type:** video (12s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – one equity curve and the claim "first ever algo based on orderflow". No rules, code or out-of-sample numbers.

**What it says:** There is no speech; the audio is music ("Adele • Skyfall" music tag). The overlay text reads "WE FINALLY CODED THE FIRST EVER ALGO BASED ON ORDERFLOW". The phone pans across two monitors:
- **Left monitor:** a NinjaTrader 8 **Strategy Analyzer** with a smooth green cumulative-net-profit curve. The visible x-axis runs over about 11,000 trades and the y-axis tops out around $44–48k. The bottom grid lists a strategy named roughly "ORDERFLOX" on a 1000-tick data series, with three backtest rows.
- **Right monitor:** an **MZpack 3.15** footprint chart of **MNQ 09-25** (Micro Nasdaq futures) on 1000-tick bars, with a delta / delta % / cumulative delta table and a volume profile.
- The analyzer's period list shows dates around 12/1/2025.

**What's actually behind it:**
- **NinjaTrader 8:** a commercial futures trading platform. It is free to use with sim data; live trading and lifetime licenses are paid. Windows only.
- **MZpack (mzpack.pro):** a paid, closed-source NinjaTrader order-flow add-on that provides footprint, big trades, volume profile and a strategy API. A web search found premium pricing quoted at about €49/month or €399 lifetime.
- **"ORDERFLOX" strategy:** private and not published. There is no website, repo or product page.

**Verification:**
- Read the on-screen UI from enlarged frame crops (work2/V06/t0.png, t4.png).
- A web search for "orderflox algo" returned nothing; only MZpack and NexusFi threads came up.
- Could not verify: the strategy logic, the fee/slippage settings, the backtest dates, or whether the results are in-sample.

**Claims vs reality:**
- "First ever algo based on orderflow": **false.** Order-flow and delta-based automated strategies are decades old (HFT, market making). Retail versions are sold for NinjaTrader, and MZpack itself ships a strategy API for exactly this. The open-source OrderFlowBot for NinjaTrader also exists.
- The equity curve looks very smooth over about 11k trades. That is typical of an in-sample, optimised backtest on tick data. NinjaTrader's default backtests fill at the limit or touch, with no queue position, and commission is often left at $0 unless it is set. Order-flow signals on 1000-tick bars are highly sensitive to fill assumptions. Treat the curve as unverified.
- No drawdown, Sharpe ratio, out-of-sample split or live statement is shown.

**Agenda:** A teaser account built around the bot ("orderflox"). It most likely leads to a paid bot, a license or a Discord. No price or link is shown in the video.

**Lab use:**
- **What you can rebuild:** delta, cumulative delta and footprint-imbalance features from tick data with aggressor side, in Python. NautilusTrader (verified in batch 1) handles trade ticks and order-book deltas with realistic fills.
- **Data:** CME futures tick data with aggressor flags is paid (for example Databento). Crypto exchanges provide free trade data with a side flag, which is the cheapest place to prototype.
- **Effort:** 1–2 weeks for a delta-imbalance signal with an honest backtest (queue and slippage modelling).
- **Open-source alternative:** NautilusTrader + Databento/crypto data; WaleeTheRobot/order-flow-bot as a NinjaTrader reference (not cloned; named from search only).

**Second-brain relevance:** NONE – A trading-bot teaser with no memory, knowledge or agent-context content.

---

## V13 | "Range sniper" automated futures system: TradingView strategy → TradersPost → Apex prop accounts on Tradovate (waitlist funnel)
- **Source:** Dropbox video V13 (VID_20261018_121124_525.mp4)
- **Account:** @tradingsignals.lfg · **Type:** video (30s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – the pipeline (TradingView alert → webhook bridge → broker) is real and well known. The strategy is closed and unnamed apart from a label, and the evidence is a 3-day backtest window plus one day of prop-account P&L.

**What it says:** The overlay reads "This is how the range sniper works". He says "this was me manually trading and this was my automated trading system", pointing at a **Tradovate** web trader (`trader.tradovate.com`) with Accounts rows APEX414834000007x/8x (Apex Trader Funding prop accounts).

Account P&L in the crop:
- Three accounts green: +$543.68, +$535.68, +$535.68
- Several red: ($695.86), ($877.94), about ($1,0xx) ×3; one with ($170.00) open

He then shows a **TradingView** chart of MNQ1! (Micro E-mini Nasdaq-100 futures, **30-second** bars, CME) with "Long TP" labels and a green moving-average line. The strategy tester reads:
- "ConFluX Advanced Strategy V3", **Jul 28 – Jul 30, 2026**, 50K USD capital
- Total PnL **+$4,777 (+9.55%)**
- Max drawdown **$935 (1.83%)**
- Profitable trades **80.95% (17/21)**
- Profit factor **4.935**

A side panel shows a multi-timeframe trend table. Next is the **TradersPost** landing page ("Your secret edge in trade execution"): "it gets sent over to this website which then gets sent over to your accounts". He closes with: "It's not open to the public but we do have a waitlist… comment the word ACCESS and we'll send that free access over."

**What's actually behind it:**
- **TradingView**: a paid/freemium charting platform. Pine Script strategies plus webhook alerts need a paid plan.
- **TradersPost** (https://traderspost.io): a commercial, paid SaaS webhook bridge from TradingView and other signal sources to brokers (Tradovate, TradeStation, NinjaTrader, tastytrade, ProjectX…). It is non-custodial and explicitly does not provide signals.
- **Tradovate**: a futures broker and platform used by most futures prop firms.
- **Apex Trader Funding**: a futures prop firm (evaluation-fee business model). Secondary sources (TradersPost blog March 2026, PickMyTrade FAQ July 2026) say Apex allows only semi-automated trading with active oversight and prohibits fully automated set-and-forget bots on funded accounts. Confirm with Apex directly.
- **"Range sniper" / "ConFluX Advanced Strategy V3"**: a closed, unpublished Pine strategy. A web search found nothing for either name.

**Verification:** I viewed all four contact sheets and read upscaled crops of the Tradovate accounts table, the TradingView header, and the strategy-tester stats. I searched the web for "Range Sniper", tradingsignals.lfg and TradersPost (TradersPost confirmed as a real bridge; no trace of the strategy) and for Apex's automation policy (secondary sources, conflicting). I could not verify the strategy logic, the waitlist product, or any live track record.

**Claims vs reality:**
- "Automated beats manual" (green vs red accounts): this shows one session. Three bot accounts made about $540 each and the manual accounts lost. It also shows he loses money trading manually, and nothing about the bot over months.
- Backtest stats (80.95% win rate, PF 4.9, 1.8% DD): the window is **3 days and 21 trades** on 30-second bars. That is statistically meaningless and easy to cherry-pick or overfit. TradingView backtests on sub-minute bars without bar magnifier are also prone to fill optimism, and commission and slippage settings are not shown.
- "Free access": the classic hook. Waitlist and "comment ACCESS" lead to a DM, then usually a paid signal group, Discord, or prop-firm affiliate links. The account handle itself is "tradingsignals".
- Running fully automated bots on Apex accounts may violate Apex rules, which risks account termination.

**Agenda:** A "comment ACCESS" waitlist funnel for a signal or automation service, plus implicit promotion of TradersPost and prop-firm evaluations (both have affiliate programs). Engagement farming.

**Lab use:**
- Nothing to download. The architecture is reproducible with open source and no SaaS:
  - Signal side: a Python strategy in NautilusTrader (backtest and live share the same code), or a Pine strategy with webhook alerts.
  - Bridge side: a self-hosted FastAPI webhook receiver that places orders through a broker API, instead of TradersPost.
  - Tradovate's API needs a funded account and API add-on; Interactive Brokers works via `ib_async`.
- For an MNQ range or ORB-type idea: get CME micro futures bars (Databento, paid per GB, or your broker's history). Backtest at least 2–3 years with commissions of about $0.50–1.00/side/contract and 1-tick slippage, and check the result across regimes. Effort: 2–4 days for a first honest test.
- If you trade prop accounts, read the firm's automation rules first.

**Second-brain relevance:** NONE – no memory or knowledge component. At most, it is a reminder to keep a trade journal (per-account fills, strategy version, regime notes) in your lab DB so you can judge systems on long records instead of 3-day screenshots.

---

## V16 | "3 most dangerous websites": Forex Factory for news, plus blind copy-trading of a "93% win rate" trader on Invo (a Hyperliquid social-trading app), behind a "comment SITE" funnel
- **Source:** Dropbox video V16 (VID_20261018_121248_523.mp4)
- **Account:** @linny.trades (watermark on every frame and the end card; the logged-in Invo account in the corner reads "Linny Fong @linnytrades") · **Type:** video (46s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – Forex Factory's economic calendar is a real free reference, but the main pitch (copy a stranger's trades because of a 93% win rate) is gambling advice with no testable content.

**What it says:** Title card: "3 Most Dangerous Websites (to become profitable quick)". Only **two** sites are shown. "1. FxFactory" (really **Forex Factory**, the screen shows its news/calendar page with an OANDA ad) "tells you the news before the TV news comes out". "2. Invo": find "a profitable trader on a site like X" (she opens X profile **@Prateek0x_**, "Prateek_0x", 2,487 posts, memecoin/"Robinhood chain trenches" posts), copy the username, search it in Invo (URL `…app.com/discover/user_search`), open a profile and point at a "Casino" portfolio: **1,485 closed trades, 93% win rate, +800.64%** P&L; smaller portfolios show 91% / +1,193%, 86% / +34.84%, 82% / +120.41%. She clicks Follow, turns on "Post Notifications" and "Trade Alerts", and says "every single time he places a trade you're going to place the exact same trade… literally the easiest way to get rich with trading". Overlay: "Comment 'SITE' for the link". The page header says "Not Financial Advice".

**What's actually behind it:**
- **Forex Factory** – https://www.forexfactory.com. Free, ad-funded forex forum, economic calendar and news aggregator (owned by Fair Economy). The calendar is the useful part. It does not deliver news "before TV" in any meaningful edge sense; scheduled releases are public and HFT firms trade them in milliseconds.
- **Invo ("invo: involio", Involio Inc.)** – https://invoapp.com, iOS app id1601301148. Closed-source crypto social-trading app built on **Hyperliquid** perpetuals (170+ futures pairs). It lets users view "verified" trader portfolios, copy positions, and lets creators sell content tied to their portfolios. The site gives no fee schedule, no definition of "win rate", and no risk disclaimer on the homepage. Reported ~$1.49B 30-day volume through its Hyperliquid builder code (Crypto Briefing).
- **The trader shown** – the X account is @Prateek0x_. The Invo profile she opens is a *different handle*, **@prateek**, whose bio reads "Discord-@prateek.3126 · Underdogs Lead · Invo Discord #8 & #7" with 39K followers. So the profile is an Invo community/Discord figure, and nothing on screen proves it is the same person as the X account; the search list shows several other "Prateek" accounts (@prateekox88, @prateek_ox …).

**Verification:** Viewed all 6 contact sheets; cropped frames of the X profile, the Invo search page/URL and the portfolio stats. Web search and a fetch of invoapp.com confirmed what Invo is (closed, Hyperliquid-based, copy trading). No search result for "linny.trades". Could not verify how Invo computes win rate, whether the 93% portfolio is net of fees, or whether the creator is paid by Invo (an affiliate/creator deal is likely given the "comment SITE" funnel but is not shown).

**Claims vs reality:**
- "3 most dangerous websites": only 2 are shown; the third is presumably in the DM.
- "Tells you the news before the TV": it is a calendar of scheduled releases and a forum. Useful, not an information edge.
- "93% win rate, are you kidding me": win rate alone means nothing. A 93% win rate with +800% total over 1,485 trades is consistent with many tiny wins and occasional large losses (the classic memecoin/"casino" profile, and the portfolio is literally named "Casino"). No drawdown, average loss, position size or time period is shown, and the stat is from a self-selected leaderboard (survivorship bias).
- "Place the exact same trade so you can profit just like him": copy-trading on perps adds latency, slippage and different fills; followers enter after the leader, on thin memecoin-style liquidity, and can be exit liquidity. Leverage on Hyperliquid perps can liquidate a follower long before the leader's stats look bad.
- "Literally the easiest way to get rich": false; this is engagement bait. The page's own "Not Financial Advice" banner contradicts the framing.

**Agenda:** "Comment SITE for the link" DM funnel, almost certainly a referral link to Invo (her own Invo account is visible). Thirst-trap opening for reach. Sells a product, not a method.

**Lab use:**
- Forex Factory: scrape or manually use the economic calendar for event filters (avoid trading around high-impact releases). Free, but scraping may break their ToS; cleaner free sources are FRED/ALFRED release calendars and the BLS/BEA schedules.
- Invo itself: not usable in a self-hosted lab (closed app). If the idea of "follow good traders" interests you, the lab version is to pull public Hyperliquid fills with the open-source `hyperliquid-python-sdk` (cloned in batch 1, `scratchpad/repos/hyperliquid-python-sdk`) and analyse wallets yourself: win rate *and* payoff ratio, max drawdown, tail losses, and how a copied fill would have slipped. Effort: 1–2 days. No GPU, no paid API.
- Do not copy-trade real money based on a leaderboard win rate.

**Second-brain relevance:** NONE – Nothing about memory, notes or agent context. The only tangential idea is keeping a journal of "who I followed and how it went", which any markdown trade log covers.

---

## V20 | "One candle is all you need": ICT-style 4H order-block/FVG + 15-minute "rejection block" 50% limit entry on NQ futures, 10-point stop, 6R target, "90% win rate", behind a "comment REJECTION BLOCK" funnel
- **Source:** Dropbox video V20 (VID_20261018_121511_101.mp4)
- **Account:** @nq.rich (watermark on most frames and the end card) · **Type:** video (55s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – the entry rule is concrete enough to code and backtest (which is the only useful thing to do with it), but the "90% win rate at 6R" claim is impossible as stated and the evidence is a cherry-picked table.

**What it says:** "Trading became extremely easy when I realized that one candle is literally all you need to be profitable… I have around a 90% win rate just by using this simple strategy." Rules: (1) on the **4-hour** chart mark "PD arrays" – **order blocks, fair value gaps** (chart labels "4H OB", "4H OB MT" = mean threshold); (2) drop to the **15-minute** chart and wait for price to trade into a 4H level; (3) wait for a 15-minute **rejection block** off that level (a long-wick candle closing back above it); (4) mark the **50% point** of that rejection candle's wick (Fib 0 / 0.5 drawn on the wick) and place a **limit order** there with a **10-point stop**, **targeting 6R**. "Plays out insanely fast with very little drawdown." Ends: "save this video… follow me and comment the word rejection block" to get the full breakdown video.

On-screen evidence: TradingView-style position tool "Target 63.00 / Risk-reward ratio 6 (6.05) / Stop 10.50"; order tickets with 26 and 3 contracts and P&L tags (−39, +1,807, −195, +2,460, +3,780, +1,785, −690 USD); a dark table (Notion-style) with six rows all "Win" – $1,355 (3R), $19,000 (6R), $17,000 (7R), $7,987 (8R), $18,960 (4R), $24,354 (7R) – and a footer "**NOT EMPTY 90.909%** · SUM $126,652.52" circled in red.

**What's actually behind it:**
- Concepts are from **ICT (Inner Circle Trader, Michael Huddleston)** "smart money concepts": PD (premium/discount) arrays, order blocks, fair value gaps, mean threshold, rejection blocks. Free on ICT's YouTube; widely repackaged in paid courses. No academic evidence that these labels add predictive power beyond generic support/resistance and mean reversion.
- **NQ** = CME E-mini Nasdaq-100 futures ($20 per point; 10 points = $200 per contract). With 26 contracts the stop is ~$5,200 of risk – prop-firm/large-account sizing.
- No repo, tool or product is named.

**Verification:** Viewed all 7 contact sheets; cropped the results table and the position-tool labels. Web search for "nq.rich" / "nqrich" found nothing about the creator (only unrelated TradingView rejection-block indicators). Could not see the account history, the full trade list or the paid "breakdown video".

**Claims vs reality:**
- "~90% win rate": the only number shown is "NOT EMPTY 90.909%", which is a column aggregate (percent of rows where the field is filled – 10 of 11 rows), not a computed win rate of an audited trade log. Only six rows are visible, all wins. A sample of ~11 trades is statistically meaningless even if genuine.
- "90% win rate while targeting 6R": as stated this would be an expectancy of ≈ 0.9×6 − 0.1×1 = **+5.3R per trade**, which no public strategy sustains; real 6R-target systems typically win 15–30% of the time. The table itself contradicts the rule: wins are 3R, 4R, 7R and 8R, not a fixed 6R, so exits were discretionary.
- "One candle is all you need": the setup needs 4H level marking (subjective: which OB/FVG?) plus a 15-minute rejection candle plus a limit at its 50% – discretionary, hard to replicate exactly, and the visual examples are hand-picked winners (green check marks).
- "Very little drawdown": no equity curve, drawdown or loss list is shown; red P&L tags (−39, −195, −690) appear on screen.
- Missing: commissions, slippage on limit fills, missed fills (price often doesn't come back to 50%), time period, and whether this is live, sim or prop-firm evaluation money.

**Agenda:** Follow + "comment rejection block" DM funnel to a longer video, the usual front of an ICT-style course/mentorship/Discord funnel. Large dollar figures ($126k sum) are the hook.

**Lab use:** Treat it as a hypothesis to falsify, not a strategy:
- Data: NQ 15-minute and 4-hour bars (free options are limited: QQQ/NDX proxies via yfinance; real NQ futures from Databento/Polygon/Kibot are paid; or use crypto perps as a free test bed).
- Code: define 4H order blocks (last opposite candle before a displacement) and FVGs (3-candle gaps) mechanically; detect a 15m rejection candle that wicks into the zone and closes outside; place a limit at 50% of the wick, stop 10 pts (or wick-relative), target 6R, with a session/time cutoff. Backtest in vectorbt/backtrader/NautilusTrader (verified in batch 1) with $2–5/contract round-trip costs and no fill if price only touches the limit.
- Report win rate, payoff, expectancy, max drawdown and number of trades over several years, and compare with random entries at the same zones. Effort: 1–2 days. No GPU, no paid API (except futures data).
- Open-source ICT indicator ports exist : e.g. https://github.com/joshyattridge/smart-money-concepts (PyPI `smartmoneyconcepts`, MIT, shallow-cloned, last commit 2026-04-03), which has order block, FVG and liquidity functions and can save time on zone detection.

**Second-brain relevance:** NONE – Pure discretionary trading content. The only tangential lesson is the value of a real, complete trade journal (every trade, losses included, with R and screenshots) stored in the lab, as opposed to a screenshot of a filtered table.

---

## V24 | "6-agent AI trading desk turned $10 into $4k overnight": a Spanish-language memecoin dashboard ("ALOOK AI / MESA DE TRADING") used as a DM-funnel hook
- **Source:** Dropbox video V24 (VID_20261018_121624_317.mp4)
- **Account:** @seb.ai (watermark and end card) · **Type:** video (53s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – there is nothing to install or verify, and the headline claim contradicts the dashboard's own numbers. The only takeaway is the generic idea of role-split agents with a human approval gate, which open-source projects already implement.

**What it says:**
- Overlay: "I BUILT A 24 SEVEN TRADING DESK THAT TURNED $10 INTO $4k IN ONE NIGHT 😱📈". Spoken: "an AI trading desk that never sleeps", 6 AI agents, "made around $4,000 last night", "built the entire thing with AI in just a couple of minutes".
- Agents:
  - Atlas "watches the big wallets"
  - Vega "scans X for narrative spikes"
  - Oren/Orion "builds the trade thesis and decides the size"
  - Titan "prepares the order"
  - Luna "helps handle execution"
  - Nova "checks the contract and liquidity and risk limits"
- "Claude Code handles reasoning, Codex handles execution tasks, and Grok watches for new information." It "runs 24/7".
- Overlays: "SAVE THIS VIDEO" and "COMMENT DESK AND I'LL SEND YOU THE ENTIRE SET UP GUIDE".
- Laptop dashboard (cropped, `work2/V24/dash1.png`):
  - Header: "ALOOK AI / MESA DE TRADING ● LIVE", uptime 07:07:52, "AGENTES 6", "OWNER GUS"
  - Balance $48,762.81, "initial $45,000.00"; "PNL DE LA NOCHE +$3,762.81 (+8.4%)"
  - "OWNER GATE 0 en cola – solo sale si aprueba gus" (orders only go out if Gus approves); "WIN RATE 73.2%"
  - Overnight balance chart, 7.1h/24h
  - Event log "SALA @mesa, 1479 EVENTOS" with lines such as "atlas SCAN 412 wallets, 3 entradas grandes", "vega SCAN 721 posts en X, $GOOSE neto +0…", "nova VERIFIED $RBNX contrato y liquidez ok", "titan ORDER $RBNX 0,8% slippage máx 1,5%", "titan CERRADA $FEATHR take profit +$186,32", "nova STOP $ARMHZ stop tocado −$48,29"
  - Agent tiles: ORION (labelled "Claude Code"), VEGA, TITAN, LUNA, NOVA, ATLAS

**What's actually behind it:**
- No repo, product, site or exchange is named, and nothing can be checked.
- The dashboard is a custom web UI in Spanish with a hard-coded "OWNER GUS". It looks like a single-file HTML/JS mock of the kind Claude generates in minutes.
- The tickers ($GOOSE, $RBNX, $FEATHR, $HOOOIE/$MOONR, $ARMHZ) read as small memecoins or placeholders. No chain, DEX, wallet address or exchange is visible.
- Pieces that do exist: Claude Code, OpenAI Codex and xAI Grok (all paid); X data needs the paid X API or scraping; "big wallet" tracking would be an on-chain analytics API (Birdeye, Helius, Nansen and similar, mostly paid).

**Verification:** Viewed all 7 contact sheets. Cropped the dashboard header and event log (two crops in `work2/V24/`). Read the transcript. No names were searchable: no repo, URL or product. Did not web-search "ALOOK AI" further because the clip itself gives nothing linking it to a real product. Whether any trade was real cannot be verified.

**Claims vs reality:**
- "$10 into $4k in one night": contradicted on screen. The dashboard's initial balance is $45,000; the night's P&L of about $3.7–4.6k (it ticks between frames) is about 8–10% on $45k, not 400×.
- "Made around $4,000 last night": no broker or on-chain proof. A self-built dashboard can display any number, and nothing shown is a fill from a venue.
- "Built the entire thing with AI in a couple of minutes": plausible for the UI. A live system that safely trades memecoins (wallet keys, MEV and slippage, rug checks) is not a couple of minutes' work.
- "Runs 24/7 with 6 named agents": persona names layered over what is basically a pipeline (signal → thesis → sizing → order → risk check). The design itself is sensible, including the human "owner gate", which is the most credible detail.
- Overnight memecoin P&L with a 73% win rate tells you nothing about expectancy. Memecoin trading has extreme tail risk.

**Agenda:** Classic "comment DESK and I'll send you the setup guide" DM funnel for engagement and follower growth, with a likely lead magnet or paid guide behind it. The "$10 into $4k" hook is engagement bait.

**Lab use:**
- Do not try to replicate the claimed returns.
- If you want a role-split agent desk for research (not live memecoin trading), use open source:
  - TradingAgents (Apache-2.0, verified batch 1: analyst/researcher/trader/risk-manager agents)
  - Vibe-Trading (verified batch 1)
- Run it on paper trading with nautilus_trader or a broker paper account, and keep the human approval gate (the one good idea here).
- On-chain or crypto pieces need paid data APIs, and X sentiment needs the paid X API.
- Effort: days to wire, weeks to evaluate honestly.

**Second-brain relevance:** LOW – The dashboard's shared event log ("SALA @mesa", 1,479 events, agents addressing each other with @mentions) is a primitive shared blackboard: agents coordinate through one append-only event stream. That idea is relevant to a lab memory design, in which each agent writes decisions and outcomes to a shared, queryable log. But nothing here is a memory system, nothing is self-hostable as shown, and nothing is shareable across VMs. For real cross-agent memory use Hindsight (banks per agent or desk, MCP per bank) or GBrain (HTTP MCP with per-agent tokens), both verified in batch 1.

---

## V28 | "Sniper Range Bot V2 has a 93% chance of passing a 50k prop eval": a TradingView MNQ backtest plus a trade-shuffle Monte Carlo, used as a DM funnel
- **Source:** Dropbox video V28 (VID_20261018_121707_812.mp4)
- **Account:** @algo.jitnems (watermark) · **Type:** video (52s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – the strategy is closed and sold through DMs. The only lab takeaway is a cautionary example of why a trade-order-shuffle Monte Carlo does not prove an edge, and how to model prop-firm pass rates properly.

**What it says:** "This automated trading strategy has a 93% chance of passing a 50k eval. The strategy I'm talking about is Sniper Range Bot V2."

He shows a TradingView backtest "over the past year": "total PNL of almost $39,000 on one 50k account and a 73% win rate". The burned-in subtitle wrongly says "on 150k account". He then runs it "through what's called a Monte Carlo simulation, essentially testing your strategy thousands of times in random order to see if you actually have an edge… the results are just ridiculous": "138 trades, average expectancy of $278", "93.36% pass rate… out of 10,000 simulated equity paths, we passed 9,336 evals".

Close: "If you want access to the strategy to start taking consistent payouts like our members, comment ACCESS and I'll DM you." A large "Access" overlay appears, along with payout certificates from Tradeify ($728 "Verified Payout", Hansel E.; another to "Bryson S." dated September 18, 2026, "LIVE FUNDED") and Lucid ($1,397 to JHONNMARQUEZ).

On screen:
- **TradingView strategy tester:** MNQ1! (Micro E-mini Nasdaq-100 futures, CME), 15-minute chart; long/short entries with TP/SL labels; a "Jesus is King" watermark.
- **Strategy "Sniper Range Bot V2"**, range Nov 30, 2025 – Oct 9, 2026, initial capital 50K USD.
- **Key stats:**
  - Total PnL +38,390.50 USD (+76.78%)
  - Max drawdown 1,973.50 USD (3.85%)
  - Profitable trades 73.19% (101/138)
  - Profit factor 2.711
- **A "Quantitative Strategy Performance Review – Automated Trading System · Evaluation Capital Readiness Report" PDF:**
  - Text in obvious LLM house style ("highly resilient automated trading system… robust capital preservation").
  - Metrics: 138 trades, 73.19% win rate, avg net P&L/trade $278.19, gross historical profit $38,390.50.
  - Monte Carlo of 10,000 iterations with starting equity $50,000, profit objective $3,000 (6%), risk threshold $2,000 maximum trailing drawdown (4%).
  - "Simulation Verdict: 93.36% Pass Rate… 9,336 out of 10,000 simulated equity paths".
- A "Monte Carlo Equity Curve Simulation (50K Combine Model)" chart.

**What's actually behind it:**
- **Sniper Range Bot V2**: no public listing found. A web search found no TradingView script by that name (similarly named range-breakout MNQ scripts exist, e.g. "AM Range Sniper [jmaxxx]", but nothing links them). It is a private, likely invite-only Pine strategy sold via DM. No code, rules, session times or cost settings are shown.
- **Tradeify and Lucid Trading**: real futures prop-evaluation firms; the payout certificates are their standard share graphics. They show that someone received payouts, not that this strategy produced them or what the evaluation fees were.
- **The "Monte Carlo"**: from the description and chart, an i.i.d. reshuffle/resample of the 138 backtest trades, checked against a $3k target before a $2k trailing drawdown.

**Verification:**
- Viewed all 7 contact sheets.
- Cropped the strategy-tester stats, the PDF header and metrics, the MC chart title and the payout certificates.
- Web search for "Sniper Range Bot" found nothing (unverified product).
- Arithmetic check: $278.19 × 138 = $38,390 ✔. 38,390.5 / 50,000 = 76.78% ✔.
- Not verifiable: commission and slippage settings, contracts per trade, whether the strategy repaints or uses intrabar/lookahead features, and the price of "access".

**Claims vs reality:**
- "93% chance of passing a 50k eval": this is a simulation of in-sample backtest trades, not a forward probability.
  - Shuffling the order of the same 138 trades preserves their mean ($278). So with a $3k target and only ~11 winning-expectancy trades needed, a high pass rate is nearly guaranteed by construction.
  - It inherits all backtest overfitting, and assumes trades are independent (no regime clustering).
  - It ignores the eval's daily loss limit, consistency rules and real fills.
- "Monte Carlo… to see if you actually have an edge": false. Reordering trades cannot reveal whether an edge exists. Only out-of-sample or forward data, or permutation tests on the price data (not the trade list), can.
- The backtest's own max drawdown was $1,973.50, within $26.50 of the $2,000 trailing limit used in his simulation. On the actual historical path the strategy came within one small loss of failing the eval.
- 73% win rate with profit factor 2.71 implies average win ≈ average loss. That is plausible for a range strategy, but on 15-minute bars TradingView's default fill assumptions (orders at bar close or limit fills on touch) flatter scalping systems. No commission/slippage setting is visible.
- About 10 months, 138 trades, one instrument, one regime (a strong Nasdaq uptrend). Not "consistent payouts" evidence.
- The PDF says "live executions", while the video calls it a back test. This is a contradiction, and the report reads as AI-written marketing.
- Payout certificates are of unknown attribution ("like our members"). Prop-firm payouts are routinely smaller than total evaluation fees spent.

**Agenda:** A "Comment ACCESS" DM funnel into a paid strategy or membership (members, payouts). It is also a prop-firm funnel: buy evals and run the bot. Possible affiliate links to Tradeify or Lucid (not verifiable without a caption).

**Lab use:**
- Nothing to install; the strategy is closed.
- What is worth building yourself (1–2 days, pure Python, CPU):
  - A prop-firm eval simulator that takes a trade or equity series from your own backtests (NautilusTrader / vectorbt) and applies real rules: trailing drawdown on intraday unrealised equity, daily loss limit, consistency rule, minimum days, fees per attempt. Output the pass probability and expected cost per funded account.
  - For robustness, use block bootstrap (preserve autocorrelation), walk-forward/CPCV (skfolio, verified in batch 1, has CombinatorialPurgedCV), the deflated Sharpe ratio, and Monte Carlo permutation of price paths. Not trade shuffling.
- Data: MNQ/NQ futures minute bars (Databento paid, or free continuous-contract proxies), with realistic $0.50–1.00 round-trip commission plus 1 tick slippage per side.

**Second-brain relevance:** NONE – No memory or knowledge component. The one transferable habit is to store every backtest's parameters, trades and Monte Carlo settings in the lab's experiment log, so claims like this can be checked against your own records. That is a generic experiment-tracking need (MLflow, or a Postgres table indexed by the second brain), not something this video provides.

---

## V02 | Omarchy (DHH's Arch/Hyprland desktop distro) pitched as "the first AI agent operating system" that fixes and upgrades itself
- **Source:** Dropbox video V02 (VID_20261018_115729_377.mp4)
- **Account:** @julian.goldie_ (watermark and end card) · **Type:** video (34s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – Omarchy is real, free and MIT-licensed, but it is a laptop/workstation desktop, not a headless quant server, and the video's claims overstate what it does.

**What it says:** Julian Goldie films his monitor showing omarchy.org ("Beautiful, fun & agentic Linux by DHH", "The malleable OS for the age of agents", "We can fix every paper cut", "Install Omarchy... as little as 35 seconds", "Download Omarchy 4.0.3", "Try it first" in a VM, "A plugin for every dream"). He says: "Omarchy is the first AI agent operating system built for AI agents, which means your computer can now fix and upgrade itself... a free forever software... comes with an AI that builds apps for you... installs in under a minute and lets AI do all the hard setup." He ends with "link in the bio".

**What's actually behind it:**
- Omarchy: https://github.com/basecamp/omarchy (site omarchy.org). **MIT** licence, © David Heinemeier Hansson. Verified in batch 1 (entry DeEtB78jJtu); I re-checked the existing clone today: last commit 2026-10-18 and very active. The website shows release 4.0.3 ("Quattro"). It is an opinionated Arch Linux + Hyprland desktop setup.
- The "agentic" part is a set of launchers and helpers: `bin/omarchy-agent*` (more than 15 scripts) that install and launch coding-agent CLIs (Claude Code, Codex, OpenCode, Grok and others via mise), show subscription usage, switch accounts and hand crash dumps to your agent, plus an experimental skill that lets an agent edit desktop configs. It does not bundle an AI model; you bring your own agent subscription or API key.

**Verification:** Viewed all 5 contact sheets and cropped the omarchy.org hero, the "fix every paper cut" section and the install section (URL `omarchy.org/#home`, version 4.0.3 visible). Reused the batch-1 verification and the existing clone at `repos/omarchy` (README, LICENSE, `bin/omarchy-agent`, `git log`). A web search confirmed that Goldie sells a paid Skool community.

**Claims vs reality:**
- "First AI agent operating system": no. It is a desktop distro with agent-CLI launchers. Any Linux box can run the same agents.
- "Your computer can now fix and upgrade itself": partly. An agent you install and pay for can edit configs or diagnose crashes when you ask it to. Omarchy's own manual calls the config-editing skill experimental and advises rollback.
- "Comes with an AI that builds apps for you": no AI is included. It launches third-party agent CLIs that need their own subscriptions.
- "Free forever": the distro is free (MIT). The agents are not.
- "Installs under a minute": the site says "as little as 35 seconds on the fastest machines... less than two minutes on the majority". It needs a full-disk or dual-boot install from USB.

**Agenda:** "Link in the bio" leads to Julian Goldie's funnels. He runs an SEO agency and a paid Skool community, "AI Profit Boardroom" (about $59–71/month according to its Skool listing and his own sites). This video is generic AI-news engagement content.

**Lab use:**
- Not for the quant server: Omarchy needs a GUI, and a headless edition exists only as a plan document in the repo.
- On a personal workstation, install from the ISO at omarchy.org (wipes or dual-boots the disk); try it in the VM first.
- Server alternative: install Claude Code, Codex or OpenCode directly on your existing distro. That takes under an hour.

**Second-brain relevance:** NONE – A desktop distro with agent launchers. It has no memory, storage, retrieval or cross-machine sharing component.

---

## V12 | "AI-cloned Bloomberg terminal + Grok bots turned $4k into $17k in a day": a re-narrated X post about meme-coin bots
- **Source:** Dropbox video V12 (VID_20261018_121059_212.mp4)
- **Account:** @seb.ai · **Type:** video (45s)
- **Category:** HYPE / UNREAL
- **Lab value:** NONE – no code, repo or method is shown. The P&L is a single day on a Solana meme coin, taken from someone else's engagement-bait X post that itself pushes an exchange referral.

**What it says:** The overlay reads "SOMEONE USED AI TO CLONE A 32,000 A YEAR BLOOMBERG TERMINAL 😱", then "COMMENT TERMINAL AND I'LL SEND YOU THE ENTIRE SETUP GUIDE" and "‼SAVE THIS VIDEO‼". Seb says the person fed screenshots of the terminal to an AI until every panel looked the same, connected his own market data, charts, news and "bot signals", and let "Grok trading bots" trade 24/7. He says this turned "$4,000 into $17,000 in one day", "thousands of dollars each hour", and was built "in a couple of hours". The screen shows a Bloomberg-styled dashboard: red/orange function bar, "POMO"/"FOMO"-style logo, a pixel-art "office" of bot desks, candles, an equity curve and a news ticker. He then scrolls an X post (status ID 2110371393774768504; tab "(16) savip…"; the "Relevant people" box shows "savip.").

The X post text, read from crops:
- "mine took one evening, zero code, and it trades them / i fed AI screenshots until every panel matched / then i plugged in my Grok bots and went to bed / one of their trades still makes no sense to me / day 2, they started with yesterday's $4,236"
- "the coin: TeleMoney, a meme coin that pays its fees to any Telegram name"
- Trade list:
  - "9:15am in at $287K, out at $425K, +$1,381"
  - "2:15pm back in at $287K, out at $776K just before the top, +$5,862"
  - "6:00pm $382K to $564K, +$3,732"
  - "8:50pm they chased a spike, -$965"
  - "12:50am $362K to $430K, +$1,849"
  - "4:45am out at $398K before the morning dump, +$1,716"
  - (the K figures are market caps)
- "$1,000 left in the coin all day ended at $1,094 / my bots did 4.2x on the same chart / at 0:06 they buy back the coin they sold 2 hours earlier, 32% cheaper / the funniest part, the news feed at the bottom is just my bots texting each other"
- "$4,236 → $5,618 → $11,480 → $15,212 → $14,247 → $16,097 → $17,868"
- "how i cloned it and every rule my bots follow is in my article below ↓ free / **my first reply has the exchange they trade on, new accounts get a bonus** / bookmark this before you pay for another trading tool / forward it to whoever still pays for theirs / which paid app would you clone first?"

The browser bookmarks of the person filming show "Axiom SOL | Pulse" (a Solana meme-coin trading terminal) and "Replit – Build apps". The left sidebar shows a logged-in account ending "…menForgeDev".

**What's actually behind it:**
- **No repo, no code, no tool name.** The "terminal" is a custom-styled web dashboard (a Bloomberg look-alike UI). Nothing about it is published in the video.
- **TeleMoney (TM):** a real Solana token and launchpad tool. It launches pump.fun coins and routes creator fees to a Telegram @username (Bitrue blog; Phantom lists the TM token as unverified, contract `6KDp…pump`). It is a days-old, extremely volatile meme coin.
- **"Grok bots":** unspecified. It presumably means LLM prompts calling xAI Grok; no implementation is shown.
- **The X post** by "savip" is the real source. Seb re-narrates it as "someone".

**Verification:** I viewed all six contact sheets and read full-resolution crops of the X post, trade list, CTA lines and dashboard. I ran web searches on TeleMoney (it exists: Bitrue explainer, Phantom token page). I did not open the X post (no access) and could not identify the "savip" account beyond the visible handle fragment. The "clone" cannot be verified at all.

**Claims vs reality:**
- "Cloned a $32,000/year Bloomberg terminal": **false.** He copied the look, not the product. Bloomberg's value is licensed real-time data, news, analytics and messaging. A screenshot-cloned UI fed with free crypto data is a themed dashboard. (A Bloomberg Terminal costs roughly $30k/year per seat, so the price is about right; the comparison is the problem.)
- "$4,000 → $17,000 in one day": **unverifiable, and meaningless if true.** It is one day, on one meme coin, entering at a $287K market cap. Moves like that come from liquidity and pump dynamics, not skill. There is no fee or slippage accounting (pump-scale coins have huge spreads), no history of losing days, and the number comes from a post that ends with an exchange-referral bonus pitch.
- "The bots know exactly how to use the Bloomberg terminal": **nonsense.** The bots don't "use" the UI; the UI displays what the bots do. The post itself admits the news feed "is just my bots texting each other".
- "Thousands of dollars profit each hour": not supported even by the post's own trade list (6 trades, one a loss).
- "Built in a couple of hours, zero code": plausible for a UI mock-up with an AI app builder (Replit is in the bookmarks). That says nothing about trading edge.

**Agenda:** Stacked funnels:
- Seb: "Comment TERMINAL" DM funnel and "save this video" engagement farming.
- The original X post: a "first reply has the exchange… new accounts get a bonus" referral link, plus "bookmark / forward" engagement prompts.

The real product being sold is an exchange signup and the creators' follower growth.

**Lab use:**
- Nothing to install from this video.
- If you want a Bloomberg-style front end for your own lab, use real open-source options already verified in batch 1:
  - OpenBB (data platform plus Workspace/CLI, with an MCP server)
  - OpenTerminal (ErTasselli, MIT) and OpenTerminalUI (Hitheshkaranth, MIT): dashboards
  - NautilusTrader: actual execution with risk controls
- LLM-driven meme-coin trading is gambling on illiquid assets. If you want to study it, paper-trade with recorded data, include realistic slippage and fees, and log every losing day.

**Second-brain relevance:** NONE – no memory or knowledge layer. The only loosely related idea is a bot "news feed" of the agents' own messages, which is just an activity log. Log agent decisions to your own store if you ever run trading agents, but nothing here shows how.

---

## V03 | "6 AIs, 1 brain": a cinematic dashboard of six content-agent personas sharing one memory, with no tool, code or architecture shown
- **Source:** Dropbox video V03 (VID_20261018_115823_891.mp4)
- **Account:** @bexruz.khamidullaev (watermark; the dashboard header reads "BEKHRUZ AI") · **Type:** video (55s, landscape 1280x720)
- **Category:** HYPE / UNREAL
- **Lab value:** NONE – a stylised animation of an agent team. It names no software, so nothing can be installed or verified.

**What it says:** "What does it look like when six AIs share one brain? Every line is an agent reading or writing, and every flash is a new memory." Six named agents orbit a glowing particle column: Radar (scanning) finds an idea and "writes it down"; Quill (writing), Reel (cutting) and Pixel (designing) "know" instantly; Pulse (measuring) "learned something" about what keeps viewers watching; Relay (scheduling) queues posts. One rule: "Nothing goes live until Bekhruz says yes"; one click and it "SHIPPED."

On-screen text (read from upscaled crops): "BEKHRUZ AI · LIVE · RUNNING 24/7", uptime "41D 06:13:56", "LOOP 28", "AGENTS ONLINE 06/06", "ONE BRAIN · Six agents. One shared memory. 1,844 notes · 6 agents · 1,188 signals/min · memory growing", "RECALL 97.3% · IN SYNC 6/6 · CONFIDENCE 0.80", "+1,290 tasks shipped by the team (last 7 days)", "signals processed 395,067", "notes written 130", approval queue items ("Post reel 'My AI Office · Part 3' · Tue 9:00", "Publish script 'One Brain, explained'", "Send 12 comment replies"), a loop strip "READ → ALIGN → COMMIT → LEARN", and memory-read bubbles ("Read RADAR's note. Writing the hook now", "Got it. Same topic, same rules").

**What's actually behind it:** Nothing identifiable. No product name, repo, URL, framework or model is shown or spoken. "Bekhruz AI" seems to be the creator's own brand. A web search on his name and "one brain" returned nothing relevant.

**Verification:** Viewed all 7 contact sheets and extracted full-resolution frames at 13s, 18s, 19.5s, 23.5s and 41s, upscaling the header, right-hand stats panel and bottom status strip. Web search for the creator and concept found nothing. There was nothing to clone.

**Claims vs reality:**
- "Six AIs share one brain": the general pattern (several agents reading and writing one shared store) is real and common, e.g. a shared notes folder or database. This video shows a visualisation of it, not an implementation.
- Metrics such as "Recall 97.3%", "Confidence 0.80" and "1,188 signals/min" have no stated definition. They look like decorative dashboard numbers, and "tasks shipped" (+1,290/week) against "notes written" (130) is unexplained.
- "Running 24/7, 41 days uptime": unverifiable.
- Human-in-the-loop approval before publishing is a sensible design, and is the one concrete idea here.

**Agenda:** Personal-brand content ("My AI Office · Part 3" is a series), very likely building toward selling an agent setup, consulting or a course. No link or offer is shown in this clip.

**Lab use:**
- Nothing to install. The useful idea is the architecture: specialised agents plus one shared memory store plus a human approval queue.
- To rebuild it, run several Claude Code / Agent SDK workers that all read and write one memory service over MCP, with a small approval table (e.g. in Postgres or SQLite) that a human clears before any action that publishes or trades. Effort: days to weeks. No GPU needed; an API subscription is.
- Open-source building blocks verified in batch 1 that do the shared-memory part: gbrain and hindsight (memory servers), claude-obsidian (markdown vault).

**Second-brain relevance:** MEDIUM (as an idea), NONE (as a product) – It shows the target concept the user wants: one memory shared by every agent, with consolidation ("Pulse learned something" and the whole team updates) and agent context injection (each agent reads others' notes before acting). But it is only an animation. There is nothing self-hostable or verifiable here, and no indication of how storage, retrieval or sync work. Build it instead from a real shared memory server exposed over MCP or HTTP to all VMs (e.g. hindsight or gbrain from batch 1), or a git-synced markdown vault.

---

## V08 | Comedy skit mocking absurd "abliterated / Heretic / Dark Planet" uncensored-model names on Hugging Face
- **Source:** Dropbox video V08 (VID_20261018_120602_267.mp4)
- **Account:** @willbrinegar.tech (watermark, end card) · **Type:** video (36s)
- **Category:** USELESS / REPACKAGED (satire)
- **Lab value:** LOW – a joke with no instructions. It points indirectly at one real tool (Heretic) and one real model family (DavidAU "Dark Planet").

**What it says:** A selfie-camera skit with captions. "Oh, you're in the AI space. Nice, and you use Fable 5.1 Ultra Code? Oh, nice!" Then, with exaggerated faces, he lists made-up chained model names:
- "Qwen 3.8 Heretic RVN Dark Planet 8D Mirrored Chaos"
- "Gemma 3 Hades Obliterated GPT"
- "Phi-4 Heretic"
- "Kardash/Car-bonnet 67.ai.io.com Re-obliterated and decomposed"
- "Age of Ultron.app 6.1 Jarvis"

It ends with "You can thank me later". There is no other on-screen text, link or code.

**What's actually behind it (the real things being parodied):**
- **"Fable 5.1 Ultra Code":** a riff on Anthropic's Claude **Fable** model line. The awesome-claude-code list (cloned for V10) links "A Field Guide to Claude Fable 5" on claude.com. "5.1 Ultra Code" is a made-up suffix.
- **Heretic:** https://github.com/p-e-w/heretic
  - AGPL-3.0, Python
  - Last commit 2026-10-17, active
  - Automatic "abliteration" (directional ablation of the refusal direction, Arditi et al. 2024), using Optuna to co-minimise refusals and KL divergence from the original model
  - This is why Hugging Face is full of "<model>-Heretic" uploads.
- **"Obliterated" / "abliterated":** community naming for refusal-ablated models.
- **"Dark Planet":** a real Hugging Face model family by DavidAU, for creative/roleplay models (e.g. L3-Dark-Planet-8B, MN-Dark-Planet-TITAN-12B). The stacked-suffix names ("Mirrored Chaos", "8D") mock DavidAU-style merge naming.
- **"Qwen 3.8", "Gemma 3 Hades", "Car-bonnet 67.ai.io.com", "Age of Ultron.app 6.1 Jarvis":** fictional.

**Verification:**
- Viewed all 5 contact sheets and read the captions.
- `git ls-remote` plus a shallow clone of p-e-w/heretic; read the README and LICENSE.
- Web search confirmed the DavidAU Dark Planet collection on Hugging Face.
- Did not verify any specific Hugging Face model card.

**Claims vs reality:**
- There are no factual claims; it is satire. The underlying point is fair: uncensored merges and abliterations have chaotic names and unclear provenance. Quality and safety vary widely, and some are low-effort re-uploads.

**Agenda:** Engagement and comedy for a tech-creator account. No funnel is visible.

**Lab use:**
- Only relevant if you run local LLMs. Heretic is a real tool (`pip install heretic-llm` per its README; not run here). It needs a GPU with enough VRAM to load the model.
- For a quant lab there is little reason to decensor models. Prefer official instruct models (Qwen, Gemma, Llama) through Ollama or llama.cpp, with known provenance.
- Treat random "Heretic/abliterated" Hugging Face uploads as untrusted. Load safetensors/GGUF only, never pickle.
- **Effort:** none needed.

**Second-brain relevance:** NONE – A comedy clip with no memory or knowledge-layer content.

---

## Batch 1: Instagram links (35 posts), ordered by usefulness

---

## DcD1vwCtGGX | "4 GitHub repos that run a hedge fund": NautilusTrader, Kronos, skfolio, Vibe-Trading
- **Link:** https://www.instagram.com/p/DcD1vwCtGGX/
- **Account:** @mirkovicdev · **Type:** video (7s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – all four repos are real, open source, Python-usable and directly relevant: an execution/backtest engine, a financial time-series foundation model, portfolio optimization, and an LLM research agent. The "hedge fund from your laptop" framing is hype.

**What it says:** The video is a 7-second clip of a man at a multi-monitor desk with the overlay "4 github repos that run a hedge fund from your laptop". Four README screenshots flash past for about one second each: **NautilusTrader** (Features + Integrations table), **Kronos** (tokenizer/causal transformer diagram, "Introduction… decoder-only foundation models pre-trained for the language of financial markets — K-line sequences", plus "Cumulative Return with Cost" and "Cumulative Excess Return with Cost" charts), **skfolio** (logo, plots, code), and **Vibe-Trading** (red-fish mascot, "What is Vibe-Trading?", Roadmap table, and the cards Self-Improving Trading Agent, Multi-Agent Trading Teams, Cross-Market Data & Backtesting, Shadow Account). The end overlay reads "Comment "REPOS" and I'll show you how to set them up". The audio is music only (the transcript is a mis-detection). The caption says: "free blueprint: four repos, wired into one trading system… 94,000 stars… cover every desk of a hedge fund: forecasting, portfolio, execution, oversight. Nobody had ever connec[ted]…". I identified the repos from 6 fps frame extraction and crops, since the 1 fps sheet missed Kronos and Vibe-Trading.

**What's actually behind it:**
- https://github.com/nautechsystems/nautilus_trader
  - License: LGPL-3.0.
  - Status: very active (commits 2026-10-18). Version v2.0.0rc8, and the Python package requires Python >=3.13,<3.15.
  - What it does: a production-grade, event-driven trading platform with a Rust core and Python API. The same strategy code runs in backtest and live, with many adapters (Binance, Bybit, IBKR, Databento, Betfair, Polymarket, …). This is the "execution" desk.
- https://github.com/shiyu-coder/Kronos
  - License: MIT.
  - Status: latest commit 2026-04-13 (about 6 months quiet; merged PRs). Paper at arXiv:2508.02739, accepted to AAAI 2026.
  - What it does: decoder-only foundation models for OHLCV K-line forecasting, using a BSQ tokenizer plus an autoregressive transformer. Weights are on HF `NeoQuasar/Kronos-mini` (4.1M), `-small` (24.7M) and `-base` (102.3M). `-large` (499M) is not released. It includes a finetuning pipeline (A-share example) and a web UI. This is the "forecasting" desk.
- https://github.com/skfolio/skfolio
  - License: BSD-3-Clause.
  - Status: very active (v1.9.4, commits 2026-10-18).
  - What it does: a scikit-learn-compatible portfolio optimization library (mean-risk, HRP/HERC/NCO, Black-Litterman, factor models, robust and distributionally robust optimization, walk-forward and combinatorial purged CV). This is the "portfolio" desk.
- https://github.com/HKUDS/Vibe-Trading
  - License: MIT.
  - Status: very active (v0.1.16 released 2026-09-29, commits 2026-10-18). From HKU Data Intelligence Lab (HKUDS).
  - What it does: an LLM agent research workspace that turns natural-language finance questions into data loading, strategy generation, backtests and reports. It has multi-agent "teams", an Alpha Zoo (462 prebuilt alphas: Qlib 158, Kakushadze 101, GTJA 191…), an options lab, and optional broker execution (e.g. Robinhood Agentic Trading) within limits you set. Install with `pip install vibe-trading-ai`. This is the "oversight/research" desk.

**Verification:** Extracted frames at 6 fps and cropped the Kronos and Vibe-Trading overlays to read them. Ran `git ls-remote` on all four, made shallow clones, read each LICENSE (LGPL-3.0, MIT, BSD-3, MIT), skimmed the READMEs and pyproject/version files, and checked git log dates. Not executed. I could not verify the "94,000 stars" total (GitHub API blocked) or the contents of the "free blueprint" DM. The caption is truncated, and no wiring code between the four repos is shown or published in the post.

**Claims vs reality:**
- "4 repos that run a hedge fund from your laptop": **hype.** These are good building blocks, but a fund needs data licensing, risk management, a validated alpha, capital and compliance. None of these repos provides an edge.
- "Cover every desk: forecasting, portfolio, execution, oversight": a reasonable mapping (Kronos, skfolio, Nautilus, Vibe-Trading), but they share no interfaces. Wiring them together is your own engineering work.
- "Nobody had ever connected them": unverifiable marketing.
- Kronos "Cumulative Return with Cost" charts: these are the authors' own backtest of forecast signals on Chinese A-shares. The README itself has a disclaimer that the finetune pipeline is "a demonstration… not a production-ready quantitative trading system". Treat the curves as research claims that need an out-of-sample replication.
- "94,000 stars" combined: plausible in magnitude (Nautilus and Kronos are both large), but unverified.

**Agenda:** A "Comment REPOS" DM funnel promising a "free blueprint". This is typical lead capture for a newsletter, community or course. The video itself carries almost no information: a 7-second lifestyle shot plus logos.

**Lab use:**
- **skfolio:** `pip install skfolio`. CPU only, pure Python/sklearn. Immediate use for portfolio construction and walk-forward or CPCV validation. Effort: hours. Highest value per effort.
- **NautilusTrader:** `pip install nautilus_trader`. Note that v2 needs Python 3.13+, so use a dedicated venv. A steep learning curve (days to weeks), but it is the serious OSS backtest-to-live engine. CPU only. Broker and data API keys depend on the venue.
- **Kronos:** clone it, then `pip install -r requirements.txt` (PyTorch) and load `NeoQuasar/Kronos-small` from HF. CPU works for mini/small, and a GPU helps for base and finetuning. Use it as a forecasting-feature experiment and benchmark it against naive baselines on your own data with strict out-of-sample splits. Effort: 1–2 days.
- **Vibe-Trading:** `pip install vibe-trading-ai` or Docker. It needs an LLM API key (OpenAI, Anthropic, etc.; paid). Useful as an agent research front-end and for its Alpha Zoo factor library. Effort: half a day.
- Simple wiring: Kronos or Alpha Zoo signals feed skfolio weights, which a NautilusTrader strategy executes in a paper account. Build it yourself; no "blueprint" is needed.

**Second-brain relevance:** LOW – Of the four repos, only Vibe-Trading has a memory component. It has file-based `PersistentMemory` (Markdown with frontmatter; types user/feedback/project/reference; file lock and dedup), an FTS5 `sessions.db` under `~/.vibe-trading`, and a stdio MCP server (`vibe-trading-mcp`). That memory is internal to Vibe-Trading's own agent and not designed as a store shared with other agents or VMs. NautilusTrader, Kronos and skfolio have no memory role. Design reference only.

---

## DegcLifkzmE | "Free trading platform" stack: OpenTerminal + OpenBB (Open Data Platform) + NautilusTrader
- **Link:** https://www.instagram.com/p/DegcLifkzmE/
- **Account:** @arwazaz_ · **Type:** carousel (8 slides)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – OpenBB and NautilusTrader are mature, real open-source Python components that form a solid data plus backtest/live engine core. The "OpenTerminal" part is ambiguous and the infographics are AI-generated mockups.

**What it says:**
- The carousel is "Build your ultimate trading platform for free. Three open-source projects, one workflow":
  - OpenTerminal = dashboard (charts, watchlists, screeners, news, macro, portfolio)
  - OpenBB Platform = data layer (Python SDK, REST API, MCP server; equities, FX, crypto, options, macro, alt data)
  - NautilusTrader = event-driven quant engine (backtesting, risk, broker integration, live trading)
- Slide 4 shows real-looking OpenBB code (`from openbb import obb; obb.equity.price.historical(symbol="AAPL", start_date=…)`). It warns that OpenBB "does not automatically provide free real-time data", so you must configure providers.
- Slide 5 shows a Nautilus "MovingAverageCross" example with a backtest card (+18.42%, Sharpe 1.36, MaxDD −6.21%, 248 trades).
- Slide 6 puts Claude Code in as the "development assistant" with a 6-step integration flow.
- Slide 7 is a sensible checklist: out-of-sample testing, costs and slippage, overfitting and look-ahead, paper trading, risk limits, and "A good-looking dashboard is not a profitable strategy."
- Slide 8: "Comment ROADMAP" for repos and a setup guide.

**What's actually behind it:**
- **OpenBB / Open Data Platform:** https://github.com/OpenBB-finance/OpenBB
  - License: Apache-2.0
  - Status: very active, last commit 2026-10-17. Now branded "Open Data Platform by OpenBB".
  - Confirmed in the clone: `openbb_platform/extensions/mcp_server` (an MCP server exists), many provider extensions (equity, crypto, derivatives, economy, fixedincome, etc.), and a desktop app (macOS/Windows binaries; Linux build only locally).
  - The `obb.equity.price.historical` code on the slide matches the real API.
- **NautilusTrader:** https://github.com/nautechsystems/nautilus_trader
  - License: **LGPL-3.0**
  - Status: very active, last commit 2026-10-18 ("Seed Interactive Brokers exec provider from cache").
  - What it is: a Rust core with Python bindings and many adapters (IB, Binance, Bybit, Databento, etc.), and the same code for backtest and live.
- **"OpenTerminal": not identifiable with certainty.** The post gives no URL or owner. Candidates I checked:
  - https://github.com/ErTasselli/OpenTerminal: MIT, last commit 2026-10-06. A Next.js/Express "Terminal-style workspace built entirely on free, public market data… zero paid API keys", some endpoints "reverse-engineered". It does not integrate OpenBB.
  - https://github.com/Hitheshkaranth/OpenTerminalUI: MIT, last commit 2026-10-06, v0.8.0. A FastAPI/React self-hosted research terminal with Kite/NSE (India), Yahoo, FMP, Finnhub, EDGAR and FRED, plus paper trading and an LLM analyst. Its India focus matches the NIFTY/BANKNIFTY watchlist in the post's mockups, but it does not use OpenBB either.
  - Neither project is documented as integrating with OpenBB or Nautilus, so "connect everything" is DIY glue code.

**Verification:**
- Cloned OpenBB, nautilus_trader, ErTasselli/OpenTerminal and Hitheshkaranth/OpenTerminalUI. Read their LICENSEs and README headers.
- Confirmed the OpenBB MCP extension and the desktop app.
- Compared the slide's Nautilus code with the repo docs. The slide uses `from nautilus_trader.strategy import Strategy` and `self.buy(bar.instrument_id, 1)`. The real import is `from nautilus_trader.trading import Strategy`, and orders go through `self.order_factory` plus `self.submit_order(...)`; the `buy()` methods in the docs are user-defined helpers. **So the slide's code is illustrative and would not run as written.**
- The dashboards and backtest numbers are AI-generated mockups, not real runs. Which "OpenTerminal" the creator meant is unverified because the link is behind the DM funnel.

**Claims vs reality:**
- "Three open-source projects, one workflow": the projects are real, but there is no ready-made integration. You write the adapters yourself, as slide 6 admits by giving that job to Claude Code.
- "For free": the software is free. Data is free only at the delayed/EOD level (yfinance, FRED, EDGAR via OpenBB). Real-time or intraday data and broker feeds cost money, as the post's own fine print says.
- "+18.42% / Sharpe 1.36 / −6.21% DD": a fabricated illustration, not a real backtest of the shown MA-cross strategy.
- The risk checklist on slide 7 is correct and better than typical IG content.

**Agenda:** "Comment ROADMAP" DM funnel for an "algo trading" creator account, likely leading to a course, community or newsletter. The content is decent but packaged as a lead magnet.

**Lab use:**
- **OpenBB:**
  - Install: `pip install openbb` (Python 3.10–3.12/3.13 per the docs).
  - Free keys: FRED and some providers' free tiers. Optionally run the REST API (`openbb-api`) or the MCP server so Claude Code can query data.
  - Effort: about 1 hour.
- **NautilusTrader:**
  - Install: `pip install nautilus_trader`, or uv from source (Rust toolchain only needed for source builds).
  - Use: write your strategy with `Strategy`, `StrategyConfig` and `order_factory`. Feed it OHLCV converted to Nautilus `Bar` objects through a data catalog (Parquet).
  - Effort: days to learn properly; the API is detailed but well documented.
  - LGPL is fine for private use.
- **Dashboard:** try ErTasselli/OpenTerminal or OpenTerminalUI in Docker for a UI. Alternatively build a Streamlit/Dash/Grafana panel over your own Parquet/DuckDB store, which is probably simpler.
- Hardware: no GPU needed. Optional paid: data vendors (Databento, Polygon) and a broker API (IBKR).
- Lighter alternatives to Nautilus for research: vectorbt (open-source edition), backtrader, or zipline-reloaded.

**Second-brain relevance:** LOW – OpenBB's MCP server (`openbb-mcp`, Streamable HTTP on port 8001 by default, optional basic auth) is a good example of one shared tool server that every agent and VM can call, but it serves market data, not memory. NautilusTrader and OpenTerminal: none.

---

## DeloQPzgbtw | Five free market-data sources for long backtests: Dukascopy, HistData, Hyperliquid API, Polymarket API, Alchemy
- **Link:** https://www.instagram.com/p/DeloQPzgbtw/
- **Account:** @taylorusesai · **Type:** video (7s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** HIGH – all five sources are real and free to start, and two of them (Dukascopy and HistData) give 10+ years of FX 1-minute data with open-source downloaders, exactly what a home backtesting lab needs.

**What it says:** Lifestyle B-roll (beach, restaurant, golf simulator, laptop) with no speech (the transcript is empty). Overlay text: "your strategy works until you test it on 10 years of data". The list: "1. Dukascopy: forex + gold minute bars; 2. HistData: years of 1-min forex; 3. Hyperliquid API: crypto + stock perps; 4. Polymarket API: every market + trade; 5. Alchemy: on-chain wallet data". The caption repeats the list with more detail: "Dukascopy (dukascopy.com): forex, gold and stock index history down to 1-minute bars and ticks. Export as CSV and keep one..." (truncated).

**What's actually behind it:**
- **Dukascopy** (Swiss bank/broker), https://www.dukascopy.com/swiss/english/marketwatch/historical/ : free historical tick and bar data for FX, metals, index CFDs and some stocks, back to about 2003 for majors. The web export may need a free account. Open-source downloader: **dukascopy-node** (https://github.com/Leo4815162342/dukascopy-node, **MIT**, last commit 2026-07-24, CLI `npx dukascopy-node -i eurusd -from 2010-01-01 -to 2026-01-01 -t m1 -f csv`). Python options also exist (e.g. `duka`, older).
- **HistData.com**: free 1-minute FX (and some metals and indices) bars back to about 2000, in ASCII/MT4/NinjaTrader formats, via a manual download form. Open-source bulk downloader: **philipperemy/FX-1-Minute-Data** (**Apache-2.0**, last commit 2025-05-04). Quality caveats: bid-only, gaps, timestamps in EST without DST.
- **Hyperliquid API** (https://api.hyperliquid.xyz/info): free public REST and WebSocket. The candle endpoint returns at most 5,000 candles per request; third-party docs (Chainstack) say only the most recent 5,000 candles per interval are served, so deep 1-minute history is **not** available natively (paid third parties such as Hydromancer and GoldRush, or self-recording, are needed). Exchange launched about 2023. Official SDK: **hyperliquid-python-sdk** (**MIT**, last commit 2026-06-05). "Stock perps" refers to the HIP-3 builder-deployed equity perps; I did not verify current listings.
- **Polymarket API**: free public Gamma (markets), CLOB (order book and prices) and Data (trades) APIs. Official client **py-clob-client** (**MIT**, last commit 2026-05-25). History starts about 2020 at most.
- **Alchemy** (https://www.alchemy.com): commercial blockchain node and data API provider. Free tier with compute-unit limits, paid above that. Closed source. Useful for wallet and transaction history. Free or open alternatives include running your own node, public RPCs, or Dune (freemium) for SQL over chain data.

**Verification:** Viewed the single contact sheet (7 frames); the transcript is empty (music only). `git ls-remote` and shallow clones of dukascopy-node, FX-1-Minute-Data, hyperliquid-python-sdk and py-clob-client; read LICENSE files and the last commit date. Web search on Hyperliquid's candle history limit. I did not run any code or test endpoints live. I did not see the full caption (truncated).

**Claims vs reality:**
- "Test on 10 years of data": good advice, but only Dukascopy and HistData can supply 10 years. Hyperliquid (2023+), Polymarket (2020+) and most on-chain venues simply don't have 10 years, and Hyperliquid's native API serves only recent candles.
- "Hyperliquid: crypto + stock perps": broadly true as of 2026, but history is short and shallow via the free API.
- "Polymarket: every market + trade": broadly true via the Data and CLOB APIs. Large pulls are rate-limited.
- Free FX data is broker-specific bid/ask from one liquidity source, not consolidated market data. Fine for research, but model the spread explicitly.

**Agenda:** Lifestyle and "AI trader" persona building (the handle is "taylorusesai"). Engagement bait. No product or funnel visible in this clip (the caption is truncated, so a funnel at the end can't be ruled out).

**Lab use:**
- FX and gold: `npx dukascopy-node` (Node 18+) or the FX-1-Minute-Data downloader (Python). Write to Parquet partitioned by symbol and year, normalise to UTC, keep bid and ask (Dukascopy) so spread costs are realistic. About 10–30 GB for many pairs at 1-minute; ticks are much larger.
- Crypto perps: hyperliquid-python-sdk `info.candles_snapshot` plus a cron job that records 1-minute candles, funding and order-book snapshots going forward to build your own history. Use Binance or Bybit public bulk data (data.binance.vision, free) for longer crypto history.
- Prediction markets: py-clob-client and the Gamma API for market metadata and trades into DuckDB.
- On-chain: Alchemy free tier with an API key, or a self-hosted node and public RPC if you want no vendor.
- No GPU. Paid only if you exceed Alchemy free limits or need deep Hyperliquid history. Effort: about 1 day to set up the downloaders and storage.

**Second-brain relevance:** NONE – Market-data sources. These belong to the lab's market-data store, a layer separate from the second brain.

---

## DegkHS3GRHJ | TradingAgents (Tauric Research): multi-agent LLM trading-desk research framework
- **Link:** https://www.instagram.com/p/DegkHS3GRHJ/
- **Account:** @simplifyinai · **Type:** carousel (3 slides)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – a real, actively maintained Apache-2.0 Python framework you can run on a Linux server with free yfinance/SEC data and either local Ollama models or any LLM API; good for agent and LLM-signal research, not a proven money-maker.

**What it says:**
- Slide 1 is the TradingAgents README header (Apache-2.0, arXiv 2412.20138, "#1 Repository Of The Day") with the claim "You can now run a whole AI trading firm on your own machine. 100% free."
- Slide 2 shows the architecture diagram: Market, Social, News and Fundamentals analysts feed a Bullish/Bearish researcher debate, then the Trader, a Risk team (aggressive, neutral, conservative), and a Manager before Execution. Text bullets read "Four analysts… Bull and bear researchers debate… risk team and portfolio manager review every decision. 100% open-source." The README's research-only disclaimer is visible but faded out.
- Slide 3 is a "Comment AI" DM funnel for "Claude's full course".

**What's actually behind it:**
- Repo: https://github.com/TauricResearch/TradingAgents
  - License: Apache-2.0 (confirmed)
  - Status: active. Last commit 2026-10-16 (v0.7.0 merge), with frequent releases v0.2 through v0.7 in 2026.
  - What it is: a LangGraph-based Python package (`tradingagents/`, `cli/`, Docker).
  - Default data vendors: yfinance for prices, indicators and news, plus SEC EDGAR and yfinance for fundamentals. Alpha Vantage and FRED are optional.
  - LLM providers: OpenAI, Anthropic, Google, xAI, DeepSeek, Qwen, OpenRouter, Groq, Ollama and others. v0.7.0 can also run on a ChatGPT Plus/Pro plan.
  - Includes backtesting over ticker/date grids, with "point-in-time integrity" claimed since v0.5.
- Paper: arXiv 2412.20138, "TradingAgents: Multi-Agents LLM Financial Trading Framework" (Xiao et al., 2024).

**Verification:**
- Ran git ls-remote and a shallow clone. Read the LICENSE and README (install steps, required APIs, news log, disclaimer) and `default_config.py`, where I checked the data-vendor defaults.
- Not run, per the brief.
- Star count and "#1 trending" status not verified (the API is blocked).

**Claims vs reality:**
- "Run a whole AI trading firm on your own machine": the orchestration runs locally, but the "firm" is a set of LLM prompts producing a buy/hold/sell rating. It is not a trading system with real execution or risk sizing.
- "100% free": the code is free, and the data defaults are free (yfinance, EDGAR). LLM calls cost API money unless you use local Ollama models, which are weaker. A multi-agent debate per ticker per day uses many tokens.
- "Mirrors real trading firms": it mirrors the roles only. The repo itself says it is "designed for research purposes… not intended as financial, investment, or trading advice."
- Performance: the paper's backtest covered a short window on a handful of large-cap US stocks. LLM non-determinism and possible training-data leakage (models may "know" the period's prices or news) make reported returns weak evidence. Recent versions add point-in-time filtering, which helps but does not remove model-knowledge leakage.

**Agenda:** "Comment AI" farms comments and DMs to sell a "Claude's full course" lead magnet and newsletter. The post repackages a public repo.

**Lab use:**
- Install: `git clone … && uv venv --python 3.13 && uv pip install .`, or `docker compose run --rm tradingagents`.
- Run: the CLI with `--ticker` and `--date` flags.
- Fully local option: `docker compose --profile ollama run --rm tradingagents-ollama` (GPU recommended for 8B+ models).
- Data needs no paid keys (yfinance, EDGAR; FRED key free and optional).
- Effort: about 1–2 hours to first run, and days to build a proper evaluation harness (fees, slippage, multiple seeds, out-of-sample windows).
- Best use: generate LLM-derived signals or reports, then evaluate them in your own backtester (vectorbt, NautilusTrader) as one feature among many. Don't trust its built-in scores blindly.

**Second-brain relevance:** LOW – TradingAgents keeps an append-only Markdown decision/reflection log (`tradingagents/memory/log.py`, `TradingMemoryLog`, file-locked) that later runs re-read. That is domain-specific episodic memory for its own agents, not a shared store. Pattern reference only.

---

## Defw9ggACu1 | claude-obsidian: Claude Code plugin that builds a cited, linked Obsidian wiki ("AI second brain")
- **Link:** https://www.instagram.com/reel/Defw9ggACu1/
- **Posted by:** Nathan Hodgson (@nathanhodgson.ai), 2026-10-15, 59 s
- **Method:** full download, Whisper transcript, every frame reviewed, repo cloned and test suite run
- **Lab value:** HIGH (revised for second-brain goal) – the original entry had no Lab value line, only a verdict. For the second-brain goal it is a top candidate for the curated, cited knowledge/wiki layer: free, keyless, local, transactional writes.

**Verdict: OPEN SOURCE, READY TO USE.** MIT license, real code, active, all tests pass.

### What the clip says (transcript summary)
Install Obsidian, install a "Claude skill" from GitHub, give it your notes, and open Graph View. Claude reads notes, pulls out concepts and links them. Claims it "gets smarter the more you use it," "never forgets context," and needs "no technical experience." Use cases: client database, Claude memory layer across projects, AI chief of staff. Ends with "comment brain and I'll send you the guide."

### What it actually is
- **Repo:** https://github.com/AgriciDaniel/claude-obsidian (the old name `cosmic-brain`, shown on screen, redirects here)
- **Author:** Agrici Daniel, not the Instagram creator
- **License:** MIT, so it's free to use, modify and redistribute
- **Status:** v2.2.0; last commit 2026-10-17; 90+ commits; outside contributors
- **Based on:** Andrej Karpathy's "LLM Wiki" pattern
- **What it does:** a Claude Code plugin made of 15 skills plus a Python core. You drop sources into `inbox/`. Claude reads them and writes linked Markdown wiki pages (sources, concepts, entities) into a normal Obsidian vault. Each page records where every claim came from. You then query the vault instead of starting from zero each session.
- **Search:** keyword search (BM25) that runs locally, with optional re-ranking through a local Ollama model.
- **Safety:** every write is previewed and approved, then applied as one change that can be rolled back. Parallel agents can't overwrite each other.

### Verification done
- Cloned and read the README, the automatic hooks, the privacy policy, and all network-calling code.
- **`make test`: all tests and checks passed** (Python 3.13, Linux).
- **Network:** no telemetry. The only outbound calls are to a local Ollama instance, plus an opt-in Anthropic API call for one optional search feature.
- **Hooks:** two read-only hooks. They write nothing and make no remote calls. Session context injection is off unless you set an environment variable.

### Claims vs. reality
| Claim | Reality |
|---|---|
| "Remembers everything / never forgets" | Overstated. It remembers what you put in, as Markdown. It's a well-organized notes database, not real memory. |
| "Gets smarter the more you use it" | The wiki grows and gets better connected. The model itself learns nothing. |
| "Links everything automatically" | Only when you run the ingest command. It doesn't watch your files in the background. |
| "No technical experience needed" | False. It needs Claude Code, Python 3.11+, the command line, and a step where you approve a hash before each write. |
| "Free" | True. No paywall in the code. |

### The creators' angles
- **Instagram creator:** "comment brain" is a lead-generation funnel. It boosts his engagement numbers and puts you on his DM list. He didn't build the tool, and the link is public anyway.
- **Repo author:** the repo's funding link points to a paid Skool community ("AI Marketing Hub Pro"). The code doesn't need it.

### Quant lab fit
- **Use it as:** a research memory. Ingest papers, strategy write-ups, backtest results and post-mortems. Then ask questions like "what have we tested on mean reversion and why did it fail?" with cited answers, across sessions.
- **Server deployment:** the core is headless Python and Markdown. Obsidian is a desktop app, so it isn't needed on the server. Keep the vault on the server, sync it with git or Syncthing, and open it in Obsidian on your desktop for the graph view.
- **Local-only option:** BM25 search runs offline. Re-ranking can use a local Ollama model, so nothing has to leave the server.
- **Known gaps:** the core extracts no text from PDFs; Claude reads them during ingest. URL and YouTube capture need a separate tool you set up yourself. It's built for notes, not market data: don't put price or tick data in it.
- **Effort:** about an afternoon to install and learn the approve-then-apply workflow.
- **Second-brain role:** the human-readable, cited wiki layer of the lab brain.
  - One vault on the lab server, kept in git as the system of record, with a single writer at a time.
  - Agents on other VMs get the skills through `setup-multi-agent.sh` and the vault through git pulls.
  - There is no MCP server or network API, so for live recall over the network, index the same Markdown into a server such as GBrain (`gbrain import <vault>`) or Hindsight.
- **Overlap:** this session already has a `research-superpowers` plugin that follows the same Karpathy wiki pattern. Choose one rather than running both on the same corpus.

### How to start
```bash
git clone https://github.com/AgriciDaniel/claude-obsidian.git
cd claude-obsidian && make test
export GENERATED_AT="$(date -u +%Y-%m-%dT%H:%M:%SZ)"
python3 scripts/claude-obsidian.py init ~/quantlab-vault --generated-at "$GENERATED_AT" --operation-id init-1
# review the JSON plan, then re-run with --approved-plan-sha256 <hash> --apply
cd ~/quantlab-vault && claude --plugin-dir /path/to/claude-obsidian
# /claude-obsidian:wiki  ->  drop a paper in inbox/  ->  /claude-obsidian:wiki-ingest
```

**Second-brain relevance:** HIGH – Covers four layers, self-hosted and keyless:
- ingest: sources dropped in `inbox/` become cited wiki pages
- storage: a plain Markdown vault that can be checkpointed in git
- retrieval: local BM25, with optional Ollama re-ranking
- consolidation: wiki-fold and wiki-lint

Writes are transactional (one vault lock, hash-checked, journaled, rolled back on failure), so parallel agents cannot overwrite each other. Multi-agent support comes from installing its skills into Claude Code, Codex, OpenCode, Gemini and ZCode (`scripts/setup-multi-agent.sh`). It ships **no MCP server or network API**; MCP/REST adapters are optional third-party read transports. Sharing across VMs therefore means git or Syncthing for the vault, with one writer at a time. Best fit: the curated, human-readable knowledge/wiki layer, paired with a server (GBrain or Hindsight) for recall over the network.

---

## DeCKnW0DAGc | 8 open-source AI repos: Open Glean, Hindsight, Foreman, OpenRig, Repolyze, OpenJev, VoiceStudio, MinerU
- **Link:** https://www.instagram.com/p/DeCKnW0DAGc/
- **Account:** @bestapps.ai · **Type:** carousel (11 slides)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – all 8 repos are real and current with permissive or copyleft licenses; MinerU and Hindsight are directly useful for a research server, and OpenRig and Foreman fit a Claude Code/Codex agent setup.

**What it says:** The cover says "8 GitHub repos hiding in plain sight". Each slide shows one product homepage with a one-line pitch and a badge such as "FREE & OPEN SOURCE · MIT LICENSE", "44K STARS ON GITHUB" or "OPEN WEIGHTS · 100M TOKENS FREE, NO CARD". Slide 10 is a "Comment REPOS" DM funnel for "The Hidden Repo List: 18 Free GitHub Repos", a blog post dated Oct 3 2026 that shows "The 8 from the post, plus 10 more". Slide 11 is a follow-bait slide ("Follow us or never see this page again").

**What's actually behind it:** All repos were checked with git ls-remote and a shallow clone. Each slide has a URL, license and last-commit date (all ≤ 2026-10-18 unless noted).
1. **Open Glean** (slide 2; the screenshot shows the HydraDB homepage)
   - URL: https://github.com/hydra-db/open-glean
   - License: Apache-2.0
   - Status: last commit 2026-10-18
   - What it is: a Next.js "second brain" workspace that answers questions with citations and has a "Deep Research" DAG mode. It proxies to `@hydradb/sdk` with `HYDRA_BASE_URL` defaulting to **api.hydradb.com (hosted)** and needs a Hydra API key. LLM answers go through OpenRouter.
   - Backend: HydraDB is at https://github.com/hydra-db/hydradb (**AGPL-3.0**, Rust graph DB on object storage, last commit 2026-10-15).
2. **Hindsight** (slide 3)
   - URL: https://github.com/vectorize-io/hindsight
   - License: MIT (Vectorize AI)
   - Status: last commit 2026-10-16. The screenshot shows 44.9k stars.
   - What it is: long-term agent memory with retain, recall and reflect operations, mixing semantic, BM25, graph and temporal retrieval. Python API in Docker on ports 8888/9999, `pip install hindsight-api` / `hindsight-client`. A paid cloud is also offered ("$5 free credit").
3. **Foreman** (slide 4; ThruWire)
   - URL: https://github.com/thruwire/foreman
   - License: MIT
   - Status: last commit 2026-10-15 (preparing v0.5.1)
   - What it is: a Python asyncio supervisor above coding-agent workers (Codex, OpenCode, Hermes, Deep Agents, Pi). It scores probabilities such as `worker_stuck`, `tests_sufficient` and `ready_to_finish`, then continues, steers or stops the worker.
   - **Catch:** it needs a paid decision-model API: TypeSafe Jev (`TYPESAFE_API_KEY`), Jev via OpenRouter, or OpenAI's Decisions API. A no-key demo mode exists.
4. **OpenRig** (slide 5)
   - URL: https://github.com/mvschwarz/openrig
   - License: Apache-2.0
   - Status: last commit 2026-10-18
   - What it is: `npm install -g @openrig/cli`, then `rig setup` and `rig up first-project`. It needs Node 22/24 and tmux. It runs Claude Code, Codex and Pi sessions as a persistent YAML-defined team with a lead agent.
   - "No second subscription" means it reuses whichever Claude Code or Codex login you already have.
5. **Repolyze** (slide 6)
   - URL: https://github.com/OssiumOfficial/Repolyze
   - License: MIT (Ossium Inc.)
   - Status: **last commit 2026-03-09, so effectively stale**. The screenshot shows 188 stars.
   - What it is: a Next.js and Prisma web app that asks an LLM to score a GitHub repo. The hosted version has a rate limit and a "Pro plan" coupon banner.
   - "Runs in your browser" only means it is a web app; the analysis is server-side through GitHub's API and an LLM.
6. **OpenJev** (slide 7; Codiv)
   - URL: https://github.com/razorback16/openjev
   - License: Apache-2.0
   - Status: last commit 2026-10-12
   - What it is: an open "System One" decision server, independent of TypeSafe. It answers yes/no, choice and score questions with probabilities through a Jev-compatible API and the OpenAI Decisions API.
   - Default model: DiffusionGemma 26B-A4B (Apache weights), run with vLLM on an NVIDIA GPU or MLX on Apple silicon. Smaller CPU-capable models are also listed (Laya 421M, Verdict 151M).
   - Codiv (https://codiv.ai) is the hosted version with 100M free input tokens.
   - Note: TypeSafe's own Jev is closed. "Open weights" is true only for this re-implementation.
7. **VoiceStudio** (slide 8; formerly OmniVoice-Studio)
   - URL: https://github.com/debpalash/VoiceStudio
   - License: **AGPL-3.0**, plus a CLA for contributors
   - Status: last commit 2026-10-18. The screenshot shows 50,000 stars and v0.5.6.
   - What it is: a local voice-cloning, dubbing, transcription and audiobook app (Electron with a Python backend). The website also sells Pro and Cloud tiers. The 646-language figure is the README's own claim and quality per language is unverified.
8. **MinerU** (slide 9)
   - URL: https://github.com/opendatalab/MinerU
   - License: Apache-2.0 **with added terms**: a separate commercial license is required above 100M MAU or $20M/month revenue, and online services must credit MinerU. That makes it fine for personal use.
   - Status: last commit 2026-10-11. The screenshot shows 81k stars and 6.8k forks.
   - What it is: a PDF/Office/scan to Markdown/JSON parser with a Python SDK, CLI, API and Gradio UI. Small models run on ONNX or Torch, and the VLM backend runs on vLLM, llama.cpp or LMDeploy.

**Verification:**
- Cloned all 9 repos (open-glean, hydradb, hindsight, foreman, openrig, Repolyze, VoiceStudio, MinerU, openjev). Read every LICENSE file and the key README sections, and checked last commits.
- Used web search to map the product names to repos: Codiv/OpenJev, ThruWire/Foreman, and VoiceStudio's rename from OmniVoice-Studio.
- Star counts are from the screenshots only; the GitHub API is blocked here.
- The 10 "bonus" repos sit behind the DM funnel and were not seen.

**Claims vs reality:**
- "Open Glean: free & open source, bring any AI model": the code is Apache-2.0, but by default it depends on the hosted Hydra DB API and key. Self-hosting HydraDB (AGPL) is possible but extra work.
- "Hindsight: free to self-host, 44K stars": true (MIT, Docker). Star count unverified.
- "Foreman: free & open source, MIT": the license is true, but **real runs need a paid TypeSafe, OpenRouter or OpenAI decision-model key**. The README itself says Jev's accuracy for this use is unproven.
- "OpenRig: free, no second subscription": true. Apache-2.0, and it uses your existing Claude Code or Codex plan.
- "Repolyze: free & open source": true (MIT), but the repo has had no commits since March 2026 and the hosted version is rate-limited and upsells Pro.
- "OpenJev: open weights, 100M tokens free": true for the open re-implementation (Apache). Self-hosting the default model needs a large NVIDIA GPU or Apple silicon.
- "VoiceStudio: free, replaces ElevenLabs, 50K stars": free and local, but AGPL. "Replaces ElevenLabs" and "646 languages" are marketing claims and were not tested.
- "MinerU: free & open source, 81K stars": essentially true. Note the extra license thresholds, which are irrelevant for personal use.

**Agenda:** An engagement funnel. "Comment REPOS" sends a DM link to the account's own blog, which builds their list. There is also follow-bait. No direct paid product is visible, though several of the tools themselves have paid tiers.

**Lab use:**
- **MinerU (HIGH):**
  - Install: `pip install -U "mineru[core]"` or use the docker/ folder.
  - Use: parse broker PDFs, 10-K filings and research papers into Markdown for RAG or LLM pipelines. Runs on CPU; a GPU speeds up the VLM tier.
  - Effort: about 1 hour.
- **Hindsight (MEDIUM-HIGH):**
  - Install: `docker run -p 8888:8888 -p 9999:9999 ...` with an LLM key, or point it at a local LLM.
  - Use: persistent memory for research agents.
  - Effort: a few hours.
- **OpenRig (MEDIUM):**
  - Install: `npm i -g @openrig/cli` with Node 22 and tmux on Linux.
  - Use: organise Claude Code agents into a team on the server.
  - Cost: uses your existing Claude Code plan.
  - Effort: about 1 hour.
- **OpenJev (MEDIUM, experimental):**
  - Install: point the TypeSafe or OpenAI SDK at api.codiv.ai, or self-host the small Laya/Verdict models on CPU.
  - Use: cheap, fast yes/no and scoring classifiers, for example news-relevance filters.
  - Alternative: an ordinary local LLM used as a judge with logprobs.
- **Foreman (LOW-MEDIUM):** needs a paid decision API. For Claude Code, Superpowers-style verification skills or plain hooks are free alternatives.
- **Open Glean (LOW):** tied to the HydraDB cloud. Open-source alternatives are Onyx (formerly Danswer), AnythingLLM or Khoj.
- **VoiceStudio and Repolyze (LOW/NONE for quant):** not relevant to a quant lab.

**Second-brain relevance:** HIGH – Two of the eight repos are direct second-brain candidates:
- **Hindsight** (MIT, v1.0.0) is a self-hostable memory server. It runs in Docker or via pip, stores data in PostgreSQL + pgvector (an embedded "pg0" Postgres by default), and uses local bge-small embeddings by default. The LLM that extracts facts and runs reflect can be Ollama or llama.cpp, or a paid API. It has an HTTP API, a per-bank MCP endpoint (`/mcp/{bank_id}/`), API-key auth via a tenant extension, and Claude Code/Codex/OpenCode integrations with auto-recall and auto-retain hooks. Several agents on several VMs can therefore share it.
- **MinerU** (4.0.x) covers ingest. It converts documents to Markdown/JSON and runs a local document library with watched folders, search and citation locators. It asks for opt-in telemetry on first run; disable it with `mineru telemetry disable`.

The others:
- Open Glean is not self-hostable as shipped. It calls Hydra's hosted `/context/*` API, and the open-source AGPL HydraDB graph database does not implement that API (a grep of its source found no such endpoint).
- OpenRig keeps agent-team state and queues in local SQLite. That is orchestration state, not knowledge.
- Foreman, OpenJev, Repolyze and VoiceStudio: none.

---

## DeRgmkvIkP4 | Superpowers (obra/superpowers) Claude Code skills plugin explained as a 7-phase pipeline
- **Link:** https://www.instagram.com/p/DeRgmkvIkP4/
- **Account:** @genai.works · **Type:** image
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – a free MIT Claude Code plugin that adds brainstorm, plan, TDD, review and debug discipline; it installs in one command and suits a Claude Code-driven quant lab.

**What it says:** The image is an infographic titled "How to use Claude Code in the best way". It describes "The 7-phase pipeline" Superpowers imposes:
1. Brainstorm: context scan, one question at a time, 2–3 approaches, design doc, approval gate.
2. Plan: dependencies, file paths, acceptance criteria, no placeholders.
3. Execute: subagent-driven, parallel, fresh context, and the orchestrator "never writes code".
4. Test: TDD "iron law", failing test first.
5. Review: two-stage, spec compliance then code quality.
6. Debug: reproduce and isolate, one hypothesis, "3-strike rule".
7. Ship: merge, PR, cleanup.

It also gives an anecdote ("coming soon page live in 30 minutes, 5 iterations"), trade-offs (consumes context, overkill for quick fixes, shines on complex work), "Getting started: install it as a Claude Code plugin", and the claim "0 to 125,000 GitHub stars in months. #1 trending on GitHub."

**What's actually behind it:**
- Repo: https://github.com/obra/superpowers (Jesse Vincent)
  - License: MIT (confirmed)
  - Status: active. Last commit 2026-10-09, "Release v7.0.0: rebuilt brainstorming…".
- Real skills in the repo: brainstorming, writing-plans, executing-plans, subagent-driven-development, dispatching-parallel-agents, test-driven-development, requesting-code-review, receiving-code-review, systematic-debugging, verification-before-completion, using-git-worktrees, finishing-a-development-branch, writing-skills, using-superpowers, diagnosing-superpowers.
- It supports Claude Code, Codex, Cursor, Antigravity, Devin and Gemini CLI.
- Install: `/plugin install superpowers@claude-plugins-official` (Anthropic's official marketplace).
- The README also has a "Commercial Services" section; the plugin itself is free.

**Verification:**
- Ran git ls-remote and a shallow clone. Read the LICENSE and README and listed the `skills/` directory.
- The 7 phases map closely to real skills, so the infographic is a fair summary.
- "125,000 stars" and "#1 trending" are not verified (no API access). The "9-step brainstorming" and "3-strike" details were not checked line by line.

**Claims vs reality:**
- "Breaks every task into 7 phases": broadly accurate. The phases are skills that trigger on context, not a rigid pipeline, as the post itself admits ("you don't always hit all 7").
- "Orchestrator never writes code": this is how the subagent-driven-development skill describes itself. It is a convention, not an enforced rule.
- "0 to 125K stars in months": plausible for a popular repo but unverified.
- The trade-offs section (context consumption, overkill for small fixes) is honest and correct.

**Agenda:** Engagement and brand building for GenAI.works (newsletter and community). No paywall on this post.

**Lab use:**
- Install: in Claude Code run `/plugin install superpowers@claude-plugins-official`.
- Cost: no dependencies, no GPU, no extra API.
- Effort: 5 minutes to install, and a few sessions to get used to the brainstorm/plan gates.
- Use it for multi-file work such as building a data pipeline, a backtest engine refactor or strategy modules with tests. Skip it for one-line fixes.
- The TDD and verification-before-completion skills are especially valuable against silent look-ahead or off-by-one bugs in quant code.

**Second-brain relevance:** LOW – The repo has no memory component: none of its 15 skills (brainstorming, plans, TDD, review, debugging, and so on) stores knowledge. It does produce durable artifacts (design docs, plans) in the repo that a second brain could index, and it shows how one skill set can be distributed to several agents (Claude Code, Codex, Cursor, Gemini CLI). Not a memory layer.

---

## DbEK3bustQ7 | Microsoft SkillOpt: real MIT-licensed tool that trains agent skill documents with validation-gated edits
- **Link:** https://www.instagram.com/p/DbEK3bustQ7/
- **Account:** @marc.kaz · **Type:** video (32s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** HIGH – genuine Microsoft Research code (MIT, on PyPI, actively maintained) that can optimize the skills/prompts of your Claude Code or Codex research agents against your own held-out tasks.

**What it says:** Title "🚨 Microsoft open-sourced self-evolving agent skills" over the GitHub README of SkillOpt, with a persistent on-screen URL "https://github.com/microsoft/SkillOpt". He says the skills "improve themselves the same way you train an AI model," so "no more guessing whether your prompt tweaks helped"; "open source, 100% free"; "it optimizes the outputs and evaluates them and rewrites the instructions themselves." The README on screen shows the title "SkillOpt: Executive Strategy for Self-Evolving Agent Skills", the tagline "Train agent skills like you train neural networks — with epochs, (mini-)batchsize, learning rates, and validation gates — but without touching model weights", Trendshift badges ("#3 Repository Of The Day", "#9 Repository Of The Week") and the loss-landscape figure ("Val Error" vs "Skill Space", "held-out selection gate", "bounded skill edits", "rejected-edit buffer"). Caption: "A base model runs the task, an optimizer rewrites the instructions based on results," and a truncated feature list ("Isolates successful paths from failures, Auto-rejects e...").

**What's actually behind it:**
- https://github.com/microsoft/SkillOpt, **MIT** (Copyright 2026 Microsoft Corporation). Exists and very active: first commit in the 50-commit clone window 2026-08-06, last commit 2026-10-18 (many community PRs). PyPI package `skillopt` v0.2.0 (requires Python ≥3.10). Real code: `skillopt/` (engine, optimizer, gradient, scheduler, evaluation, model backends; 92 Python files), benchmark envs (searchqa, spreadsheetbench, docvqa, officeqa, alfworld, livemathematicianbench), `skillopt_sleep/`, a Gradio WebUI, tests and docs.
- Paper: "SkillOpt: Executive Strategy for Self-Evolving Agent Skills", Yang et al., arXiv 2605.23904 (2026); Microsoft Research blog post "SkillOpt: Agent skills as trainable parameters."
- Method: a frozen target model runs scored rollouts; a separate optimizer model turns them into bounded add/delete/replace edits on one skill document; an edit is accepted only if it strictly improves a held-out validation score; a textual "learning rate" budget, rejected-edit buffer and epoch-wise slow/meta update stabilize it. Output: a `best_skill.md` (≈300–2,000 tokens) with zero extra inference calls at deployment.
- Backends: openai_chat, claude_chat, qwen_chat, minimax_chat, copilot_chat, openai_compatible, and exec harnesses codex_exec, claude_code_exec, cursor_exec, copilot_exec.
- `skillopt-sleep` (preview): nightly harvest of Claude Code/Codex/Copilot/Cursor/Pi/OpenCode transcripts → mine recurring tasks → replay → gated consolidation → staged proposal you adopt.

**Verification:** `git ls-remote` + shallow clone (depth 50); read LICENSE, README, requirements.txt, pyproject.toml, docs/sleep/README.md, git log; listed package structure. Web search confirmed the Microsoft Research blog and paper pages. Did not run any code and did not reproduce the paper's numbers.

**Claims vs reality:**
- "Microsoft open-sourced it": true (microsoft org, Microsoft copyright, MSR blog).
- "Open source, 100% free": the code is MIT and free; running it costs LLM API calls (rollouts plus optimizer calls per epoch) unless you use a local model via vLLM/openai_compatible.
- "Skills that improve themselves the same way you train an AI model": an analogy. Nothing is trained in weight space; it is validation-gated text editing of a skill file. The README says exactly that.
- "No more guessing whether your prompt tweaks helped": true only if you supply a scored task set with a held-out split. Without a metric there is nothing to optimize.
- Paper results (best or tied on 52/52 cells; +19 to +25 points on GPT-5.5) are the authors' own claims on their benchmarks; not independently verified here.

**Agenda:** Engagement/news-repost account; the link is given openly on screen and no funnel is visible in the clip.

**Lab use:**
- Install: `pip install skillopt` in a venv (core deps: openai, pyyaml, numpy, openpyxl, azure-identity, httpx; extras for claude, qwen/vLLM, webui). Entry points: `skillopt-train`, `skillopt-eval`, `skillopt-sleep`.
- Concrete use: write a small benchmark env (template in `skillopt/envs/_template`, simplest reference `searchqa`) of 30–100 quant-research tasks with automatic scoring, e.g. "given this dataset, produce a backtest script" scored by deterministic checks (no look-ahead, fees applied, correct split, script runs, metric within tolerance). Train a skill for your Claude Code research agent, then drop `best_skill.md` into `.claude/skills/`.
- Or run `skillopt-sleep` over your own Claude Code session logs to propose skill updates for recurring lab chores; review proposals before adopting.
- Needs: an API key (Anthropic/OpenAI/Azure) or a local GPU with vLLM for the target/optimizer. Budget tokens; each epoch replays many tasks.
- Effort: an hour to install and run a bundled benchmark; 1–3 days to build a meaningful scored task set for your own workflows (that task set is the real work).

**Second-brain relevance:** MEDIUM – Covers the consolidation layer. `skillopt-sleep` (preview) harvests local Claude Code/Codex/Copilot/Cursor/Pi/OpenCode transcripts, mines recurring tasks, replays them, and stages validated edits to skills and a memory document that you then `adopt`. Every edit is gated on held-out tasks. It runs locally (MIT, Python), but replay and judging send transcript excerpts to the LLM backend you configure; its docs warn that outbound prompts are not guaranteed secret-free. It also costs tokens (a per-night token cap is configurable). It is not a store or a server: it produces files (SKILL.md, a memory doc) that you distribute to agents yourself, for example via git. Treat it as a nightly "dream" job on top of the brain, not as the brain.

---

## Dem60yJDELo | "Company brain / context package": a whiteboard pitch for connecting Claude Code to an org knowledge base, aimed at AI consultancies
- **Link:** https://www.instagram.com/p/Dem60yJDELo/
- **Account:** @lostandlucky · **Type:** video (57s)
- **Category:** USELESS / REPACKAGED
- **Lab value:** MEDIUM (revised for second-brain goal) – the clip itself is an empty consulting pitch with no tool, repo or method, but its concept is exactly the user's second-brain goal, and the real project it points to (GBrain, MIT) is a leading candidate for the shared memory server.

**What it says:** At a whiteboard reading "Consultancy Lives" with circles "M/O" (management/org), "SB" (second brain), "T/I" (technical solution) and "P/HR", plus "JOB" in the corner, he says there is "a huge opportunity for something called second brains ... company brains, context packages." If a technical solution, "Claude Code or something like that", connects to "a large database" holding the org chart, who manages what and the SOPs, "anyone in the company can now ask what to do," so "you no longer need a whole bunch of people helping with management." Consultancies will build "the systems that will manage you" rather than manage. He refers to his other videos on second brains and "graph architectures." Caption repeats this.

**What's actually behind it:**
- No product, repo or URL is shown or named. Only Claude Code is mentioned, generically.
- The concept maps onto existing, real things: Claude Code with CLAUDE.md/skills plus an MCP connection to a knowledge store; enterprise search products; and open-source agent memory such as GBrain, https://github.com/garrytan/gbrain, **MIT**, exists, very active (last commit 2026-10-18). Its README says it gives agents "a memory you control" with sourced facts, corrections, sharing across agents, and "works as a company brain too" with access grants. (Named here as an example, not by the creator.)

**Verification:** Read the transcript and every frame (the whiteboard has only the abbreviations above). Shallow-cloned garrytan/gbrain and read LICENSE, README and log as an example of the real category. Nothing executed. Nothing in the post itself to verify.

**Claims vs reality:**
- "Huge opportunity for company brains": plausible as a consulting niche; it is already a crowded product category.
- "Anyone can ask what to do ... you no longer need people helping with management": overstated. Retrieval over SOPs answers process questions; it does not replace judgment, prioritization or accountability, and stale or conflicting SOPs produce confidently wrong answers.
- "Consultancies will build the systems that manage you": opinion.

**Agenda:** Positions the creator as an AI-consulting thought leader and drives views to his other videos. No direct funnel in this clip.

**Lab use:**
- The relevant, small version for a personal quant lab: a "lab brain" for your agent. Keep a repo of markdown notes (data sources and quirks, strategy specs, backtest results, decisions, failed ideas) plus CLAUDE.md pointing Claude Code at it; optionally index it with a local MCP memory server.
- Open-source option if you want more than files: GBrain (MIT; check its install guide; it has keyless keyword retrieval by default, embeddings optional). Alternatively an Obsidian vault plus grep/ripgrep is enough at personal scale.
- No GPU needed; embeddings via a local model or an API are optional. Effort: an hour for the file-based version.
- Second-brain role: the clip itself adds nothing. Evaluate GBrain as the central memory server for all VMs and agents:
  - Run `gbrain init --pglite --no-embedding` on one host to start keyless.
  - Move to Postgres + pgvector once several machines write to it.
  - Serve it with `gbrain serve --http` (OAuth 2.1 scopes) or `gbrain mcp expose` on a Tailscale tailnet.
  - Give each agent its own token with `gbrain agent register <name> --harness claude-code`.
  - Embeddings can be local (Ollama or llama.cpp). Note that new installs default to Voyage, a paid API, once embeddings are enabled.
  - Requires Bun 1.4+. Never install it from npm; the npm `gbrain` package is unrelated.
  - Effort: an afternoon for a single host, 1–2 days for an authenticated multi-VM setup.

**Second-brain relevance:** MEDIUM – The concept (a "company brain / context package": an agent wired to one central store of who, what and how) is exactly the user's goal, but the video gives no tool, schema or method. The value is the entry's pointer to GBrain (MIT):
- Storage: Markdown in git is the system of record, indexed into PGLite (the keyless default) or into Postgres + pgvector for multi-machine setups.
- Interfaces: stdio MCP, or HTTP MCP with OAuth 2.1 scopes (`gbrain serve --http`, or `gbrain mcp expose` over Tailscale), with per-agent tokens (`gbrain agent register`).
- Clients: Claude Code, Codex, OpenCode, Hermes and OpenClaw.

So it is self-hostable and designed to be shared by several agents and machines.

---

## DemXvfSjwCM | Three positioning data sources (CFTC COT, Goldman prime-brokerage data, dealer gamma exposure) as a funnel to the Crown Macro Letter newsletter
- **Link:** https://www.instagram.com/p/DemXvfSjwCM/
- **Account:** @nicholascrown · **Type:** video (145s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** MEDIUM – COT data is free and easy to add to the lab, and GEX can be approximated from free option-chain data; the Goldman prime-book part is not obtainable legitimately.

**What it says:** Walking on a Miami Beach promenade, he says "price is a lagging indicator and positioning is actually what really matters," and that mastering three positioning sources lets you "literally operate like a hedge fund." (1) CFTC Commitments of Traders: "published every single Friday at 3:30pm", "free, public", "covers 20 trillion dollars in futures contracts" from agriculture to nat gas, crude, gold and the E-mini S&P; it shows crowded trades, squeeze risk and forced sellers. (2) Goldman Sachs prime-brokerage data, "the holy grail", tracking "every single hedge fund book they finance", gross/net exposure by sector (e.g. semiconductors); "if you're not a hedge fund you really shouldn't be able to get your hands on this, but ... it gets leaked all the time." (3) Gamma exposure: dealer positioning by strike; short-gamma levels accelerate moves, positive-gamma levels "act like a magnet or a pin" and "are the actual support and resistance levels." CFTC data "you can pull yourself for free"; everything else is rolled into his weekly newsletter. End card: "Comment 'LETTER' for the link to the newsletter" plus a not-investment-advice disclaimer.

**What's actually behind it:**
- On-screen CFTC page (cftc.gov, Market Data & Economic Analysis → Commitments of Traders), showing "Reports Dated July 07, 2026 – Current Disaggregated Reports." Real, free source: https://www.cftc.gov/MarketReports/CommitmentsofTraders/index.htm. Free historical files are also on the CFTC site and via the public reporting environment (Socrata API).
- On-screen chart "Prime Book: US Equities (Single Stocks + Macro Products)", 2019–Jul 2024, a weekly net-flow z-score-style series with a −3 red line and a circled final print. This is a Goldman Sachs Prime Services chart of the type that circulates on X/news sites; it is from mid-2024, not current, and it is proprietary client-only research.
- On-screen chart "SPX Gamma Exposure by Strike" watermarked "The Crown Macro Letter ©": bars at 7,000 ("Major Put Wall / Ultimate Floor", about −270M), 7,300 ("Put Wall / First Support"), 7,425 ("Local Gamma Support"), a "Gamma Flip" at 7,471.67, "Last Close 7,483.24", and call walls at 7,500 ("Primary") and 7,550 ("Secondary"). This is his own estimate; the method is not shown.
- Free tool for (1): `cot_reports` Python library, https://github.com/NDelventhal/cot_reports, **MIT**, exists, last commit 2023-12-30 (v0.1.3; quiet but functional against CFTC's file layout as far as the README goes).
- The Crown Macro Letter: no public listing, pricing or archive found by web search. Unverified.

**Verification:** Read the full transcript and every frame; cropped the CFTC page, prime-book chart and GEX chart at full resolution. `git ls-remote` + shallow clone of NDelventhal/cot_reports (read LICENSE, README, log). Web searches on the newsletter and on public alternatives to prime-brokerage positioning data. Nothing executed.

**Claims vs reality:**
- "Price is a lagging indicator, positioning is what really matters": overstated. Positioning is a useful contrarian/crowding input, but it is also lagged (see below) and noisy.
- COT "published every Friday at 3:30pm": correct (3:30pm ET), but the data are **as of the prior Tuesday**, so it is 3 days old on release. Holiday weeks shift the schedule.
- COT "free and public", covers ag, energy, metals, E-mini S&P: correct. "Covers $20 trillion": I could not verify that figure; treat as a rough talking point.
- Prime-brokerage data tracks "every single hedge fund book they finance": it is Goldman's own aggregated client data, i.e. GS-financed funds only, not the whole industry. It is distributed to GS clients. "It gets leaked all the time" means screenshots get reposted; acquiring the actual data without authorization is not a legitimate route.
- Gamma exposure: the sign convention ("when you buy an option a dealer has to sell it to you") is a model assumption. Public GEX estimates assume customers are long puts/short calls or similar, and real dealer inventory is unknown. "Positive gamma levels are the actual support and resistance" is a strong overstatement; pinning effects are real near large open interest at expiry, but they are not reliable S/R.
- "Master all three and operate like a hedge fund": marketing.

**Agenda:** Comment-"LETTER" lead magnet for his weekly newsletter (same funnel as DenSGzckhBw). The GEX chart is branded with the newsletter name.

**Lab use:**
- COT: `pip install cot_reports` (or download the CFTC yearly zip/CSV files directly). Build weekly managed-money net-position percentiles / z-scores per contract (ES, CL, NG, GC, ZN, 6E...). Remember the Tuesday-as-of date when aligning with prices to avoid look-ahead. Effort: half a day. No GPU, no paid API.
- GEX approximation: CBOE publishes delayed SPX option chains (free CSV on cboe.com delayed quotes); compute per-strike gamma with Black-Scholes (scipy) × open interest × 100 × S² × 0.01 under an explicit dealer-sign assumption, then find the zero-gamma "flip" by repricing over a spot grid. Effort: 1–2 days. Treat outputs as a sentiment map, and backtest before trading on "walls."
- Prime-brokerage substitute (legal, free, slower): SEC 13F filings from EDGAR (quarterly long positions, 45-day lag), FINRA bi-monthly short interest, and the COT "leveraged funds" category in the Traders in Financial Futures report.

**Second-brain relevance:** NONE – Positioning-data sources and a newsletter funnel. No memory component.

---

## DatpvftE-Iq | TraderAlice/OpenAlice: an open-source local "AI trading orchestrator" (agents + market data + broker accounts)
- **Link:** https://www.instagram.com/p/DatpvftE-Iq/
- **Account:** @gittrend.io · **Type:** video (32s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – a real, actively developed AGPL-3.0 workspace that connects Claude Code/Codex/OpenCode agents to market data, scheduled research and paper or live broker accounts with human approval. It is useful as research tooling and an architecture reference, not as an edge generator.

**What it says:** The voiceover says "Run a one-person Wall Street 24/7 for free with OpenAlice", which "automates research, entry, position management and exits across stocks, crypto, commodities and forex". You install it locally, add broker keys, and scheduled jobs research, size and "propose trades for your approval". It unifies multiple brokers and keeps a full trade history. "Comment trade." On screen it scrolls through `github.com/TraderAlice/OpenAlice`: Public, Fork 874, Star 5.4k (cropped), AGPL-3.0 license tab, latest merge by luokerenx4 "2 days ago". The README sections shown are Full-spectrum/Full-lifecycle/Full-control bullets, a red **Caution** box ("experimental software in active development… Do not use this software for live trading with real funds unless you fully understand and accept the risks… no guarantees of correctness, reliability, or profitability"), and Features: Unified Trading Account (CCXT, Alpaca, Interactive Brokers), Trading-as-Git, Guard pipeline, account snapshots, market data with "zero API keys" via the hosted TraderHub, Automation (cron and webhooks), Interface (Web UI, Workspaces, Inbox, MCP server), multi-provider AI and an "Evolution mode".

**What's actually behind it:**
- https://github.com/TraderAlice/OpenAlice
  - License: AGPL-3.0.
  - Status: exists and is very active. Latest commit 2026-10-04 (0.95.0 beta release merge). About 5.4k stars and 874 forks on screen.
  - Stack: TypeScript/pnpm/turbo monorepo with Electron desktop and a Bun CLI. Packages include `uta-broker-alpaca`, `uta-broker-ccxt`, `uta-broker-ibkr`, `uta-broker-longbridge`, `uta-broker-leverup`, `opentypebb` (an OpenBB-derived data layer), `guardian-runtime`, plus `services/uta` and `services/connector`.
  - What it does: a local orchestrator that runs your existing agent CLIs (Claude Code, Codex, OpenCode, Pi) inside Git-backed "Workspaces" with market data, fundamentals and news tools. It supports scheduled "Issues" (recurring research), an Inbox, AutoQuant (quant research workspace) and Auto Prediction. Brokers sit behind a "Unified Trading Account". Agents stage orders as commits and a human approves execution ("Trading as Git").
  - Website: openalice.ai, with docs, Discord and a QQ group.

**Verification:** Read all four contact sheets and cropped the repo header (TraderAlice/OpenAlice, Fork 874, Star 5.4k). Ran `git ls-remote`, made a shallow clone, and read the LICENSE (AGPL-3.0), current README, `docs/cli-installer.md` and git log, and listed packages and services. Not executed. The current README has been rewritten since the video was recorded (it now leads with Workspaces, Issues and Inbox), but the Caution box remains: "Trading execution is beta. Start with simulator, paper, demo, or testnet accounts." I did not verify the hosted TraderHub data service's terms or limits.

**Claims vs reality:**
- "One-person Wall Street, 24/7, for free": the **software is free** (AGPL). The LLM usage is not: you pay for your Claude/OpenAI/etc. credentials. Some data is "zero key" through their hosted TraderHub, a third-party dependency.
- "Automates research, entry, position management, exits": it **automates proposing** these. Execution is gated by human approval, and the authors call trading execution beta and experimental.
- "Stocks, crypto, commodities, forex": broker coverage is through CCXT, Alpaca, IBKR, Longbridge and LeverUp, so actual asset coverage depends on the broker.
- "Full trade history you can inspect": **true** (Trading-as-Git commit log and account snapshots).
- **Implied profitability: none.** There is no evidence of edge, and the README explicitly disclaims profitability. An LLM agent proposing trades is not a validated strategy.

**Agenda:** gittrend.io drives traffic to its site and uses a "Comment trade" DM funnel. The voiceover is broadly faithful to the README but omits the big caution box. The upstream project has its own community and website, with no paid tier evident in the README.

**Lab use:**
- Fit: a front-end for agent-driven research on your Linux server. Use Claude Code as the agent, keep scheduled research notes per ticker in Git workspaces, and paper-trade through the Alpaca paper or IBKR paper adapters with manual approval. The `uta-broker-*` packages and the Trading-as-Git pattern are good designs to borrow for your own Python execution layer.
- Install on a server: `curl -fsSL https://openalice.ai/install | bash` (CLI, needs `flock`, `tar`, `sha256sum`), or from source with `pnpm install && pnpm dev`. Inspect the install script before piping it to bash.
- Dependencies: Node/pnpm (source) or a native Bun binary (CLI), an agent CLI with credentials (Claude Code subscription or API), and broker API keys. No GPU.
- Effort: half a day to run with paper accounts. AGPL matters only if you expose a modified version as a network service to others.
- OSS alternatives in Python: `HKUDS/Vibe-Trading` (MIT), `TauricResearch/TradingAgents` (Apache-2.0), or NautilusTrader for the execution layer.

**Second-brain relevance:** LOW – OpenAlice keeps each research Workspace as a Git directory, stores its own state under `~/.openalice`, and its README lists an MCP server. That is trading-workspace context for the agents it launches, not a general memory layer. It is self-hostable (AGPL, local), but I did not verify what its MCP server exposes or whether it can bind beyond localhost. The "workspace = git repo" convention is sound; a second brain should index those repos rather than live inside OpenAlice.

---

## DeUE0tQPmgX | Industry (SIC) codes on filings are stale; label companies by what their revenue does, with human-reviewed agent labels (fidetolabs series #6, behind it the MIT-licensed Qanat repo)
- **Link:** https://www.instagram.com/p/DeUE0tQPmgX/
- **Account:** @fidetolabs · **Type:** video (36s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – a sound, practical point about peer-group construction for screens and factor ranks, and the creator's MIT-licensed point-in-time data platform (Qanat) is usable, but the agent workflow shown is not in the repo, and the numbers are illustrative.

**What it says:** An animated diagram titled "How To Build A Self-Improving AI Trading Agent #6". You have a thesis ("a story about who bills by the task"), and an agent must turn it into a list of companies by calling "the data platform". Step 1: screen on the filing's industry code (on-screen "CODES 7370, 7372, 7389": SIC codes for software and IT services), giving "128 filers, 3 codes". Step 2: read revenue instead. "63 of those 128 don't bill by the task", 65 are on both lists, and 30 that do bill that way are filed under other codes. The revenue list totals 95. Step 3: the 30 misses are spread across "finance services 13, management consulting 7, help supply services 4, telephone communications 3, engineering services 2". "Rank a company against the wrong peers and the rank is about a different industry." Step 4: the agent proposes 40 labels, you reject the wrong ones ("34 of 40 accepted"), and the label is stored as a column beside the code with fields: code on the cover (7370), revenue billed by the task (68.8%), who said so (the agent), and whether you accepted it. "Those 6 are saved, and next session it reads them before it labels anything." The sample table uses tickers XYV, GEJ and ETQ, which are not real US tickers (placeholders).

**What's actually behind it:**
- FidetoLabs, https://www.fidetolabs.com/ : one anonymous quant builder. Data and Agents products are waitlisted (no pricing shown). Also offers research notes, a newsletter and a free Discord (about 1,248 members claimed). Open-source page lists "Qanat" and "Blurr" (in progress, no repo).
- **Qanat**, https://github.com/fidetolabs/qanat , **MIT** license, PyPI `qanat-fdtl` 0.4.1. First commit 2026-09-06, last 2026-10-18 (active, about 60 commits in the shallow history, 158 files). It is "a data platform for investment research" with ingest, save (dedup, dated), transform and serve, plus its own orchestrator. Its key feature is **point-in-time data**: two dates per number (period_end and filed_at), with as-of views during replays to prevent look-ahead. Storage is DuckDB or Postgres. Connectors are HTTP, SQL, CSV and a synthetic market. It is delivered as an MCP server (`claude mcp add qanat -- qanat mcp --scope research`). Status: beta. README admits "No industry grouping", no SEC parser yet ("You bring the data"), no backfills, and that it does not trade. Version 0.4.0 removed the backtest, significance and IC tooling.
- SIC codes: real. SEC EDGAR assigns or keeps a self-reported Standard Industrial Classification on each filer, and it is rarely updated. That is a well-known limitation; researchers use text-based industries such as Hoberg–Phillips TNIC for this reason.

**Verification:** Viewed all 5 contact sheets and cropped the text panels. Fetched fidetolabs.com, /open-source and /about. `git ls-remote` and a shallow clone of fidetolabs/qanat; read the README, LICENSE (MIT), pyproject, CHANGELOG, git log and file tree. No code was executed. I could **not** verify the 128/63/65/30 figures: no real tickers are shown, and the repo's filings example states "Every number in this example is invented." The "self-improving" labeling-with-rejection-memory agent does not exist as code in the repo; it is a described workflow.

**Claims vs reality:**
- "The industry code is one number the company picked for itself, and it doesn't move when the business does": essentially true for SEC SIC codes. That is a real source of peer-group error.
- "Self-improving agent": in practice, saving the rejected labels to a file and re-reading them next session. That is a few-shot memory, not learning, but it is honest and useful.
- Specific counts: illustrative and unverifiable. The placeholder tickers suggest synthetic data.

**Agenda:** Building an audience for FidetoLabs: waitlisted paid data and agent products, newsletter, Discord. Educational and fairly candid in tone. No "comment for link" funnel seen in this clip.

**Lab use:**
- Install: `uv tool install qanat-fdtl` (or `pip install qanat-fdtl`), `qanat init my-research --demo`. Then `claude mcp add qanat -- qanat mcp --scope research` to use it from Claude Code. Python 3.10+, DuckDB, FastAPI and uvicorn. No GPU, no API key for the demo. Review the code before running it, since it is a young beta from a single anonymous author.
- Rebuild the labeling idea yourself (1–2 days): pull SIC codes and 10-K text from SEC EDGAR (free, needs a User-Agent header; `edgartools` is MIT), have Claude classify the revenue model from Item 1 and the segment notes into your own taxonomy, store `(cik, label, evidence, model, accepted, reviewed_at)` in DuckDB, and feed accepted and rejected examples back as few-shot context. Keep the labels point-in-time (date stamped), or a backtest will leak today's classification into the past.
- Free alternatives and benchmarks: Hoberg–Phillips text-based industry classifications (free download, Hoberg-Phillips data library), and Fama–French 48/49 industry mappings from SIC (Ken French data library).
- Effort: Qanat demo about 10 minutes; a real pipeline with EDGAR fundamentals about 1 week.

**Second-brain relevance:** LOW – Qanat is a domain data store (point-in-time DuckDB or Postgres) served over MCP, either stdio or Streamable HTTP with a bearer token (`qanat mcp --http --token ...`), with one writer per project. It is a good model for sharing market data with every agent, but it is not personal memory. Two ideas are worth copying into a brain:
- The post's "self-improving" labeler: store each agent-proposed fact with provenance (who said so, accepted or rejected, date) and have the agent re-read the rejections next session.
- Qanat's two-date (as-of) model, a sound design for time-stamped facts.

---

## DeosAIWFZN2 | Indra OCR (datalab-to/indra): a fast CPU OCR model, sold by the voiceover as a "local LLM runner"
- **Link:** https://www.instagram.com/p/DeosAIWFZN2/
- **Account:** @repopicks · **Type:** video (32s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – a real, pip-installable CPU OCR tool (Apache-2.0 code) that is useful for turning PDFs (filings, papers, broker statements) into markdown or JSON. The post itself misdescribes it.

**What it says:** The voiceover says "Datalab Toe just solved the biggest headache with running heavy AI models locally", that running LLMs "usually requires expensive enterprise GPUs", and that Indra "optimizes C++ execution to run cutting-edge models locally with minimal memory". It claims "over 583 stars" (the caption says 568) and ends with "Comment LOCAL" for the link. On screen the whole time is the actual README of `datalab-to/indra` ("Indra OCR … Fast CPU OCR: line detection, CTC recognition, reading…", 583 Stars badge). The README has nothing to do with LLMs.

**What's actually behind it:**
- https://github.com/datalab-to/indra
  - License: Apache-2.0 for the code. Model weights (downloaded from https://huggingface.co/datalab-to/indra-ocr) use a modified OpenRAIL-M license: free for research, personal use and startups under $20M funding/revenue, and not allowed for use that competes with Datalab's API.
  - Status: exists, very new (first commit 2026-10-13), latest commit 2026-10-15 (v0.3.2, by Vik Paruchuri). About 583 stars per the on-screen badge.
  - What it does: a roughly 1M-parameter OCR recognizer plus line detection, layout and reading order, running on ONNX Runtime with no PyTorch. It converts PDFs and images to markdown, text or JSON with boxes. It claims about 49 pages/s on 32 CPU cores and 11–17x the speed of Tesseract and PaddleOCR. It uses the PDF's own text layer when one exists.
  - It comes from Datalab, the company behind marker, surya and chandra. The README upsells its paid managed platform (Chandra model, $5 free credits).

**Verification:** Read the frames (README visible throughout). Ran `git ls-remote`, made a shallow clone, and read the LICENSE (Apache 2.0), README, pyproject (deps: numpy, opencv-python-headless, onnxruntime, pypdfium2, huggingface_hub) and git log. Real code exists in `indra_ocr/` (cli, pipeline, det_post, layout_post, order_post, viewer, …) plus `bench/` and `tests/`. I did not run it, so the benchmark numbers are unverified. The weight license terms are taken from the README; I did not open the HF license file itself.

**Claims vs reality:**
- "Running heavy AI models / modern open-source LLMs locally": **false.** It is an OCR model, not an LLM runtime.
- "Optimizes C++ execution": **misleading.** It is a Python package on ONNX Runtime, which is C++ underneath, as all ORT is.
- "100% free and open-source": **partly true.** The code is Apache-2.0, but the weights are under a restricted OpenRAIL-M variant with a revenue cap and a non-compete clause. That is fine for a personal lab.
- "Over 583 stars": matches the on-screen badge (the caption says 568).
- The speed and accuracy figures come from the README and are self-reported by the vendor on its own benchmark (OmniParseBench). The README is candid about its limits: complex tables, handwriting (~8%), degraded scans (~20%) and some scripts.

**Agenda:** A templated "repo of the day" engagement farm. The same script ("X just solved the biggest headache…", "hands control right back to you with zero friction", "Comment X and I will DM you") is pasted over any repo, with an AI voiceover that does not match the repo. It uses a comment-for-link funnel and a "Get the 5 best…" newsletter teaser in the caption. The upstream README also funnels to Datalab's paid API.

**Lab use:**
- Install: `pip install indra-ocr`, then `indra-ocr file.pdf` (markdown to stdout), `--format json` for boxes, and `indra-ocr-viewer` for a local web viewer on :8765. Python 3.10+. Tested on Linux x86_64/aarch64.
- Dependencies: CPU only, about 18 MB of models fetched from Hugging Face on first run. No GPU, no paid API.
- Uses: bulk OCR of 10-K/annual-report PDFs, research papers and scanned statements into markdown for RAG or agent pipelines.
- Effort: about 15 minutes.
- Alternatives (all OSS): for complex tables and math, use `datalab-to/marker` or `surya` (GPL, heavier) or Docling (MIT). For classic OCR, use Tesseract or PaddleOCR.

**Second-brain relevance:** MEDIUM – Covers capture/ingest: fast CPU-only OCR of PDFs and scans to Markdown/JSON. It is pip-installable and needs no GPU or API, so it can run on any lab VM as the scanned-documents step of an ingest pipeline. It is CLI/Python only, with no server or MCP; port 8765 serves a local viewer. The weights use a restricted OpenRAIL-M variant, which is fine for personal use. It is narrower than MinerU (DeCKnW0DAGc), which adds a document library and search, and it is very new (v0.3.2, first commit 2026-10-13).

---

## DemfalkFKqU | TensorTrade: a real Apache-2.0 RL trading framework, shown via a recycled 2021 docs tutorial and a sine-wave "performance" chart
- **Link:** https://www.instagram.com/p/DemfalkFKqU/
- **Account:** @quantscience_ · **Type:** carousel (8 slides)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – a real, recently revived RL-trading sandbox that is good for experiments, but its own README shows the agent loses money once commissions are included.

**What it says:** "BREAKING: A new Python library for algorithmic trading", introducing TensorTrade as an open-source RL framework "leveraging numpy, pandas, gym, keras, tensorflow". The slides show three code steps: (1) download hourly yfinance data for ticker `TTRD` and add log_return/RSI/MACD with pandas_ta, saving training.csv and evaluation.csv; (2) a `create_env(config)` with a 0.35% commission, a USD/TTRD portfolio, SimpleProfit reward and the BSH action scheme; (3) a Ray Tune `tune.run("PPO", ...)` grid search over FC sizes, learning rates and minibatch sizes. Then come a "Reward Agents (AI)" slide showing the `PBR` reward-scheme class and a "Performance" chart (price/net-worth curve rising from $10k to about $50k). Slide 1 has a "Portfolio Reallocation Chart (Sharpe 0.33, MDD 15.78%)" on smooth synthetic asset curves. The last slide is an ad for a free Oct 22 workshop: "learn.quantscience.io/join (630+ registered)", over a stock Interactive Brokers TWS screenshot.

**What's actually behind it:**
- TensorTrade: https://github.com/tensortrade-org/tensortrade, **Apache-2.0**. It exists and was revived in Feb 2026 after being mostly dormant since 2022 (last commit 2026-02-09; v1.0.4 on PyPI 2026-02-06, version file says 1.0.5-dev). Commit years in the 50-commit shallow clone: 88 in 2022, 16 in 2024, 1 in 2025, 30 in 2026. The project dates from 2019, so it is not "new". It now requires Python 3.12+, gymnasium (not gym), tensorflow>=2.15 and ta. Training goes through Ray/RLlib or Optuna as optional extras. It is a modular RL-trading environment (Exchange/Wallet/Portfolio, action schemes, reward schemes such as PBR, data feeds, renderers).
- Code on slides 3–5 is copied almost verbatim from the repo's own `docs/source/examples/train_and_evaluate_using_ray.md`. That doc explicitly says TTRD / "TensorTrade Corp" is a **fictional** ticker.
- `PBR` on slide 6 is `tensortrade/env/default/rewards.py`, class PBR (position-based returns, R_t = (p_t − p_{t−1})·x_t).
- The performance chart on slide 7 is from `docs/source/tutorials/ray.md`, which trains on a synthetic **sine curve** (`50*np.sin(3*x)+100`, "TensorTrade Coin" TTC) as a sanity check. It is not market data.
- The chart on slide 1 also uses smooth synthetic curves. I could not find its exact source in the repo.
- The tearsheet/IBKR image on slide 8 is a generic TWS screenshot (it shows TWTR and 2019-era prices), unrelated to TensorTrade.

**Verification:** Shallow-cloned the repo and read LICENSE, README, requirements.txt, version.py, git log, docs/EXPERIMENTS.md, the ray tutorial and the train-and-evaluate example, and rewards.py. Checked PyPI JSON for `tensortrade`. Checked quantscience.io via a web search; the join page returned an empty body. Did not run any code. I could not confirm the origin of the slide-1 chart.

**Claims vs reality:**
- "BREAKING: a new Python library": false. It has existed since 2019, was dormant in 2022–2025 and was revived in 2026.
- "leveraging gym, keras, tensorflow": partly outdated. It now uses gymnasium. The shown example trains with Ray RLlib using `"framework": "torch"`, and Keras is not a direct dependency.
- Performance chart: a toy sine wave a trivial agent should solve, not evidence of edge. The repo's own README says so: on BTC/USD, the PPO agent made +$239 at 0% commission but **−$650 at 0.1% commission** (worse than buy-and-hold at −$355). EXPERIMENTS.md concludes "Model overfits to training patterns that don't transfer" and that overtrading destroys the edge once fees apply.
- "Reward Agents (AI)" is an invented term. PBR is a reward function, not an agent.
- Code correctness, step 1: `yfinance` on `TTRD` returns nothing (fictional ticker). Yahoo's `60m` interval only serves about the last 730 days, so the 2021 dates fail today.
- Code correctness, step 2: `fillna(method='backfill')` is deprecated in pandas 2.x and also **backfills the indicator warm-up NaNs with future values**, a small look-ahead leak. Use dropna instead.
- Code correctness, step 3: `tune.run("PPO", …)` with this config dict is the old Ray API (deprecated in Ray 2.x).
- Methodology: the grid search picks the best run by `episode_reward_mean` on training data after only 5 iterations. Evaluation is about 6 weeks of hourly data on one ticker, which leaves heavy overfitting/selection risk.
- PBR subtlety: PBR sets position = −1 (short) when action == 0, but the BSH action scheme can only go to cash. The reward therefore pays the agent for a short P&L the portfolio never earns, and PBR ignores commission. Reward and real P&L are misaligned.

**Agenda:** Engagement post funneling to a "free workshop" at learn.quantscience.io/join. Quant Science (Matt Dancho of Business Science and Jason Strimpel of PyQuant News) sells a paid algorithmic-trading-with-Python course program. The free workshop is the top of that sales funnel. The library itself is unaffiliated and legitimately free.

**Lab use:**
- Install: `python3.12 -m venv .venv && pip install tensortrade`, or clone and `pip install -e .`. Install `pip install -r examples/requirements.txt` for Ray/RLlib.
- Entry point: `examples/training/train_simple.py`. The repo's own docs (overfitting, commission, walk-forward tutorials) are the most useful part.
- CPU is fine for toy runs, and no paid APIs are needed. TensorFlow plus Ray make it a heavy install.
- Effort: half a day to run; days to adapt honestly (walk-forward evaluation, commission in the reward, no backfill).
- Alternatives: Stable-Baselines3 + gymnasium with FinRL or gym-anytrading for RL. For non-RL backtesting, vectorbt, backtrader or Nautilus Trader.

**Second-brain relevance:** NONE – An RL trading library. No memory component.

---

## Dd4JGF1lIhA | QuantMuse: a small, template-README "production-ready" trading system repo (largely scaffolding) plus a course-funnel ad
- **Link:** https://www.instagram.com/p/Dd4JGF1lIhA/
- **Account:** @quantscience_ · **Type:** carousel (4 slides)
- **Category:** USELESS / REPACKAGED
- **Lab value:** LOW – MIT-licensed and readable, but it is a nine-commit hobby project with a stub C++ "execution engine". Use it at most as a structural reference.

**What it says:** "Some guy made a quant trading system that uses AI, real-time data processing, and risk management. Then open sourced it for free in Python." It shows the README header ("Status: Production Ready", MIT, Python 3.8+) and an architecture diagram: a Python layer (data fetchers, factor analysis, strategy framework, backtesting engine, real-time data, AI/ML, visualization, web UI) on top of a C++ core engine (order execution, risk management, portfolio, data loading, strategy engine, performance). It links github.com/0xemmkty/QuantMuse. The last slide is the same ad for a free Oct 22 workshop at learn.quantscience.io/join, illustrated with a **QF-Lib** tearsheet ("Generated with QF-Lib, Example Strategy, 23 May 2019, MQP Strategy – maxsharpe, garch").

**What's actually behind it:**
- QuantMuse: https://github.com/0xemmkty/QuantMuse, **MIT** ("Copyright (c) 2024 Quantitative Trading System"). It exists, but there are only **9 commits** (2025-01-14 to 2025-07-28, authors "prxr" and "EKMM"), with no activity since July 2025. It has about 13.6k lines across 79 .py files and roughly 730 lines of C++. It contains committed `__pycache__`, an `egg-info` folder and a Windows `test.exe` binary.
  - The C++ `OrderExecutor::executeOrder` just sets the status to FILLED (comment in Chinese: "implement actual order execution logic").
  - The Python `BacktestEngine` (221 lines) hands the whole DataFrame to the strategy function in one call. It has no event loop, no look-ahead guard and no slippage, only a flat 0.1% commission.
  - "Strategies" are factor screeners built on yfinance/Binance/Alpha Vantage data with optional OpenAI/LangChain sentiment.
- The README "Production Ready" badge links to `github.com/yourusername/tradingsystem`, an unedited template placeholder.
- QF-Lib (the image on slide 4, unrelated to QuantMuse): https://github.com/quarkfin/qf-lib, **Apache-2.0**, actively maintained (last commit 2026-08-24; PyPI qf-lib 4.0.7). It is an event-driven backtester with look-ahead-bias protections and PDF tearsheets, a far more serious library than QuantMuse.

**Verification:** Shallow-cloned both repos and read LICENSE, README, git log, backtest_engine.py, builtin_strategies.py and order_executor.cpp. Checked PyPI for qf-lib (quantmuse is not on PyPI). Did not run any code, including test.exe.

**Claims vs reality:**
- "Production-ready": false. It has a stub execution engine, no broker integration, a naive backtester and 9 commits. The badge is self-awarded with a placeholder link.
- "C++ core engine for low-latency order execution": stub code only.
- "Comprehensive risk management": a 91-line C++ risk_manager plus Python limits. Untested in live use.
- "Strategies that actually work" (ad slide): no performance evidence for QuantMuse is shown. The tearsheet shown is a 2019 QF-Lib example from a different project, a misleading visual pairing.

**Agenda:** Repo-of-the-day content farming that funnels to Quant Science's free workshop, which leads into their paid algorithmic-trading course (Matt Dancho / Jason Strimpel).

**Lab use:**
- Do not deploy. At most, read `data_service/factors/` and `strategies/` for ideas on factor-screener structure.
- Install entry, if you want to read it: `pip install -e .` in a venv. It needs OpenAI/Alpha Vantage keys for the AI parts. Do not execute `test.exe`.
- Effort to make it trustworthy: high, and it is not worth it.
- Better open-source alternatives: **QF-Lib** (the library that actually appears in the post's last slide, Apache-2.0); Microsoft Qlib for factor research and ML; Nautilus Trader or backtrader for event-driven backtests; Alphalens-reloaded for factor analysis.

**Second-brain relevance:** NONE – No memory or knowledge component.

---

## DenP7kUD3Az | openchamber/openchamber: an open-source desktop/web/VS Code/mobile GUI for OpenCode coding agents
- **Link:** https://www.instagram.com/p/DenP7kUD3Az/
- **Account:** @meow.codes · **Type:** video (43s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** MEDIUM – a real, very active MIT-licensed UI and remote-control layer for OpenCode agents. It is useful for driving agent sessions on a headless lab server from a browser or phone, but it is built for OpenCode, not Claude Code.

**What it says:** The voiceover says OpenChamber "has already racked up over 11,000 stars" and runs on desktop, web, VS Code and mobile. It is an open-source environment to "launch an OpenCode AI coding agent, watch its changes, and ship the result". The voiceover also lists these features: session goals that keep the agent working until it hits a target, comparing up to five model runs side by side and "fusing" the best parts, a built-in preview where you point at UI elements and send screenshots, cross-device sync, recurring scheduled tasks, and a QR-code private relay. On screen it scrolls through the README at `https://github.com/openchamber/openchamber` (cropped URL bar): "Run agent work. Keep control. Ship from anywhere.", "What you can do with OpenChamber", Quick start (deb/rpm/AppImage, VS Code Marketplace, CLI for Web/PWA requiring Node.js 24.14+, `curl … scripts/install.sh | bash`), Guides, Why OpenCode?, Acknowledgments and License: MIT.

**What's actually behind it:**
- https://github.com/openchamber/openchamber
  - License: MIT (Copyright (c) 2025 Bohdan Triapitsyn).
  - Status: exists and is extremely active. Latest commits 2026-10-18, with PR numbers above #5100. The star count was not legible on screen (the badge rendered blank), so the "11,000 stars" figure is unverified.
  - Stack: TypeScript/Bun/Vite with Docker, a Caddyfile and nix flake.
  - What it does: a workspace UI around the OpenCode agent CLI. It provides session goals, Multi-run (the same task on up to five models in separate worktrees) plus Fusion, Changes Walkthrough, an app preview with element picking and screenshots, GitHub issue/PR context, scheduled prompts, and remote access through an end-to-end encrypted Private Relay paired by QR code, or Cloudflare/ngrok tunnels or SSH.
  - The README states it is independent and not affiliated with the OpenCode team. Desktop bundles the matching OpenCode CLI.

**Verification:** Read all six contact sheets and cropped the URL bar. Ran `git ls-remote`, made a shallow clone, and read the LICENSE (MIT), README and git log. Not executed. I could not verify the star count (the GitHub API is blocked and the badge is not legible). I did not audit the relay's security claims.

**Claims vs reality:**
- "Runs on desktop, web, VS Code and mobile": **true per the README** (desktop apps, Web/PWA, VS Code extension, iOS/Android through the web/relay).
- Session goals, compare five runs, fuse, preview with element picking, sync, scheduled tasks, QR relay: **all listed in the README.** The voiceover is a faithful summary.
- "Over 11,000 stars": **unverified.**
- "Prompt to production without leaving your editor": marketing. It is an agent UI, and quality depends on the model you use.

**Agenda:** @meow.codes is a repo-showcase account. This post has no comment-for-link funnel in the transcript and is a fairly accurate README read-out. Mild engagement farming only.

**Lab use:**
- Fit: run `openchamber` on the Linux lab server and reach agent sessions from a laptop or phone through the private relay or a tunnel. Schedule recurring agent jobs, for example a nightly data-pipeline check or a backtest refresh. Multi-run is handy for comparing models on the same refactor.
- Install: CLI/Web needs Node.js 24.14+ and the OpenCode CLI (`opencode.ai`). The install script is `curl -fsSL https://raw.githubusercontent.com/openchamber/openchamber/main/scripts/install.sh | bash` (read it first). It binds to localhost by default and offers a `--ui-password` option. Linux deb/rpm/AppImage builds exist for desktop.
- Dependencies: model API keys or subscriptions for OpenCode's providers (Anthropic, OpenAI, local models through OpenAI-compatible endpoints). No GPU unless you use local models.
- Effort: 1–2 hours.
- Caveat: if you standardize on Claude Code, OpenChamber's OpenCode dependency is a parallel stack. Claude Code's own remote/web sessions or OpenCode itself may be simpler.

**Second-brain relevance:** LOW – A UI and remote-control layer for OpenCode sessions (cross-device access through an end-to-end-encrypted Private Relay, scheduled prompts). It keeps OpenCode sessions but provides no knowledge store, search or memory API. It is useful only as a way to reach agents that use a second brain, not as part of one, and it does not drive Claude Code.

---

## Dd2iE-vjl1- | "Top 15 GitHub repositories for finance projects (ranked by GitHub stars)": carousel slides NOT retrievable, only the cover and metadata
- **Link:** https://www.instagram.com/p/Dd2iE-vjl1-/ (the user's link pointed at slide 5, `img_index=5`)
- **Account:** @raph.thefinanceguy (Raphael | Financial Markets) · **Type:** carousel (slide count unknown, at least 5; probably 15+ given the title)
- **Category:** REFERENCE / RESEARCH MATERIAL (provisional: the list itself could not be read)
- **Lab value:** MEDIUM (provisional) – a star-ranked list of finance repos is useful reference material. The four repos the page metadata hints at are real, open source and actively maintained, but the actual 15 entries, and which one is slide 5, could not be recovered.

**What it says:** Only the caption and a cropped cover were retrieved. The caption (posted September 28, 2026; 500 likes, 22 comments) reads: "Top 15 top GitHub to build a finance project. 🏴‍☠️ As a disclaimer, GitHub Stars measure developer enthusiasm, not necessarily the investment performance or production readiness of the tool to be implemented. But it is a good way to learn!! The 15th is the one you re going to build 😎 #nyc #wallstreet #quant #finance #trading". The cover (a 640×640 center-crop) shows "@raph.thefinanceguy", "[To]p 15 GitHub [re]positories [for] finance project[s]", "[rank]ed by GitHub stars". The page's `keywords` meta tag lists "github finance projects, trading agents, 0 access, ai hedge fund, qlib, quantconnect, finance tools, investment strategy, trading platform, algorithmic trading, machine learning, portfolio optimization, wall street, nyc". This strongly suggests (but does not prove) that the list includes the repos below.

**What's actually behind it (inferred from the page keywords, not from the slides):**
- **TradingAgents:** https://github.com/TauricResearch/TradingAgents
  - License: Apache-2.0
  - Status: exists, last commit 2026-10-16 (existing clone)
  - Multi-agent LLM trading-research framework (analyst, researcher, trader and risk-manager agents).
- **ai-hedge-fund:** https://github.com/virattt/ai-hedge-fund
  - License: MIT
  - Status: exists, last commit 2026-10-02
  - Proof-of-concept LLM "investor persona" agents. The README states "educational purposes only… the system does not actually make any trades". It needs a Financial Datasets API key (paid beyond the free tickers) and an LLM API key.
- **Qlib:** https://github.com/microsoft/qlib
  - License: MIT
  - Status: exists, last commit 2026-10-08
  - Microsoft's AI-oriented quant research platform: data layer, alpha factors, ML models and backtesting.
- **LEAN (QuantConnect):** https://github.com/QuantConnect/Lean
  - License: Apache-2.0
  - Status: exists, last commit 2026-10-16
  - The open-source C#/Python algorithmic trading engine behind QuantConnect. It runs locally; the cloud data and service are paid.
- The other ~11 entries, and the "15th one you're going to build", are unknown.

**Verification:**
- Retries against the mirror, about 25 requests over 3 rounds with pauses, using a Discordbot user agent:
  - `https://uuinstagram.com/p/Dd2iE-vjl1-/` returned 200 twice and 429 twice. It serves Instagram's own HTML page (caption, date and likes, with only the cover in `og:image` and no carousel child URLs).
  - `/p/…/?img_index=5` returned 429.
  - `/images/Dd2iE-vjl1-/1…10` returned 500 "post not found" in all three rounds.
  - `/videos/Dd2iE-vjl1-/1–2` returned 500 "post not found".
- The cover thumbnail was downloaded from Instagram's CDN and saved as `c/Dd2iE-vjl1-/m01_cover_crop.jpg`. The uncropped CDN URL returned 403.
- Web searches for the handle and the post title found nothing.
- Keyword repos: checked with `git ls-remote` and shallow clones (licenses and last-commit dates read; ai-hedge-fund README skimmed). Not executed.
- instagram.com was not hit directly (it is rate-limited).
- **Status:** the post *exists* and is public (Instagram's page returns its caption and metadata), so it is not deleted. The carousel media could not be retrieved through the mirror, which fails on this post's media. This may be a mirror limitation or a restricted/age-gated media flag. Slide 5's content is unknown.

**Claims vs reality:**
- "Ranked by GitHub stars" plus the caption's own disclaimer that stars ≠ performance or production readiness: an honest framing, as far as can be seen.
- "The 15th is the one you're going to build": a tease, so the 15th repo is unknown. It may be the creator's own project or course.
- Nothing else could be checked without the slides.

**Agenda:** A finance-education creator farming saves and engagement with a list post. No funnel is visible in the caption, and the slides could not be read.

**Lab use:**
- To recover the list: open the post in the Instagram app or browser while logged in and screenshot the slides (especially slide 5), or retry the mirror later.
- Meanwhile, the four inferred repos fit a Python quant lab:
  - **Qlib:** `pip install pyqlib`, then download the community CN/US daily data. CPU is fine; GPU is optional for deep models. Effort: about 1 day to a first factor backtest.
  - **LEAN:** `pip install lean` (CLI, needs Docker). Local backtests require bringing your own data. Effort: about half a day.
  - **TradingAgents / ai-hedge-fund:** need paid LLM API keys (Anthropic/OpenAI/etc.), and ai-hedge-fund needs a Financial Datasets key. Use them as agent-architecture references, not as profitable strategies. Effort: about 1–2 hours each to run read-only experiments.

**Second-brain relevance:** NONE – A list of finance repos (slides not retrieved). Nothing memory-related could be identified. Of the inferred repos, TradingAgents has only an append-only Markdown decision log (see DegkHS3GRHJ).

---

## Dd4QRzpFM00 | "Mine SSRN for strategy ideas": a podcast clip pointing at a free paper archive, with a standard idea-to-live pipeline drawn on a whiteboard
- **Link:** https://www.instagram.com/p/Dd4QRzpFM00/
- **Account:** @chartfanatics · **Type:** video (46s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** MEDIUM – SSRN is a real, free, high-value source of testable strategy papers, but the clip gives no specific paper, rule or result.

**What it says:** A guest on the ChartFanatics podcast says "90% of institutional trading strategies are coming from this one place": the Social Science Research Network (on-screen "ssrn.com"). He says it holds academic and industry papers on trading strategies; you read the findings and the "why", don't copy one-to-one, and use it as the starting point for your rules. The caption is pure bait ("THIS Made Him BILLIONS (MUST WATCH)", on-screen "The Secret That Made Billions"). B-roll shows an SSRN search page for "Trading" (e.g. "Statistical Arbitrage Trading Strategies and High Frequency Trading", Hanson & Hall, 2012, 5,850 downloads; "Informed Trading, Institutional Trading, and Spread", Dey & Radhakrishna; "Time Varying Liquidity Trading, Private Information and Insider Trading", Lei & Wang). A cropped whiteboard (about 41–43s) reads: "RET -> chase trades / INST -> validated trading strat / Pipeline: Idea -> Rules -> Encoded -> Backtest -> Validate (1. IS vs OOS, 2. MC) -> Live trading auto (1. performance 2. risk)"; "SSRN.COM -> do not copy -> findings / why"; "95% = research -> acad. / industry"; Monte Carlo equity-curve fan sketches; "DD > 10k$".

**What's actually behind it:**
- SSRN, https://www.ssrn.com/ (owned by Elsevier). A free preprint and working-paper repository. Reading and downloading most papers is free (some need a free account). Its Financial Economics Network (FEN) holds thousands of anomaly and factor papers. It exists and is active.
- No named strategy or indicator is given, so there are no rules to recover or test from this post.
- Speaker: not named on screen. A web search found a transcript of a near-identical clip ("ninety percent of institutional traders ... Social Science Research Network") attributed to Matteo Conte, a former institutional trader who now sells trading education. That match is likely but **not confirmed**.

**Verification:** Viewed all 6 contact sheets. Cropped the SSRN results list and the whiteboard with ffmpeg. Web search for SSRN and for the clip's origin. I could not confirm the speaker's identity or any of the profit claims attached to him.

**Claims vs reality:**
- "90% of institutional strategies come from SSRN" (the whiteboard says 95%): an invented statistic. Institutions do read academic papers, but most published anomalies decay after publication. McLean & Pontiff (2016, J. Finance) found returns fall roughly 26% out of sample and 58% after publication. Hou, Xue & Zhang (2020, "Replicating Anomalies") found most anomalies fail once microcaps and realistic tests are applied.
- "Made him billions": nothing in the clip supports it. It is a clickbait caption.
- Whiteboard pipeline (idea, rules, code, backtest, IS/OOS, Monte Carlo, live with risk monitoring): sound and standard practice. This is the useful part.

**Agenda:** Engagement farming for the ChartFanatics podcast and brand ("Follow to master trading"). ChartFanatics also sells trading education, and guests often have their own courses. No link funnel appears in this clip.

**Lab use:**
- Entry point: browse SSRN FEN, or use curated, already-coded paper lists that replicate SSRN papers: Quantpedia (freemium summaries), the "Papers With Backtest" podcast, and the open Open Source Asset Pricing dataset (Chen & Zimmermann, https://www.openassetpricing.com/, about 200 replicated anomaly signals with free data and code).
- Testing workflow: for each paper, (1) write the exact rule, (2) code it in vectorbt, backtrader or a plain pandas event loop, (3) apply realistic costs (equities about 5–10 bps per side plus a borrow cost for shorts; FX spread plus commission), (4) run walk-forward or anchored IS/OOS with the post-publication period as the true OOS, (5) Monte Carlo trade reshuffles or a block bootstrap for drawdown distribution, (6) correct for multiple testing (deflated Sharpe ratio, Bailey & López de Prado).
- Dependencies: Python with pandas, numpy and vectorbt or backtrader. No GPU. Free data (yfinance or Stooq for prices, SEC EDGAR for fundamentals).
- Effort: low to start reading; 1–3 days per paper to replicate properly.
- Red flags: hype caption, made-up percentage, no concrete strategy. Treat it as a pointer, not a method.

**Second-brain relevance:** NONE – SSRN is a content source that could be ingested into a research knowledge base, but the post offers nothing about storing or retrieving knowledge.

---

## DenSGzckhBw | "If you trade, you need to code": a reasonable case for automated signal scanning, used to funnel viewers to the Crown Macro Letter newsletter
- **Link:** https://www.instagram.com/p/DenSGzckhBw/
- **Account:** @nicholascrown · **Type:** video (99s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – the idea (a config-driven scanner that checks many rule-based signals across many tickers and alerts to Slack) is sound and easy to build yourself; the creator's own code is private.

**What it says:** Title card "If you trade, you need to code." He says working memory holds 3–4 items (a "1952 study" said 7), so a trader watching a few indicators on a few tickers finds "two or three big trades a year" and then forces trades, "the number one reason why traders lose money." Hedge-fund PMs therefore build infrastructure "to watch the entire surface." His own dashboard "tracks roughly 1,700 signals" across technicals, pairs and statistical relationships and posts to Slack when "something breaks a multi-year regime." Options: build it yourself (months), pay "two and twenty", or follow someone who has built it: "I publish mine every single Monday morning at 5am" with "exact levels and setups." End card: "Comment 'LETTER' for the link to the newsletter" plus a disclaimer ("Educational purposes only. Not investment advice...").

**What's actually behind it:**
- On-screen MIT News article: "When four is not four, but rather two plus two", Emily Finn, MIT News Office, June 23, 2011 (MIT neuroscientists on the limits of visual working memory). It is a real article.
- On-screen code (about 0:62–0:68, cropped): a VS Code window on a project named **OMNEUS-ENGINE** showing `reports/crown_macro_letter_2026-04-30.txt`, with source folders `asset/` (asset_factory.py, simple_asset.py, spread_asset.py), `indicator/` (distance_from_mo..., historical_volatility..., indicator_factory.py, moving_average_..., range_width_indic..., relative_correlatio..., relative_performan..., relative_ratio_indic..., returns_indicator.py), `data_provider/`, `cli/`, `config/`. The report lines read like `[SOXX] Distance From 50DMA Extended High — Technical state: current close is materially extended above the 50-day moving average. Starter threshold set to 3%. Value 0.2519, Status TRIGGER, Details {'operator': 'gt', 'threshold': 0.03}`, repeated for XLRE, KRE, ARKK, GDX, JETS.
- The engine is not public; no repo name or URL is given. The "1,700 signals" are, from what is visible, ticker × rule threshold checks (e.g. distance from 50DMA > 3%).
- The Crown Macro Letter: web searches found no public listing, pricing or archive. Unverified.

**Verification:** Read the full transcript and every frame; cropped the code screen and the MIT News card at full resolution. Web searches for "Crown Macro Letter" / Nicholas Crown returned nothing relevant. Did not find a public repo for "omneus-engine." Nothing executed.

**Claims vs reality:**
- "Study in 1952 ... seven things": the classic paper is George Miller, "The Magical Number Seven, Plus or Minus Two" (1956), not 1952. The "revised down to 3 or 4" point matches Cowan (2001) and the 2011 MIT work shown; that is fair.
- "Number of things you watch is the number of real opportunities": partly true (breadth helps, per the fundamental law of active management), but scanning 1,700 signals multiplies false positives. Without out-of-sample testing, multiple-comparison control and costs, more alerts do not mean more edge.
- "Number one reason traders lose money is forcing trades": opinion; unsupported.
- "Modern PMs first build infrastructure to watch the entire surface": broadly true at systematic and large discretionary funds.
- "Breaks a multi-year regime ... I hear about it instantly": the visible rules are simple threshold triggers (price vs. 50DMA), not regime detection.
- No performance record for the newsletter's setups is shown.

**Agenda:** Comment-"LETTER" funnel to his weekly newsletter (price unknown). The video is a lead magnet; "follow someone who's already done the build" is the pitch.

**Lab use:**
- Rebuild it: a YAML-configured scanner in Python. Universe list (sector ETFs, futures, pairs) → data provider (yfinance/Stooq for free EOD, or your broker API) → indicator classes (distance from MA, rolling z-score, relative ratio vs. benchmark, rolling correlation, historical volatility, range width) → rules `{indicator, operator, threshold}` → daily report plus Slack webhook. That is exactly the structure visible in his IDE.
- Dependencies: pandas, numpy, pyyaml, requests (Slack incoming webhook); optional `pandas-ta` or `ta` for indicators. No GPU, no paid API needed for EOD data.
- Effort: a weekend for a working v1 (cron job at 05:00 writing a markdown report); 1–2 weeks to add pairs/cointegration (statsmodels), regime breaks (e.g. rolling z-score > 3, ruptures for change points) and a backtest of each rule's hit rate so you know which alerts actually matter.
- Open-source building blocks: plain pandas (or a backtesting library you already use; check its license) for testing each rule's forward returns; `statsmodels` for cointegration. Not verified here: specific scanner repos, since the post names none.

**Second-brain relevance:** NONE – A YAML signal scanner is a lab tool. Its daily reports could be ingested as notes, nothing more.

---

## DenJITWMbi2 | Seven-file folder pattern for "self-improving" agents (PROMPT.md, handovers, KNOWLEDGE.md, read-only evals, skills), with a comment-for-guide funnel
- **Link:** https://www.instagram.com/p/DenJITWMbi2/
- **Account:** @claragig_ · **Type:** video (56s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – a sensible, free, tool-agnostic pattern you can apply to Claude Code agents in the lab today; nothing to install, but also nothing new.

**What it says:** "Seven things that make your AI agents self-improve and get better every single week," and "it all comes down to pretty good folder and file structure." (1) PROMPT.md with role, goals and tools (on screen: `# Role / Content strategist / # Goals / - find trends / - grow sav...`). (2) Handovers written after every session (on screen: `handover-10-16.md` with `# Did – posted 2 videos / # Went wrong – hook too slow / # Next – test a new hook`). (3) KNOWLEDGE.md of lessons (`hooks under 2 s win`, `post at 7 pm`, `saves beat views`). (4) Evals: a self-test the agent runs, 10 criteria, must hit 8/10 (on screen EVALS.xlsx with `=COUNTIF(C2:C11,"pass")`, criteria "Backed by real data, Cites every source, Only scientific sources (no Reddit), Neutrally written, No undertone, No jargon, No judgment, Concise, Every source is dated, Clear and simple", showing 5/10 then "Accepted 8/10"). (5) The evals are read-only for the agent (macOS file-permissions dialog: agent → "Read only") "because agents tend to find loopholes and try to cheat." (6) Review failures together and let the agent rewrite PROMPT.md (chart "mistakes per session", Session 1→20, "PROMPT.md updated"). (7) Repeated jobs become skills (toggles `/write-captions`, `/be-direct`, `/handover`, `/scriptwriter`, `/analyst`, `/trendscout`). Final folder `agent/`: PROMPT.md, handovers/, KNOWLEDGE.md, EVALS.xlsx, review.md, skills/. End: "comment self-improvement, I'll send it to you."

**What's actually behind it:**
- No tool, repo or product is named. The pattern is generic agent hygiene that Claude Code supports natively: CLAUDE.md (≈ PROMPT.md), memory/notes files, `.claude/skills/` (skills), hooks or a test script as evals, file permissions or a deny rule to keep evals read-only.
- The "mistakes per session" chart is an illustrative graphic with no real data or axis values beyond "12" at the top.
- A rigorous, open-source version of step 6 exists: Microsoft SkillOpt, https://github.com/microsoft/SkillOpt, **MIT**, active (last commit 2026-10-18, v0.2.0 on PyPI). It edits a skill file only when a held-out validation score improves, and its `skillopt-sleep` tool mines past Claude Code/Codex sessions nightly. (Named here as an alternative, not by the creator.)

**Verification:** Read the transcript and every frame; read the on-screen file contents and spreadsheet criteria. Shallow-cloned microsoft/SkillOpt (see DbEK3bustQ7) for the comparison. The "self-improvement guide" itself was not obtainable (comment funnel). Nothing executed.

**Claims vs reality:**
- "Self-improve every single week": the agent improves only in the sense that its prompt and notes get edited after human-reviewed failures. Model weights do not change. Reasonable if stated plainly.
- "8/10 criteria to accept": the criteria shown are mostly subjective and the agent self-grades them. A self-graded checklist is weak evidence; checks should be deterministic where possible.
- "Make evals read-only because agents cheat": good, real advice (reward hacking / editing tests is a known agent failure mode). Note that an agent with shell access can still copy or bypass an Excel file; true isolation needs the grader to run outside the agent's write scope.
- "It's just really good folder and file structure": mostly true for this pattern.

**Agenda:** "Comment self-improvement" to receive her guide (DM funnel, likely list-building for a creator/agency business). Content is aimed at social-media content agents, not trading.

**Lab use:**
- Apply directly to a research agent in Claude Code: `CLAUDE.md` (role: quant research assistant; tools: data dir, backtest CLI), `handovers/YYYY-MM-DD.md` written by a Stop hook or a `/handover` command, `KNOWLEDGE.md` (data quirks, rejected hypotheses, known look-ahead traps), `.claude/skills/` for repeated jobs (fetch data, run walk-forward backtest, write tearsheet).
- Make evals deterministic and outside the agent's reach: a pytest suite or script owned by another user / mounted read-only that checks no look-ahead (timestamps), fees and slippage included, out-of-sample split respected, results reproducible from seed. Deny edits to that path in Claude Code permissions.
- If you want automated prompt/skill optimization with a validation gate, try SkillOpt (`pip install skillopt`; Python ≥3.10; needs an LLM API backend such as OpenAI/Azure/Claude, or a local model via vLLM).
- Effort: 1–2 hours for the folder pattern; a day to wire hooks and a proper eval script.

**Second-brain relevance:** MEDIUM – Covers the consolidation and agent-context-injection layers as a convention:
- PROMPT.md (roughly CLAUDE.md)
- per-session handovers (an episodic log)
- KNOWLEDGE.md (distilled lessons)
- read-only evals
- skills

It is pure files, so it is self-hostable and shareable via git, but it has no automatic capture, search or server, and at scale the handovers need an indexer. It fits as the per-agent or per-project file layout. SkillOpt-sleep (DbEK3bustQ7) is the validated, automated version of steps 6–7.

---

## DYYaA1LKtoO | Use an Obsidian vault of four Markdown files (README/STATUS/progress/decisions) as portable, model-agnostic AI project memory
- **Link:** https://www.instagram.com/p/DYYaA1LKtoO/
- **Account:** @actuallydamy · **Type:** video (138s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** MEDIUM – not trading-related, but a simple, free, immediately usable memory convention for Claude Code and agent work on the lab server. It is essentially what CLAUDE.md and memory-bank patterns already do.

**What it says:** "how to use obsidian to build your own AI memory system", so that you can "switch models within a matter of minutes" without being trapped in one vendor's ecosystem. Step 1: download the free Obsidian desktop app and create a vault ("a fancy name for a folder"). Step 2: pick a project and make a folder for it. Step 3: link that folder to an AI tool with local read and write access. She shows Claude Cowork's "Allow Claude to change files in 'Content'?" dialog and says any tool works. Then a startup prompt has the AI create four core files:
- README.md: stable overview, who it's for, links, how AI helps.
- STATUS.md: current snapshot, next action, blockers, items needing review.
- progress.md: dated diary of what happened and changed, and what's next.
- decisions.md: decisions made, why, options rejected, and whether each can be revisited.
The on-screen prompt adds: "Do not mix multiple projects into one folder", "keep the structure minimal", and "If important context is missing, ask me before inventing it." There is an alternate prompt for migrating from a Claude chat or project ("Extract only the useful ongoing context. Do not copy the whole conversation ... Format the output with clear headings for each file so I can manually copy each section"). Step 4 shows the OpenAI Codex desktop app ("Ask Codex anything", model "5.5 Medium", project "personal-content") with a prompt telling it to read the four files as "the source of truth" and summarise status, next action and gaps. Step 5 is an end-of-session prompt: "Before we finish, update my project memory. Please give me: 1. An updated STATUS.md 2. A new progress.md entry 3. Any new decisions for decisions.md 4. Any README.md updates if the project direction changed."

**What's actually behind it:**
- Obsidian, https://obsidian.md : free for personal use, **closed source** (proprietary app). Notes are plain local Markdown files, so there is no lock-in. Sync and Publish are paid add-ons.
- Claude Cowork (Anthropic desktop agent) and OpenAI Codex app: the AI tools shown. Both are paid or subscription-based. Neither is required; any agent with file access works.
- No repo or plugin is named. The prompts are shown in full on screen, so the "comment OBSIDIAN" guide adds little.

**Verification:** Viewed all 18 contact sheets and cropped the prompt and Codex screens. Read the full transcript. Obsidian's licensing is from general knowledge (well established); no web check was needed for an app this well known. Nothing else to verify; no performance claims.

**Claims vs reality:**
- "Own your AI memory, switch models in minutes": true in the sense that plain Markdown files are portable across Claude, Codex and local LLMs.
- "Obsidian is completely free": true for personal use, but the app is not open source. Obsidian itself is not needed for the AI part; the files are what matter.
- "The system only works if you keep the files updated": correct, and the main weakness is manual discipline. A hook can automate it.

**Agenda:** "Comment OBSIDIAN" DM funnel for prompts and follower growth ("follow for more AI content"). Low-stakes; no product sold in the clip.

**Lab use:**
- For each research project on the server (e.g. `~/lab/projects/<strategy>/`), keep `README.md`, `STATUS.md`, `progress.md` and `decisions.md` in git, with `CLAUDE.md` pointing to them. For a quant lab, add `experiments.md`: every backtest variant tried, with parameters, dates and result. That doubles as the trial count you need for deflated-Sharpe and multiple-testing corrections.
- Automate the end-of-session update with a Claude Code Stop or SessionEnd hook or a slash command, instead of remembering to paste the prompt.
- Open-source alternatives to Obsidian: Logseq (AGPL), Joplin (AGPL), or any editor plus git. Basic Memory (MCP server over Markdown; licence believed AGPL, not checked here) or similar MCP note servers give agents structured access.
- Dependencies: none (plain Markdown). Effort: about 30 minutes.

**Second-brain relevance:** MEDIUM – Covers the storage-schema and agent-context-injection layers for one project: four plain Markdown files (README/STATUS/progress/decisions) that any agent reads at session start and updates at session end. Self-hostable by definition (files in git on the lab server) and shareable with every VM and agent through git or a network mount. But it is a convention plus prompts, not a memory system: no search, no cross-project index, no automatic capture, and Obsidian (closed source, desktop-only) adds nothing on a server. Use it as the per-project "front page" of the brain and pair it with an indexing memory server (GBrain or Hindsight, see Dem60yJDELo and DeCKnW0DAGc) for retrieval.

---

## DdtaUOCNmNs | "Claude Code Project Structure" cheat sheet (by Brij Kishore Pandey), reposted; broadly right but with several made-up or incorrect details
- **Link:** https://www.instagram.com/p/DdtaUOCNmNs/
- **Account:** @julianvelez1997 · **Type:** image
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** MEDIUM – a useful mental model for organising a Claude Code quant-lab repo (CLAUDE.md, .claude/commands, skills, agents, hooks, .mcp.json), but verify each detail against the official docs.

**What it says:** The infographic is credited "by Brij Kishore Pandey" (linkedin.com/in/brijpandeyji). It shows a `my_project/` tree containing CLAUDE.md, .claude/ (settings.json, settings.local.json, commands/{review,deploy,test-all,bootstrap}.md, skills/{code-review,test-writer,security-audit,refactor}/SKILL.md with scripts/references/assets, agents/*.yml, plugins/manifest.json), .mcp.json, src/, tests/, docs/, scripts/, Dockerfile and so on. Fifteen numbered panels cover key components, CLAUDE.md essentials, extension types, hook events, skill structure, popular MCP servers, slash commands, agent-team patterns, context management thresholds, security practices, CLAUDE.md anti-patterns, debugging and pro tips. The caption says the creator has "used this Claude Code project structure multiple times… battle-tested."

**What's actually behind it:** No repo. It is a reposted third-party infographic about Anthropic's Claude Code (https://docs.claude.com/en/docs/claude-code). The poster is not the author.

**Verification:** Read the full image (every panel) and compared it with my knowledge of Claude Code's documented features. I did not fetch the docs live.

**Claims vs reality:**
- Correct:
  - `npm i -g @anthropic-ai/claude-code`.
  - CLAUDE.md as project memory; `.claude/settings.json` and `settings.local.json` (git-ignored); `.claude/commands/*.md` as custom slash commands; `.claude/skills/<name>/SKILL.md` with optional scripts and references; `.mcp.json` for project MCP servers.
  - Hook events PreToolUse, PostToolUse, SessionStart, SessionEnd and Notification exist; `/compact`, `/clear`, `/cost`, `/init`, `--resume` and `--verbose` exist.
- Wrong or misleading:
  - Subagents are **Markdown files with YAML frontmatter** in `.claude/agents/*.md`, not `.yml` files.
  - Plugins use `.claude-plugin/plugin.json` (and marketplace.json), not `.claude/plugins/manifest.json`.
  - There is **no "PreCommit" hook event** in Claude Code. A secret-scanning gate would be a git pre-commit hook or a PreToolUse hook on `git commit`. The panel also omits real events such as UserPromptSubmit, Stop, SubagentStop and PreCompact.
  - `/deploy`, `/test-all`, `/bootstrap`, `/document` and `/refactor` are not built-ins; they only exist if you write them. `/review` is built in.
  - `--resume` resumes a past conversation; it does not "replay failed sessions".
  - The "0–50 / 50–70 / 70–90 / 90%+" context rules are the author's rule of thumb, not official, and the 70–90% line is printed twice.
  - Panels 8 and 9 are duplicated, a layout error that suggests careless or AI-assisted production.
  - "Keep CLAUDE.md under 500 lines" is reasonable advice, but the number is arbitrary.

**Agenda:** LinkedIn-style cheat-sheet engagement (the original author's LinkedIn is in the footer). The reposter is farming saves with a "battle-tested" claim. Nothing is sold directly.

**Lab use:**
- Apply the pattern to the quant-lab repo:
  - CLAUDE.md: data sources, the backtest conventions (no look-ahead, costs, walk-forward) and how to run tests.
  - `.claude/commands/backtest.md`.
  - A `skills/backtest-review/SKILL.md` checklist.
  - A `.claude/agents/quant-reviewer.md` subagent.
  - A PostToolUse hook that runs ruff/pytest.
- Free, needs only a Claude plan or API key. Effort is 1–2 hours.
- Use the official docs (docs.claude.com → Claude Code: memory, slash commands, skills, subagents, hooks, plugins) as the source of truth instead of this image.

**Second-brain relevance:** MEDIUM – Covers the agent-context-injection layer for Claude Code. CLAUDE.md is project memory, `.claude/skills` holds procedures, hooks (SessionStart / UserPromptSubmit / Stop) are where memory gets injected and captured, and `.mcp.json` is where a shared memory MCP server is registered per project. It is a partly inaccurate cheat sheet, not a memory system, and it is Claude Code-specific: other agents need their own equivalents (AGENTS.md, Codex hooks). Take the real hook event names from the official docs when wiring memory capture.

---

## Ddei3-cy1cC | "Build your first trading bot": paste an SSRN paper into Astral (a paid AI trading workspace) and hope for good results
- **Link:** https://www.instagram.com/p/Ddei3-cy1cC/
- **Account:** @larprichie · **Type:** video (30s)
- **Category:** PAID / CLOSED – USABLE
- **Lab value:** LOW – the core idea (turn an academic paper's strategy into code and backtest it) is good, and Claude Code can do it locally for free. The advertised tool is a closed $30/month SaaS, and the "results" shown are not a backtest at all.

**What it says:** Overlay title "How to build ur first trading bot (5 min)". He says to go to "papers.ssrn" (spoken "papers.ssm"), where "people publish their trading strategies from firms, colleges", and click one. Then "copy this entire published document", paste it into Astral's AI, and "tell it to build this exact strategy". He says Astral codes the strategy and does everything, and that "most of the time your results won't be good but sometimes your results will be like this. And that's how you know you found yourself a nice gold mine."

On screen:
- The SSRN Advanced Search shows search term "intraday trading", "Displaying results 1 to 50 of 10000". Visible results include "Intraday Index Predictability and Options Trading Profitability" and "Informed Trading During the Intraday: The Case of Short Sellers".
- The PDF is opened and the text is copied into the Astral chat panel. The paste is legible: "Electronic copy available at: http://ssrn.com/abstract=2265977 INFORMED TRADING DURING THE INTRADAY: THE CASE OF SHORT SELLERS by Benjamin M. Blau, Tyler J. Brough, and Julian Zhang(?) ABSTRACT: Theory in Admati and Pfleiderer (1988) predicts that informed…".
- The Astral terminal (`heyastral.ai/terminal/session-…`) greets with "Hey, I'm Astral!" and suggests prompts such as "Build a 20 EMA trend-follow strategy for MSFT on 1h".
- The "result" screen shows an NVDA chart with indicators "Start_Price", "Target_Price" and "50Pct_Rally_Window". The chat reply starts "Do one trade with 50%…" and reads: "Here is an example of a 50%+ gain on NVIDIA ($NVDA) from early 2024… NVDA 53.4% Rally (Jan 2 – Feb 14, 2024): start price $48.17, end price $73.90, return +53.42%, timeframe 6 weeks", followed by an "Analysis" paragraph about AI demand and Q4 earnings.

**What's actually behind it:**
- **Astral (https://heyastral.ai):** a closed, paid AI trading workspace. Per its own site, you describe a strategy in plain language and it writes the code, backtests it (equity, drawdown, Sharpe, trade list), sets alerts and connects to supported brokers. Pricing is $9 for the first month, then $30/month. There is no free trial or free tier. The operator is not named beyond "© 2026 Astral". Code export is not mentioned; the code is "visible" inside the app.
- **SSRN (https://papers.ssrn.com):** Elsevier's free preprint server for social-science and finance papers. It is a legitimate and very useful source of strategy ideas. Most papers are academic studies, not ready-made "strategies from firms".
- **The paper shown:** SSRN abstract 2265977, "Informed Trading During the Intraday: The Case of Short Sellers" (Blau, Brough et al., read from the on-screen paste). It studies whether intraday *short-sale volume* predicts returns. That requires short-sale transaction data (Reg SHO / exchange short-volume files), not plain OHLCV. SSRN returned 403 to my fetch and a web search did not find this exact title, so the details come only from what is legible on screen.

**Verification:** Viewed all 4 contact sheets and individual frames 17 and 22 to read the paste, the URL bar and the NVDA result card. Fetched heyastral.ai (product description, pricing, FAQ). Web-searched the paper title, which surfaced related Blau/Brough short-selling papers but not this exact one. I could not test Astral (subscription required).

**Claims vs reality:**
- "Easiest way to build your first trading bot (5 min)": what is shown is pasting a PDF into a chatbot. No bot is built or run on screen.
- "Sometimes your results will be like this": **misleading.** The "result" is not a backtest of the pasted paper. It is a chat answer highlighting NVDA's buy-and-hold move from $48.17 to $73.90 (+53.42%, Jan 2 – Feb 14, 2024; split-adjusted prices, which are roughly correct). It is a cherry-picked historical price rally with hindsight, not strategy performance. The browser URL also changes between the paste screen (session ID beginning `cea771…`) and the result screen (`session-30c5e79d…`), so the result comes from a different chat session than the paper that was pasted.
- "SSRN is where firms publish their strategies": partly true. Some practitioner papers exist, but most are academic. Many reported anomalies decay after publication, or need data you don't have (as with this short-sale paper).
- Missing: out-of-sample testing, transaction costs, data requirements, and overfitting risk from trying many papers until one "looks like a gold mine". That last practice is classic data-snooping.

**Agenda:** Engagement-farming ("follow @larprichie for more") and an apparent promotion of Astral. No affiliate link or sponsorship disclosure is visible in the caption.

**Lab use:**
- Replicate the workflow for free with Claude Code on the lab server:
  - Download the SSRN PDF.
  - Have Claude extract the exact signal definition, universe, holding period and data needs.
  - Implement it in Python (`pandas`, plus `vectorbt` or `backtesting.py`, or `zipline-reloaded` / `qlib` for cross-sectional factors).
  - Run it on in-sample and out-of-sample periods with costs.
- Data: free daily data from yfinance/Stooq. Free short-volume data: FINRA daily short sale volume files (Reg SHO) are published free and are what a short-seller paper like this would need at the daily level. Intraday short data is paid.
- Effort: from a few hours (simple daily anomaly) to several days (intraday microstructure paper). No GPU. Paid APIs only if the paper needs intraday or options data.
- Guard against snooping: keep a log of every paper tried, use walk-forward splits, and apply a multiple-testing haircut (e.g. deflated Sharpe ratio).
- Open-source alternative to Astral: Claude Code + Jupyter + vectorbt/backtesting.py. Or the open-source LEAN engine (QuantConnect) run locally.

**Second-brain relevance:** NONE – Closed SaaS. "Paste a paper into a chatbot" is ingestion with no persistence. The free equivalent (paper PDF, then Claude Code, then notes in the lab repo) belongs in the brain's ingest workflow, but nothing in this post provides it.

---

## DekhFIbgQTO | "9 EMA + VWAP cross" intraday options strategy, used as a funnel into the paid FiFi's TQE / Alertsify ecosystem
- **Link:** https://www.instagram.com/p/DekhFIbgQTO/
- **Account:** @tqe_fifi_trades · **Type:** video (50s)
- **Category:** REBUILDABLE IDEA
- **Lab value:** LOW – the rules are simple enough to code and backtest in an hour, but nothing about them is new. The headline profits are unverifiable marketing P&L cards, and the "free indicator" is a Whop checkout lead magnet.

**What it says:** He opens with "This one strategy is how I can average about 45K a month in profits", over Alertsify-branded monthly P&L calendars, and the overlay "If you aren't using this strategy, you must hate money". The rules on screen: "3m timeframe", "Enter when candle closes through VWAP", "Exit when candles closes through EMA". The example chart is labelled **TSLA – 3m** (watermark "FiFi Trades"). After a red candle closes below VWAP, he waits for a retest on the next candle and buys puts. He says the TP hit "to the penny here at 380", then he exits when a candle closes back above the EMA (a red dot marks the VWAP cross and a pink triangle marks the exit). The video ends with a three-step funnel: "1. You HAVE TO follow me 1st, 2. Comment 'EMA', 3. Check DMs". The overlay adds "If you can't follow those instructions, you aren't getting it."

**What's actually behind it:**
- **The strategy:** the on-screen guide is titled "FiFi's Trade Qualification Engine (TQE). Free strategy guide: THE 9 EMA + VWAP STRATEGY. Two lines, two jobs, one exit rule…". The transcript's "90 EMA" is a mis-hearing of **9 EMA**, and the guide's chart legend reads "9 EMA / VWAP".
  - Entry: a 3-minute candle closes through session VWAP. Optionally wait for a retest on the next bar, then trade in that direction (puts for shorts, calls for longs).
  - Exit: the first 3-minute candle that closes back through the 9 EMA, or a fixed TP.
  - Not specified: the TP rule ("380" is a discretionary level, and the chart has no price axis), the stop-loss, options strike/expiry selection, position size, time-of-day filters, and what "three ways to trade it, and when to skip it" means (that part is gated behind the DM).
- **"Free indicator":** the guide's button reads "GET THE FREE INDICATOR – TQE 9EMA / VWAP Cross draws both lines, marks every cross, and prints the exit for you", linking to `whop.com/checkout/plan_BWYbkMedi4eJ5…` (partly legible). Whop is a paid-community / digital-product marketplace. A web search shows the same seller ("fifi-trades") listing a "TQE Suite + Private Discord" at about **$119.99/month** with a 7-day trial, a "TQE Lite" intraday indicator, and a free-indicators tier. The indicator itself is closed TradingView code.
- **Alertsify:** the P&L cards carry the Alertsify logo and the footer "Every trade auto-executed. Every result on-chain verifiable. Follow. Automate. Repeat." Per its July 2026 press release, Alertsify is a copy-trading service that grew out of Discord alerts and auto-executes a lead trader's orders in followers' broker accounts. Its user and volume figures are self-reported. The cards are promotional material for copy-trading this trader.

**Verification:** Viewed all 7 contact sheets. Cropped the P&L calendars, the chart label (TSLA – 3m), the guide's title, and the Whop checkout link. Web-searched FiFi Trades / TQE (Whop listings) and Alertsify (press release). I could not open the Whop checkout or Alertsify pages to verify the actual trade records, and the "on-chain verifiable" claim could not be checked.

**Claims vs reality:**
- "Average about 45K a month": the cards show June +$76,862.01, July +$40,381.73, August +$35,268.96 and September +$47,087.65, about $50K/month on average. These are screenshots of a branded marketing card from the copy-trading platform he promotes. Account size, capital at risk and drawdowns are not shown, and the cards prove nothing about *this* strategy specifically.
- The cards undercut the "one strategy" story:
  - Win/loss days are roughly June 15/7, July 14/11, August 12/11 and September 13/10. That is close to coin-flip at the day level.
  - The best day in July (+$55.6K) is larger than the whole July total (+$40.4K). The best day in August (+$53.6K) is larger than the whole August total (+$35.3K). The rest of each month was therefore net *negative*: about -$15K in July and about -$18K in August.
  - The P&L is concentrated in a few outlier days of high-leverage options trading, not a smooth edge. Trade counts are 203, 244, 215 and 173 a month, so this is active short-dated options trading.
- "Hit our TP to the penny at 380": a single cherry-picked TSLA example with no price axis visible. One example is not evidence.
- "Free indicator": free to start, but it is delivered through a Whop checkout and DM funnel into a $119.99/month suite.
- Missing from the claims: options spread and slippage, a stop-loss rule, and any multi-month backtest of the rule set itself.
- The 9 EMA / VWAP cross is a decades-old retail intraday setup. On 3-minute bars, crosses through VWAP whipsaw heavily in ranging sessions.

**Agenda:**
- Lead generation: follow + comment "EMA" + DM, which games engagement.
- A Whop checkout for a closed indicator, upselling into the $119.99/month TQE suite and private Discord.
- Promotion of Alertsify copy-trading, where followers mirror his trades.

**Lab use:**
- Easy to rebuild and test honestly. Pull 1–3-minute bars (e.g. Polygon/Alpaca/IBKR, or the free yfinance 1m for the last 7–30 days). Compute session-anchored VWAP and EMA(9) in pandas. Then define:
  - Entry: a bar closes on the other side of VWAP from the prior bar.
  - Optional filter: the next bar retests VWAP.
  - Exit: the first close back across the EMA(9).
- Backtest on the underlying (TSLA, SPY, QQQ) with `vectorbt` or `backtesting.py`. Then stress-test it with realistic costs, avoiding the 9:30–9:45 open, and with/without the retest filter.
- Modelling the options P&L needs historical intraday options quotes, which are paid data (e.g. Polygon options, ThetaData).
- Effort: 1–2 hours for an underlying-only backtest. No GPU or paid API is needed for the equity version.
- Open-source alternative to the paid indicator: about 20 lines of Pine Script or pandas. TradingView's built-in VWAP + EMA already draw both lines.
- Expect a near-random edge after costs. It is worth running only as a sanity-check exercise.

**Second-brain relevance:** NONE – An indicator funnel. No memory or knowledge component.

---

## DemxOm_AS9a | "Midday sell" EURUSD H1 pattern from vagafx's "Algory" bot, framed with a Renaissance/Laufer day-of-week story
- **Link:** https://www.instagram.com/p/DemxOm_AS9a/
- **Account:** @vagafx · **Type:** image (1 frame; the post metadata says "videos", but only the cover JPG was in the material, so any further frames of a reel were not available)
- **Category:** REBUILDABLE IDEA
- **Lab value:** LOW – the rule is mostly recoverable and cheap to test, but the shown evidence (40 of 71 hits) is statistically indistinguishable from a coin flip.

**What it says:** Caption: "Jim Simons' fund made money from what day of the week it was. Comment ALGO and I'll send you the details of the pattern my bot found." It then retells Henry Laufer's observation that Monday often moved like Friday ("Buy late on a rising Friday, ..."; truncated). The image is titled "before its stop 56" (meaning 56% hit target before stop). "THE MIDDAY SELL · 12:00 · EURUSD". "LAST 12 MONTHS: 71 TIMES, 40 HIT TARGET FIRST". Chart labels: "2-DAY LOW", "YESTERDAY'S CLOSE", "2+ ATR ABOVE THE LOW", "SELL" at "TODAY 12:00", "STOP" box above and "TARGET" box below the entry. Footer: "THE RULE, ILLUSTRATED · EURUSD H1 · 12:00 SERVER TIME"; "COUNTS: ALGORY PATTERN SEARCH, OCT 2025 TO OCT 2026, NEVER TRAINED ON".

**Recovered rule (from the illustration; exact parameters withheld behind the "ALGO" DM):**
- Instrument and timeframe: EURUSD, 1-hour bars.
- Trigger time: the 12:00 bar in broker "server time" (timezone not stated; usually GMT+2/+3 for MT4/5 brokers).
- Condition: at 12:00 today, price is at least 2 ATR above the lowest low of the last 2 days. In the drawing, price is also above yesterday's close after a rally. ATR length is not given.
- Action: sell short at 12:00.
- Exit: the target appears just below yesterday's close and the stop sits above the recent high. Exact distances are not given, but the box drawing suggests roughly 1:1.
- The caption's separate Laufer idea (buy late Friday if rising, sell early Monday) is a different rule and is not what the chart shows.

**What's actually behind it:**
- "Algory" (the account's own bot or brand): no public product, website or repo found. algory.ai is an unrelated Webflow web-design agency. A GitHub org "AlgoryProject" is an unrelated crypto tool. Closed, unverifiable.
- The Laufer and Renaissance anecdote: real. It comes from Gregory Zuckerman, *The Man Who Solved the Market* (2019). Reader notes confirm the passage: Laufer found day-of-week sequences such as Monday following Friday, and Medallion would buy late Friday in an uptrend and sell early Monday. That was a 1980s–90s commodities and futures finding, long since arbitraged away, and it has no connection to this EURUSD midday-short rule.

**Verification:** Viewed the image in full and cropped the footer text. Web searches for vagafx, Algory and the Laufer passage. I could not verify the bot, the 71/40 count, the ATR parameter, the server timezone or the exact stop and target.

**Claims vs reality:**
- "56% hit target before stop" on 71 trades: the standard error is about 5.9 pp, so 56% is about 1 SE from 50%, which is not significant. With a 1:1 reward-to-risk, a 56% hit rate minus EURUSD spread and commission (about 0.6–1.2 pips round trip at retail) may be near breakeven, depending on target size.
- "Never trained on" a 12-month holdout: if this pattern is one of the "19 that held up" out of millions of tests (see sister post DekL5L-gzAy), then the holdout was used for selection and is no longer out-of-sample. That is classic multiple-testing and data-snooping bias.
- "Jim Simons' fund made money from the day of the week": a loose borrowing of credibility. The illustrated rule is a time-of-day mean reversion, not a day-of-week effect.

**Agenda:** "Comment ALGO" DM funnel to a guide, which almost certainly leads to a paid bot, course or signal group. Borrows Renaissance credibility. Glossy infographic, no equity curve, no costs.

**Lab use:**
- Testable in an afternoon. Free EURUSD 1-minute data from Dukascopy (dukascopy-node, MIT) or HistData (FX-1-Minute-Data, Apache-2.0), resampled to H1 in UTC. Define server time explicitly (try GMT+2/+3 with DST, and UTC, to check sensitivity).
- Grid: ATR length (14 or 24), ATR multiple (1.5–3), target (yesterday's close vs fixed R) and stop (recent high vs k·ATR). Use at least 10 years (2010–2026), with walk-forward (e.g. 3-year train, 1-year test, rolling) and spread of at least 0.8 pip plus commission. Report per-year hit rate and expectancy in R, and a binomial or bootstrap p-value. Count every variant tried and apply a deflated Sharpe or Bonferroni-style haircut.
- Tools: pandas plus vectorbt or backtesting.py. No GPU, no paid APIs.
- Effort: about 0.5–1 day.
- Expectation: intraday mean reversion in EURUSD exists weakly in the literature, but a single 71-trade sample at 56% is noise until shown across a decade.

**Second-brain relevance:** NONE – A closed EURUSD pattern claim. No memory component.

---

## DejYce1ADfB | Dr David Paul names the Gartley 222 (H.M. Gartley, 1935) as his single favourite entry pattern
- **Link:** https://www.instagram.com/p/DejYce1ADfB/
- **Account:** @marketscoach · **Type:** video (33s)
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** LOW – a historically real chart pattern from a classic book, presented without testable rules. It can be coded as a swing-pattern detector, but the clip offers no evidence of an edge.

**What it says:** An interviewer asks, "What are your favorite entry and exit methods?" Dr David Paul (labelled "DR DAVID PAUL") answers that if he had to pick one methodology it would be H.M. Gartley's. He says Gartley "wrote a book in 1930 called Profits in the Stock Market. It's an absolute gem". He adds that on page 222 there's a pattern called the Gartley 222, "very, very similar to Richard Wyckoff's upthrust", and that it is "a thrust up the page and then a three-wave pullback. That's my favorite entry tool."

The clip includes an animated checklist card, "MY ONE ENTRY · GARTLEY 222":
- Page: 222 · Figure 27
- Pattern: Gartley 222
- Step 1: A thrust up the page
- Step 2: A three-wave pullback
- Stop: Above B
- Entry: Sell short

It also shows a side-by-side "WYCKOFF · UP THRUST" diagram (a break above the range that fails) against a "GARTLEY 222" diagram (A→B thrust, C pullback, "PLACE STOPS" just above B). The video ends on an end card reading "TRADING PSYCHOLOGY BY GUY LEVY".

**What's actually behind it:**
- **Book:** H.M. Gartley, *Profits in the Stock Market* (1935, not 1930 as spoken; the caption correctly says 1935). The "222" pattern takes its name from the illustration on page 222. The label "Gartley 222" was popularised later by Larry Pesavento (*Trade What You See*, with Leslie Jouflas). The modern "Gartley" harmonic pattern, an XABCD with Fibonacci ratio rules (B at about 0.618 of XA, D at about 0.786), is a later reinterpretation by Pesavento and Scott Carney, not Gartley's original text. The book is still in print as a reprint and is not free.
- **Dr David Paul:** a long-time trading educator and mentor. A podcast bio describes him as trading since the early 1980s and representing VectorVest (a paid stock-rating service) in the UK.
- **@marketscoach:** the end card and branding point to trading-psychology coach Guy Levy, who has a newsletter and coaching business. The account repurposes interview clips of other traders. A web search found a coaching directory listing but no official page tying the handle to him, so this link is not fully confirmed.

**Verification:** Viewed all 5 contact sheets and read every overlay card. Web-searched Dr David Paul, the Gartley 222 history, and @marketscoach / Guy Levy. I did not access the 1935 book to confirm Figure 27 on page 222, or to confirm whether Gartley's original example is the bearish (sell-short) variant shown on the card. Gartley's description is commonly quoted as a buy setup after a decline and a partial rally/retracement, with a mirror-image short version.

**Claims vs reality:**
- "Book from 1930": **wrong year.** It was published in 1935, and the post's own caption says 1935.
- "Very similar to Wyckoff's upthrust": **loosely true.** Both are failure-of-thrust ideas, but Wyckoff's upthrust is a false break *above a trading range*. The overlay's own diagrams differ: one is a range break, the other a trend leg plus pullback.
- "Thrust up, three-wave pullback, sell short, stop above B": the card's version is internally odd. A three-wave (A-B-C) pullback after an up-thrust is classically read as a *continuation* (buy) setup. Selling short after the pullback is a reversal bet that only works if C fails to make a higher high. The clip gives no rule for how far C should retrace, when to enter, or where the target is.
- No performance evidence of any kind is offered. It is an expert's preference, not a tested edge.

**Agenda:** Clip-farming for a trading-psychology coaching brand (Guy Levy end card). The caption is a teaser ("Most traders keep collecting entry methods…"). There is no explicit DM funnel in the visible caption, which is truncated.

**Lab use:**
- Testable with open-source tooling if you pin the rules down:
  - Detect swing pivots with a ZigZag (percentage or ATR threshold).
  - Define a thrust A→B (e.g. ≥ N×ATR), then a three-leg corrective pullback B→C retracing 38–79% of AB.
  - Enter on the break of C's minor swing (long for continuation, or short if testing the card's reversal version). Stop beyond B or C, target AB=CD or a prior swing.
  - Backtest across many symbols with `vectorbt` or `backtesting.py`, and compare against random-entry baselines with the same stop/target.
- Data: free daily bars (yfinance/Stooq) are enough.
- Effort: about half a day to build the pivot detector and pattern rules. No GPU or paid API.
- Reference material: Pesavento and Jouflas, *Trade What You See*. Open-source harmonic-pattern detectors exist on GitHub, but none were verified here, so write your own detector to control the rules.

**Second-brain relevance:** NONE – A chart-pattern clip. No memory or knowledge component.

---

## Dd2f6r5BfAy | "I have ADHD" Claude skill: almost certainly the MIT-licensed ayghri/i-have-adhd output-style skill (video not retrievable, identified from the cover)
- **Link:** https://www.instagram.com/p/Dd2f6r5BfAy/
- **Account:** @creativelyange · **Type:** video (length unknown – only the cover image could be downloaded)
- **Category:** OPEN SOURCE – READY
- **Lab value:** LOW – a free, harmless output-style skill that makes Claude lead with the next action. It is a personal-preference tweak, not a quant tool.

**What it says:** The cover reads "CLAUDE SKILL / I have ADHD / STRAIGHT TO THE POINT" with the caption "made a skill". The creator holds a crocheted fox. Caption: "if you have adhd you need this skill. #adhd #adhdclaude #adhdskill #techforgood". The video itself (and so any spoken content, repo URL or demo) could not be retrieved: the mirror only serves the 132 KB JPEG thumbnail, and ddinstagram is blocked by the proxy.

**What's actually behind it (inferred, not confirmed from the video):**
- https://github.com/ayghri/i-have-adhd, **MIT** (© 2026 Ayoub Ghriss). Exists and is active: first commit 2026-07-21, last 2026-10-11. Press reports put it at about 30k stars; I could not check the star count myself.
- `skills/i-have-adhd/SKILL.md` (about 7 KB) is invoked with `/i-have-adhd` and stays on until "stop adhd mode". Its rules: lead with the next action, number steps, restate state, suppress tangents, give concrete time estimates, make wins visible.
- It ships as a Claude Code plugin (`.claude-plugin/plugin.json` and marketplace.json) with an **opt-in** SessionStart hook. The hook injects SKILL.md only if `~/.claude/.i-have-adhd-always` exists.
- It also targets Cursor, Gemini, Qwen and Kimi.
- A different project also called "ADHD" (a tree-of-thought tool built on the Claude Agent SDK) exists. The cover's "straight to the point" matches ayghri's.
- The caption phrase "made a skill" could mean the creator made her own skill rather than promoting this one. I cannot rule that out.

**Verification:** Read the cover image and info.json. Video download attempts via uuinstagram/kkinstagram returned only the JPEG. Ran a web search, then shallow-cloned ayghri/i-have-adhd and read LICENSE, SKILL.md (start), hooks.json and always-on.sh (benign: reads one flag file and prints the skill text). Ran nothing.

**Claims vs reality:**
- "If you have ADHD you need this skill": it is a prompt-style formatting preference, not a treatment or accommodation tool. It is useful if you like terse, action-first answers.
- "Made a skill": unverified whether she authored it or is showcasing the popular repo.

**Agenda:** Personal and creator engagement. No visible funnel in the cover or caption.

**Lab use:**
- Install: `claude plugin marketplace add ayghri/i-have-adhd` then `claude plugin install i-have-adhd@i-have-adhd` (per the README/INSTALL.md), or copy `skills/i-have-adhd/` into `~/.claude/skills/`.
- No dependencies (Node is optional for the hook). Takes 5 minutes.
- Alternative: write a short "answer-first" style section into your CLAUDE.md.

**Second-brain relevance:** NONE – An output-style skill. Its only tangential relevance is the mechanism: an opt-in SessionStart hook that injects a text file into context. A second brain would use the same mechanism to inject memory into Claude Code.

---

## DeRM7RVjZLw | AgriciDaniel/compass: a free Obsidian "Life OS" vault template (journaling, habits, planning, AI helper)
- **Link:** https://www.instagram.com/p/DeRM7RVjZLw/
- **Account:** @gittrend.io · **Type:** video (27s)
- **Category:** OPEN SOURCE – READY
- **Lab value:** LOW – a real MIT-licensed Obsidian vault for personal productivity. It is not quant-related, though its agent and approval wiring (AGENTS.md, MCP via Local REST API) is a modest reference.

**What it says:** The voiceover says "Keep your journal, habits and plans in one free Obsidian folder. Compass turns Obsidian into your whole life system. Each night it asks a short set of questions and writes your answers into today's note", and that it tracks habits, runs quarterly retreats, and keeps tasks and writing boards in one place. "An AI helper works in your vault, but every edit needs your approval. Comment vault." On screen it scrolls through `github.com/AgriciDaniel/compass#readme`, read from a crop of the URL bar: "Life OS", status "development candidate", demo video, Mike Schmitz "Obsidian Replaced EVERYTHING" video, Quick start, "What is inside" folder tree, and "The seven workflows" table. The repo shows an MIT license tab.

**What's actually behind it:**
- https://github.com/AgriciDaniel/compass
  - License: MIT for the templates, dashboards, scripts, config and prompts. CC BY 4.0 for the `Guide/` prose. Bundled third-party plugins in `.obsidian/plugins/` keep their own licenses.
  - Status: exists. Shallow history runs 2026-08-26 to 2026-09-14 (latest: "add Compass video demo to README"). The README says "development candidate, not a newly accepted public release". The current release is 1.0.2 and 1.1.0 is pending. Requires Obsidian 1.13.1+. Star count was not visible on screen.
  - What it does: an Obsidian vault (the repo root *is* the vault) with Daily/Weekly/Quarterly notes, nightly 1–10 question prompts, a habit canvas, quarterly retreat notes, Kanban writing boards, Tasks, a DataviewJS dashboard, 16 AI prompts, and a "Life OS" first-party plugin. AI integration goes through the Agent Client plugin and the Obsidian Local REST API (MCP at 127.0.0.1:27123) with a read-only MCP tool allowlist for Claude.
  - It is an independent re-implementation of the system in Mike Schmitz's (Practical PKM) video, and the README says it is not affiliated with him.

**Verification:** Cropped the URL bar to confirm the owner `AgriciDaniel`. Ran `git ls-remote`, made a shallow clone, read the LICENSE (MIT), LICENSE-GUIDE.md (CC BY 4.0 for the Guide), README, `.mcp.example.json` and git log, and listed the bundled plugins (agent-client, dataview, life-os-app, obsidian-kanban, obsidian-local-rest-api, obsidian-tasks-plugin, omnisearch, periodic-notes, quickadd, seo, templater-obsidian). Not executed. I did not verify the "every edit needs your approval" mechanism beyond the README and the read-only MCP allowlist in `.claude/settings.json`.

**Claims vs reality:**
- "Free Obsidian folder for journal, habits, plans": **true** (MIT).
- "Each night it asks questions and writes answers into today's note": **true per the README** (Ctrl/Cmd+Shift+Q).
- "AI helper, but every edit needs your approval": **plausible.** It uses approval-aware prompts, a read-only MCP allowlist for Claude, and the Agent Client plugin. Desktop-only.
- Caveat the post omits: the Quick start tells you to turn off Obsidian Restricted Mode, which activates the 11 bundled community plugins (third-party JS binaries shipped inside the repo). Review them or install them fresh from the official plugin store.
- The status is a pre-release, which the post does not mention.

**Agenda:** gittrend.io is a repo-showcase account. It drives traffic to gittrend.io and uses a "Comment vault" DM funnel. Its voiceover matches the README accurately, which is better than @repopicks. Nothing is sold directly.

**Lab use:**
- Not a quant tool. As a research journal it could be adapted: a daily note template for trade/research logs, DataviewJS dashboards over notes, and an AGENTS.md pattern that lets Claude Code read the vault through the Local REST API MCP with a read-only allowlist.
- Install: clone, then open as a vault in Obsidian desktop. No Python, GPU or paid API. The AI helper uses whatever agent CLI you connect.
- Effort: about 30 minutes to try, plus time to strip the "life" content.
- Alternatives: the plain Obsidian Starter Vault, or a Markdown + git research journal driven by Claude Code.

**Second-brain relevance:** LOW – Covers personal/life logging (daily and weekly notes, nightly questions, habits) as an Obsidian vault schema. It exposes the vault to agents through the Obsidian Local REST API MCP on 127.0.0.1:27123, with a read-only allowlist for Claude. That MCP needs the Obsidian desktop app running and is loopback-only, so it cannot serve headless VMs or agents. The Markdown templates could be reused as the "life log" section of a server-side brain that a real indexer (GBrain, claude-obsidian) reads.

---

## Del5xpMtE-t | "20 Quant Trading Strategies": an icon-grid list of strategy family names, with no detail
- **Link:** https://www.instagram.com/p/Del5xpMtE-t/
- **Account:** @quantfinance.ai · **Type:** image
- **Category:** REFERENCE / RESEARCH MATERIAL
- **Lab value:** LOW – the taxonomy is accurate but offers only names (no rules, parameters, papers or code), so its use is as a checklist of topics.

**What it says:** The infographic is branded "quantfinance.ai – Quant Research" and lists 20 strategy families with icons: 1 Momentum, 2 Mean Reversion, 3 Statistical Arbitrage, 4 Pairs Trading, 5 Trend Following, 6 Market Making, 7 Event-Driven, 8 Factor Investing, 9 Carry Trade, 10 Volatility Arbitrage, 11 Options Strategies, 12 Order-Flow Signals, 13 Cross-Sectional Alpha, 14 Intraday Reversal, 15 Breakout Trading, 16 Risk Parity (Equity/Bonds/Real Estate/Commodities pie), 17 Portfolio Optimization, 18 Regime Switching (Bull/Bear), 19 Machine Learning Alpha, 20 Execution Algorithms. The caption (truncated) reads: "Quant trading isn't just about predicting where the market goes. It's about finding statistical edges, testing hypotheses, managing risk…"

**What's actually behind it:** No repo, paper or tool is named. All 20 are standard, legitimate categories, though some overlap: pairs trading is a subset of stat-arb, cross-sectional alpha overlaps factor investing and momentum, and risk parity and portfolio optimization are allocation methods rather than alpha strategies. Execution algorithms (TWAP/VWAP/IS) are not trading strategies at all. quantfinance.ai returned HTTP 503 when fetched, so I could not verify who runs it or what it sells.

**Verification:** Read the single image and the info.json caption. Tried quantfinance.ai (HTTP 503). There was nothing else to verify.

**Claims vs reality:**
- "Every quant should know": fair as a vocabulary list. It does not convey the actual statistical edges, costs or capacity limits involved.
- No performance claims are made, so there is nothing to debunk. Several items are realistically out of reach for a retail personal lab: market making, order-flow and execution algos need L2/L3 data and low latency, and vol arbitrage needs options-chain data.

**Agenda:** Generic, likely AI-generated infographic for follower and save farming. The site's business could not be checked.

**Lab use:**
- Use it as a roadmap. Retail-feasible on daily data with free sources: momentum/trend (time-series and cross-sectional), mean reversion and pairs/cointegration (statsmodels `coint`), factor investing (Fama-French data library), carry (FX/futures with free data is harder), risk parity and portfolio optimization (Riskfolio-Lib, PyPortfolioOpt), regime switching (statsmodels `MarkovRegression`, hmmlearn), and ML alpha (Qlib, scikit-learn with purged walk-forward CV).
- Good free references to pair with it: Kakushadze & Serur, "151 Trading Strategies" (2018; free SSRN preprint), and the Fama-French data library.
- No GPU or paid API is needed. Effort ranges from 1 day per simple strategy to weeks for an honest multi-strategy backtest with costs.

**Second-brain relevance:** NONE – A strategy-name infographic. Could serve as a topic taxonomy for research notes, nothing more.

---

## DeEtB78jJtu | Omarchy 4.0 "Quattro" (DHH's Arch/Hyprland distro with agent launchers) hyped as a world-changing "AI agent OS", wrapped in end-times talk and a consulting pitch
- **Link:** https://www.instagram.com/p/DeEtB78jJtu/
- **Account:** @kevinunk_ai · **Type:** video (180s)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – Omarchy is real, MIT-licensed and actively maintained, but it is a desktop distro for a laptop/workstation, not a headless quant server, and the post adds no information about it.

**What it says:** Filmed lying in bed, the creator says "Omarchy Quattro is a Linux distribution that literally just changed the world. This is not hype." He credits OpenClaw (an "agentic runtime" from January with "more GitHub stars than any other repo ever", praised on stage by Nvidia's CEO), then says Quattro, "released two weeks ago", is a distro "custom tailored for thousands of hours" so agents can "live inside your operating system" and change it "with no limitations", running "local AI unrestrained 24/7 swarms of agents" for research, content and leads. He then moves to millionaires buying "100,000 laptops", "puppet masters", "end times", Revelation 13, and ends with "comment AI" to book a Zoom call or have him build a system. On-screen text is only chapter titles ("Omarchy changed everything", "Open Claw explosion", "Agents live inside Linux", "Local AI swarms 24/7", "Wealth and power shift", "End times warning", "Learn it with me") and word-by-word captions. No screen recording, URL or demo is shown.

**What's actually behind it:**
- Omarchy: https://github.com/basecamp/omarchy (site omarchy.org), **MIT** (Copyright David Heinemeier Hansson). It exists and is very active: last commit 2026-10-18, `version` file `4.0.0.alpha` on main, commit messages refer to 4.0.5 and the "quattro" line. It is an "omakase" Arch Linux + Hyprland + Quickshell desktop setup. The README calls it "a beautiful, fun & agentic Linux distribution by DHH."
- "Quattro" is the real codename of Omarchy 4.0 (confirmed by linuxiac.com, itsfoss.com and the repo's commit history). There is no separate "AI Omarchy" or "AI Omarchy Quattro" variant; "AI Omarchy" is the creator's own label.
- What the "agentic" part actually is (manual/17-ai.md): launchers that lazily install coding-agent CLIs via mise (claude, codex, opencode, copilot, crush, grok, pi, hermes, cursor-agent and others), a default-agent hotkey, an agents panel showing subscription usage limits, multi-account switching, a crash watcher that hands core dumps to your agent, an "Omarchy skill" that lets an agent edit Hyprland/bar/theme configs (the manual calls it "experimental" and advises plan mode and rollback), plus optional OpenClaw/Hermes desktop apps and LM Studio/Ollama for local models.
- OpenClaw: https://github.com/openclaw/openclaw (git ls-remote confirms the repo exists). Third-party trackers (star-history.com and others) report it became the most-starred *software* project on GitHub (about 382k stars by July 2026), and Jensen Huang praised it publicly in March 2026.

**Verification:** `git ls-remote` and a shallow clone of basecamp/omarchy; read LICENSE, README, manual/01 and manual/17-ai.md, plans/server.md and git log. `git ls-remote` on openclaw/openclaw (not cloned; it is context, not the subject). Web searches on Omarchy 4 "Quattro" and on OpenClaw's star count and Huang quote. Did not run any code. I did not check OpenClaw's star count on GitHub itself.

**Claims vs reality:**
- "Just changed the world": no. It is a well-made personal desktop distro with agent CLI launchers and conveniences. Any Linux box can run the same agents.
- "Custom tailored for thousands of hours so agents can live inside your OS": exaggerated. The agent integration is launchers, a usage panel, a crash-diagnosis skill and one experimental config-editing skill. Agents run as normal user processes.
- "Adjust and change your operating system with no limitations": the launch shortcuts do start agents in auto-approve ("don't-stop-to-ask") modes, which is a risk, not a feature. The manual itself warns you may need `omarchy reinstall configs` if an agent "makes a mess."
- "Local AI unrestrained 24/7 swarms": nothing like that ships. Local models mean installing LM Studio or Ollama yourself, with whatever GPU you have.
- "Released two weeks ago": consistent with 4.0 "Quattro" being recent (4.0.x point releases in October 2026).
- OpenClaw "more stars than any repo ever": overstated. Trackers say most-starred *software* project, not the most-starred repo overall (aggregator/list repos rank higher).
- Wealth-concentration, "puppet masters", Revelation 13: opinion, not about the software.

**Agenda:** "Comment AI" funnel to book a Zoom call or pay him to "build a system for you." No link, product or demo is given.

**Lab use:**
- Not suited to a headless quant server. Omarchy is a Hyprland desktop (GUI stack, laptop hardware detection); an "Omarchy Server" headless edition exists only as a plan document (`plans/server.md`) in the repo.
- If you want it on a workstation: install from the ISO at omarchy.org (Arch-based; full-disk install). Free; agents need their own subscriptions or API keys.
- For the lab server itself, the equivalent is simpler: install Claude Code (or Codex/OpenCode) directly on your existing distro, and use Ollama or vLLM if you have a GPU for local models. Effort: under an hour.
- Do not copy the auto-approve agent launch pattern onto a machine holding broker keys or data you care about.

**Second-brain relevance:** NONE – A desktop distro with agent launchers. No memory, storage or sharing component, and not relevant to a server-side brain.

---

## DekL5L-gzAy | "8 million tests, 19 patterns held up": vagafx's closed "Algory" data-mining bot on EURUSD H1
- **Link:** https://www.instagram.com/p/DekL5L-gzAy/
- **Account:** @vagafx · **Type:** image (1 frame; the post metadata says "videos", but only the cover JPG was in the material)
- **Category:** HYPE / UNREAL
- **Lab value:** LOW – brute-force pattern mining is a real technique you can rebuild, but this post discloses no rules or stats, and its own numbers describe a textbook data-snooping setup.

**What it says:** Caption: "My bot ran 8 million tests on raw price data. 19 patterns held up. Comment ALGO and I'll send you the guide." It adds that "For two years, Algory has built trading strategies out of concepts people already trade: indicators, price action, my own ideas. This week w..." (truncated). The image reads: "019 HELD ON A YEAR OF DATA IT WAS NEVER TRAINED ON". Breakdown: "12 ENTRY SIGNALS", "6 FILTERS TO STAY OUT", "1 LONGER BIAS". "EURUSD · 1H · THE RULE, ILLUSTRATED". The sample chart shows a swing low after a down move, then "BUY" at "08:00" with a target box above. Footer: "SOURCE · ALGORY PATTERN SEARCH, 14 OCT 2026 · 8 MARKET FRAMES · LAST 12 MONTHS HELD BACK".

**Recovered rule:** Only one example is drawn: EURUSD H1, after a series of lower bars forms a swing low, buy at the 08:00 (server-time) bar, with the stop below and the target above. Swing-low definition, confirmation, stop and target are not given. The other 18 patterns are not disclosed. Not reproducible from the post.

**What's actually behind it:**
- "Algory": no public product, site or repo found (algory.ai is an unrelated web agency; GitHub "AlgoryProject" is an unrelated crypto tool). Closed and unverifiable.
- The method described (mass-generating rule combinations and keeping those that pass a holdout) is the same idea as commercial strategy generators (StrategyQuant X, EA Studio, Adaptrade Builder) and the open-source genetic-programming tools (DEAP, gplearn).

**Verification:** Viewed the image and cropped the footer. Web searches for vagafx and Algory found nothing. I could not verify the 8M figure, the 19 patterns, or any performance numbers; none are shown.

**Claims vs reality:**
- "8 million tests → 19 held up on a year it never trained on": at a 5% false-positive rate, 8 million independent tests would yield about 400,000 "passes" by luck. Even at very strict thresholds, surviving 19 out of 8M is fully consistent with chance unless the threshold is extreme and the tests are adjusted for multiplicity. Once the "held-back" year is used to pick the survivors, it becomes part of the selection, so the claim that the patterns were never trained on it is false in substance.
- "8 market frames": unclear; probably 8 symbol and timeframe combinations. Not explained.
- No hit rate, expectancy, cost model, trade count or equity curve for the 19 patterns: nothing is testable from the post.

**Agenda:** "Comment ALGO" DM funnel ("the guide"), very likely to a paid bot, course or signal service. A series of slick posts (see DemxOm_AS9a) builds the impression of a quant operation.

**Lab use:**
- Rebuildable idea, done properly: a pattern-mining harness in Python. Generate rules from a grammar (time-of-day × swing condition × ATR filter × trend filter), evaluate them vectorised in vectorbt or numpy on 10+ years of free Dukascopy or HistData EURUSD 1-minute data resampled to H1, include spread plus commission, and control false discoveries: Benjamini–Hochberg FDR across all tested rules, White's Reality Check or Hansen SPA (the open-source `arch` package has `SPA`), the deflated Sharpe ratio, and a truly untouched final holdout looked at once.
- Dependencies: pandas, numpy, vectorbt, arch. CPU is enough; numba helps. No paid APIs.
- Effort: 2–5 days for a sound harness. The harness itself (with honest multiple-testing correction) is the valuable artifact, not this account's patterns.
- Open-source alternatives to a paid generator: DEAP or gplearn (genetic programming), Optuna for parameter search, and mlfinlab-style purged k-fold CV (implement yourself; the mlfinlab licence is restrictive).

**Second-brain relevance:** NONE – A closed pattern-mining claim. No memory or knowledge component.

---

## DemHMk4AOWB | Supermedo/uncharted_pc: a PS4 Uncharted port for Windows, falsely narrated as an "AI memory layer"
- **Link:** https://www.instagram.com/p/DemHMk4AOWB/
- **Account:** @repopicks · **Type:** video (31s)
- **Category:** USELESS / REPACKAGED
- **Lab value:** NONE – the repo is a Windows game port, and the "AI persistent memory" narration is fabricated.

**What it says:** The voiceover says "SuperMeto just solved the biggest headache with AI context amnesia… Meet Uncharted PC… It stores persistent long-term memory, so your AI coding agents remember your entire workflow… 100% free and open source with over 1,000 stars. Comment REPO". The header tag on screen reads "AI Memory Layer" and "1.0K Stars". The page scrolled on screen is the real README: "Uncharted: The Nathan Drake Collection for Windows – Uncharted 1, 2 and 3 from the PS4 collection running natively on Windows 10 and 11", with Features (FSR/DLSS, 60/120 FPS), Requirements (Vulkan 1.3 GPU, 6 GB VRAM), Known problems, Building (MSYS2 CLANG64), Credits and License (GNU GPL v2 or later). The caption names `github.com/Supermedo/uncharted_pc` and says 969 stars.

**What's actually behind it:**
- https://github.com/Supermedo/uncharted_pc
  - License: GPL-2.0 (or later per the README). Third-party components keep their own licenses.
  - Status: exists and is very active (first commit in the shallow history 2026-10-07, latest 2026-10-18, v0.3.6). About 1.0K stars on screen and 969 in the caption.
  - What it does: a static-recompilation/compatibility port that runs the PS4 Uncharted collection's game code natively on Windows, with graphics translated to Vulkan. It builds on the author's Bloodborne port and on shadPS4 work. It requires your own decrypted PS4 game dump. No game files are included, and it is not affiliated with Sony or Naughty Dog.

**Verification:** Read all four contact sheets (the README is legible throughout). Ran `git ls-remote`, made a shallow clone, and read the LICENSE (GPL v2), README and git log. The structure (src, gpu, launcher, patches, third_party, build.sh, msys2-env.sh) confirms a game-port codebase. There is no AI, LLM or memory functionality anywhere in it. Not executed.

**Claims vs reality:**
- "Solves AI context amnesia / persistent long-term memory for AI coding agents": **completely false.** It is a video-game port.
- "Connects directly into your developer workflow": **false.**
- "Free and open source, 1,000 stars": roughly true (GPL-2.0, about 969–1.0K stars). Note that it requires a decrypted copy of a commercial game.

**Agenda:** An automated engagement farm. The voiceover script is generic and evidently AI-generated from the repo's name or tags, with no regard for the content. "Comment REPO" is a DM funnel, and the caption pushes a newsletter. This post is the clearest evidence that @repopicks does not check what it posts, so treat every claim from this account as unreliable.

**Lab use:**
- None for a quant lab. It is Windows-only gaming software and irrelevant here.
- If you actually wanted persistent memory for coding agents, OSS options include the Claude Code memory/CLAUDE.md conventions, `mem0ai/mem0` (Apache-2.0), `letta-ai/letta` (Apache-2.0), or a local vector store (Chroma, LanceDB) wired in through an MCP server.

**Second-brain relevance:** NONE – The "AI memory layer" is fabricated; the repo is a game port. Real self-hostable agent-memory projects exist. `git ls-remote` confirms these repos exist: mem0ai/mem0, letta-ai/letta, basicmachines-co/basic-memory. Their licences and features were not checked in this pass. The memory projects inspected in depth in this batch are GBrain (Dem60yJDELo), Hindsight (DeCKnW0DAGc) and claude-obsidian (Defw9ggACu1).

---

## DeY-l9KjXVd | Five chained "learn anything" prompts for Claude, shown in full, behind a "comment BRAIN" funnel
- **Link:** https://www.instagram.com/p/DeY-l9KjXVd/
- **Account:** @msbintel · **Type:** carousel (8 slides)
- **Category:** USELESS / REPACKAGED
- **Lab value:** LOW – sensible generic study prompts with nothing quant- or lab-specific. All five are fully visible, so commenting to "get" them adds nothing.

**What it says:** Slide 1 hook: "I installed a 'brain' in Claude… 5 prompts that make learning feel illegal". The five prompts, verbatim:
1. "I want to understand [topic]. Give me the 5 big ideas behind it, in the order I should learn them. Explain each one with an everyday comparison and one real example."
2. "Which of those 5 ideas do beginners get wrong most often? Break that one down step by step, then give me a short memory trick so it sticks."
3. "Now turn this into a 7-day plan, 20 minutes a day, using only free resources. If you're not sure a resource exists, say so. Don't guess."
4. "I usually quit learning plans by day 3 because [no time / I get bored / my phone]. Change the plan so it's easier for me to stick to."
5. "Quiz me on everything so far, one question at a time. Then go one level deeper on whatever I got wrong. If you mention a book or paper, tell me how sure you are it exists."

Slide 7 says "Your own tutor… Claude can still be wrong. Prompt 5 makes it say how sure it is." Slide 8 says "Comment 'BRAIN' and I'll send you all 5 prompts."

**What's actually behind it:** No tool, repo or "brain" install. It is plain prompting in one chat. MSB Intel is an AI-tips content account.

**Verification:** Read all 8 slides and the caption. There was nothing external to verify.

**Claims vs reality:**
- "Installed a brain in Claude": false framing; these are just five prompts.
- "Learning feel illegal": hype.
- The prompts themselves are reasonable: chunking, misconception focus, spaced plan, retrieval practice and calibration requests.
- Asking the model "how sure are you it exists" helps a little, but it does not prevent hallucinated citations. Verify any book or paper it names, for example with an OpenAlex or arXiv lookup.

**Agenda:** "Comment BRAIN" engagement and DM funnel to grow reach and the DM list, even though the content is already fully shown.

**Lab use:**
- Could become a Claude Code slash command, `.claude/commands/learn.md` with `$ARGUMENTS` as the topic, for ramping up on quant topics (e.g. "cointegration", "purged k-fold CV").
- Pair prompt 5 with real reference verification.
- Effort is 10 minutes, with no dependencies.

**Second-brain relevance:** NONE – The "brain" is five chat prompts. Nothing persists.

---

## Dea-ayyDW8t | Six generic "passive income" ChatGPT/Claude prompts dressed up as Warren Buffett's system
- **Link:** https://www.instagram.com/p/Dea-ayyDW8t/
- **Account:** @aified.studio · **Type:** carousel (8 slides)
- **Category:** USELESS / REPACKAGED
- **Lab value:** NONE – generic business-coaching prompts about digital products and marketing, with no link to investing, quant research or Buffett's actual methods.

**What it says:**
- Slide 1 shows a Buffett photo with the line "Claude can now build you the exact system Warren Buffett used to turn $10,000 into $130 billion. Here are the exact prompts."
- Slides 2–7 are six role-play prompts:
  1. Build your passive income operating system
  2. Find your perfect income stream
  3. Build something that sells while you sleep
  4. Automate the boring parts
  5. Get customers without chasing them
  6. Add more income streams in the right order
- Each prompt follows the pattern "Act as a world-class X… before you build anything, ask me [skills/budget/risk/time]… then cover [list]… give me the single first move."
- The topics are digital products, affiliate marketing, SaaS, courses, newsletters, SEO, email automation, referrals and reinvestment percentages.
- Slide 8: "Comment SYSTEM".

**What's actually behind it:** No tool, repo or product, just prompt text. Claude (claude.ai) is the only named product, used as a general chatbot.

**Verification:**
- Read all 8 slides in full.
- Nothing to clone or look up. The Buffett framing was checked against public knowledge: Buffett's fortune came from value investing and from running Berkshire Hathaway, an insurance float plus capital-allocation conglomerate. It did not come from "passive income streams", digital products or marketing funnels.
- His net worth has been in the roughly $100–150B range in recent years. The "$10,000 → $130B" figure is a loose meme number, not a documented fact.

**Claims vs reality:**
- "The exact system Warren Buffett used": false. None of the six prompts mentions investing, compounding in securities, margin of safety, moats or insurance float. The content is generic creator-economy advice.
- "Claude can now build your passive income system (for free)": any LLM will produce a generic plan from these prompts. The prompts are reasonable but ordinary ("separate what is proven from what is an assumption" is a decent instruction).
- The "$1K/$5K/$10K per month" scaling framing is aspirational, with no evidence.

**Agenda:** A clickbait celebrity hook to farm "SYSTEM" comments and DMs, very likely feeding a prompt pack, newsletter or course funnel. Engagement farming.

**Lab use:**
- None for quant work.
- If you want Buffett-style material for the lab, use primary sources instead: Berkshire Hathaway shareholder letters (berkshirehathaway.com/letters, free), and the academic factor replication of his returns, Frazzini, Kabiller & Pedersen, "Buffett's Alpha" (2018, Financial Analysts Journal), which attributes his returns largely to cheap, safe, quality stocks plus about 1.6x leverage from insurance float.
- These are rebuildable as a quality/value/low-beta factor backtest in Python using free data (Kenneth French library, AQR factor datasets).

**Second-brain relevance:** NONE – Generic prompts. No memory or knowledge component.

---

## DeRXBt_kxDh | Trading-psychology explainer on "akrasia" (appetite vs reason) as a funnel to the Knights of Gold "Camelot" community
- **Link:** https://www.instagram.com/p/DeRXBt_kxDh/
- **Account:** @knights_of_gold · **Type:** video (100s)
- **Category:** USELESS / REPACKAGED
- **Lab value:** NONE – generic pop-psychology about impulsive trading, with no tool, data or testable rule. Its only takeaway, rewarding process over P&L, is standard trading-journal advice.

**What it says:** A whiteboard-style hand drawing on lined paper, under a fixed caption: "Exposing the exact reason why your LIMBIC SYSTEM beats your logic every time in trading". It writes "AKRASIA → WHY / HOW", then "* When we know it's wrong why do we do it?" The diagram is:
- APPETITE (impulses, craves dopamine) → MIND ← REASON (planned action, logic) → DECISIONS
- Appetite is labelled FAST and reason SLOW.
- "IGNORE APPETITE" is crossed out and replaced with "NEW DIET ✓".
- "MONEY FOCUSED APPROACH" is contrasted with "SYSTEM FOCUSED APPROACH".

The voiceover: appetite comes from the limbic system and reason from the prefrontal cortex. Willpower can't suppress appetite, so give it "a new diet" by switching from a P&L focus to a system focus that "instantly rewards us for following our system and risk management". It ends with "I have other videos on my page that talk about this."

**What's actually behind it:**
- **Akrasia** (Greek "lack of self-command", acting against one's better judgment) is a real concept from Plato and Aristotle. The fast/slow framing echoes dual-process theory (Kahneman's System 1/System 2). The "limbic vs prefrontal" and "dopamine diet" framing is a pop-neuroscience simplification. The transcript spells it "Acracia".
- **Knights of Gold / KOG:** a gold- and forex-focused signals and education brand. Its public Telegram channel "Knights of Gold (Gold/FOREX Analysis/Trade ideas)" posts XAUUSD and forex levels ("KOG targets") and promotes an "Excalibur" indicator. The caption pushes the paid/private "Camelot" community, a "Comment TRAINING" DM funnel, a "Free Telegram in bio", and tradewithkog.com. I did not open tradewithkog.com, so pricing was not verified.

**Verification:** Viewed all 13 contact sheets, read the complete final diagram, and read the full transcript. Web-searched Knights of Gold / tradewithkog / Camelot, which surfaced only the public Telegram channel. The Camelot membership price and contents were not verified.

**Claims vs reality:**
- "Exposing the exact reason why your limbic system beats your logic every time": overstated. The limbic system / prefrontal cortex split is a simplification of decision neuroscience. Nothing here is "exact", and no research is cited.
- "Willpower can't ignore appetite, so give it a new diet (system-focused rewards)": reasonable, conventional behavioural advice (process goals, rule-adherence scoring). It is not new.
- The video promises "how" but defers it to other videos and the paid community.

**Agenda:** Funnel into Knights of Gold: comment "TRAINING" for a DM, free Telegram, the paid "Camelot" community, and tradewithkog.com. Gold/forex signal-group style.

**Lab use:**
- Nothing to install. The one actionable idea is a rule-adherence journal: log every trade or strategy deviation, and score process compliance (rule followed / not followed) separately from P&L. In a quant lab this maps to:
  - logging every manual override of a systematic strategy
  - comparing paper vs live fills
  - tracking discretionary interventions in a Postgres/SQLite table or Markdown journal
- Effort: under an hour, with no dependencies.
- Free reference instead: Kahneman, *Thinking, Fast and Slow*. Brett Steenbarger's trading-psychology blog (free) covers the same ground with more substance.

**Second-brain relevance:** NONE – Psychology content. The rule-adherence journal idea is trivial structured logging.
