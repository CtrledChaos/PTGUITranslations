# Batch 3, part 02 of 06: full entries

This part continues the full entries in category order. The summary table and cross-cutting findings are in part 00, and the complete single document is research/instagram-quant-lab-review/BATCH3-REPORT.md.

<a id="e-ddkexw5t68n"></a>

## DdKExW5t68N | @felixcallahan.ai | Talking-head reel on Tencent's open-source "TencentDB Agent Memory" (4-tier agent memory; −61% tokens, PersonaMem 48%→76%), shown over its GitHub README
- **Link:** https://www.instagram.com/p/DdKExW5t68N/
- **Account:** @felixcallahan.ai (Felix Callahan) · **Posted:** 2026-09-11 · **Type:** reel (63s, 159 scene frames; mostly a scrolling README plus B-roll, with burned-in word-by-word subtitles)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; identical to the mirror text plus hashtags)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE – the repo is real, MIT-licensed, by Tencent and active, but "fully local" is overstated (it needs an LLM API endpoint) and the headline numbers are the project's own, measured with OpenClaw

### Post description
> Tencent open-sourced Tencent DB Agent Memory, a local memory system that enables AI agents to recall long-term user preferences and habits like a human brain. This four-tier system reduces token costs by 61% and boosts task success by over 50%, making AI interactions more efficient and personalized. #Tencent #AgentMemory #AItechnology #AImemory #OpenSourceAI

### Audio
Creator voice-over (English):
- [0.0–7.6] "Tencent just open sourced a fully local memory system that gives any AI agent human-like long-term recall."
- [7.6–13.5] "It's called Tencent DB agent memory, and it fixes a huge problem in agentic use right now."
- [13.5–23.9] "Every agent you use starts from absolute scratch. Every time you close it and open a new one, it has no idea who you are, what you prefer, or what you were working on last week."
- [23.9–36.9] "So Tencent built a four-tier memory system that changes this completely. Think of how your own brain works. Short-term memory handles what's happening right now, and long-term memory stores your habits, preferences, and personality over time."
- [36.9–49.6] "Their system works the same way. It watches your conversations, pulls out key facts like this user prefers Python, or always wants concise responses, and stores them in layers that get smarter the longer you use the agent."
- [49.6–60.5] "It cuts token costs by 61%, and improves task success by over 50%, because the agent isn't burning context window space or rereading the same background every session."
- [60.5–63.2] "And it's fully open source and runs local."

### On-screen content, page by page
The layout is a split screen with B-roll or a screen recording on top and the presenter below. The headline overlay "Tencent Changed AI Memory Forever" runs from 0 to about 7.5s. Word-by-word subtitles repeat the audio and are not repeated here.
**Page 1 (0.0–1.4s):** GitHub README header: logo, tagline "Agents remember. Humans innovate.", badge "GITHUB TRENDING – #1 Repository Of The Day", shields "npm v1.0.1", "License MIT", "node >=22.16", "OpenClaw >=2026.3.13", "Hermes Gateway".
**Pages 2–37 (1.4–5.5s, fast README scroll):** "Discord Join"; nav links "Installation · What is it? · Team Play · Technical Implementation · Benchmark"; "English · 简体中文"; "Latest: Team Memory Beta is evolving quickly — install it and start exploring in …". Install block: "Start all three services in one go (memory-core + memory-hub + proxy):" then `git clone https://github.com/Ten[centCloud/TencentDB-Agent-Memory]`, `cd TencentDB-Agent-Memory/deploy`, `cp .env.example .env`, `$EDITOR .env  # Fill in two …`, `./start-all.sh  # Launch ever[ything …]`. "Open the panel: http://localhost:8125". "Complete installation documentation (standalone Memory Hub deployment, Proxy + Claude Code usage, stop and cleanup, port reference, etc.) is available in INSTALL.md (中文: INSTALL_CN.md)". "Migrating data from an older version: If you're already on an older release (v1.x / v0.x) and want to bring your existing data over to v2.0.0+, we provide a migration tool: See Data Migration Tool (v2 → v3) for full usage and flags. New installations can skip this." Section "What is TencentDB Agent Memory?": "We started from a practical question: How do you reduce repetitive work when using Agents?" followed by the README paragraph about not re-explaining context, and "Memory here means more than just 'remembering conversations.' Any information that helps the next Agent avoid reinventing the wheel should be saved, organized, and reused." with the code line "Existing information → Reusable".
**Pages 38–51 (5.5–16.6s):** Animated B-roll: a cartoon figure, a logo animation ("IT'S CALLED 10[CENT]"), and a chat app UI with tabs "Agent / Style" and "New Chat".
**Page 63 (16.9–17.6s):** n8n-style workflow canvas: "When chat message received" → "Get Memories" → "Aggregate" → "Merge".
**Page 64 (17.6–18.1s):** A Claude Code v2.1.92 terminal showing "Welcome back farza!", "Opus 4.6 with high effort · Claude Pro", "farza@buildspace.so's Organization", path "~/Developer/farza-wiki/wiki_v3", and the query "/wiki-query whats my biggest inspiration?". This is a screen recording from a different creator (Farza), reused as B-roll.
**Page 65 (18.1–18.8s):** Claude chat start screen "Good afternoon, team vm", model "Sonnet 4.6".
**Pages 72–82 (19.1–24.9s):** Mock "AI support agent" chat: "Hi! How can i help you today?" / "Hey, I'm facing a serious b[ug] now. Every time I export the rep[ort] … 'Something went wro[ng]'" / "Looks like I have to start …".
**Page 85 (24.9–28.0s):** Stock clip of a man typing quickly at a keyboard (film-style footage) with the subtitle "FOUR TIER MEMORY".
**Pages 95–106 (28.7–36.7s):** Product UI: Memory Hub panels "Skills", a pyramid diagram, "Long-Term Memory … Habits". README excerpt: "…recall must be hierarchical. TencentDB Agent Memory [uses] layering as its unified architectural paradigm: Short-term context layering. The bottom layer archives tool outputs (refs/*.md); the middle layer extracts step-level summaries (jsonl); the top layer condenses state into a lightweight Mermaid canvas. The Agent only needs to attend to the top-layer structure in context, and drills down to the lower layers via node_id when an error occurs. Long-term personalization layering. In place of flat logs, build a semantic pyramid: L0 Conversation (raw dialogue) → L1 Atom (atomic facts) → L2 Scenario (scene blocks) → L3 Persona (user profile). … Skill generation layering. … The middle layer derives common solution patterns (Scenario) from bottom-layer execution traces (Conversation), and the top layer distills reusable Skills …". A demo chat "Q2 Risk Assessment Report.pdf … Now summarize only the risks".
**Pages 115–119 (37.1–44.3s):** Memory Hub "Team Assets" (pr-review-checklist "PR review checklist v1", changelog-writer "Compile git commit…"), a glowing graph of nodes (conversation, CHANGELOG.md, .gitignore, config.json), a chat answer about fzf / ripgrep, and a "L0 Raw Log" card.
**Page 123 (44.5–47.2s):** Screenshot of an X post by "How To Prompt (@HowToPrompt_)", summarised: "China has killed the entire vector database industry." It says Tencent open-sourced TencentDB Agent Memory and that it gives any AI agent long-term memory that "runs 100% locally". It then lists: "No Pinecone. No cloud APIs. No repeating yourself every session. – 61% fewer tokens – PersonaMem accuracy: 48% → 76% – Zero external API dependencies – Runs on plain SQLite". It adds that most memory systems compress history into an opaque vector pile, while this one "builds a semantic pyramid".
**Pages 124–127 (47.2–51.7s):** GitHub repo page "TencentCloud / TencentDB-Agent-Memory (Public)": Issues 39, Pull requests 57, branch main, last commit by "Yuntong8888 2 days ago". Folders: .github, assets/images, bin, docker/opensource, hermes-plugin/memory/memory_tencentdb, scripts, src, .gitignore.
**Pages 133–147 (52.3–55.3s):** README "Highlights": "TencentDB Agent Memory = symbolic short-term memory + layered long-term memory … cutting token usage and improving task success." Then: "When integrated with OpenClaw, it cuts token usage by up to 61.38%, improves pass rate by 51.52% (relative), and raises PersonaMem accuracy from 48% to 76%." Benchmark table:

| Memory Capability | Benchmark | OpenClaw Success | With Plugin | Relative Δ |
|---|---|---|---|---|
| Short-term | WideSearch | 33% | 50% | +51.52% |
| Short-term | SWE-bench | 58.4% | 64.2% | +9.93% |
| Short-term | AA-LCR | 44.0% | 47.5% | +7.95% |
| Long-term | PersonaMem | 48% | 76% | +59% |

Footnote: "These results are measured over continuous long-horizon sessions, not isolated turns. For example, SWE-bench runs 50 consecutive tasks per session to simulate the context-accumulation pressure of real-world long-horizon agents."
**Page 148 (55.3–60.3s):** Presenter with a bright overlay. A Memory Hub "Task Board" UI with the sidebar Workbench, Organization & P…, Team Members, Agent Management, API Key, Resource Manag…, Wiki, Code Graph, Skills, Chat Memory.
**Page 159 (60.6–63.2s):** Black end card with animated "SUBSCRIBE / LIKE / NOTIFICATION" buttons (YouTube-style) and the subtitles "OPEN SOURCE AND RUNS LOCALLY".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| TencentDB Agent Memory – github.com/TencentCloud/TencentDB-Agent-Memory | repo | caption, audio, pages 1–37, 124–147 | Real, official Tencent Cloud repo. MIT licence ("Copyright (C) 2026 Tencent"). Last commit 2026-10-20 ("fix(panel): restore body styles when resizing ends (#1671)"). Current release v2.0.0, with v2.0.1 planned. Components: MemoryCore, MemoryKnowledge, MemoryPanel, MemoryProxy, sdk, adapters. |
| "4-tier" memory: L0 Conversation → L1 Atom → L2 Scenario → L3 Persona | architecture | audio, pages 101–106 | Matches the README. Retrieval uses BM25 + vector retrieval + RRF fallback to L1/L0. |
| −61% tokens (README: "up to 61.38%"), +51.52% pass rate, PersonaMem 48%→76% (+59%) | claims | caption, audio, pages 123, 139–142 | These are the project's own numbers, measured as an OpenClaw plugin. "Task success +50%" is the single WideSearch result (33%→50%). SWE-bench gained only +9.93% and AA-LCR +7.95%. The current README keeps only the PersonaMem row. |
| `./start-all.sh`, `.env` with "two sets of LLM parameters", panel http://localhost:8125 | setup | pages 3–10 | Verified in the README. `deploy/global-images/.env.example` needs MEMORY_LLM_BASE_URL, MEMORY_LLM_API_KEY and MEMORY_LLM_MODEL (example: https://api.deepseek.com/v1, deepseek-chat). |
| SQLite default store (optional MongoDB) | storage | page 123 tweet | True per INSTALL.md: "The default storage backend is sqlite". |
| npm @tencentdb-agent-memory/memory-tencentdb (v1.0.1 badge), node >=22.16, OpenClaw >=2026.3.13, Hermes Gateway | badges | page 1 | README badges. Hermes Agent (Nous Research) skill code is credited in the README. |
| OpenClaw | agent framework | page 1, benchmark text | The open-source agent the plugin was benchmarked with. |
| "GitHub Trending #1 Repository Of The Day" | claim | page 1 | A badge shown in the README image. Not independently verified. |
| How To Prompt (@HowToPrompt_) X post | third-party post | page 123 | Hype source. "Zero external API dependencies" is wrong: an LLM endpoint is required. |
| Claude Code v2.1.92 screen of "farza@buildspace.so" | B-roll | page 64 | Footage from another creator, not from this product. |
| n8n workflow, Claude "Sonnet 4.6" chat screen | B-roll | pages 63, 65 | Generic illustration, not this product. |
| @felixcallahan.ai | handle | account | AI-news reel account. No product found by web search. |

### What's being promoted / the funnel decoded
No paid funnel. There is no comment keyword, link or product. The end card is a generic "subscribe/like/notification" animation and the call to action is implicitly "follow". It is an engagement-driven news reel about a free open-source project.

### Verification & insights
- The repo was cloned (shallow, to scratchpad/repos/TencentCloud__TencentDB-Agent-Memory). The README and LICENSE were read and the code was not run. The repo is genuine, MIT-licensed and very active, with 39 issues and 57 PRs shown in the video.
- "Fully local / runs local" is partly true. Data is stored locally (SQLite) and the panel is localhost. But memory extraction needs an LLM through an OpenAI- or Anthropic-compatible API: the `.env` example points at DeepSeek's cloud API. It is local only if you point it at a self-hosted model. The tweet's "zero external API dependencies" is false as stated.
- "Cuts token costs by 61%" is the best case ("up to 61.38%") in the vendor's own OpenClaw long-session benchmark. "Improves task success by over 50%" comes from one benchmark (WideSearch 33%→50%). The other task benchmarks gained 8–10%. There is no independent replication.
- "Human-like recall" and "like a human brain" are marketing framing for a layered summarisation and retrieval pipeline.
- Part of the B-roll comes from other creators (a Farza Claude Code wiki demo, an X screenshot, a stock movie clip). The presenter's own lines carry the claims.
- Not verified: the "#1 Repository Of The Day" badge and the current star count (the GitHub API was not available in this session).

---

<a id="e-deo3htrcnrq"></a>

## Deo3htrCNrq | @mattmurphyai | Talking head: "what hardware to buy to run AI models locally", VRAM per model size, used-GPU prices, and the serving stack (vLLM/TGI, Nginx/Caddy, health checks, logging)
- **Link:** https://www.instagram.com/p/Deo3htrCNrq/
- **Account:** @mattmurphyai (Matt Murphy) · **Posted:** about 2026-10-17/18 (estimated from neighbouring shortcodes; no metadata was retrievable) · **Type:** reel (129s, 5 scene pages, all the same talking-head shot with word-by-word subtitles)
- **Caption source:** possibly truncated (mirror). The yt-dlp refetch returned HTTP 429 twice.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. The architecture advice is sound: size the serving stack first, then the GPU. But the hardware facts are off. A 3090 has 24 GB, not 16 GB; used 3090s and 4090s cost about 2–3× the quoted $400 / $1,000 in late 2026; and the A6000 has 48 GB and is not a $1,000 card.

### Post description
> A follower just asked what hardware to buy to run AI models locally.
>
> Before you buy anything understand what you are actually running. A 7B model runs on 16GB VRAM. A used RTX 3090 costs four hundred dollars. But the hardware is not the hard part. ...

(This is the mirror text, cut off at about 250 characters. The rest of the caption could not be fetched because Instagram returned 429.)

### Audio
English, the creator speaking to camera (selfie angle, star-projector lights on the ceiling, "FACTION" hoodie). No music. The speech runs about 330 words; timestamped notes, with key lines quoted:
- [0.0–11.1] A follower DM'd him ("hey Matt") asking what hardware to buy to run AI models locally; he says first understand what you will actually run.
- [11.1–18.2] Claim: most people overspend on the GPU and underspend on the architecture underneath that makes it useful.
- [18.2–26.9] A 7-billion-parameter model runs on a single GPU with **16GB of VRAM**; a **used RTX 3090 costs about $400**.
- [26.9–41.3] A **13-billion-parameter model needs 24GB**, so an **RTX 4090 or a used A6000** works; both can likely be found second-hand for about **$1,000**.
- [41.3–63.4] "The hard part is the stack around it": the inference server, API layer, load balancing for multiple requests, monitoring, and restart logic for when the process crashes "at three in the morning, and it will". The real cost is the system around the GPU.
- [63.4–95.7] What to build: a dedicated server or VPS with a GPU (**Hetzner, OVH, or a bare-metal** provider); an inference engine (**vLLM or text generation inference**); a reverse proxy in front (**Nginx, Caddy**); a health check that restarts the process on failure; and a logging layer to show what happened when it fails.
- [95.7–102.6] "The GPU is a component. The architecture is the system that makes it useful."
- [102.6–128.5] Suggested prompt: "direct your AI to map the full inference stack for a self-hosted model", covering model size, VRAM requirements, inference framework, API layer, reverse proxy, health check and logging pipeline. "Do not start with hardware recommendations." Start with the core architecture diagram for your use case, then size the hardware to fit it.

### On-screen content, page by page
**Pages 1–5 (0.0–129.1s):** The same shot throughout: the creator at close range in a dark "FACTION" hoodie. The only text is the burned-in, word-by-word subtitles in white and yellow (e.g. "A follower on here just DM'd", "Most people overspend", "sixteen gigabytes", "A thirteen…", "But the hardware", "the inference", "the monitoring", "and it will.", "You need a dedicated server", "OVH, or bare metal", "VLLM or text…", "Nginx,", "the process", "happened when it does fail.", "The GPU", "framework, the API", "Start with the core architecture", "hardware to fit"). The scene changes are only lighting shifts from the star projector. No charts, screenshots or links appear.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| 7B model on 16 GB VRAM | claim | audio 18s, caption | Roughly right. At FP16 the 7B weights are about 14 GB, so 16 GB fits with a short context; 4-bit quantized models need about 5 GB. |
| Used RTX 3090, "$400" | claim / price | audio 23s, caption | The card is real, but it has **24 GB** of VRAM, not 16. Late-2026 used prices reported by tracking sites are about **$1,250–1,450** (some supplier listings say $700–1,100). $400 is far below the market. |
| 13B model needs 24 GB | claim | audio 27s | FP16 13B weights are about 26 GB, which does **not** fit in 24 GB. You need 8-bit (~13 GB) or 4-bit (~7–8 GB) quantization. |
| RTX 4090 / used RTX A6000, "~$1,000" | claim / price | audio 27–41s | The 4090 has 24 GB. Its used price was about **$2,500–3,000** in Sept 2026, above its $1,599 launch price. The A6000 is a 48 GB workstation card, historically several thousand dollars used; no reliable 2026 used price was found. $1,000 is unrealistic for either. |
| Hetzner, OVH | GPU server / VPS hosts | audio 70s | Real European hosting companies with GPU dedicated-server offerings |
| vLLM | inference engine | audio 74s | Real, open source (Apache-2.0) LLM serving engine with an OpenAI-compatible API |
| Text Generation Inference (TGI) | inference engine | audio 77s | Real, Hugging Face's serving engine |
| Nginx, Caddy | reverse proxies | audio 82s | Real, open-source web servers / reverse proxies |
| "FACTION" | brand on hoodie | all pages | Probably the creator's "Faction Builders" community (named in his earlier post DePHrhRgU-o). No public listing was found. |

### What's being promoted / the funnel decoded
- No CTA, keyword, link or product is visible in the reel or the cut-off caption. It is personal-brand / consulting content. The "FACTION" hoodie points to his community ("Faction Builders", per an earlier post), but no price or URL could be found. The missing end of the caption could contain a CTA.

### Verification & insights
- **Sound advice:** a production self-hosted LLM needs an inference server (vLLM/TGI), an API layer, a reverse proxy with TLS, process supervision and health checks (systemd/Docker restart policies, Kubernetes probes), and logging/monitoring. This is standard practice.
- **Factual errors:** the 3090 VRAM is wrong (24 GB); 13B at full precision does not fit in 24 GB; and the price figures look years out of date. Used-GPU prices rose sharply in 2025–26 with AI demand and memory shortages (per 2026 buying guides), so plan on about $1.3k for a used 3090 and $2.5k+ for a used 4090, and check current eBay sold listings.
- Renting cloud GPUs by the hour (Hetzner/OVH or GPU clouds) can be cheaper than buying for occasional use. Running locally on a desktop also needs no VPS at all.
- **Not verified:** the full caption; the exact upload date; whether "Faction" is a paid community.
- **Sources:** openclawdc.com and runaihome.com (2026 used RTX 4090 prices); pcserverandparts.com and renderosity.com (used RTX 3090 prices).

---

<a id="e-deqfyvjxkay"></a>

## DeqfyVJxKaY | @bengusberg | "Loop engineering": a 4-step process for turning a recurring task into a scheduled Claude loop, citing Boris Cherny's "my job is to write loops"
- **Link:** https://www.instagram.com/p/DeqfyVJxKaY/
- **Account:** @bengusberg (Ben Gusberg) · **Posted:** 2026-10-19 (decoded from the post ID) · **Type:** reel (93s, talking head with overlay cards; 26 scene frames)
- **Caption source:** possibly truncated (mirror). The text has no ellipsis and looks complete. yt-dlp got HTTP 429.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. The Boris Cherny quote is widely reported, and the 4 steps are sensible generic advice. The opening framing ("doesn't think you should build AI agents anymore") overstates it: loops are agents run on a schedule. The "exact prompt" is gated behind a comment, and the creator's credentials ("Stanford founder", "$4 million") could not be verified.

### Post description
> AI is more than prompting #ai #aitips #claude #founder #startup

### Audio
The creator speaks to camera. Condensed into timestamped notes; only key lines are quoted exactly.
- [0.0–6.2] Hook: "The guy who invented Claude Code doesn't think you should build AI agents anymore." He says that person has moved to a much simpler system.
- [6.2–17.7] Relatable problem: you've downloaded **15 skills** and started **10 projects**, but only a few are even half done because you never have time to go back.
- [17.7–23.0] The simpler way is called **loop engineering**, and he promises to show the setup "in 30 seconds."
- [23.0–26.7] Credentials: he introduces himself as **Ben Gusberg**, a Stanford founder of an AI startup that has raised **$4 million**.
- [26.7–31.2] He quotes "the inventor Boris": "I don't prompt Claude anymore. My job is to write loops."
- [31.2–44.7] Definition: a prompt is you asking AI for something; a loop is AI doing the job on its own, checking its work and improving each run. Projects stall because each one waits for you to type the next message.
- [44.7–74.2] Four steps:
  1. Give Claude a task: one weekly repeat job (inbox, leads, weekly report).
  2. Show Claude what done looks like, an explicit goal so it can check its own work in a loop until it meets it.
  3. Have Claude track what it learns: instead of re-explaining, let it note its mistakes and the fix so they don't recur.
  4. [69.7] Give it a schedule: say how often the loop should run.
- [74.2–81.2] Example: Boris supposedly has a loop that reads what people say about Claude online and briefs him **every 30 minutes**, unasked.
- [81.2–93.2] CTA: stop starting new AI projects and turn an existing one into a loop; "comment loop and I'll send you the exact prompt". Then: follow Ben Gusberg for more on "AI Founder Life and Leadership."

### On-screen content, page by page
The video is a talking head in an apartment, holding a mic, with yellow/white word-by-word captions.
- **0–6s:** title card "HOW TO CREATE **Agent Loops** · A SIMPLE 4 STEP PROCESS TO TURN ONE TASK INTO AN ONGOING LOOP".
- **6–26.7s:** talking head only ("TELL ME IF", "BUT ONLY A", "THANKFULLY", "I'M BEN GUSBERG").
- **26.7–31.2s:** inset photo of a man on an orange background (presented as Boris, the Claude Code creator): "THE INVENTOR BORIS".
- **32.2–34.4s:** a screenshot of a Claude.ai composer with a prompt typed in: "Restructure this using Steve Jobs' Rule of Three. Identify the 3 most important points and cut or merge everything else. Give each point a short, memorable headline and one line of support. Then write a one-sentence opening that previews all 3 and a closing line that ties them together. Let me know what you cut." The bottom bar shows "Project or folder", "Opus 5.5 · Medium", "Manual". Caption "A PROMPT IS".
- **34.4–41.1s:** diagram "The Basic Agent Loop": 1 Observe ("Gather information about the current situation") → 2 Think ("Decide what to do next") → 3 Act ("Execute that decision (call an API, generate text, use a tool)") → 4 Reflect ("Learn from the results and update understanding"). Caption "A LOOP IS".
- **47.5–54.4s:** card **"1 · Give Claude a task to start with"**: "Clearly explain what you want it to do. Be specific about the goal and any context or constraints."
- **54.4–60.7s:** card **"2 · Show Claude what done looks like"**: "Provide an example of the desired output so it understands the format, quality, and level of detail you expect."
- **61.3–69.5s:** card **"3 · Have Claude track what it learns"**: "Instruct Claude to log key learnings, patterns, and improvements so it gets better over time."
- **70.5–81.1s:** card **"4 · Give it a schedule"**: "Set a recurring time for Claude to run the task (e.g. daily, weekly, monthly) so it continues the work automatically."
- **86.3–89.5s:** label **Comment "LOOP"**.
- **89.5–93.2s:** "I'M BEN GUSBERG" (outro).

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Boris Cherny ("the inventor Boris") | person | audio 1.8s/26.7s, photo | Creator and lead of Claude Code at Anthropic. Widely quoted (spring 2026 talks) as saying: "I don't prompt Claude anymore. I have loops running that prompt Claude and figuring out what to do. My job is to write loops." Exact venue and date vary by source. |
| "Loop engineering" | concept | audio 19.7s | A term popularised in 2026 (credited to Addy Osmani, echoed by Peter Steinberger) for designing recurring agent loops instead of one-off prompts. |
| Boris's loop that "briefs him every 30 minutes" | claim | audio 74s | Secondary write-ups describe Cherny's recurring loops on 5/30/60-minute intervals (e.g. PR babysitting and sweeping). The specific "reads what people say about Claude online" loop is not independently confirmed. |
| Claude, Claude Code, Opus 5.5 | product/model | audio, screenshot | Anthropic products. Scheduling is possible via Claude Code features or external schedulers. |
| Steve Jobs' Rule of Three prompt | prompt | 32–34s | Example prompt shown on screen, quoted above. |
| "The Basic Agent Loop" (Observe/Think/Act/Reflect) | diagram | 34–41s | A generic agent-loop diagram. |
| Ben Gusberg, "Stanford founder", "$4 million raised" | claims | audio 23s | Not verified. Web search found no match for the name, startup or round. |
| "LOOP" | CTA keyword | audio, 86s card | Comment-to-DM for "the exact prompt". |

### What's being promoted / the funnel decoded
"Comment LOOP" sends a DM with "the exact prompt", a single loop-setup prompt. It is a free lead magnet to grow the creator's "AI Founder Life and Leadership" audience; no price was shown. The four cards already contain the substance: a concrete recurring task, a definition of done or example output, a self-maintained learnings log, and a schedule.

### Verification & insights
- I web-searched the Boris Cherny quote. It is widely reported in very close wording, mostly via secondary sources (blogs, LinkedIn, video summaries) and not a primary transcript.
- The video's opener ("doesn't think you should build AI agents anymore") misframes the quote. Cherny's point is that he runs agents in automated loops instead of prompting by hand, so loops are still agents.
- **"Set it up in 30 seconds":** an exaggeration. Truly unattended runs need a scheduler (e.g. Claude Code scheduled tasks, cron or CI), tool permissions and a memory file. The video does not show any actual setup.
- **Steps 2 and 3** (explicit success criteria and a persistent learnings file such as CLAUDE.md or a notes log) are good, standard practice.
- **Not verified:** the creator's Stanford affiliation, startup and $4M raise.

---

<a id="e-deohajhnmw1"></a>

## DeohAJhNMw1 | @opusjake | "Claude Mods": three use-cases (sessions that talk to each other, a "cheapest model" saver, a custom dashboard), with a comment-"MOD" DM funnel
- **Link:** https://www.instagram.com/p/DeohAJhNMw1/
- **Account:** @opusjake (Opus Jake) · **Posted:** 2026-10-18 · **Type:** reel (33s, 21 pages)
- **Caption source:** full (Instagram, refetched with yt-dlp)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. Claude Code "mods" are real: they shipped in v2.1.287 on 2026-10-01. But the three "mods" are only illustrated with stylized mock-ups. Nothing is named, linked or shown to exist, and the actual files sit behind a comment-for-DM gate. Cross-session messaging is already a separate built-in feature of Claude Code.

### Post description
> Comment "MOD" and I'll send you all the mods 👇
>
> Your Claude setup could be doing way more.
>
> These 3 mods let you connect Claude chats so they work together, use cheaper models for simple tasks, and add a custom dashboard for your to-dos and messages.
>
> One chat finds leads. Another drafts the outreach. You manage the workflow.
>
> Follow @opusjake for more ways to put AI to work.
>
> #Claude #ClaudeAI #AI #AITips #AITools

At the time of posting: 1,659 likes and 1,848 comments. The very high comment count reflects the comment-keyword gate.

### Audio
English, fast talking head. No identifiable music. Whisper writes "Claude" as "cloud".
- [0.0–6.0] "[Claude] just got its biggest update ever and most people still don't know how to use it. It's called mods and here are the three best ways you should be using it."
- [6.0–16.6] "Number one is making your Claude sessions talk to each other because now you can have one Claude chat talk to another Claude chat. One can do prospecting, the other one can do cold outreach and you can have another session that acts as the manager."
- [16.6–23.8] "The second way is optimizing your use so you never waste money again. You can set up a mod to always make sure you're using the most cost effective model so you never waste credits on simple tasks."
- [23.8–31.1] "And the third way is actually customizing the way Claude looks so you can have a built-in dashboard that has a to-do list, messages you need to answer or anything else."
- [31.1–33.2] "So if you want all these mods and more just follow me and comment mod and I'll shoot them over."

### On-screen content, page by page
Split screen: the top half shows pixel-art and Claude-UI mock-ups, the bottom half the creator. Captions are in all-caps mono labels.
**Page 1 (0.0–1.6s):** Pixel town at night. A crate with the Claude starburst and "**v2.1.287**" plus a download bar; the Claude crab mascot with a "!" above it. Label "CLAUDE JUST GOT".
**Page 2 (1.6–3.2s):** Pixel crowd of people with terminal windows. "AND MOST PEOPLE".
**Page 3 (3.2–4.1s):** Crab mascot beside the "✳ Claude" logo. "HOW TO USE IT".
**Page 4 (4.1–5.1s):** Empty pixel shelf. "IT'S CALLED MODS".
**Page 5 (5.1–6.1s):** A pixel game console with a blue "MOD 1" cartridge. "YOU SHOULD".
**Page 6 (6.1–8.5s):** Cartridge "**MOD 1 – LINK-UP**" (chat-bubble icon) on a desk. "BE USING IT".
**Page 7 (8.5–11.1s):** Two Claude desktop-app windows. "**Prospector**": "Found 40 gyms with no online booking." The second is "**Outreach**". Both have a "Reply to Claude…" box with Chat / Cowork tabs and the model "Opus 5.5".
**Page 8 (11.1–13.4s):** Google Sheets file "leads" with columns A–D "gym · area · owner · booking" (empty), and a pixel crab with a pickaxe.
**Page 9 (13.4–15.3s):** Pixel office: one crab mining, one carrying mail, and a desk monitor. "AND YOU CAN HAVE".
**Page 10 (15.3–16.0s):** Green cartridge "**MOD 2 – SAVER**" (coin icon) in a console.
**Page 11 (16.0–17.0s):** Claude "Usage" panel: "Session limit 31% used – Resets in 54 min", "Weekly 18% used – Resets Wed 3:00 AM". "IS OPTIMIZING".
**Page 12 (17.0–18.1s):** Pixel scene of coins falling from a box. "SO YOU NEVER".
**Page 13 (18.1–19.2s):** Claude home, "Good afternoon, Jake", with the prompt "**Always use the cheapest model**" (Opus 5.5 selected). "WASTE MONEY AGAIN".
**Page 14 (19.2–20.3s):** A tag "the typos in this email" sent to a small crab with a money bag. Crabs in decreasing size. "ALWAYS MAKE SURE".
**Page 15 (20.3–21.6s):** "**Price per million output tokens**" chart of crabs shrinking from left to right, labelled **Fable 5.1 · Opus 5.5 · Sonnet 5.5 · Haiku 5.5**. No numbers. "THE MOST".
**Page 16 (21.6–22.6s):** Two stacks of coins, one taller. "SO YOU NEVER".
**Page 17 (22.6–23.6s):** A blank green/white page. "ON SIMPLE TASKS".
**Page 18 (23.6–25.8s):** Purple cartridge "**MOD 3 – DESIGN**" (presumed from the icon; the label is tiny) over a small chat window. "AND THE THIRD WAY".
**Page 19 (25.8–30.1s):** Dark-theme Claude chat. User: "Help me sell online booking to gyms in Austin" → "Happy to help. Let's start with a list of gyms." User: "Find 40 gyms in Austin with no online booking" → "Found 40. They're in a sheet called Gym leads." User: "Write a short email to each gym on my list" → "Done. 40 emails drafted." A widget reads "▦ Dashboard – **4 messages to answer**". A game-style HUD bar shows rows of shirts, hearts, green bars and the number "**25**". Input "Describe a task or ask a question", "Auto", "Opus 5.5 Extra". "SO YOU CAN HAVE".
**Page 20 (30.1–31.6s):** Shelf holding the three cartridges: MOD 1 (LINK-UP), MOD 2 (SAVER), MOD 3.
**Page 21 (31.6–33.5s):** Card: "① **Follow** @opusjake [Follow]" / "② **Comment** [Add a comment…]" / "➤ I'll DM you all the mods".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude Code mods / v2.1.287 | product feature | audio 0–6s, page 1 | Real. The anthropics/claude-code CHANGELOG at 2.1.287 reads "Added Claude Mods: plugins may now modify deeper behavior". Mods are plugins with a TypeScript hooks module that can rewrite prompts, gate tools, open panes and register commands/tools. Press coverage dates the launch to 2026-10-01. Built-in mods in the repo: sec-default, diff, telemetry, agents-md (plus "You should know"; see post Deo8i2rEQi5). |
| "MOD 1 – LINK-UP" (sessions talking to each other) | claimed mod | audio 6–16s, pages 5–9 | Not named or linked. Claude Code already has **built-in cross-session messaging** (SendMessage / ListAgents between sessions on the same machine, per the CHANGELOG), so a mod is not strictly needed. The "Prospector"/"Outreach" windows are mock-ups. |
| "MOD 2 – SAVER" (always use the cheapest model) | claimed mod | audio 16–24s, pages 10–16 | Technically plausible: mods can rewrite prompts and settings. But no code was shown. "Always use the cheapest model" is a risky rule, since cheaper models fail more often on hard tasks. |
| "MOD 3" (dashboard: to-dos, messages to answer) | claimed mod | audio 24–31s, pages 18–19 | Plausible: mods can draw panes and status rows. The UI shown is a mock-up (pixel HUD, "4 messages to answer"). |
| Fable 5.1, Opus 5.5, Sonnet 5.5, Haiku 5.5 | AI models | page 15 | Real Anthropic model names. The chart has no numbers, only relative crab sizes. Elsewhere Fable 5.1 is reported at $50 per million output tokens. |
| Claude "Usage" panel (31% session, 18% weekly) | UI | page 11 | Real Claude usage-limit UI style; the numbers are illustrative. |
| "40 gyms in Austin with no online booking", "40 emails drafted" | example | pages 7, 19 | Example cold-outreach workflow. No real data or businesses are shown. |
| Comment "MOD" | CTA | caption, audio 31s, page 21 | Auto-DM keyword |

### What's being promoted / the funnel decoded
- "Follow + comment MOD → I'll DM you all the mods." This is a ManyChat-style engagement gate: 1,848 comments against 1,659 likes. What arrives in the DM (plugin files, a GitHub link, or a landing page or newsletter sign-up) is not visible, and no product or price is named. Web searches for "Opus Jake" / "opusjake" found no website, course or community.
- You do not need the DM to get the features. Built-in mods turn on with `/plugin`, cross-session messaging is built in, and Claude Code can write a mod for you in a session (the CHANGELOG mentions "the mods Claude writes in a session").

### Verification & insights
- **Checked:** a blobless clone of anthropics/claude-code (scratchpad/repos/anthropics__claude-code; last commit 2026-10-20). Read mods/README.md and the CHANGELOG entries for 2.1.287 (mods, You should know) and cross-session messaging. Web: The New Stack, pasqualepillitteri.it and gigazine.net on the launch of mods.
- A mod is code that hooks every event in your session, including tool calls, permissions and prompts. Installing mods DM'd by a stranger gives that code deep access. Read the source first, or have Claude write the mod for you.
- "Biggest update ever" is hype. Mods are a significant extensibility feature, but the reel shows no real mod running.
- **Not verified:** what the DM delivers; whether the creator actually built these three mods.

---

<a id="e-deo8i2reqi5"></a>

## Deo8i2rEQi5 | @jackroberts___ | Two Claude Code mods for long sessions: the built-in "You should know" side-agent and an "auto-handoff" mod that writes a brief and moves the work to a fresh session before compaction
- **Link:** https://www.instagram.com/p/Deo8i2rEQi5/
- **Account:** @jackroberts___ (Jack Roberts) · **Posted:** 2026-10-18 · **Type:** reel (44s, 32 pages)
- **Caption source:** full (Instagram, refetched with yt-dlp)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. "You should know" is a real built-in mod, confirmed in the official CHANGELOG at v2.1.287. "auto-handoff", said to be "free on GitHub", is shown running on screen, but the repository could not be found or verified, and it sits behind a comment-for-DM gate.

### Post description
> Comment "MODS" and I'll send you the setup for both.
>
> Long sessions don't break at the start.
>
> They break near the end.
>
> That's when Claude Code compacts itself.
>
> And the details you needed get squashed.
>
> Mod one is You Should Know.
>
> It's built right in.
>
> A second AI watches the session.
>
> It flags what you or Claude missed.
>
> Mod two is auto-handoff.
>
> It's free on GitHub.
>
> Right before compacting, it writes a brief.
>
> Then hands it to a fresh session.
>
> Like a shift change at a hospital.
>
> The next nurse gets the full chart.
>
> So your work keeps moving.
>
> And nothing important gets dropped.
>
> #claudecode #claudemods #claude #aiagent #aicoding

At the time of posting: 748 likes and 1,095 comments. The comments are inflated by the keyword gate.

### Audio
English talking head (the same creator and set as DepMtMyEciv: cap, "BASQUIAT" hoodie). No identifiable music. Whisper writes "Claude" as "Cloud".
- [0.0–7.6] "Most people don't know that Claude Code just got an upgrade that stops it from quietly forgetting your work halfway through a job."
- [7.6–14.6] "They're called Claude Mods and there are two that you need to turn on. The first one is already built in and it's called You Should Know."
- [14.6–20.7] "Just switch it on. And the second AI watches your back and flags anything that Claude misses."
- [20.7–32.0] "And the second one actually stops Claude from losing your work. On long sessions, the context fills up and Claude starts to compact itself. Which is where important stuff gets lost."
- [32.0–41.6] "So this one runs right before that happens and hands everything to a fresh session. With the short brief, so you can pick up exactly where you've left off."
- [41.6–44.2] "Comment mods and I'll send you a setup for both of them."

### On-screen content, page by page
Split screen of animated graphics on top and the creator below, with burned-in subtitles.
**Page 1 (0.0–1.1s):** Pixel people with "?" over their heads. "Most people".
**Page 2 (1.1–2.9s):** The Claude crab mascot over a progress bar on a pastel background. "Claude Code".
**Pages 3–5 (2.9–4.0s):** Talking head. "that stops it".
**Page 6 (4.0–7.7s):** The crab above a blank app-window wireframe. "quietly".
**Page 7 (7.7–8.9s):** The Claude starburst logo in a circle. "they are".
**Page 8 (8.9–11.1s):** The crab between two dashed panels. "and".
**Page 9 (11.1–12.9s):** Terminal "claude": "**Claude Code v2.1.299** · Opus 5.5 · Claude Max", with "> /plugin" and "Mods" below. "first one is".
**Pages 10–14 (12.9–15.6s):** Talking head. "and it's", "called", "You should".
**Page 15 (14.6–15.6s):** Terminal with "› **/plugin enable** ▌". "just switch".
**Page 16 (15.6–18.0s):** Terminal "Claude Code v2.1.299 · Opus 5.5 · Claude Max" with "• Editing checkout…" (tiny text). "and a".
**Page 17 (18.0–20.7s):** Window "claude · changes": "✓ Updated checkout.tsx", "✓ Added the Postgres schema", "– Skipped email.test.ts", "✓ Renamed the API routes", "– New migration not run". "and flags".
**Page 18 (~20.7–22.3s):** An orange "↳" (handoff) icon on a starfield.
**Page 19 (22.3–24.5s):** Stacked notes: "Built the login page", "Fixed the checkout bug", "Picked Postgres for the data", "Named every API route", "Wrote the sign-up emails". "Claude".
**Page 20 (24.5–27.1s):** A blank card. "On long".
**Page 21 (27.1–29.6s):** A document filling with colored bars (the context window filling up). "and Claude".
**Page 22 (29.6–32.0s):** The colored bars squashed into a thin strip (compaction). "which is".
**Pages 23–24 (32.0–34.5s):** An apparently real terminal: "Now reading part 3: / Read 1 file / • **[auto-handoff] A tool call was refused at the h[andoff threshold…] fresh session.** / ✻ Baked for 10s · done 2:38 AM / **auto-handoff · 71k / 80k** / writing brief". "so".
**Page 25 (34.5–37.5s):** Two terminals, "Claude Code v2.1.299 – **long session**" (context bar full and red) and "Claude Code v2.1.299 – **fresh session**" showing "↳ **Handoff from session**". "And hands".
**Page 26 (37.5–38.5s):** File card "**handoff-brief.md**" with a heading like "## Work in Progress" and "Sign-up…". "with".
**Page 27 (38.5–41.5s):** A wireframe app window above a terminal with an almost empty "Context" bar. "so".
**Pages 28–32 (41.5–44.3s):** Talking head. "Comment mods", with the keyword shown large as **"MODS"**, then "and I'll send", "you the".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude Code mods | feature | audio 7.6s, caption | Real. Added in v2.1.287 ("Added Claude Mods: plugins may now modify deeper behavior"). |
| "You should know" | built-in mod | caption, audio 11–20s, pages 9–17 | **Real.** CHANGELOG 2.1.287: "Added You should know, a built-in mod where a side agent watches your back and flags things you or Claude might miss. Turn it on with `/plugin enable cc-plugin-you-should-know@builtin` (for first-party sessions with telemetry on)." Later releases changed the notes to say "we / the main agent / you" and fixed them always being written in English. |
| auto-handoff | mod ("free on GitHub") | caption, audio 20–41s, pages 23–26 | **Not found.** Web searches found no GitHub project by that name. Similar existing tools: sclaude (PyPI; at about 70% context it has Haiku write a handoff doc and respawns Claude), 392fyc/claude-handoff, and REMvisual/claude-handoff (manual /handoff skills). The terminal on screen shows it firing at "71k / 80k" tokens and "writing brief". |
| handoff-brief.md | file | page 26 | The brief the mod is said to write for the fresh session |
| Claude Code v2.1.299, Opus 5.5, Claude Max | version / model / plan | pages 9, 16, 25 | A plausible current build (mods need ≥ 2.1.287). Claude Max is Anthropic's paid plan. |
| Compaction / "context fills up" | concept | audio 24–32s, pages 21–22 | Real. Claude Code auto-compacts (summarizes) the conversation near the context limit, which can lose detail. |
| Comment "MODS" | CTA | caption, audio 41.6s, pages 28–32 | Auto-DM keyword |

### What's being promoted / the funnel decoded
- Comment "MODS" → a DM with "the setup for both". The first needs no DM: run `/plugin enable cc-plugin-you-should-know@builtin`, which requires a first-party Anthropic sign-in with telemetry on. The second presumably arrives as a GitHub link the creator does not name publicly.
- The same creator (Jack Roberts) uses the identical comment-keyword pattern in DepMtMyEciv ("SPLIT"). A web search ties a "Jack Roberts" to the paid Skool community "AI Automations by Jack" (about $77/month reported). That this account belongs to the same person is likely but not confirmed. No product is sold in this reel.

### Verification & insights
- **Checked:** the anthropics/claude-code CHANGELOG via a blobless clone at scratchpad/repos/anthropics__claude-code (last commit 2026-10-20). "You should know" is listed at 2.1.287 with its enable command; the repo's mods/ folder holds the other built-ins (agents-md, diff, sec-default, telemetry).
- "You should know" runs a side agent, which uses additional model usage.
- The handoff idea is sound. A focused brief often preserves the important state better than a generic compaction summary, and Claude Code users have requested it (anthropics/claude-code issue #11455). But a mod that intercepts tool calls ("A tool call was refused at the handoff threshold") and spawns sessions is powerful code. Read any DM'd repo before installing it.
- **Not verified:** the auto-handoff repo's existence, author and license; what the DM contains.
- **Sources:** github.com/anthropics/claude-code (CHANGELOG, mods/README.md); pypi.org/project/sclaude; github.com/392fyc/claude-handoff; github.com/REMvisual/claude-handoff.

---

<a id="e-ddwnd3mkyxm"></a>

## DdwnD3mkyxm | @arwazaz_ | "Algo Trading with Jev": 7-slide architecture putting TypeSafe's Jev model as a "decision layer" between a feature engine and a code-controlled risk engine, connected to Indian brokers, MT5, TradingView and crypto; comment "JEV" for a starter-code pack
- **Link:** https://www.instagram.com/p/DdwnD3mkyxm/
- **Account:** @arwazaz_ (Arwaz Az) · **Posted:** 2026-09-26 · **Type:** carousel (7 slides)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; the mirror copy was cut off after "JEV ↓ ...")
- **Category:** AI tools / Trading strategy
- **Verdict:** PARTLY TRUE. The architecture and risk-control advice is sound and generic. The slides misdescribe Jev, which returns typed probabilities, not free-text reasoning or entry, stop and target levels. There is no evidence of edge. The funnel is a free DM resource pack.

### Post description
> 💬 COMMENT "JEV" and I'll send you the complete Algo Trading × Jev architecture + starter code + resources.
>
> What happens when you put Jev inside an algorithmic trading system?
>
> Not: CHART → SIGNAL → TRADE

- **Proposed pipeline instead:** market data → feature engine → Jev → decision → risk engine → execution → feedback. "The interesting part is that Jev becomes a decision layer."
- **Structured market state fed to Jev:** price, trend, RSI / MACD, volume, volatility, position state, market context, risk parameters. Jev returns a structured decision that your code can evaluate.
- **Key rule:** "AI DOESN'T GET UNLIMITED CONTROL." Code still controls position sizing, exposure, slippage, daily loss limits, order validation, kill switch, execution and order verification.
- **Environments it can connect to:** TradingView, MetaTrader 5, Zerodha Kite, Angel One, Upstox, Dhan, crypto APIs, forex infrastructure.
- **Stated goal:** not a "magic AI trading bot" but a modular decision architecture you can backtest, forward-test, paper trade, measure and improve.
- **Calls to action:** comment "JEV" for "the complete setup + resources"; "🔖 SAVE THIS if you're building AI-powered algo trading."
- **Disclaimer:** "Educational content only. Not investment advice. Trading involves market risk."
- **Hashtags:** #AlgoTrading #Jev #AITrading #QuantTrading #AlgorithmicTrading

*Caption condensed – full text is on the original post.*

### Audio
None (image carousel).

### On-screen content, slide by slide
Every slide has the header "ARWAZ AZ — ALGO TRADING × AI × A BETTER YOU", a counter "0N / 07", the footer "Educational content only. Not a trading recommendation." and the signature "Same Markets. A Smarter Trader."

**Slide 1 (01/07):** "**ALGO TRADING WITH JEV.**" / "WHAT HAPPENS WHEN AI BECOMES THE DECISION LAYER?" A central Jev logo is wired to: MetaTrader 5, TradingView, Kite (Zerodha), Bitcoin, Dhan, Forex (Major Pairs), upstox, Angel One, and a Python logo. Bottom flow: MARKET DATA (Real-time data from multiple sources) → JEV (Structured decision with probabilities) → RISK (Position size, limits and safety checks) → EXECUTION (MT5, TradingView, Kite, Dhan and more).

**Slide 2:** "**YOUR ALGO DOESN'T HAVE TO BE JUST RULES.**" / "COMBINE RULE-BASED LOGIC WITH AI DECISIONS USING JEV."
- **TRADITIONAL APPROACH** ("Fixed rules, limited flexibility."). Python:
  ```
  if ema_fast > ema_slow:
      signal = "BUY"
  elif ema_fast < ema_slow:
      signal = "SELL"
  else:
      signal = "HOLD"
  ```
  Cons: Only works for predefined conditions · Struggles in complex or mixed market states · No context or reasoning · Difficult to adapt to new situations.
- **JEV ENHANCED APPROACH** ("Understands market state and returns a structured decision."). JSON:
  ```
  {"symbol": "NIFTY", "timeframe": "15m",
   "indicators": {"ema20": 24412.3, "ema50": 24388.1, "rsi": 62.4, "volume_ratio": 1.37},
   "market_context": "uptrend with pullback", "position": 0, "question": "What is the best action?"}
  ```
  Pros: Analyzes multiple indicators and context · Returns BUY / HOLD / SELL with probabilities · Handles complex and uncertain market states · Works across different markets and timeframes.
- Flow: MARKET DATA (Price, indicators, volume, news, etc.) → FEATURE ENGINE (Create structured market state) → JEV (Analyze and return structured decision) → CODE EXECUTION (Your strategy handles the logic) → BROKER / EXCHANGE (Place orders via Kite, MT5, Dhan, etc.).

**Slide 3:** "**DON'T GIVE JEV A CHART. GIVE IT A STATE.**" / "STRUCTURED MARKET DATA LEADS TO BETTER AND MORE RELIABLE DECISIONS."
- **RAW CHART (NOT IDEAL)** (candlestick image) ↓ Market Data (Price, volume, order book, news, etc.) · Feature Engine (Calculate indicators and create structured state.) · Add Context (Trend, volatility, news, positions, risk parameters.)
- **STRUCTURED MARKET STATE (IDEAL)** ("Key data, indicators and context for Jev."). JSON:
  ```
  {"symbol": "NIFTY", "timeframe": "15m", "price": 24412.3, "trend": "bullish",
   "indicators": {"ema20": 24385.6, "ema50": 24310.2, "rsi": 62.4, "macd": 0.84, "volume_ratio": 1.38},
   "market_context": "uptrend with pullback", "news_impact": "neutral", "position": 0,
   "available_capital": 100000, "risk_per_trade": 0.01, "question": "What is the best action?"}
  ```
  Side tags: Price & Timeframe / Technical Indicators / Market Context / Position & Risk Info / Specific Question for Jev.
- Flow: MARKET DATA (Live or historical data from broker / provider) → FEATURE ENGINE (Indicators, signals, market state) → STRUCTURED STATE (Clean input for Jev) → JEV (Analyze and return a decision) → DECISION OUTPUT (BUY / HOLD / SELL with reasoning).

**Slide 4:** "**JEV DOESN'T PLACE THE TRADE.**" / "JEV GIVES A STRUCTURED DECISION. YOUR CODE CONTROLS WHAT HAPPENS NEXT."
- Steps:
  1. MARKET STATE (Live data, indicators, positions, market context, risk parameters.)
  2. JEV (Analyzes the market state and returns a structured decision with probabilities.)
  3. DECISION OUTPUT (BUY / HOLD / SELL + reasoning, confidence and key factors.)
  4. RISK ENGINE (Checks position size, exposure, limits and safety rules.)
  5. EXECUTION LAYER (Places orders via broker / platform (Kite, MT5, Dhan, etc.).)
  6. FEEDBACK LOOP (Monitors execution, updates positions, and sends new market state to Jev.)

  A loop arrow reads "REPEAT WITH UPDATED MARKET STATE".
- **EXAMPLE: JEV DECISION OUTPUT** (JSON):
  ```
  {"action": "BUY", "confidence": 0.73, "position_size": 0.02,
   "reasoning": ["Uptrend with pullback", "RSI in healthy range", "Volume above average" },
   "risk_notes": "Watch for resistance",
   "key_levels": {"entry": 24412.5, "stop": 24320.0, "target": 24600.0}}
  ```
  The "reasoning" array is closed with "}" instead of "]" on the slide, which makes it invalid JSON.
- **RISK ENGINE CONTROLS:** Position sizing rules · Maximum exposure per trade · Daily loss limit · Slippage and spread checks · Confidence threshold · Duplicate order protection · Kill switch · Market hours and liquidity checks.
- Bottom: AI DECIDES (Understands context and returns a decision.) → CODE CONTROLS (Applies risk rules and business logic.) → BROKER EXECUTES (Places the trade via API / platform.) → SYSTEM LEARNS (Uses execution results to update the next state.)

**Slide 5:** "**ONE DECISION ENGINE. MULTIPLE MARKETS.**" / "BUILD ONCE. CONNECT TO MULTIPLE PLATFORMS." Jev labelled "AI DECISION LAYER", connected to:
- TradingView (Charts, alerts and market data)
- MetaTrader 5 (Forex, CFDs, multiple markets)
- Forex (Major currency pairs)
- Kite Zerodha (Indian stocks, F&O (Kite Connect))
- Angel One (Indian stocks, F&O (SmartAPI))
- Dhan (Indian stocks, F&O (DhanHQ API))
- upstox (Indian stocks, F&O (Upstox API))
- Crypto (Research & execution (via supported APIs))
- Global Markets (Stocks, ETFs, Indices, Commodities)

"WHY A MULTI-MARKET SETUP?": MORE OPPORTUNITIES (Different markets, different conditions) · FLEXIBILITY (Switch between asset classes) · DIVERSIFICATION (Reduce single-market dependence) · SAME AI BRAIN (One decision engine across platforms) · MODULAR DESIGN (Easy to add or remove brokers and markets).

**Slide 6:** "**THE ALGO LEARNS FROM THE MARKET STATE.**" / "A CONTINUOUS DECISION LOOP WITH JEV."
- Loop:
  1. MARKET DATA (Live or historical data from broker / provider.)
  2. FEATURE ENGINE (Calculate indicators and create structured market state: Trend, RSI, MACD, Volume, Volatility, News / Events)
  3. JEV DECISION (`{"action": "BUY", "confidence": 0.72, "reasoning": "Uptrend with pullback, volume above average"}`)
  4. RISK CHECK (Validate with your risk management rules: Position size (rules), Exposure limits, Stop loss / Take profit, Slippage & spread checks, Daily loss limit, Kill switch)
  5. EXECUTION (Place orders via broker / platform (Kite, MT5, Dhan, etc.); logos Kite, MetaTrader 5, Dhan, Upstox)
  6. ORDER RESULT (Status: Filled · Entry Price: 24412.5 · Quantity: 50 · Time: 09:45:12 · Broker: Kite · Order ID: 24091872)
  7. FEEDBACK LOOP (Update market state, track performance and improve the next decision: P&L Tracking, Performance Metrics, Strategy Refinement)
- "TEST. VALIDATE. THEN SCALE.": BACKTEST (Test on historical data.) → FORWARD TEST (Validate on recent data.) → PAPER TRADE (Run in live market without real capital.) → LIVE (Start with small capital and scale.)
- "MEASURE THE SYSTEM": Win rate · Expectancy · Max drawdown · Sharpe ratio · Profit factor · Slippage & execution quality.

**Slide 7:** "**THIS ISN'T JUST A BOT. IT'S AN AI DECISION ARCHITECTURE.**" / "ONE SYSTEM. MULTIPLE MARKETS. REAL INFRASTRUCTURE."
- Left (inputs, same descriptions as slide 5): TradingView, MetaTrader 5, Kite, Dhan, Angel One, Upstox, Crypto. These feed DATA IN → Jev → FEEDBACK LOOP (Execution results update the next decision).
- Right: JEV DECISION (Buy / Hold / Sell with reasoning) → RISK ENGINE (Position sizing, limits, safety rules, kill switch) → EXECUTION (Place orders via broker / platform) → ORDER RESULT (Filled / Rejected / Partial fill) → UPDATE STATE (Update positions, P&L and market state).
- CTA box: "**COMMENT "JEV"** and I'll send you the complete Algo Trading × Jev architecture + starter code + resources." Checklist: Full architecture diagram · Broker integration resources · Starter code (Python) · Risk engine framework · Backtesting and testing workflow · Recommended tools and libraries · Multi-market setup (India, Forex, Crypto) · Implementation guide.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Jev | AI model (TypeSafe AI) | caption, every slide | TypeSafe AI's closed "System One" typed-decision model (public launch 15 Sep 2026; early access via typesafe.ai; priced at $0.042 per 1M input tokens with free output). It returns typed answers (yes/no with confidence, choice probabilities, scores), not free-text reasoning. Verified in the earlier review (DeL4K4hk6k9) via launch coverage and the open re-implementation razorback16/openjev (Apache-2.0). |
| TradingView | platform | caption, slides 1, 5, 7 | Real charting platform (free and paid plans). Webhook alerts can drive bots. |
| MetaTrader 5 | platform | caption, slides 1, 5–7 | Real (MetaQuotes) forex/CFD platform with a Python API. |
| Zerodha Kite / Kite Connect | broker / API | caption, slides 1, 2, 5–7 | Real Indian broker. The Kite Connect API is a paid monthly subscription. |
| Angel One (SmartAPI), Upstox (Upstox API), Dhan (DhanHQ API) | brokers / APIs | caption, slides 1, 5–7 | Real Indian brokers with trading APIs. |
| Bitcoin / Crypto APIs, Forex major pairs, Global Markets | asset classes | caption, slides 1, 5, 7 | Generic. |
| Python | language | slides 1, 2, 7 | Starter-code language. |
| NIFTY example values (ema20 24412.3/24385.6, ema50 24388.1/24310.2, rsi 62.4, macd 0.84, volume_ratio 1.37/1.38, capital 100000, risk_per_trade 0.01, confidence 0.73/0.72, position_size 0.02, entry 24412.5, stop 24320.0, target 24600.0, qty 50, 09:45:12, Order ID 24091872) | example numbers | slides 2–4, 6 | Illustrative mock-ups, not a real run. |
| "JEV" | comment keyword | caption, slide 7 | DM trigger for the resource pack. |

### What's being promoted / the funnel decoded
- Comment "JEV" leads to an auto-DM with the "complete Algo Trading × Jev architecture + starter code + resources" (the sister post DeL4K4hk6k9 says "I'll send you the PDF"). No price is shown. Same creator, same week, same keyword as DeL4K4hk6k9; the 100K-strategies e-book post Dd3gT_0k6hp uses the same pattern.
- The creator is a small Indian algo-trading account ("Same Markets. A Smarter Trader."). The aim is engagement and list growth via the trending "Jev" keyword. No affiliate link to TypeSafe, and no paid product visible yet.

### Verification & insights
- **Jev mismatch:** slides 3, 4 and 6 show Jev returning prose "reasoning", "risk_notes" and price "key_levels" (entry, stop, target). Jev is a typed-decision model: you would have to pose those as typed questions (e.g. a BUY/HOLD/SELL choice with probabilities), and the levels and prose would come from your own code or a separate LLM. "With probabilities" (slides 1, 2, 4) is the accurate part.
- **Sound parts:** "AI doesn't get unlimited control", the deterministic risk engine (sizing, exposure, daily loss limit, kill switch, duplicate-order protection, market hours) and backtest → forward → paper → small live are correct, standard practice.
- **No evidence of edge:** feeding a model the same EMA, RSI and MACD values a rule would use does not create alpha by itself. No backtest, P&L or comparison against the "traditional" EMA rule is shown.
- **Regulatory note:** India's SEBI retail algo framework (in force from 2025, phased) requires broker-approved and registered algos and static IPs for API orders above a frequency threshold. DIY starter code wired to Kite, Dhan, Upstox or Angel One must comply.
- **Slides look AI-generated** (uniform poster style, the JSON bracket error on slide 4).
- **Not verified:** the contents of the DM pack and whether any working code exists.

---

<a id="e-deernoaeysa"></a>

## DeErnOaEySa | @arwazaz_ | "10 AI agents, one trading system": 10-slide architecture of 8 analysis agents plus a deterministic risk engine and execution engine; comment "AGENT" for a PDF blueprint
- **Link:** https://www.instagram.com/p/DeErnOaEySa/
- **Account:** @arwazaz_ (Arwaz Az) · **Posted:** 2026-10-04 · **Type:** carousel (10 slides)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; the mirror copy was cut off after "07 — Quant...")
- **Category:** AI tools / Trading strategy
- **Verdict:** PARTLY TRUE. The architecture (specialised agents, AI only for research, deterministic risk and execution) is a sensible, widely used design. The "REAL RESULTS" slide shows mock metrics (52.3% win rate, Sharpe 1.18, −12.4% max DD) with no actual track record. The funnel is a free PDF.

### Post description
> COMMENT "AGENT" 👇
>
> What if you stopped asking one AI to do everything?
>
> Instead, build a trading system where every agent has a specific job.
>
> 01 — Market Regime
> 02 — Technical
> 03 — Multi-Timeframe
> 04 — News
> 05 — Sentiment
> 06 — Fundamental
> 07 — Quant
> 08 — Strategy
>
> Then the system adds:
>
> 09 — Risk Engine
> 10 — Execution Engine
>
> The workflow:
>
> RESEARCH → ANALYZE → TEST → VALIDATE → RISK → EXECUTE → IMPROVE
>
> The important part:
>
> AI doesn't need to make every decision.
>
> Use AI for research and analysis.
>
> Use deterministic rules for risk and execution.
>
> That's how you move from:
>
> "AI, give me a trading signal."
>
> to:
>
> "Build me a system that can systematically research, test and execute trading ideas."
>
> Want the complete 10-agent AI Trading System blueprint?
>
> COMMENT "AGENT" 👇
>
> I'll send you the PDF.
>
> Save this post 🔖
>
> Educational content only. Not financial advice.
>
> #AITrading #AlgoTrading #QuantTrading #ClaudeCode #trading

### Audio
None (image carousel).

### On-screen content, slide by slide
Every slide has the header "ARWAZ AZ — AI × TRADING × A BETTER YOU", top right "RESEARCH / AUTOMATE / IMPROVE" with counter "NN / 10", and corner text "IDEAS DATA ANALYSIS STRATEGY EXECUTION" / "RESEARCH BACKTEST VALIDATE RISK IMPROVE". Style: AI-generated steampunk-metal "agent pods".

**Slide 1:** "**10 AI AGENTS. ONE TRADING SYSTEM.**" / "Each agent has one job." A hub "AI TRADING SYSTEM" is surrounded by pods 01 MARKET REGIME, 02 TECHNICAL, 03 MULTI-TIMEFRAME, 04 NEWS, 05 SENTIMENT, 06 FUNDAMENTAL, **08** QUANT (mislabelled; should be 07), 08 STRATEGY, 09 RISK, 10 EXECUTION. Corner text: "SYSTEMATIC DATA-DRIVEN DISCIPLINED", "BETTER TRADING A BETTER YOU".

**Slide 2:** "**DON'T ASK ONE AI TO DO EVERYTHING.**" / "Use specialized agents. A structured workflow."
- Pods: TECHNICAL AGENT (Market Analysis), NEWS AGENT (Data & News), SENTIMENT AGENT (Sentiment), FUNDAMENTAL AGENT (Fundamentals), QUANT AGENT (Quant Research), STRATEGY AGENT (Strategy).
- These feed a **SHARED MARKET STATE** (Price data · News & events · Sentiment data · Fundamental data · Strategy hypotheses) → DECISION ENGINE → RISK ENGINE (← RULES & CONSTRAINTS) → EXECUTION ENGINE → BROKER / MARKET. A loop reads "LEARN & IMPROVE".

**Slide 3, "01 — MARKET INTELLIGENCE LAYER":** "**UNDERSTAND THE MARKET FIRST.**" / "Three agents. One market state."
- 01 MARKET REGIME AGENT ("What market are we in?"): Trending or ranging · High or low volatility · Market phase detection · Regime shift alerts (screen tags TRENDING / RANGING / HIGH VOL / LOW VOL).
- 02 TECHNICAL AGENT ("What is price doing?"): Price structure · Momentum · Support / resistance · Volume analysis.
- 03 MULTI-TIMEFRAME AGENT ("Does the setup align?"): Higher timeframe trend · Trading timeframe setup · Lower timeframe entry · Multi-timeframe confluence (HTF / TTF / LTF).
- Output **MARKET STATE:** REGIME TRENDING · VOLATILITY MODERATE · DIRECTION BULLISH · ALIGNMENT STRONG.

**Slide 4, "04 — INFORMATION INTELLIGENCE LAYER":** "**TURN INFORMATION INTO CONTEXT.**" / "Three agents. One information state."
- 04 NEWS AGENT ("What just changed?"): Breaking news · Economic events · Company announcements · Real-time market updates (BREAKING NEWS / ECONOMIC CALENDAR / COMPANY UPDATES).
- 05 SENTIMENT AGENT ("How is the market reacting?"): News sentiment · Social sentiment · Market positioning · Fear / Greed signals.
- 06 FUNDAMENTAL AGENT ("Does the story support it?"): Earnings & financial data · Macro factors · Valuation metrics · Long-term growth drivers (EARNINGS / FINANCIALS / MACRO / VALUATION).
- Output **INFORMATION STATE:** NEWS FLOW · SENTIMENT · FUNDAMENTALS → POSITIVE / NEUTRAL / CAUTION / NEGATIVE.

**Slide 5, "07 — QUANT RESEARCH LAYER":** "**DOES THE IDEA HAVE A REAL EDGE?**" / "Turn data into evidence. Not opinions."
- INPUTS: Historical data · Market variables · Alternative data · Multiple timeframes.
- 07 QUANT AGENT screen: bell curve with **Win Rate 52.3% · Expectancy 0.42R · Sharpe 1.18 · Max DD −12.4%**.
- ANALYSIS: Statistical relationships · Factor analysis · Pattern detection · Probability modelling.
- HYPOTHESIS (Identify and define a testable idea.) → TEST (Backtest, analyze and validate.) → EVIDENCE (Clear metrics, not opinions.)

**Slide 6, "08 — STRATEGY LAYER":** "**TURN RESEARCH INTO RULES.**" / "Define, test and refine trading strategies."
- INPUTS: Market analysis (from agents) · Quant research results · Market regime & context · Your trading ideas.
- 08 STRATEGY AGENT (ENTRY → RULES → EXIT / FILTER).
- OUTPUT — CLEAR STRATEGY RULES: Entry conditions · Exit conditions · Position filters · Time / session rules · Instrument specific rules.
- RULES (Convert idea into rules.) → BACKTEST (Test on historical data.) → RESULTS (Analyze performance.) → REFINE (Improve and iterate.)

**Slide 7, "09 — RISK MANAGEMENT LAYER":** "**GOOD IDEAS NEED STRONG RISK RULES.**" / "Check risk before every trade."
- SIGNAL INPUT: Entry price · Stop-loss · Timeframe · Strategy type · Confidence score.
- 09 RISK ENGINE: Position size · Max risk per trade · Daily loss limit · Drawdown limit · Correlation check · Volatility adjustment.
- RISK RULES: Position sizing · Max exposure · Daily loss limit · Drawdown limit · Correlation check · Volatility filter.
- **BLOCKED** (Risk limit exceeded · High correlation · Volatility too high · Weak setup) / **APPROVED** (Risk within limits · Position size set · All rules passed · Send to execution) → EXECUTION ENGINE → BROKER MARKET.

**Slide 8, "10 — EXECUTION LAYER":** "**THE SYSTEM EXECUTES THE PLAN.**" / "From signal to position."
1. SIGNAL (Validated trading signal)
2. RISK CHECK (Position size · Risk limits · Exposure · Correlation)
3. ORDER (Market/Limit · Quantity · Order type · Slippage control)
4. BROKER API (Connect · Authenticate · Send order · Track status)
5. POSITION (Entry filled · Manage trade · Exit rules · Log & monitor)

These route to BROKER / MARKET (Stocks · Options · Futures · Forex · Crypto). Footer: AI RESEARCH (Finds opportunities) · CODED RULES (Control decisions) · CONTROLLED EXECUTION (Keeps you in the game).

**Slide 9, "09 — THE COMPLETE SYSTEM"** (the section number is repeated; it should be 09/10 overall): "**10 AI AGENTS. ONE TRADING SYSTEM.**" / "From data to decisions to execution."
- "01–08 AI AGENTS (RESEARCH & ANALYSIS)": MARKET REGIME, TECHNICAL, MULTI-TIMEFRAME, NEWS, SENTIMENT, FUNDAMENTAL, QUANT, STRATEGY. These feed MARKET INTELLIGENCE / INFORMATION INTELLIGENCE / QUANT RESEARCH.
- → 09 RISK ENGINE (Position sizing · Risk limits · Drawdown control · Correlation check) → 10 EXECUTION ENGINE (Order routing · Broker API · Slippage control · Position tracking) → BROKER / MARKET (Stocks · Options · Futures · Forex · Crypto).
- Side labels: DATA ANALYSIS RESEARCH STRATEGY / RISK MANAGEMENT / EXECUTION / REAL MARKET. Arrow: DISCOVER → ANALYZE → TEST → VALIDATE → CONTROL → EXECUTE → IMPROVE.

**Slide 10, "FROM CONCEPT TO EXECUTION":** "**SAME SYSTEM. REAL RESULTS.**" / "A repeatable, research-driven edge."
- DISCOVER (Find high probability ideas with data.) → BUILD (Test, validate and refine with AI.) → EXECUTE (Automate and follow rules.) → IMPROVE (Learn from results and iterate.)
- Monitors:
  - RESEARCH (Stocks, Options, Futures, Forex, Crypto)
  - BACKTEST (**Win Rate 52.3% · Sharpe 1.18 · Max DD −12.4%**)
  - LIVE EXECUTION table: AAPL BUY Executed · EURUSD SELL Executed · NIFTY BUY Executed · BTCUSD BUY Executed · RELIANCE SELL Executed.
- Books "IDEAS / DATA / SYSTEMS / DISCIPLINE / FREEDOM" and an "AZ" mug.
- CTA: "**COMMENT "AGENT"** TO GET THE COMPLETE GUIDE (PDF)". Footer: RESEARCH BACKTEST EXECUTE · AI AGENTS REAL DATA REAL DISCIPLINE · BETTER TRADING A BETTER YOU.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| 10 agents (Market Regime, Technical, Multi-Timeframe, News, Sentiment, Fundamental, Quant, Strategy, Risk Engine, Execution Engine) | architecture | caption, all slides | A generic design. No specific software, model or code is named. |
| Win Rate 52.3%, Expectancy 0.42R, Sharpe 1.18, Max DD −12.4% | numbers | slides 5, 10 | Mock dashboard values. No strategy, period or instrument is given. Not evidence. |
| AAPL, EURUSD, NIFTY, BTCUSD, RELIANCE | tickers | slide 10 | Decorative "live execution" rows (a US stock, an FX pair, an Indian index, BTC, Reliance Industries). |
| #ClaudeCode | hashtag | caption | Implies the system is built with Claude Code. Nothing on the slides shows it. |
| "AGENT" | comment keyword | caption, slide 10 | DM trigger for a "complete 10-agent AI Trading System blueprint" PDF. |

### What's being promoted / the funnel decoded
Comment "AGENT" leads to a DM with a PDF blueprint. No price is shown. This is the same creator and the same pattern as DdwnD3mkyxm and DeL4K4hk6k9 ("JEV") and Dd3gT_0k6hp ("100K" e-book): a small Indian algo-trading account growing followers and a DM list with free PDFs. No affiliate link or paid product is visible.

### Verification & insights
- **Known open-source equivalents of this exact idea** (verified clones in scratchpad/repos, not executed):
  - **TauricResearch/TradingAgents**: Apache-2.0, last commit 2026-10-16 (v0.7.0). Multi-agent LLM framework with fundamental, sentiment, news and technical analysts, bull/bear researchers, a trader and a risk-management team.
  - **virattt/ai-hedge-fund**: MIT, last commit 2026-10-02 (v2.5.0). Investor-persona agents plus a risk manager and a portfolio manager.

  These are the substantive versions of what the carousel sketches.
- **Sound design point:** "Use AI for research and analysis, deterministic rules for risk and execution" is the right separation, and matches the risk-engine checklists shown.
- **Misleading point:** slide 10's headline "SAME SYSTEM. REAL RESULTS." sits over illustrative metrics. No backtest, data source, cost assumptions or live record is provided. A 52.3% win rate with Sharpe 1.18 is unremarkable even if real.
- **Practical caveats:**
  - LLM news and sentiment agents add latency and cost, and their signals are hard to backtest without look-ahead (models may already "know" historical news).
  - Multi-agent setups multiply the number of tested variants, so overfitting risk rises.
  - For Indian brokers (NIFTY/RELIANCE examples), SEBI's retail algo framework requires broker-approved algos.
- **Slide errors:** the Quant pod is numbered "08" on slide 1, and the slide 9 section header reuses "09". The images are AI-generated.
- **Not verified:** the contents of the PDF.

---

<a id="e-dejurmglr-g"></a>

## DejuRmGlR_g | @nathanhodgson.ai | "Give Claude eyes": two unnamed Claude skills that download a video and extract frames so Claude can analyse visuals (comment "EYES")
- **Link:** https://www.instagram.com/p/DejuRmGlR_g/
- **Account:** @nathanhodgson.ai (display name not in data) · **Posted:** 2026-10-16 (decoded from the post ID) · **Type:** reel (39.1s, 19 pages)
- **Caption source:** possibly truncated (mirror). It is cut off at "can't actually see your footage or any…". yt-dlp got 429.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. Downloading a video with yt-dlp, extracting frames with ffmpeg and having Claude read the images is a real, working technique (the demo shows exactly that). The two skills are never named in the visible material, so they are hidden behind the DM. "Zero API costs" ignores that Claude's own usage (subscription or tokens) pays for reading the frames.

### Post description
> Claude Code has been working blind this whole time. Most people have no idea how much it's been missing.
>
> Comment "EYES" to get this.
>
> When you're building with Claude Code, it reads transcripts and text. But it can't actually see your footage or any…

(Cut off by the mirror.)

### Audio
The creator speaks to camera.
- [0.0–3.8] "You can now give Claude its own pair of eyes. Let me show you how."
- [3.8–9.5] "By default, Claude can only transcribe videos and therefore misses half of the visual detail."
- [9.5–18.8] "These **two Claude skills** fix that completely. The first one grabs the video, the second one then rips it frame by frame so Claude can analyze every single second of footage."
- [18.8–22.8] "Plus it works on reels, shorts, even **30 minute long videos**."
- [22.8–30.0] "It all runs **locally** on your machine too so there's **zero API costs**, no cloud uploads and no extra keys needed."
- [30.0–34.3] "You just install both skills and Claude can literally see everything that you can."
- [34.3–39.0] "So if you would like to check it out for yourself just comment **eyes** and I will send you the link."

### On-screen content, page by page
Word-by-word subtitles appear throughout ("you", "eyes", "let", …).
**Pages 1–4 (0–3.8s):** The creator to camera (cream jumper, lav mic).
**Page 5 (3.8–7.0s):** Purple background with the Claude desktop app start screen: "✳ Let's noodle", an empty prompt box, model selector "Sonnet 5" (small).
**Pages 6–7 (7.0–9.5s):** A Claude chat ("Video analysis") beside a browser: Claude's answer describes "Thinking Mode best practices" and "Interact with Claude" slides from a YouTube video; on the right, a YouTube page "Getting started with Claude.ai" (Anthropic) and a thumbnail "HOW TO USE CLAUDE AI".
**Page 8 (9.5–11.9s):** Purple transition ("these").
**Page 9 (11.9–13.4s):** Claude Code session "Video analysis" (Windows path "D:"). Text: "yt-dlp and ffmpeg aren't installed on this machine. Want me to install them via winget so I can download the video and extract frames?" → "Yes, install via winget" → "Installed yt-dlp and ffmpeg via winget" → "Both installed (yt-dlp was already present, ffmpeg just got installed). PATH needs a fresh shell session — let me locate the binaries directly and download the video." → "Found both. Now downloading the video into the scratchpad." A blurred PowerShell block follows.
**Pages 10–11 (13.4–15.6s):** "Video and audio downloaded separately (ffmpeg wasn't yet in PATH for yt-dlp to merge, but I don't need audio for frames). Now extracting frames using the explicit ffmpeg path." "Confirmed: 5:18 duration, 1280x720. Now extracting one frame every 15 seconds for a frame-by-frame overview." "Extracted one frame every 15 seconds", then "frames extracted (one every 15s). Let me look at a few to identify the visually distinct/representative ones before showing examples." "Read frame_001.png". A frame image (a blank Google Doc page) and "Good, matches the "blank page" opening line. Let me look through the rest of the frames."
**Pages 12–13 (15.6–22.8s):** Purple/black transitions ("so", "plus").
**Pages 14–15, 18–19 (22.8–39.1s):** The creator to camera; the last page has a frowning expression ("just").
**Pages 16–17 (~30–34s):** A Claude chat with a pasted youtu.be link and "analyze this video". Claude: "WebFetch couldn't pull the actual page content (YouTube is JS-heavy). Let me try loading it in the browser instead." … "I pulled the video's metadata directly from YouTube. Full closed captions aren't available for this video, so I can't quote a scene-by-scene transcript, but here's the analysis based on its title, description, and structure." Right side: YouTube "Getting started with Claude.ai", channel Anthropic, ~7.2K likes, "2M views 8 months ago". This is the "before" (blind) case.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "Two Claude skills" (unnamed) | skills | audio 9.5s | Not named in the video or the visible caption. Similar public option: **bradautomates/claude-video** ("/watch", MIT, last commit 2026-09-25), which turns a URL or local file into timestamped frames plus a transcript for Claude Code. It may or may not be what he sends. |
| yt-dlp | tool | page 9 | Free open-source video downloader (Unlicense) |
| ffmpeg | tool | pages 9–10 | Free open-source media toolkit (LGPL/GPL) |
| winget | tool | page 9 | Windows package manager |
| Claude Code / Claude desktop (Sonnet 5) | app | pages 5–17 | Anthropic's products |
| "Getting started with Claude.ai" | YouTube video | pages 6–7, 17 | Anthropic's official tutorial used as the test video |
| 5:18 duration, 1280x720, 1 frame / 15s | numbers | page 10 | Demo parameters |
| EYES | comment keyword | caption, audio 36s | DM automation |

### What's being promoted / the funnel decoded
Comment "EYES" to get a DM with the link to the two skills; the creator collects engagement and DMs (likely a lead list for a newsletter or community). A web search found nothing on nathanhodgson.ai's offers, so there is no evidence of a price. The capability itself can be obtained without the DM (claude-video, or simply asking Claude Code to use yt-dlp and ffmpeg, as the demo shows).

### Verification & insights
- The existing clone of bradautomates/claude-video was checked: MIT, last commit 2026-09-25 "chore: release 0.3.2". Per its README it works in Claude Code (desktop Code tab, VS Code, terminal), not in plain Claude chat.
- **Claims vs reality:**
  - "By default Claude can only transcribe videos": Claude chat doesn't natively ingest video. The demo's "blind" case is actually Claude reading metadata only, since there were no captions.
  - "Every single second of footage": the demo extracted **one frame every 15 seconds** (≈21 frames for 5:18), not every second. A 30-minute video at 1 fps would be 1,800 images, which is costly in context and tokens.
  - "Zero API costs, no keys": the download and extraction are local and free, but Claude reading images consumes plan usage or API tokens.
  - Downloading YouTube or Instagram videos with yt-dlp can breach those platforms' Terms of Service; fine for your own content.
- **Could not verify:** the names of the two skills; the rest of the caption.

---

<a id="e-dekcpukh1du"></a>

## DekCPuKh1Du | @mikeeshattuck | Car selfie rant: "cancel Claude Code and Codex, use free freebuff.com or opencode.ai", plus a "DM me your workflow" engagement CTA
- **Link:** https://www.instagram.com/p/DekCPuKh1Du/
- **Account:** @mikeeshattuck (Mikee Shattuck) · **Posted:** 2026-10-16 · **Type:** reel (80.5s, 3 scene pages)
- **Caption source:** full (Instagram)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. Freebuff and OpenCode are real and free to use. But "100% free with the best models out there" overstates it: Freebuff runs ad-supported open-weight models, and OpenCode is free software where you still pay for, or bring, the model. "Cancel Claude Code / Codex" is opinion. The CTA collects detailed descriptions of viewers' work in comments and DMs.

### Post description
> 👇 Want AI doing your computer work?
>
> Tell me exactly how you do your work on your computer, and I'll show you how to get AI to do it for you.

- Asks for step-by-step detail via six bullet questions: the task done most; which programs, tabs and tools are opened; what is clicked, copied, pasted, typed and sent; where the info comes from and goes; how long it takes and how often; and "Which part makes you want to throw your laptop out the window?"
- Promise: more detail gets a more detailed reply on exactly how to hand the work to AI "while you do literally anything else."
- CTA: "Comment below or DM me. Don't be shy and don't leave anything out"; even boring, repetitive tasks are what AI is best at. "I'll personally reply with a step-by-step plan for your exact workflow. 🤖"
- Tags: #AI #Automation #ClaudeCode #WorkSmarter #AIAutomation, plus "BuiltNotRented" without "#".

*Caption condensed – full text is on the original post.*

### Audio
The creator speaks to camera while sitting in a car. Whisper wrote "Cancel your cloud, though. Cancel codecs"; in context this is "Cancel your Claude Code. Cancel Codex." Condensed into timestamped notes:
- [0.0–9.0] Hook: "we got a tiny window, maybe a year or two, but AI can do all your work on a computer"; anyone working on a computer "must do this."
- [9.0–18.1] "Cancel your Claude Code. Cancel Codex." He calls them old news that won't survive, and says there are free apps.
- [18.1–28.5] The apps: **freebuff.com** or **opencode.ai**, "**100% free with the best models out there**. They will do all your work."
- [28.5–44.7] Offer: comment or DM what your computer work is, and he will explain "very quickly and very easily and very simply how to get AI to do it all."
- [44.7–69.9] If you are clicking buttons on a computer, AI should do it while you monitor, so you can go to Magic Kingdom, Disney World, hiking or the beach.
- [69.9–80.2] Repeated CTA: comment or DM; "I hold nothing back."

### On-screen content, page by page
**Page 1 (0.0–58.8s):** selfie video in a car. Top label: "**The open source AI window**".
**Page 2 (58.8–61.1s):** same label, plus subtitle "go to Magic Kingdom Go to Disney World go hiking, go to the beach, whatever".
**Page 3 (61.1–80.5s):** same (camera shake). No other on-screen text, links or prices.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| freebuff.com (Freebuff) | site / CLI coding agent | audio 18s | Free, ad-supported version of Codebuff (open-source terminal coding agent by Manicode / James Grugett, YC F24). Install with `npm i -g freebuff`. Uses open-weight models (reviews list e.g. DeepSeek, MiniMax, MiMo), which vary by region. Not "the best models", and ads fund it. |
| opencode.ai (OpenCode) | site / open-source coding agent | audio 18s | Open-source terminal/desktop coding agent. The software is free, but you connect your own model provider or paid plan. It offers some free models for limited periods. Frontier models are not free. |
| Claude Code, Codex | products | audio 9s | Anthropic's and OpenAI's coding agents. He says to cancel them (opinion) |
| "BuiltNotRented" | tag | caption | Appears to be his slogan or brand; nothing linked |
| Magic Kingdom / Disney World | — | audio, p2 | Lifestyle imagery only |

### What's being promoted / the funnel decoded
No product is shown. The CTA asks viewers to comment or DM a detailed, step-by-step description of their computer work (tools, data sources, what they copy and paste), with a promise of a "personally" written plan. This works as engagement bait and lead generation. Some of that detail could be sensitive work or employer information. Searches found no public offer, price or bio-link product for the account, so whatever follows the DM (consulting or a paid offer) is unverified. You don't need to engage: the two tools he names are freebuff.com and opencode.ai.

### Verification & insights
- Web search confirmed Freebuff (Codebuff's free, ad-supported tier) and OpenCode exist as described above.
- "100% free with the best models": misleading. Free tiers run open-weight models with rate limits or ads. Top proprietary models need paid access.
- "Cancel Claude Code/Codex… won't survive": unsupported opinion.
- "AI can do all your work while you go to Disney World": hype. Agents still need supervision, which he concedes ("you just monitor it").
- Privacy: don't post detailed workflow, client or employer specifics publicly.
- Couldn't verify: any paid offer behind the DMs.

---

<a id="e-dc-nhfob3-r"></a>

## Dc-nHfOB3_r | @sadie.ontech | Hype explainer of Google's TimesFM time-series forecasting model ("predict stock prices, weather, energy demand")
- **Link:** https://www.instagram.com/p/Dc-nHfOB3_r/
- **Account:** @sadie.ontech · **Posted:** unknown (not in metadata; Instagram re-fetch got 429) · **Type:** reel (47s, 29 pages)
- **Caption source:** full (Instagram, fetched after the first review)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. TimesFM is a real, free, open-source Google Research model, but the reel is stale ("just released"; it dates from 2023–24 and is now at v3.0), overclaims ("predict literally anything", stock prices), and gets the origin story wrong.

### Post description
> Google released TimesFM, an open source model that forecasts any time series data with zero fine-tuning needed. Pre-trained on massive real-world datasets, it predicts stock prices, weather patterns, energy demand, and more right out of the box. #GoogleAI #TimesFM #TimeSeriesForecasting #MachineLearning #OpenSourceAI

### Audio
English voice-over by an on-camera presenter (a man in a grey shirt in a studio set; the style suggests a possibly AI-generated avatar, unconfirmed):
- [0.0–2.3] "What if you could predict the future?"
- [2.3–8.6] "Google just released Times FM, an open source model that lets you forecast literally anything over time."
- [8.6–15.3] "Stock prices, energy demand, weather patterns, retail sales, if it's a time series, this model can predict it."
- [15.3–23.7] "And here's what makes it wild. It was pre-trained on a massive data set of real world time series data, so it works out of the box, zero fine tuning needed."
- [23.7–27.4] "You just feed it your historical data and it tells you what's coming next."
- [27.4–33.3] "Google built this for internal use first and it was so powerful they decided to open source it for everyone."
- [33.3–37.4] "Researchers, developers, businesses, anyone can use it right now."
- [37.4–42.4] "We're talking about a foundation model for time, the same way GPT is a foundation model for language."
- [42.4–47.5] "This is a huge deal. Go check out Times FM on GitHub and start predicting your future today."

### On-screen content, page by page
(Grey caption pills repeat the narration's keywords. The images are mostly illustrated, AI-style B-roll.)
**Pages 1–4 (0.0–2.2s):** split screen. Top: a slide "TimesFM: A Decoder-Only Foundation Model for Time-Series Forecasting – Bringing the zero-shot generalization of Large Language Models to the world of forecasting." with stat chips "200M Parameters · 100B Training Time-Points · Zero-Shot Inference" and a "Raw Time-Series Data (Noisy)" curve. Bottom: the presenter. Pill: "WHAT IF YOU COULD PREDICT THE FUTURE?"
**Pages 5–6 (~2.2–7s):** a sketch "CHAOS INPUT → [filter] → ALIGNMENT PROCESS" turning tangled coloured lines into an ordered ribbon of data. Pills "JUST RELEASED TIMES", "FROM AN", "OPEN", "OPEN SOURCE MODEL", "THAT LETS", "YOU FORECAST", "LITERALLY".
**Pages 7–8 (~8–12s):** "TimesFM 2.0" in a serif font over 3D cubes, with an animated counter "4xx → 500 Million Parameters". Pills "ANYTHING OVER TIME", "STOCK", "STOCK PRICES".
**Page 9 (12.2–15.1s):** a hand-drawn multi-line chart. Pill "RETAIL SALES".
**Page 10 (15.1–20.7s):** blur transition. Pill "CAN PREDICT IT".
**Pages 11–13 (20.7–27s):** a progress-bar graphic and the presenter. Pill "TIME SERIES DATA".
**Pages 14–16 (~27–29s):** an illustrated chip with coloured input bars and a 3D waveform chart. Pill "WHAT'S COMING NEXT".
**Pages 17–22 (29.3–33s):** an illustrated server rack with cables. Pill "USE FIRST"; then a blue light beam into the rack.
**Page 23 (33.1–37.2s):** streak transition. Pill "FOR EVERYONE".
**Pages 24–25 (37.2–40.5s):** an illustrated spreadsheet titled "TimesFM" with numeric columns (meaningless filler numbers) above the presenter. Pill "RIGHT NOW".
**Pages 26–27 (40.5–43.6s):** an illustrated red cube on a conveyor, labelled "…ALIGNMENT PROCESS". Pill "THE SAME WAY GPT".
**Pages 28–29 (43.6–47.1s):** a sketched code snippet "configuration { target-vest-co… normalize-x… normalize-x… target-input" (pseudo-code, not real TimesFM API). Pill "DEAL".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| TimesFM | repo/model | caption, audio, pages 1–8, 24 | github.com/google-research/timesfm, **Apache-2.0** code. Last commit 2026-09-29 (e51928e). Paper "A decoder-only foundation model for time-series forecasting" (arXiv 2310.10688, ICML 2024). Latest: **TimesFM 3.0** (Aug 2026: multivariate, covariates). Its **weights are non-commercial only** (timesfm-non-commercial-license-v1.0); weights up to 2.5 are Apache-2.0. Commercial use of 3.0 goes via BigQuery ML / Google Cloud |
| "200M parameters / 100B training time-points" | numbers | page 1 | Matches TimesFM 1.0 (~200M params, ~100B time-points) |
| "TimesFM 2.0 … 500 Million Parameters" | numbers | pages 7–8 | TimesFM 2.0 = 500M; 2.5 went back down to 200M with 16k context |
| Stock prices, energy demand, weather, retail sales | use-case claims | audio, caption | Generic forecasting; see below |
| #GoogleAI #TimesFM #TimeSeriesForecasting #MachineLearning #OpenSourceAI | hashtags | caption | Topic tags only |
| GitHub | site | audio 43.8s | The repo above |
| @sadie.ontech | handle | account | AI/tech explainer account; no CTA or product in this post |

### What's being promoted / the funnel decoded
No CTA, product or link; it is a pure engagement explainer pointing to the free GitHub repo. No affiliate signs.

### Verification & insights
- Shallow clone of google-research/timesfm into scratchpad/repos/timesfm: LICENSE Apache-2.0; README read; code not executed.
- "Just released": false as of the post. TimesFM was announced in 2023–24; v2.0 (Dec 2024), v2.5 (Sep 2025) and v3.0 (Aug 2026) followed.
- "Built for internal use first … so powerful they decided to open source it": not supported. It was published as a research paper with open weights; Google products (BigQuery ML, Sheets, Vertex) came afterwards.
- "Zero fine-tuning needed": zero-shot works and benchmarks well (the repo claims #1 on fev-bench, TIME and GIFT-Eval for 3.0), but fine-tuning is supported and often helps.
- "Predicts stock prices": a forecasting model can extrapolate any series, but there is no evidence it beats a random walk on liquid asset prices. Treating its output as a trading signal is unproven, and the hype framing ("predict your future") is misleading for markets.
- Commercial users: the 3.0 self-hosted weights cannot be used commercially or in production.
- Related: other repos in scratchpad/repos (e.g. Kronos, a financial candlestick foundation model) cover similar "time-series foundation model for markets" posts.
- Full caption (fetched later): only the hashtags are new; the claims are the same as in the narration.
- Could not verify: the post date.

---

<a id="e-da5be6dj6fi"></a>

## Da5be6dJ6Fi | @petergriffin.ai | Peter/Stewie (Family Guy AI voices) skit hyping Ruflo (formerly Claude Flow): 60+ agents, shared memory, model routing, "250% more Claude Code usage"
- **Link:** https://www.instagram.com/p/Da5be6dJ6Fi/
- **Account:** @petergriffin.ai (display name not retrieved) · **Posted:** not retrieved (Instagram returned HTTP 429) · **Type:** reel (66.3s, 70 scene pages)
- **Caption source:** full (Instagram, fetched after the first review)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. Ruflo/claude-flow is real, free and MIT-licensed. "Ranked #1 on GitHub" is unverified hype, and the "cut tokens 50% / extend usage 250%" figures are the project's own unbenchmarked marketing. The CTA funnels to a Telegram/broadcast channel.

### Post description
> This open-source project is currently ranked 1 on GitHub, and it's changing how people use AI for coding and complex tasks. Instead of relying on a single AI, Ruflow coordinates 60+ AI agents that collaborate on research, coding, testing, and reviews while continuously improving through shared memory.
>
> […] helping reduce token costs by up to 50% and extend Claude Code usage by up to 250%. […]
>
> Comment "Ruflow" below, and I'll DM you the link.

The rest of the caption, in summary:
- It says Ruflow "intelligently routes each task to the most suitable AI model", which is what produces the token-cost and usage figures above.
- It calls the project "completely free and open source".
- A bracketed SEO keyword block follows: Ruflow, GitHub trending, AI agents, Claude Code, multi-agent AI, open source AI, AI coding assistant, GitHub projects, AI automation, coding tools, developer tools, artificial intelligence, software development, GitHub AI.
- Hashtags: #claude #claudeai #github #coding #programming
- Note that the caption spells the name "Ruflow"; the project is **Ruflo**.

*Caption condensed – full text is on the original post.*

### Audio
A scripted dialogue between AI-cloned voices of Peter Griffin (P) and Stewie Griffin (S) from *Family Guy*, over Minecraft Nether parkour footage. This is AI voice impersonation of copyrighted cartoon characters, not the creator's own voice. Whisper wrote "RooFlo"; the product is **Ruflo**.
- [0.0–6.2] P hook: "This thing is rank number one on GitHub right now. It's completely free and almost nobody knows about it." S asks if it's really #1 and free.
- [6.2–19.6] P: it's called Ruflo; it spins up 60+ AI agents that work together to build whatever you want and "get better after every single run". S: so it's an actual team, not one AI?
- [19.6–36.2] P: queen agents manage the teams and tactical agents do the work (researching, coding, testing, reviewing). S jokes they work while he plays video games. P: they share a collective memory and improve over time; S jokes it won't forget his name the next day.
- [36.2–50.7] P: it judges task complexity and routes it to the right model automatically (simple → cheap model, complicated → powerful one), so you can "cut your token usage by up to 50% and extend your Claude Code usage by 250%".
- [50.7–59.8] S: "250% more usage for less money", basically paying him to use it. P repeats: open source, completely free, ranked #1 on GitHub.
- [59.8–66.1] S asks how to get the link. P (CTA): "just join my broadcast channel or check my telegram from bio."

### On-screen content, page by page
The bottom half shows a Peter or Stewie cutout over Minecraft parkour. The middle has word-by-word captions (cyan/white) that repeat the speech. Inserted images appear in the top half:
**Pages 1–5 (0–3.6s):** Minecraft Nether plus Peter; "THIS THING IS", "AND ALMOST NOBODY".
**Page 6 (3.6–3.9s):** GitHub repo file list for **ruvnet/ruflo** (folders agents, .claude-plugin, .claude, .githooks, .github…; commits by "ruvnet and Reuven"). Tabs: Actions, Projects, Wiki, Security and quality, Insights. "201 Branches", "1463 Tags".
**Pages 7–8 (3.9–4.6s):** README: "RuFlo v3.5: Enterprise AI Orchestration Platform" with a neon "Ruflo" sign logo; tabs README, MIT license, Security.
**Page 9 (4.6–4.7s):** README feature list: "Agent Booster (WASM) — Skip LLM for simple code transforms" / "Token Optimizer — reduces token usage via pattern caching and smart routing" / "Anti-Drift Swarm Configuration — Prevent goal drift in multi-agent work" / heading "Claude Code: With vs Without Ruflo".
**Page 10 (4.7s):** Comparison table, Capability | Claude Code Alone | Claude Code + Ruflo:
- Agent Collaboration | Agents work in isolation, no shared context | Agents collaborate via swarms with shared memory and consensus
- Coordination | Manual orchestration between tasks | Queen-led hierarchy with 3 consensus algorithms (Raft, Byzantine, Gossip)
- Hive Mind | Not available | Queen-led swarms with collective intelligence, 3 queen types, 8 worker types
- Consensus | No multi-agent decisions | Byzantine fault-tolerant voting (f < n/3), weighted, majority
- Memory | Session-only, no persistence | HNSW vector memory with sub-ms retrieval + knowledge graph
- Vector Database | No native support | RuVector PostgreSQL with 77+ SQL functions, ~61µs search, 16,400 QPS
- Knowledge Graph | Flat insight lists | PageRank + community detection identifies influential insights (ADR-049)
- Collective Memory | No shared knowledge | Shared knowledge base with LRU cache, SQLite persistence, 8 memory types
- Learning | Static behavior, no adaptation | SONA self-learning with sub-millisecond pattern matching…
**Pages 11–15 (4.7–7.4s):** Stewie: "WAIT IT'S RANKED", "NUMBER ONE AND"; Peter: "IT'S CALLED RUFLO".
**Pages 16–17 (6.6–8.2s):** Neon "Ruflo" sign logo; "AND BASICALLY".
**Page 19 (8.7–11.3s):** Card "60+ Specialized Agents — Coordinated swarms with 5 consensus protocols — Deploy ready-to-use AI agents for coding, review, testing, security, and DevOps. Queen-led hierarchy with 8 worker types".
**Page 22 (11.6–14.0s):** Unrelated stock website mockup ("REFRESHIN[G]" drink-can landing page), used as a filler "build whatever you want" visual.
**Pages 24–25 (14.2–16.0s):** Terminal "claude-flow@v3: ~": "Ok to proceed? (y) y" / "Initializing Claude Flow v3 with RuVector Intelligence" / "✓ Created CLAUDE.md (Claude Flow v3 …" / "✓ Configured 6 LLM providers with automatic failover" / "✓ Loaded 170+ MCP tools for Claude Code integration" / "✓ Created 42+ skill definitions" / "✓ Created 17 intelligent hooks" / "✓ Created 60+ specialized agent configs" / "✓ Initialized SONA self-learning system" / "✓ Initialized memory database with HNSW (150x faster)" / "[2026-01-24T15:26:22.719Z] INFO [ruvector] Initialized Pos[tgres]…" / "✓ RuVector: 77+ SQL functions, ~61µs search, 16,400 QPS".
**Pages 26–35 (16–30s):** Captions "60 AGENTS SO", "TEAM EXACTLY", "THE ACTUAL WORK", "ALL OF IT", "THAT'S CRAZY".
**Pages 36–37 (28.7–30.4s):** Meme of a man in sunglasses typing on a toy laptop; "SO THEY CAN", "GAMES".
**Pages 39–40 (31.2–33.6s):** Hand-drawn diagram "Shared Memory Multi-Agent" (AI agents around a centralized memory space; "Memory Consistency Challenges"). Captions "ALL SHARE A", "COLLECTIVE MEMORY".
**Pages 41–43 (33.6–36.4s):** "FINALLY SHARED MEMORY", with a smiling-robot meme.
**Pages 44–47 (36.4–40s):** "HERE'S THE THING", "HOW COMPLEX YOUR".
**Page 48 (40.0–41.4s):** Diagram "Routing: How AI Agents Make Decisions" (Router → Chain A / Chain B / Chain C / Escalate). Caption "AND ROUTES IT".
**Page 49 (41.4–45.5s):** Neon two-column graphic "Simple task" | … Caption "MODEL AUTOMATICALLY".
**Pages 50–52 (45.5–47.9s):** Terminal "CLAUDE TOKEN MONITOR": Token Usage bar 53.8%, Time to Reset 2h 58m, "Tokens: 18,838 / ~35,000 (16,162 left)", "Burn Rate: 156.4 tokens/min", "Predicted End: 23:00", "Token Reset: 00:16", "Tokens will run out BEFORE reset!". Overlay "Reduce token usage upto 50%". Captions "SO YOU CAN", "CUT YOUR TOKEN", "TO 50%".
**Pages 53–55 (47.9–51.6s):** Claude logo card "Extent [sic] claude usage by 250%". Captions "AND EXTEND YOUR", "CLAUDE CODE USAGE", "THAT'S INSANE 250%".
**Pages 61–64 (55.8–59.8s):** GitHub ruflo repo file list with green "Open source" label. Captions "AND THE CRAZY", "PART IT'S OPEN", "ON GITHUB".
**Pages 66–70 (60–66.3s):** "AWESOME THIS IS", "EXACTLY WHAT I", "GET THE LINK", "SIMPLE", "CHECK MY TELEGRAM".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Ruflo / RuFlo v3.5 (github.com/ruvnet/ruflo; also reachable as ruvnet/claude-flow) | repo | caption, audio 6.2s, pages 6–10, 61–64 | Exists. MIT, © 2024–2026 ruvnet (Reuven Cohen). npm package name **claude-flow**, v3.59.2. HEAD 2276232, 2026-10-20. ruvnet/claude-flow resolves to the same HEAD. The README now says **"100+ specialized agents"** (98 agents, 60+ commands, 30 skills in the full install). |
| "Ranked #1 on GitHub" | claim | caption, audio 0.0s, 55.7s | Not supported. No such ranking appears in the README. At most it may have trended on some day. |
| 60+ agents, queen/worker hierarchy, Raft/Byzantine/Gossip consensus, HNSW memory, RuVector Postgres (77+ SQL functions, ~61µs, 16,400 QPS), SONA self-learning | features/numbers | pages 9–10, 19, 24–25 | All copied from Ruflo's own README/CLI output. Self-reported performance figures. |
| "Cut token usage up to 50%", "extend Claude Code usage by 250%" | claim | audio 45–50s, pages 52–55 | From Ruflo's docs/USERGUIDE.md: "Extend your Claude Code subscription by 250%" via smart routing (WASM for simple edits, cheaper models for medium tasks). Elsewhere the same doc says "30–50% cost savings" and "75% lower costs". These are inconsistent, unbenchmarked marketing numbers. |
| "CLAUDE TOKEN MONITOR" terminal | tool | pages 50–52 | Appears to be a separate open-source Claude Code usage-monitor CLI, not Ruflo. Used as an illustration. |
| Comment "Ruflow" → DM | CTA | caption | Comment-to-DM keyword automation; the "link" is the public GitHub URL |
| Keyword block ("[keywords: Ruflow, GitHub trending, …]") | SEO text | caption | Search-bait keyword stuffing, no extra information |
| Telegram / "broadcast channel" in bio | CTA | audio 62.8s, page 70 | The creator's Telegram/IG broadcast channel. Link not retrieved. |
| Family Guy characters (Peter, Stewie Griffin) | IP | whole video | AI voice/likeness of Fox's copyrighted characters |

### What's being promoted / the funnel decoded
- The repo itself is free on GitHub (github.com/ruvnet/ruflo). The "link" is just that URL.
- There are two different CTAs. The caption says to comment "Ruflow" for a DM (keyword auto-DM, which grows comment engagement). The audio says to join the broadcast channel or the Telegram in the bio. The audio CTA ("join my broadcast channel or check my telegram from bio") exists to grow the account's Telegram/IG broadcast audience, which is typically later monetized with promos or other links.
- The account (@petergriffin.ai) is a faceless "AI cartoon voices explain tech" page. No product or price was found, and web searches turned up nothing on the account.

### Verification & insights
- Clone of ruvnet/ruflo: LICENSE MIT; package.json name "claude-flow"; last commit 2026-10-20 "release: 3.59.2". No code was run.
- **Claims vs reality:**
  - "Free, open source": true (MIT).
  - "#1 on GitHub": unverified hype.
  - "60+ agents… get better every run": the agents are prompt/config definitions orchestrated around Claude Code. "Self-learning" (SONA) is the project's own label. No independent evaluation was found.
  - "250% more usage": a routing claim from the project's own guide. Real savings depend entirely on how many tasks can be routed to cheaper models or skipped. Note too that running many agents in parallel can *increase* total token use.
- **Practical caution:** installation creates CLAUDE.md, 17 hooks and 170+ MCP tools in your project (per the CLI output shown). That is a large, invasive footprint for a coding environment; review before installing.
- The full caption (fetched later) repeats the same claims ("ranked 1 on GitHub", 60+ agents, up to 50% lower token costs, up to 250% more Claude Code usage, free and open source) and adds a comment-to-DM CTA. Nothing in it changes the verdict.
- **Not verified:** upload date, account display name, the Telegram link.

---

<a id="e-deh0mi5yisc"></a>

## Deh0mi5yISC | @samdespomarketing | News recap of Anthropic's "Claude Dashboards" (live-data dashboards from connected warehouses/CRM) and "Claude Motion" (animated report videos), launched in beta on 8 Oct 2026
- **Link:** https://www.instagram.com/p/Deh0mi5yISC/
- **Account:** @samdespomarketing (display name not in data) · **Posted:** 2026-10-15 (decoded from the post ID) · **Type:** reel (44.5s, 11 scene pages; talking head with inset product clips)
- **Caption source:** possibly truncated (mirror). It is cut inside the hashtags; the yt-dlp full-caption fetch returned HTTP 429.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. Both features are real and launched in beta on 8 Oct 2026, and the description of live updates, click-to-edit and one-click export matches the coverage. Inaccuracies: per secondary coverage, Dashboards is on paid plans generally (not only Team/Enterprise), Motion is Team/Enterprise only, and "released to personal very soon" was not confirmed. "Why is nobody talking about this?" is hype; the launch was widely covered.

### Post description
> Claude released Dashboards and Motion which change the way we interact with our data. It's currently in beta so they're available on enterprise and team plans, but Claude said they will be released to personal very soon 
>
> #claude #claudeupdate #claud...

(cut off by the mirror; the remaining hashtags could not be retrieved because Instagram returned 429)

### Audio
The creator speaks to camera (English). Full transcript:
- [0.0–6.1] "Claude just released two major updates and why is nobody talking about this? The first one is called Claude Dashboards and this is literally game changing."
- [6.1–20.7] "If you connect your data into Claude through any tool like AWS, BigQuery or Salesforce, you can then prompt Claude to build these interactive dashboards where you can fully customize everything. But the best part is all of your data stays live so if the dashboard changes because something changes in your data then it automatically updates."
- [20.7–44.2] "Then the next major update is Claude Motion and this is where Claude can turn boring reports into these interactive narrative videos. Now it's so easy to use: either upload a report or from your dashboard prompt Claude to create an animation and these look amazing. But the best part is if you want to edit anything just click on the video and tell Claude what you want to change, or you can manually change anything just by clicking on numbers or text, and once you're done export with a single click or you can share it straight to your design tool."

### On-screen content, page by page
Captions in white repeat the speech.
**Pages 1–3 (0.0–6.1s):** Talking head (office background) with the header "✱ Claude – **Claude released major updates that change everything** 🚨". Captions: "Claude just released two major updates", "The first one's called Claude Dashboards".
**Page 4 (6.1–7.1s):** Inset card: a database icon → "✱ Claude", "**Connect your data**".
**Page 5 (7.1–10.5s):** A row of six data-source logos: AWS, BigQuery (magnifier-chart icon), ClickHouse (yellow bars), Databricks, Salesforce, Snowflake. Caption: "through any tool like AWS, BigQuery or Salesforce".
**Pages 6–7 (10.5–28.0s):** An inset Claude screen-recording: a chat on the left builds a dashboard titled "**System overview**" with KPI tiles (≈445K, 2,999, 21%, 4,200, 77%, 92), line charts, histograms, a scatter/bubble map and a horizontal bar chart. Captions: "to build these interactive dashboards", "where you can fully customise everything", "The best part is all of your data stays live", "then it automatically updates". A "**Claude Motion**" label appears at about 26s.
**Page 8 (28.0–32.0s):** The inset dashboard again. Caption: "Either upload a report or from your dashboard".
**Page 9 (32.0–37.3s):** A Motion animation: a 3-D isometric city map with bike-dock markers, the label "**6:25 am**" and a "**Fernhill – 20 bikes**" tooltip (a bike-share demo). Caption: "And these look amazing."
**Page 10 (37.3–40.5s):** The Motion editor with an animated scene (trees, a bike-dock icon), titled "…the morning rush", with a "Share" button and an "All comments" panel. It shows three short collaborator comments from a sample demo team about renaming a route, reusing "the 4,200" figure on a slide, and holding a shot longer. Caption: "Or you can manually change anything".
**Page 11 (40.5–44.5s):** A cursor clicking an orange export-style button. Caption: "just by clicking on numbers or text."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude Dashboards | Anthropic feature | caption; audio 3s; pages 3–8 | Real. Launched in beta 8 Oct 2026 (tbreak, The New Stack, others). It builds dashboards on live connected data, each chart shows its last refresh, and clicking a number shows the underlying query. Connectors: Amazon Redshift, BigQuery, ClickHouse, Databricks, Snowflake, plus Salesforce. Dashboards can be sent to Amplitude, Grafana, Hex, Mixpanel, Omni, Perplexity, PostHog and Sigma; Looker, monday.com and Tableau are "coming soon". Availability: "beta on paid plans". |
| Claude Motion | Anthropic feature | caption; audio 20.7s; pages 7–11 | Real. Launched in beta 8 Oct 2026, **Team and Enterprise only**. It generates animated explainer videos by writing animation code (not a video-generation model). You edit by prompting or directly (any word, number or timing), download as MP4, and can open in Adobe, Descript, HeyGen, Higgsfield, invideo, Luma AI and Runway, with Canva and Captions "coming soon". |
| AWS, BigQuery, Salesforce (audio); ClickHouse, Databricks, Snowflake (logos) | data platforms | audio 6–10s; page 5 | Supported sources per coverage. "AWS" here means Amazon Redshift. |
| "Released to personal very soon" | claim | caption | Not confirmed in the coverage found. Dashboards already appears to cover paid individual plans (one source says Pro/Max with a data connection); no Motion date for Pro/Max was found. |
| "System overview" dashboard, "Fernhill – 20 bikes", "6:25 am", "4,200" | demo content | pages 6–10 | Sample/demo assets (bike-share example), apparently from Anthropic's launch materials. |
| Related: Docs, Slides, Design out of beta | context | not in post | Same 8 Oct announcement: these are now on all plans, including Free. Artifacts gained customer-managed encryption keys. |
| @samdespomarketing | handle | account | Marketing creator. No product promoted in this post. |

### What's being promoted / the funnel decoded
- No CTA, link or product in the video or the visible caption. It is a news/update reel that builds the creator's audience. The account name suggests a marketing service or agency, but nothing is sold here.

### Verification & insights
- Checked by web search and by fetching tbreak.com coverage: launch date 8 Oct 2026; Dashboards on paid plans in beta; Motion on Team/Enterprise only; Enterprise admins must enable both under Organization settings → Artifacts; on Team/Enterprise, dashboards stay inside the organization unless an owner enables external sharing.
- Claims vs reality:
  - "Connect through any tool like AWS, BigQuery or Salesforce": true for the listed connectors, but not "any tool".
  - "Data stays live / automatically updates": true per coverage.
  - "Click on numbers or text to change; export with one click or share to your design tool": true (MP4 export; open in Adobe and others; Canva coming soon).
  - "Only Team/Enterprise": correct for Motion, but too narrow for Dashboards.
  - "Nobody is talking about this": false; there was broad coverage.
- Not verified: Anthropic's own announcement page (only secondary coverage was read), the "personal plans very soon" statement, and the full hashtag list.

---

<a id="e-dcgovk9swpi"></a>

## DcgoVk9SwPi | @cjtrowbridge | Creator reacts to Alibaba's open-weights Qwen3.8-Flash-Next (125B MoE, 6B active) over Qwen's own benchmark table
- **Link:** https://www.instagram.com/p/DcgoVk9SwPi/
- **Account:** @cjtrowbridge (CJ Trowbridge) · **Posted:** unknown (not in metadata; the model was released 2026-08-26, so late Aug/Sep 2026) · **Type:** reel (177s, 11 pages; the creator appears as a picture-in-picture face over screen captures)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. The model is real, open-weight and strong on vendor benchmarks, but "runs on your phone easily" is false (125B total parameters; even a 1-bit quant needs about 75 GB RAM). "Better than anything OpenAI/Anthropic has" overstates vendor-reported, mixed results.

### Post description
> Qwen 3.8:flash-next is really revolutionary

### Audio
English monologue (about 450 words) by the creator; timestamped notes with a few key lines quoted:
- [0.0–12.2] Recalls a model from about a week earlier that was free, ran on most computers and was, he says, better than anything rentable in the cloud and better than "GPT salt" [sic, a GPT model name as transcribed] (he shows the Qwen3.8-27B page).
- [12.2–17.1] Says a new release "blows this one out of the water" and is also free: "3.8 flash next", available today.
- [17.1–38.6] It is much larger but a mixture of experts, so the whole model need not sit in memory; says they fundamentally rethought how such models work, with "incredible" results.
- [38.6–71.7] Anecdote: a complicated 3D-model coding problem. He ran "GPT salt" on high at about $20 per prompt, five attempts (about $100), and it failed; the Qwen model (27B, per context) "was like no sweat I got it."
- [71.7–92.6] Claims it is very good at long-horizon work, much better than Claude and DeepSeek on long multi-step problems left to run for a couple of days, and that the new one is better still.
- [92.6–116.6] Claims it "performs like 125 billion parameter model" while only 6 billion parameters are active, so it runs at 6B speed and would run easily on a phone.
- [116.6–134.6] Claims it is significantly better than anything OpenAI or Anthropic has, pointing to benchmarks on screen: "it's just blowing everything out of the water".
- [134.6–176.7] Running at home: top speed needs the whole model in VRAM, but you can keep it in system RAM and put the KV cache and encoder/decoder layers in a few GB of VRAM. Says Ollama, other GGML products, LM Studio and llama.cpp do this automatically, loading experts from system RAM as needed. Closes: "this is really revolutionary".

### On-screen content, page by page
**Pages 1–7 (0.0–14.7s):** a Hugging Face page at huggingface.co/Qwen/Qwen3.8-27B: "Qwen/Qwen3.8-27B", like 10.6k, Qwen org with 98k followers; tags Image-Text-to-Text, Transformers, Safetensors, qwen3_5, conversational, Eval Results, License: apache-2.0; Community 125; Downloads last month 415,039.
**Pages 8–9 (14.7–25.8s):** the Qwen blog: "Qwen3.8-Flash-Next: A New Architecture, Towards Ultimate Cost-Efficiency", 2026/08/26 · 12 min · 2381 words · Qwen Team, Translations: 简体中文, a "Try Qwen Studio" button, a "Now Available: Qwen3.8-Flash-Next: Now Open Weights" banner, and links HUGGING FACE, MODELSCOPE, TECH REPORT, FLASHQLA, DISCORD.
**Page 10 (25.8–33.2s):** the blog "Introduction" (third-party text, summarized). It opens the weights of Qwen3.8-Flash-Next, a multimodal MoE that serves as an early look at architecture for the coming Qwen4 family. It upgrades four aspects:
- **Attention:** a GDN + QSA hybrid (Gated DeltaNet compresses history; Qwen Sparse Attention cuts long-sequence cost).
- **Residual:** Gated Residual widens the residual stream into 4 branches with a dynamic gate.
- **Embedding:** N-gram Embedding, a table lookup on local context that adds capacity cheaply, with asynchronous prefetching.
- **Optimization:** the Muon optimizer, refined (orthogonalization accuracy, Muon/AdamW split, fused-parameter splitting), with the scaling law refitted.
**Page 11 (33.2–177.0s):** Qwen's benchmark table. The creator's face overlay moves around; hidden cells were read from other frames:

| | Qwen3.8-Flash-Next | Qwen3.8-27B | Qwen3.7-Plus | DeepSeek-V4-Flash-0731 | Claude-Opus-4.8 (Max) |
|---|---|---|---|---|---|
| # Params | 125B | 27B | 397B | 284B | – |
| # Activated params | 6B | 27B | 17B | 13B | – |
| # N-gram embedding params | 51B | – | – | – | – |
| Agentic coding (DeepSWE 1.1) | **58.7** | 42.2 | 16.5 | 54.4 | – |
| Agentic coding (SWE-bench Pro) | **62.5** | 61.7 | 55.8 | 56.0 | 53.4 |
| Multilingual SWE (SWE-bench Multilingual) | **81.0** | 73.8 | 75.8 | – | 77.5 |
| Repo-level code generation (NL2Repo-Bench) | 48.1 | 42.3 | 41.1 | **54.2** | 47.6 |
| Long-horizon office work | **73.9** | 70.7 | 65.1 | 45.1 | 68.2 |
| Professional job tasks | **55.7** | 33.4 | 27.6 | 41.3 | 36.6 |
| Frontier agentic tasks (Pass@1 / Score) | 24.3 / **51.2** | 20.4 / 42.9 | 13.2 / 33.6 | **25.2** / – | – |
| Real-world tool use | **73.5** | 67.1 | 50.6 | 70.3 | – |
| Instruction following (IFBench) | **81.3** | 79.5 | 79.1 | 79.2 | 62.5 |
| Scientific reasoning (GPQA Diamond) | **91.7** | 89.2 | 90.3 | 90.8 | 91.3 |
| Multidisciplinary reasoning (HLE) | 35.9 | 30.8 | 34.7 | 33.8 | **40.0** |
| Competitive coding (LiveCodeBench v6) | **91.9** | 90.3 | 89.6 | 90.6 | 88.8 |

Column headers and benchmark sub-labels are blurry in the video. Model names are confirmed via the Gigazine report; sub-labels are best reads. Footnotes (small) say the coding evals used the Claude Code / mini-SWE-agent harnesses and that "–" means not available.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Qwen3.8-Flash-Next | model | caption, audio, pages 8–11 | Alibaba Qwen open-weights MoE released 2026-08-26 (HF: Qwen/Qwen3.8-Flash-Next): 125B total, 6B active, plus 51B N-gram embedding params; 262k context (up to 1M with YaRN). Paid API version "Qwen3.8-Flash" at about $0.15–0.16/M input and $0.47/M output tokens (reported) |
| Qwen/Qwen3.8-27B | model | pages 1–7 | Earlier dense open model, Apache-2.0, 415,039 downloads/month on screen |
| DeepSeek-V4-Flash-0731, Qwen3.7-Plus, Claude-Opus-4.8 (Max) | models | page 11 | Comparison models in Qwen's own table |
| "GPT salt" | model name (as transcribed) | audio 8–12s, 47–68s | Unclear; an OpenAI GPT-5.x tier he says cost about $20/prompt on max settings |
| Ollama, LM Studio, llama.cpp, GGML | tools | audio 154–164s | Real local-inference tools; partial CPU/GPU offload of MoE experts is supported in llama.cpp-based tools |
| Unsloth GGUF quant | product | (web) | unsloth/Qwen3.8-Flash-Next-GGUF; its 1-bit build needs ≥75 GB RAM, with about 80% accuracy retained (per Unsloth via Gigazine) |

### What's being promoted / the funnel decoded
No CTA, product or link. This is an enthusiast reaction video; no affiliate signs.

### Verification & insights
- The release date, architecture and parameter counts match press coverage (Gigazine 2026-08-27, Alibaba Cloud blog, OrcaRouter). All benchmark numbers are **vendor-reported**; no independent replication was found.
- **"Runs on your phone easily": false.** Only 6B parameters are active per token, but all 125B (plus 51B embeddings) must be stored and paged. Even a 1-bit quant needs about 75 GB RAM; MoE gives 6B-model speed per token only when weights are resident.
- **"Better than anything OpenAI/Anthropic has … at everything": overstated.** In Qwen's own table, Claude-Opus-4.8 (Max) wins HLE (40.0 vs 35.9), DeepSeek wins repo-level codegen (54.2) and Pass@1 frontier agentic (25.2), and no OpenAI model is in the table at all.
- The "$100 of GPT failed, Qwen solved it" story is a single anecdote.
- "Encoder decoder" layers on GPU is technically loose (these are decoder-only models); the general idea of offloading attention/shared layers to GPU and experts to RAM is valid.
- Could not verify: the license of the Flash-Next weights (the 27B is Apache-2.0), and the post date.

---

<a id="e-deincohjloh"></a>

## DeiNCoHjloH | @tism.maxxing | "NVIDIA is giving 4 strong AI models for free": DeepSeek V4.1 Flash, GLM 5.3, GLM 5.3 Flash, Kimi K3 via build.nvidia.com (repost of an X post)
- **Link:** https://www.instagram.com/p/DeiNCoHjloH/
- **Account:** @tism.maxxing (Luke Luck engineer) · **Posted:** 2026-10-16 · **Type:** reel (20.6s, 5 scene pages)
- **Caption source:** full (Instagram)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. NVIDIA's build.nvidia.com does offer free, rate-limited trial API endpoints (OpenAI-compatible base URL integrate.api.nvidia.com/v1) with a free account. Whether these four exact models have free endpoints right now could not be confirmed. The free tier is for prototyping, with rate limits, not unlimited production use. The reel reposts an X post by @pengsonal and funnels to a "comment FREE" DM.

### Post description
> going on vacation so I am reposting my best value vids while I am gone
>
> this one is the free model roundup — Kimi K3, GLM 5.3 and DeepSeek, all free through NVIDIA. no credit card, just a free account. check the story out to get set up

### Audio
The creator speaks over a green-screen X-post background (Whisper wrote "Amidia" and "Kimmy"):
- [0.0–2.6] "Please, steal this!"
- [2.6–15.5] "Get all of this completely for free, because NVIDIA is saving the day giving us DeepSeek, GLM, GLM Flash, and Kimi all for free, no credit card required."
- [15.5–19.9] "So please comment the word free if you want to tap in."

### On-screen content, page by page
Background on every page is a screenshot of an X post by **Peng (@pengsonal) · 5h**, verified badge:
> NVIDIA IS GIVING 4 STRONG AI MODELS FOR FREE 🤯
> you can use:
> • DeepSeek V4.1 Flash • GLM 5.3 • GLM 5.3 Flash • Kimi K3
> get access: build.nvidia.com
> base URL: integrate.api.[nvidia.com]/v1 (partly hidden by the creator's head)
> hope this helps

Below it, NVIDIA catalog cards: "DeepSeek AI · **deepseek-v4.1-flash** · 552B MoE, 8B active params with native multimodal sup[port]… [sparse] attention, lower API cost using smaller KV cache · multimodal moe +3 · Free Endpoint" and "Z.ai · **glm-5-3-flash** · Multimodal 320B-total / 18B-active MoE with hybrid KDA and sparse MLA attention, native FP8 weights, reasoning and tool calling · multimodal +6 · Free Endpoint · 28d".
**Page 1 (0–2.3s):** overlay "**Please Steal this 👀**".
**Page 2 (2.3–5.4s):** same.
**Page 3 (5.4–10.1s):** "no credit card required" (from the post) emphasised.
**Page 4 (10.1–15.2s):** caption overlay "**FLASH, AND KIMI**".
**Page 5 (15.2–20.6s):** "**Comment "FREE"**" / "**I'll send you the link to set this up**".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| build.nvidia.com | site | X post on all pages | NVIDIA's API catalog (NIM). A free developer account gets rate-limited trial access to many hosted models, labelled "Free Endpoint". |
| integrate.api.nvidia.com/v1 | API base URL | X post (partly hidden) | NVIDIA's real OpenAI-compatible endpoint. Needs an API key from build.nvidia.com. |
| DeepSeek V4.1 Flash (deepseek-v4.1-flash) | model | X post, audio | DeepSeek model. Card says 552B MoE / 8B active. Web search found deepseek-v4-flash labelled "Free Endpoint" on NVIDIA, but nothing on "v4.1-flash". Unverified. |
| GLM 5.3 / GLM 5.3 Flash (glm-5-3-flash) | models | X post, audio | Z.ai models. Card: 320B total / 18B active. NVIDIA also publishes a Dynamo self-hosting recipe for GLM-5.3-Flash. Free-endpoint status unverified. |
| Kimi K3 | model | X post, audio, caption | Moonshot AI model. Listed in NVIDIA's catalog (moonshotai/kimi-k3). Free status unverified. |
| @pengsonal (Peng) | X account | all pages | Original author of the content being reposted |
| "check the story" / comment FREE | CTA | caption, page 5 | DM or story with setup steps |

### What's being promoted / the funnel decoded
"Comment FREE" gets you a DM link for setup. The caption also points to his Instagram story. The underlying "product" is just NVIDIA's free developer trial. Nothing is paid and no affiliate link is visible. The repost is engagement farming ("going on vacation… reposting my best value vids"). What you actually need: create a free account at build.nvidia.com, generate an API key, and use base URL `https://integrate.api.nvidia.com/v1` with the model ID from the catalog.

### Verification & insights
- NVIDIA's free endpoints are real but are a trial tier: rate-limited (requests per minute), meant for prototyping, and the model list and free status change often. The catalog card on screen itself shows a "28d" freshness tag.
- Inputs sent to hosted trial endpoints are subject to NVIDIA's terms. Don't send sensitive data.
- "Strong AI models for free": these are capable open-weight models, but they are not equal to frontier closed models.
- Could not verify: current free status of each of the four named model IDs, or the exact parameter counts on the cards.

---

<a id="e-dei3n2vapq6"></a>

## Dei3N2vAPq6 | @nathanhodgson.ai | "5 MCP servers you actually need for Claude Code": Perplexity, Playwright, Firecrawl, Glif, Chrome (DevTools) MCP
- **Link:** https://www.instagram.com/p/Dei3N2vAPq6/
- **Account:** @nathanhodgson.ai (Nathan Hodgson) · **Posted:** 2026-10-16 (decoded from the shortcode; mirror gave no date) · **Type:** reel (50.7s, 23 scene pages; talking head with GitHub-style repo cards and B-roll)
- **Caption source:** possibly truncated (mirror). yt-dlp got a 429 and then an "empty media response", so the full caption was not retrievable.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. All five MCP servers are real, open-source (MIT/Apache-2.0) and actively maintained. But "all of these MCPs are completely free" is wrong: Perplexity's needs a paid Perplexity API key, Glif spends account credits, and Firecrawl's keyless tier is rate-limited and covers only some tools. The spoken "Chrome MCP… already built into Claude Code" (Claude in Chrome) is not the repo shown on screen (Google's chrome-devtools-mcp).

### Post description
> Comment "MCP" to get these tools.
>
> Claude Code gets more useful when it can reach the tools your work actually needs. These are five connections worth understanding, with a different job for each one.
>
> Perplexity brings web research into the workflow...

(Cut off by the mirror at this point. The rest of the caption could not be fetched.)

### Audio
The creator speaks throughout, in English. Whisper's "Publicity MCP" means **Perplexity MCP**, "Glyph" means **Glif**, and "compensation" means "conversation" or "context".
- [0.0–5.4] "If you use Claude code, these are the five MCP servers that you actually need."
- [5.4–12.6] "First is **Perplexity MCP** that lets Claude search the entire internet in real time without ever leaving your workflow."
- [12.6–20.0] "Second is **Playwright**. This gives Claude full browser control so it can fill in forms, upload videos and test web apps in seconds."
- [20.0–26.7] "Third is **Firecrawl**. This allows Claude to crawl any website and load everything straight into your [conversation]."
- [26.7–34.8] "Fourth is **Glif** [spoken 'Glyph']. It connects Claude to hundreds of image and video generation models and it automatically optimizes your prompt for each one."
- [34.8–43.3] "Number five is **Chrome MCP**. It's already built into Claude code and it allows it to see and interact with whatever you have open inside of Google Chrome."
- [43.3–50.5] "All of these MCPs are completely free and if you would like to check them out for yourself just comment MCP and I will send you all of the links."

### On-screen content, page by page
Most pages put a word-by-word caption over the talking head (white bold word in a dark pill). The times come from the scene-change frames.
**Pages 1–3 (0.0–1.3s):** Talking head with a podcast mic. Caption "If you".
**Page 4 (1.3–5.2s):** Pale-green card with the Claude asterisk logo and the text **"Claude Code"**. Caption "these".
**Page 5 (5.2–6.8s):** GitHub-repo-style card: "**ppl-ai/** **modelcontextprotocol**", "A Model Context Protocol Server connector for…" (Perplexity logo). Caption "First".
**Page 6 (6.8–10.8s):** Dark chat UI screenshot (a Perplexity/Claude-style answer pane, unreadable). Caption "that lets".
**Page 7 (10.8–12.1s):** Screenshot of a browser window on a macOS desktop. Caption "ever".
**Page 8 (12.1–13.5s):** Card: "**Playwright**", "@ Model Context Protocol" (Playwright masks logo). Caption "Second".
**Pages 9–10 (13.5–19.7s):** Screen recordings of a terminal or agent window next to a browser (Claude driving a browser). Captions "This", "Claude".
**Page 11 (19.7–21.2s):** Card: "**firecrawl/** **firecrawl-mcp-server**", "Official Firecrawl MCP Server - Adds powerful…" (flame logo). Caption "Third".
**Page 12 (21.2–26.4s):** B-roll of the **ChatGPT** web app with "Developer mode" and "Memory is not used for this chat" above an "Ask anything" box. This is unrelated stock footage. Caption "This allows".
**Page 13 (26.4–27.4s):** Card: "**glifxyz/** **glif-mcp-server**" (pink Glif logo). Caption "Fourth".
**Page 14 (27.4–34.7s):** Retro green-on-black terminal animation: "READY. WAITING." / "SYSTEM OK" / "SYSTEM OK INPUT:" with the line "**Glyph's** MCP turns" (Glif's promo spelled "Glyph's"). Caption "It".
**Page 15 (34.7–36.3s):** Card: "**ChromeDevTools/** **chrome-devtools-mcp**", "Chrome DevTools for coding agents" (Chrome DevTools logo). Caption "Number".
**Page 16 (36.3–41.5s):** B-roll of the **Windsurf** IDE ("Windsurf", "Write with Cascade" panel). Caption "It's".
**Page 17 (41.5–41.8s):** Transitional card (dark icon square). Caption "open".
**Page 18 (41.8–43.2s):** B-roll of **SuperGrok** ("What do you want to know?", model label "Grok 4", buttons "Create Images", "Edit Image", "Latest News"). Caption "inside".
**Page 19 (43.2–48.0s):** Talking head. Caption "all of these".
**Pages 20–23 (48.0–50.7s):** Green screen with an animated Instagram comment box. A "C…" is being typed (comment "MCP"), and a cursor clicks the share/send arrow. Caption "MCP". The last frame is black.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude Code | app | audio 0.0s; page 4 | Anthropic's agentic coding CLI/app, where these MCP servers get attached. |
| Perplexity MCP, `ppl-ai/modelcontextprotocol` | repo | audio 5.4s; page 5; caption | Real. Perplexity's official MCP server (MIT, © 2025 perplexity). Last commit 2026-10-16, "Prepare version 1.4.0 (#154)". **Needs a Perplexity API key** (console.perplexity.ai). It offers a remote server at `https://api.perplexity.ai/mcp` or a local server via `npx -y @perplexity-ai/mcp-server`. The Sonar API is paid per token and per request, and third-party guides report no standing free tier. |
| Playwright MCP | repo | audio 12.6s; page 8 | Real. microsoft/playwright-mcp (Apache-2.0), last commit 2026-10-19. Free. It runs a local browser that the agent drives through accessibility snapshots. |
| `firecrawl/firecrawl-mcp-server` | repo | audio 20.0s; page 11 | Real. Official Firecrawl MCP (MIT, © 2025 vrknetha), last commit 2026-10-20. The README says: "On the keyless free tier, `scrape`, `search`, and `parse` work without an API key (rate-limited). Other tools such as `crawl`, `map`, and `agent` still need a key." Crawling "any website" therefore needs a Firecrawl key and credits. |
| Glif, `glifxyz/glif-mcp-server` | repo/site | audio 26.7s; pages 13–14 | Real. Glif's MCP server (MIT, © 2025 Spellcasters, Inc), last commit 2026-10-08. Remote endpoint `https://glif.app/api/mcp` with OAuth sign-in to a Glif account. The README says generation spends credits from the account and read-only tools are free. Third-party listings report about 10 free credits a day plus paid credit packs. |
| Chrome MCP (spoken) vs `ChromeDevTools/chrome-devtools-mcp` (on screen) | repo / built-in feature | audio 34.8s; page 15 | The repo shown is Google's Chrome DevTools MCP (Apache-2.0), last commit 2026-10-20. It is free, but it is a separate server you install. What he *describes* ("already built into Claude Code", acting on "whatever you have open inside of Google Chrome") is Anthropic's **Claude in Chrome** extension integration. That is a different thing. |
| ChatGPT "Developer mode", Windsurf, SuperGrok (Grok 4) | apps (B-roll) | pages 12, 16, 18 | Stock screen footage only. None of them is one of the five recommendations. |
| "MCP" comment keyword | CTA | caption, audio 47.5s, pages 20–23 | Comment-to-DM automation. |

### What's being promoted / the funnel decoded
- "Comment MCP and I will send you all of the links" is a keyword-triggered auto-DM. All five links are public GitHub repos, listed above, so there's no need to comment.
- Nathan Hodgson is a UK AI-tools creator (about 145k followers on Instagram and about 145k on TikTok per CreatorDB). His profile lists brand deals, including Perplexity, Descript and Suno. This reel shows no sponsorship label, but Perplexity is listed first and he has worked with them before. Treat the ranking as possibly brand-influenced.
- Nothing is sold on screen. The DM most likely delivers the links plus a follow or newsletter prompt (not verified, since the funnel wasn't engaged).

### Verification & insights
- **Repos checked** (shallow clones in `scratchpad/repos/`): ppl-ai__modelcontextprotocol (MIT, 2026-10-16), firecrawl__firecrawl-mcp-server (MIT, 2026-10-20), glifxyz__glif-mcp-server (MIT, 2026-10-08), ChromeDevTools__chrome-devtools-mcp (Apache-2.0, 2026-10-20), playwright-mcp (existing clone, Apache-2.0, 2026-10-19). All are active.
- **"Completely free": false for three of the five.** Perplexity needs a paid API key. Glif runs on account credits. Firecrawl gives limited keyless scrape/search/parse, but crawl needs a key and credits. Playwright and Chrome DevTools MCP are free and local.
- **"Search the entire internet in real time":** this is Perplexity's Sonar search via the API, and it's billed.
- **"Hundreds of image and video models… automatically optimizes your prompt":** this is Glif's marketing claim. Glif does run many community "glifs" (workflows) over many models, but prompt optimization depends on the workflow.
- **The Chrome item is mismatched.** The visual (chrome-devtools-mcp) and the narration (the built-in Claude in Chrome integration) refer to different tools. Both exist.
- **Privacy:** connecting a browser-control MCP to your logged-in Chrome gives the agent your sessions. Use a separate profile.
- **Not verified:** the full caption (blocked by Instagram), and what the DM actually sends.

---

<a id="e-dduu9f-ubl0"></a>

## DdUu9f_uBL0 | @gennaroautomates | "AI this week in 60 seconds": Meta Muse Glimmer, xAI Grok Bot, the AI Website Cloner Claude skill, Qwen3.8-27B, an AI watermark remover and Zhipu GLM-5.3, with a "comment AI" DM funnel
- **Link:** https://www.instagram.com/p/DdUu9f_uBL0/
- **Account:** @gennaroautomates (Gennaro Santoro | AI Systems and Automation Strategist) · **Posted:** 2026-09-15 · **Type:** reel (46.3s, 58 scene pages)
- **Caption source:** full (Instagram, fetched with yt-dlp)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. All 6 items are real releases (mostly mid-August 2026, so not "this week" for a 15 Sept post). But the headline "Claude Opus-level model that runs on your laptop" is backed by on-screen benchmark charts of **Qwen3.8-Max** (Alibaba's large flagship), not the 27B model. "Free" is also overstated: Grok Bot requires premium plans, and GLM-5.3 weights were only "promised".

### Post description
> Comment “AI” and I’ll send you links to all 6 tools from this week’s roundup.
>
> China dropped a Claude Opus-level model that runs on your laptop. For free.
>
> This week: local agents, cloud bots with their own CRM access, and an open-source coding model that beats everything else on benchmarks.
>
> The free tier is winning.

### Audio
The creator speaks in English to camera (white "SEMPRA SYSTEMS" cap) over B-roll.
- [0.0–6.9] "China just dropped a Claude Opus level open source model that runs on your computer. Here's everything that happened in AI this week in 60 seconds."
- [6.9–11.4] "One, Meta Muse Glimmer 3[0]B just released, a model built for local always-on agents." (Whisper heard "Metamuse Glimmer 3DB".)
- [11.4–16.9] "Two, xAI Grok Bot. Each bot now gets its own cloud computer, signs into your email and CRM, runs 24/7." (Whisper: "Grockbot… CM runs 24-setup".)
- [16.9–22.6] "Three, we now have a new Claude skill that drives Chrome to rebuild any site from a single URL, and it looks amazing."
- [22.6–28.6] "Four, Alibaba released Qwen 3.8 27B. It's multimodal and has Claude's Opus level intelligence while being free and private."
- [28.6–32.0] "Five, there's a new watermark remover, open source, for Claude, Gemini, and OpenAI."
- [32.0–35.4] "Six, GLM 5.3 increases coding performance [by] 50%. Top ranked on Terminal Bench." (Whisper: "GPUGM 5.3".)
- [35.4–46.0] "It's clear that the open source stack is slowly outpacing paid subscriptions. If you're building with AI, pay attention to what your competition is using for free. Comment AI and I'll send you the link to the full article."

### On-screen content, page by page
Big burned-in captions repeat the speech (for example "CHINA DROPPED / CLAUDE OPUS", "LEVEL", "THAT RUNS ON", "YOUR COMPUTER"). The B-roll sits on an orange cutting-mat grid background.
**Pages 1–9 (0–4.1s):** A relief map of western China, then laptops showing code editors and an app, with fragments of a side title "Always-on… Work…".
**Pages 10–11 (4.1–5.9s):** A numbered list 1–6 over the creator, deliberately **pixelated or scrambled** so it can't be read (the shapes match META MUSE / GROK BOT / CLONE WEB / QWEN 3.8 / WATERMARK / ZHIPU GLM-5.3).
**Page 12 (5.9–6.9s):** A glowing "60:0" timer.
**Pages 13–17 (6.9–11.5s):** "1 META MUSE" with the Meta logo, then a screenshot: "Introducing Muse Glimmer: An Open Agentic Model That Runs on Your Device", caption "GLIMME[R] 3B", "A MODEL BUILT".
**Pages 18–24 (11.5–16.9s):** The xAI "X" logo, then a dark desktop chat app with bots named **Chief, Sales Outbound, Inbox Manager, Account Manager, Talent Scout, Expense Manager, Offsite crew**; user "Armand Segall". Chief's message: "✓ Deck — numbers checked against finance's sheet · 2 stale slides flagged ✓ Offsite — 3 venues shortlisted · dates held on each… two things need you today: the deck review at 2pm, and a yes/no on the venue. everything else is handled." A later message: "✓ Venue — marina house booked · deposit paid ✓ Calendar — invites updated for all 40 ✓ Holds — other two released with a thank-you". The Sales Outbound thread: "Checking what's connected. Hex, Gmail, and LinkedIn are already signed in. Salesforce isn't." A "Computer – Action needed" card: "Sign in to Salesforce so I can see the accounts you own", buttons "Take over" / "I'm done". Captions "EACH BOT NOW", "SIGNS INTO", "YOUR EMAIL AND CRM".
**Pages 25–29 (16.9–22.6s):** "3 CLONE WEB" with a sunglasses-avatar logo (JCodesMore). A GitHub README: "AI Website Cloner Template – Clone any website with one command – Give your AI coding agent a URL, and watch it recreate the website as a clean Next.js app – Best results with Claude Code + Opus 5. Works with Codex, Cursor, Gemini, and more", with README sponsor ads "Rapidproxy – High-quality proxy service Starting from $0.65/GB" and "Atlas Cloud". Captions "HAVE A NEW CLAUDE", "CHROME". Then a side-by-side of an "AI that works for you… Hire a digital employee. Integrated everywhere." landing page, labelled "Original" and "Clone".
**Pages 30–43 (22.6–32.0s):** "4. ALIBABA", "4 QWEN 3.8" with Alibaba and Qwen logos, then a "Qwen3.8 27B" title card. A Qwen X post: "We promised open weights for Qwen3.8. Now, time to meet them! ⚡ Qwen3.8-27B: A native multimodal dense model. With just 27B parameters, it outperforms Qwen3.7-Plus overall and shines in real-world coding & office workflows. – 262K native context, easily extendable to 1M tokens via YaRN. – Built for builders. Highly efficient, high-quality, and licensed under Apache 2.0. 🚀 The open weights for Qwen3.8-2.4T-A95B (Max-level) have also been released recently. Whether you're shipping lightweight applications with Qwen3.8-27B locally or building agents with Qwen3.8-2.4T-A95B, they're yours now!" (6M views, Aug 14). Captions "IT'S MULTIMODAL", "AND HAS CLAUDE OPUS", "LEVEL INTELLIGENCE", "WHILE BEING FREE".
  - **Benchmark chart 1 (p39–40), legend "Qwen 3.8 Max", "Qwen 3.7 Max", "Qwen 3.7 Plus" plus two Anthropic-logo bars and an OpenAI bar.** Order: Qwen3.8 Max / Qwen3.7 Max / Anthropic / Anthropic / (Gemini where shown) / OpenAI.
    - SWE-Pro: 67.7 / 60.6 / 69.2 / 80.0 / 64.6
    - TerminalBench-2.1: 86.6 / 74.5 / 84.6 / 84.6 / 88.8
    - QwenReactBench: 1724 / 1538 / 1694 / 1770 / 1564
    - CoWorkBench: 74.8 / 64.6 / 72.3 / 75.9 / 71.5
    - BabyVision (w/o & w/ python): 91.3 (82.0) / 70.8 (64.7) / 81.2 / 90.5 (42.5) / 68.5 (55.9) / 88.8 (65.5)
    - CharXiv (RQ): 93.5 (88.4) / 85.9 / 89.9 (78.5) / 93.5 (87.8) / 89.9 (84.4) / 89.1 (85.1)
    - LVBench: 81.8 / 76.2 / 67.3 / 75.1 / 78.8
    - Vision2Web: 69.0 / 42.1 / 62.4 / 70.5 / 62.1
  - **Chart 2 (p42–43), legend "Opus4.8", "Fable5", "Gemini3.1-Pro", "GPT5.6 Sol (max)", led by the Qwen 3.8 Max bar.**
    - PaperBench: 93.0 / 64.8 / 80.3 / 88.8 / 90.5
    - FrontierSWE: 73.5 / 40.7 / 70.0 / 88.8
    - JobBench: 53.4 / 31.3 / 48.4 / 57.4 / 45.4
    - Agents' Last Exam: 52.4 / 31.1 / 45.1 / 53.6
    - ERQA: 77.8 / 69.8 / 57.2 / 70.0 / 68.0 / 70.0
    - PerceptionBench: 63.5 / 51.1 / 47.2 / 57.2 / 56.2 / 59.7
    - MobileWorld: 77.8 / 51.2 / 67.5 / 85.5 / 58.1 / 76.9
    - OSWorld-Verified: 86.1 / 73.3 / 83.4 / 85.0 / 76.2 / 83.2
**Pages 44–47 (32.0–33s):** "5 WATERMARK" with a "WATERMARK REMOVER" logo. An explainer card: "ordinary dice – numbers from: a fresh dice roll at every fork – numbers used: 0.77 · 0.61 · 0.55" versus "watermark key – numbers from: hash(secret key + words so far) – numbers used: 0.14 · 0.29 · 0.06 · 0.26" (how statistical text watermarks work).
**Pages 48–51 (33–36.7s):** "6 ZHIPU GLM-5.3" with the Z.ai logo. Table "Performance across comparison models", with columns GLM-5.3 / GLM-5.2 / Kimi K3 / DeepSeek-V4 Pro-0813 / Qwen3.8-Max / Opus 4.8 (cut off). CODING rows:
  - Terminal Bench 2.1: 88.2 / 81.0 / 88.3 / 87.9 / 86.6 / 86.0
  - Terminal Bench 3.0: 28.3 / 4.6 / 17.4 / – / – / 21.1
  - DeepSWE: 66.9 / 46.2 / 67.5 / 62.7 / 56.6 / 58.0
  - NL2Repo: 58.0 / 48.9 / 58.0 / 61.1 / 55.9 / 69.7
  - ProgramBench: 19.0 / 9.5 / 17.5 / – / 10.6 / 15.5
  - FrontierSWE: 78.1 / 67.5 / – / – / – / 65.5
  - SWE-Marathon: 42.5 / 19.4 / 48.1 / – / – / 48.8
  - PostTrainBench: 39.9 / 31.7 / 32.0 / – / – / 32.9
  Captions "INCREASED CODING", "TOP RANKED".
**Page 52 (36.7–40s):** An "Open-source" logo ring: Hugging Face, DeepSeek whale, Z.ai, Ollama, Kimi "K", Mistral and others. Caption "IT'S CLEAR".
**Pages 53–58 (40–46.3s):** The creator: "IF YOU'RE BUILDING WITH AI", "PAY ATTENTION TO WHAT", then a mock comment box with a send arrow (the "comment AI" prompt).

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Meta Muse Glimmer | model | p13–17, audio 6.9s | Real: Meta Superintelligence Labs' open-weights (Apache-2.0) agentic model, released 2026-08-10. The main model is **30B** (4-bit fits about 24–32 GB); the release also includes a 3B assistant model. The on-screen "3B" is misleading or garbled. |
| xAI / SpaceXAI Grok Bot | product | p18–24, audio 11.4s | Real, early beta since 2026-08-11. Agents with their own cloud computer that sign into your apps (Gmail, CRM and so on) and keep working while you're away. **Not free**: bundled with SuperGrok Heavy, Cursor Ultra or Cursor Teams Premium. |
| AI Website Cloner Template (github.com/JCodesMore/ai-website-cloner-template) | repo / Claude Code skill | p25–29, audio 16.9s | Real, MIT. A Claude Code `/clone-website <url>` command run with `claude --chrome`. Recreates a site as a Next.js app. Copying others' designs and assets raises copyright and ToS issues. |
| Rapidproxy ($0.65/GB), Atlas Cloud | sponsors | p27 | Sponsor banners inside that README, not part of the creator's pitch |
| Qwen3.8-27B (Alibaba) | model | p30–43, audio 22.6s, caption | Real: dense 27B multimodal open weights, Apache-2.0, 262K context (1M via YaRN), released 2026-08-14. Runs locally when quantized (about 16 GB GPU or Mac). |
| Qwen3.8-Max / Qwen3.8-2.4T-A95B | model | p36–43 | The large flagship. **All the benchmark charts shown are this model**, not the 27B. |
| Opus 4.8, Fable5, Gemini 3.1 Pro, GPT-5.6 Sol (max) | comparison models | p42–43 legend | Frontier models used as comparisons in Alibaba's own chart |
| Watermark remover ("watermarks-remover" by Guillaume Meyer; also the PyPI "dewatermark") | open-source tool | p44–47, audio 28.6s | Real, about 14K stars. Strips invisible Unicode and metadata and tries rewriting against statistical watermarks (Anthropic's announced Claude text watermark, Gemini SynthID-Text, OpenAI provenance). Reporting says removal of statistical marks is unproven. Using it to pass off AI text can breach provider terms or academic rules. |
| Zhipu / Z.ai GLM-5.3 | model | p48–51, audio 32.0s | Real, released 2026-08-14. Model card: Terminal-Bench 2.1 = 88.2 (vs 81.0 for GLM-5.2), TB 3.0 28.3 vs 4.6. Post-training only on the GLM-5.2 base. At launch it was available via the GLM Coding Plan or ZCode, with open weights "promised". **Not top-ranked on TB 2.1 in its own table**: Kimi K3 (88.3) and GPT-5.6 Sol (88.8) are higher. |
| "increases coding performance 50%" | claim | audio 32s | Not supported as stated. TB 2.1 rose about 9% relative (81.0→88.2). Only TB 3.0 jumped (4.6→28.3), and DeepSWE about 45% (46.2→66.9). |
| SEMPRA SYSTEMS | brand on cap | all talking-head pages | Presumably the creator's company; nothing found by web search |
| "Comment AI" | CTA | caption, audio 43s, p57–58 | DM automation (see funnel) |

### What's being promoted / the funnel decoded
"Comment AI and I'll send you links to all 6 tools" / "the full article". This is a ManyChat-style comment-to-DM automation that grows engagement and the DM list. Everything it would send is free to find; the table above gives every link. The account (an "AI Systems and Automation Strategist" wearing a "Sempra Systems" cap) suggests an automation agency or consulting business behind it. No price or affiliate code is visible in the post.

### Verification & insights
- Each named item was confirmed by web search (Muse Glimmer, Grok Bot, JCodesMore cloner, Qwen3.8-27B, watermarks-remover, GLM-5.3). Most releases are dated 10–14 Aug 2026, about a month before the post, so "this week" is stale.
- **Main misleading point:** "Opus-level that runs on your laptop" mixes up two models. The charts are Qwen3.8-**Max**, a roughly 2.4T-parameter model that cannot run on a laptop. Qwen claims only that the 27B "outperforms Qwen3.7-Plus". Self-reported benchmarks, not independently verified.
- "Free" is mixed: Glimmer, Qwen3.8-27B and the cloner are free and open. Grok Bot requires premium subscriptions. GLM-5.3 weights were not downloadable at launch.
- The opening list in the video is deliberately pixelated (a retention trick), and the CTA keeps the links behind DMs.

---

<a id="e-dehlpgthomw"></a>

## DehLpgthOMw | @tykozak811 | "Uncensored AI on your computer": Hugging Face model OBLITERATUS/Qwen3.8-27B-OBLITERATED run via LM Studio or Ollama
- **Link:** https://www.instagram.com/p/DehLpgthOMw/
- **Account:** @tykozak811 (display name not available) · **Posted:** 2026-10-15 (decoded from the shortcode) · **Type:** reel (47.9s, 17 scene pages; phone filming a Mac screen, with bold captions)
- **Caption source:** possibly truncated (mirror), but it is short and ends with hashtags, so it is very likely complete. No re-fetch was attempted, to spare the rate limit.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. The model, LM Studio and Ollama are real, and local inference does avoid per-token fees. But this is an **abliterated (safety-removed) model** pitched for "private" or "censored" topics. The model card's own table shows capability loss. A 27B model needs a strong machine. "Dm me I set it up" is an unpriced setup service.

### Post description
> Your own AI. On your computer. Would you try it? 👀
> Dm me I set it up !!👇
> #ai #aitools #tech #huggingface #artificialintelligence

### Audio
The creator speaks throughout, in English. Whisper's "hugging things" means "**Hugging Face**", "chat GBT" means "ChatGPT", and "olama.com" means **ollama.com**.
- [0.0–6.8] "I found this really, really cool AI model on Hugging Face. If you don't know what it is, then you're in for a shock."
- [6.8–18.7] "So imagine you're in ChatGPT and maybe you wanna talk about something that's like a little bit more private, a little bit more censored. Well, you never have to worry about that ever again with this right here."
- [18.7–23.2] "They completely removed all censorship off this AI and it literally can do whatever you want."
- [23.2–28.4] "What you're gonna wanna do is go to LM Studio or you're gonna wanna go to ollama.com"
- [28.4–41.0] "and what these programs do for you is basically acts as the app interface. You go download these apps, you will connect it to that AI model and then you'll be able to instantly chat with it and it's hosted there."
- [41.0–48.0] "So you're not paying for token. It's basically living live in your computer available to you 24 seven. You're welcome."

### On-screen content, page by page
A handheld phone films a MacBook browser. Bold yellow and white burned-in captions repeat the speech.
**Pages 1–5 (0.0–28.4s):** Browser tabs "Keio Sales Pro OS", "**OBLITERATUS/Qwen3.8-27B…**", "Muse — Your Personal AI Ag[ent]" (later "LM Studio Bionic – Agent for…"). URL **huggingface.co/OBLITERATUS/Qwen3.8-27B-OBLITERATED**. Hugging Face model page "**OBLITERATUS / Qwen3.8-27B-OBLITERATED**", ♡ Like **1.46k**, Follow. Tags: Text Generation, MLX, Safetensors, GGUF, qwen3_5, abliterated, unc[ensored]. Tabs: Model card, Files and versions (xet), Community **17**. Card text:
  - "Qwen3.8-27B — OBLITERATED"
  - Quote: *"Genuinely uncensored. Real answers, not safety lectures. Near-stock capability."*
  - "V3: Deep Liberation — V3 applies iterative refinement on top of V2's complementary blend, with targeted corpus expansion. The result: **genuine liberation — not just removal of hard refusals but elimination [of] safety-lecture deflections.**"
  - Table (columns: Stock Qwen3.8-27B · V1 · V2 · V3):
    - MMLU (lm-eval, 0-shot): **84.5% (n=5700)** · **81.4%** · **84.3%** · **82.3%**
    - vs stock: — · **-6.0pp** · **-0.3pp** · **-2.1pp**
    - Liberation quality: refuses · hard refusals removed · soft deflections remain · genuinely answers
    - Cyber/code tasks (20 prompts): refuses · untested · untested · **20/20 with working code ✅**
    - Advanced real-world: 5/8 · untested · 7/8 · 7/8
    - Thinking mode: ✓ · ✗ · ✗ (refuses) · ✓ (partly read)
  - Overlays: page 2–4 a large red "**Warning ⚠️**" sticker; captions "I FOUND THIS", "WHAT YOU'RE GOING".
**Pages 6–7 (28.4–29.5s):** ollama.com: "Ollama is the most popular way to build with open models. Access the latest open models with complete privacy locally or in the cloud. Your prompts are never stored or trained on." "Get started". Stats **9M+**, **1B+**, **200T+**. Logo row (Apple, NVIDIA, Microsoft, Meta, NASA, IBM, Nike, Intel, VISA…). Overlay "**1. DOWNLOAD & INSTALL**" / "**LM Studio: lmstudio.ai**".
**Pages 8–10 (29.5–34.9s):** lmstudio.ai Bionic page: "The agent for your co[mputer]" / "**Bionic is LM Studio's agent for open models.** Natively local. Built for creativity, work, and code." Button "Download LM Studio Bionic". App mock-up: a "Create a portfolio site" project with "My Portfolio" and "Field Notes". Overlay "APP INTERFACE".
**Page 11 (34.9–37.5s):** Overlay "**DOWNLOAD THE MODEL**" / "**GGUF / MLX • match your RAM**". Caption "YOU WILL CONNECT".
**Pages 12–14 (37.5–42.5s):** Same Bionic page. A Gmail tab "Inbox (1,320)" is visible.
**Pages 15–17 (42.5–47.9s):** Overlay "**DOWNLOAD → LOAD → CHAT**" / "**Save this video for the setup steps**". Captions "IT'S BASICALLY LIVING", "COMPUTER AVAILABLE TO".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| OBLITERATUS/Qwen3.8-27B-OBLITERATED | Hugging Face model | pages 1–5; audio 0.0s | Exists (listed on Hugging Face, Featherless and Interfaze, with several mirror re-uploads under other users). An **abliterated** derivative of Alibaba's **Qwen3.8-27B** (released 2026-08-14, Apache-2.0, 27.78B params, multimodal, 262k context). Hosts list GGUF quants of roughly 14–27 GB and bf16 safetensors of about 54 GB. Card figures are self-reported. |
| OBLITERATUS | tool / org | page 1 | The abliteration toolkit associated with **elder-plinius** ("Pliny the Prompter"). It finds "refusal directions" in hidden states (SVD/PCA) and projects them out of the weights. Reported as AGPL-3.0, with optional telemetry. |
| Qwen3.8-27B (stock) | base model | page 1 table | Real Alibaba open-weight model (Apache-2.0, per multiple reports). |
| LM Studio, lmstudio.ai | app | audio 23.2s; pages 7–17 | Real, free desktop app for running local models (GGUF/MLX). |
| LM Studio Bionic | app | pages 8–17 (tab and page) | Real. LM Studio's separate agent app for open models, launched July 2026 (preview). Local, remote or LM Studio cloud models. |
| Ollama, ollama.com | app | audio 25.5s; pages 6–7 | Real, free open-source local model runner, with an optional cloud. Its homepage stats are as shown. |
| "Muse — Your Personal AI Agent", "Keio Sales Pro OS", Gmail | browser tabs | pages 1–5, 12 | Incidental tabs. Not promoted. |
| "Dm me I set it up" | service | caption | An implied paid setup service. No price shown. |

### What's being promoted / the funnel decoded
- "Dm me I set it up !!" means the creator offers to install a local "uncensored" AI for followers. No price, site or product is shown. It is a DM sales lead for a done-for-you setup. Everything involved is free to do yourself: install LM Studio or Ollama, then download a GGUF or MLX quant that fits your RAM.

### Verification & insights
- **"Completely removed all censorship… can do whatever you want":** that is the model card's own pitch ("Genuinely uncensored", "20/20 with working code" on cyber tasks). Abliteration does strip refusals. That is the point, and also the risk: it will produce harmful content (e.g., malware) as readily as benign answers, and the legal responsibility for use stays with the user. The base license (Apache-2.0) permits derivatives, but Hugging Face's content policy and local laws still apply.
- **"Near-stock capability" vs. the table:** MMLU drops from 84.5% to 82.3% for V3 (about -2.2pp; the card says -2.1pp). The card's "-6.0pp" for V1 doesn't match its own 84.5→81.4 numbers (-3.1pp), an internal inconsistency in the self-reported table.
- **"Not paying for tokens":** true for local inference, but a 27B model needs roughly 16–32 GB of RAM or VRAM even quantized (Q4 is about 16 GB), and runs slowly on ordinary laptops. "Instantly" is optimistic.
- **Privacy is the legitimate benefit:** local models keep prompts on your machine. That is achievable with the stock, non-abliterated Qwen3.8-27B too.
- Not executed or downloaded.

---

<a id="e-degaswxxidy"></a>

## DegASWXxIDY | @thedigitalkinggg | "Double your Claude usage": an unnamed skill that routes easy tasks to Haiku 5.5 subagents and keeps Opus 5.5 for thinking ("$1 → $0.10 per token")
- **Link:** https://www.instagram.com/p/DegASWXxIDY/
- **Account:** @thedigitalkinggg (display name not available) · **Posted:** 2026-10-15 (decoded from the shortcode) · **Type:** reel (34.5s, 12 scene pages; talking head with animated explainer cards)
- **Caption source:** possibly truncated (mirror), but it is short and ends with hashtags, so it is very likely complete. No re-fetch, to spare the rate limit.
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. The Haiku 5.5 price on screen is real ($0.10/MTok input for prompts up to 100k tokens, vs $1 for Haiku 4.5), and routing chores to Haiku subagents is a real, documented Claude Code pattern. But the specific skill is never named (it's gated behind "comment LIMIT"). "Double your usage" and the "83%" figure are unsupported. API per-token prices do not map one-to-one onto subscription usage limits.

### Post description
> Comment "LIMIT" to get the link!
>
> Claude is so useful LLM but 99% of people consume the limit in no time but I found an AI hack that changes everything!!!
>
> #aitips #claude #claudeai

### Audio
The creator speaks throughout, in English. Whisper's "swords" means "sorts".
- [0.0–4.7] "You can now double your Claude usage for free and never waste your limit again"
- [4.7–10.7] "because right now Opus handles everything even renaming a file and every one of those eats into your limit."
- [10.7–16.5] "So someone built a skill that sorts every task first."
- [16.5–23.0] "The easy stuff like searching files and reading logs get sent to **Haiku 5.5** and only the real thinking goes to Opus."
- [23.0–29.2] "And here's the thing Haiku 5.5 costs 90% less per token than the old one so all that easy work barely touches your limit."
- [29.2–34.5] "Same plan way more done before you hit the wall. Now comment limit and I'll send you the link."

### On-screen content, page by page
The upper half holds animated cards and the lower half the talking head with word-by-word subtitles.
**Pages 1–2 (0.0–1.3s):** Dark network graphic, then "**YOUR CLAUDE USAGE**" with a huge green "**2×**". Subtitle "You can now".
**Page 3 (1.3–2.6s):** Claude logo (orange asterisk tile) bursting. Subtitle "your Claude".
**Page 4 (2.6–4.3s):** Card "✳ Claude · weekly usage" with a red banner "**LIMIT REACHED**". Days Mon–Sun, Wed highlighted, Thu/Fri locked. Subtitle "and never waste".
**Page 5 (4.3–10.5s):** "**Its most expensive brain.**" over a gold coin "**Opus**" with a "search files" tag. Subtitle "Because right".
**Page 6 (10.5–10.7s):** "**Even renaming a file.**" A `rename file.txt` chip over a bitten Opus coin, red sticker "**Opus for THIS?!**". Subtitle "into your limit".
**Page 7 (10.7–14.6s):** Black, then the talking head. Subtitle "into your limit".
**Page 8 (14.6–22.0s, from 2-fps frames):** Banner "**HAIKU TAKES THE CHORES**". A shop-like "✳ **SKILL**" machine taking a "search files" ticket. Then a funnel labelled "**SORTER**" with the texts "**Haiku does the chores.**" and "**Opus does the thinking.**" Subtitle "first".
**Page 9 (22.0–30.0s):** Banner "**FROM $1 TO $0.10**". "$1.00" counts down to "**$0.10**", with pixel characters in "OPUS 5.5" hard-hats. Pricing table: **Claude Haiku 5.5** ("For high-volume,…"): Input "**$0.10 / MTok** for prompts up to 100,000 tokens" (circled red), Output "**$0.50 / MTok**"; **Claude Haiku 4.5**: Input "**$1 / MTok**", Output "**$5 / MTok**". Red stamp "**-90% PER TOKEN**". Subtitle "And here's".
**Page 10 (~30.0s):** Banner "**SAME PLAN, MORE WORK**". Scoreboard "JOBS 0" and "LIMIT **83%**". Pixel workers racing over hurdles ("OPUS 5.5" hat vs a blue-cap worker). Subtitle "Same plan".
**Page 11 (30.0–32.1s):** Dark card "**OPUS VS OPUS + SUBAGENTS**" with chips "✓ Same task", "✓ Same result". Subtitle "Same plan".
**Page 12 (32.1–34.5s):** Talking head. Subtitle "hit the wall".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude Haiku 5.5 | model | audio 16.5s; pages 8–9 | Real. Released 2026-10-07 per several outlets. Priced **$0.10 input / $0.50 output per MTok for prompts ≤100k tokens**, rising to $0.50 / $2.50 above 100k. Batch halves it. One source notes a newer tokenizer yields about 30% more tokens than Haiku 4.5, which trims the real saving. |
| Claude Haiku 4.5 ($1 / $5 per MTok) | model | page 9 | Correct list price. So "-90% per token" is accurate for input under 100k, and output is also -90%. |
| Opus 5.5 | model | pages 9–10; audio | Anthropic's current flagship (the post's "most expensive brain"). |
| The "skill that sorts every task" | skill (unnamed) | audio 10.7s; page 8 | **Not identified.** No name, repo or handle on screen or in the caption. The same effect is native to Claude Code: the built-in **Explore** subagent already runs on Haiku for search and read-only work, custom subagents can set `model: haiku` in frontmatter, and `CLAUDE_CODE_SUBAGENT_MODEL` sets a default. Several community "model-router" skills and agents do the same. |
| "2×", "LIMIT 83%", "Same task / Same result" | claims/graphics | pages 1, 10, 11 | Illustrative. No measurement, source or methodology. |
| "LIMIT" keyword | CTA | caption; audio 29.2s | Auto-DM with "the link". |

### What's being promoted / the funnel decoded
- "Comment LIMIT to get the link" withholds the skill's identity so that viewers comment (engagement plus DM-list building). Most likely the link is a GitHub skill or a creator's resource page. There's no sign of a paid product in the post, but it couldn't be confirmed without engaging. You can get the same result without the link by defining Haiku subagents yourself, or relying on Claude Code's built-in Explore/Haiku subagent.

### Verification & insights
- **Price claim: accurate** (Haiku 5.5 vs Haiku 4.5, input under 100k tokens). The narration says "costs 90% less per token than the old one", which is correct relative to Haiku 4.5, not relative to Opus.
- **"Double your Claude usage for free": unsupported.** Subscription limits are usage-weighted by model, so shifting chores to Haiku does stretch a plan. How much depends on what share of your work is "chores". The orchestrating Opus session still reads the subagents' results, and Claude Code already sends much exploration to Haiku by default.
- **"Opus handles everything, even renaming a file":** only if your main model is Opus and you don't use subagents. The built-in Explore subagent and model settings (e.g. `/model`, `opusplan`-style modes) already split the work.
- **"Same task, same result":** not generally true. Haiku makes more mistakes on ambiguous work, and a mis-sorted task can cost a retry.
- **Not verified:** which skill the DM delivers.

---

<a id="e-deim3srdnn-"></a>

## DeiM3sRDNn- | @imjonathanacuna | Claude Code "ultracode" walkthrough: /config → Dynamic workflows + Ultracode keyword trigger = true, then /effort ultracode
- **Link:** https://www.instagram.com/p/DeiM3sRDNn-/
- **Account:** @imjonathanacuna (Jonathan Acuña - Doctor AI) · **Posted:** 2026-10-16 · **Type:** reel (29.4s, 20 scene pages, a phone video of a laptop terminal)
- **Caption source:** full (Instagram)
- **Category:** AI tools
- **Verdict:** PARTLY TRUE. "ultracode" is a real Claude Code effort option (xhigh effort plus dynamic-workflow orchestration), but it isn't a "secret hidden menu". It's a documented setting, and it can use substantially more tokens.

### Post description
> Claude has a hidden menu called ultra code and most people never turn it on.
>
> Here is how I unlock it in two steps.
>
> Step 1: Type forward slash config. Go down to dynamic workflows and hit tab. Go down to ultra code keyword trigger and set it to true.
>
> Step 2: Type forward slash effort and hit tab. You will see ultra code show up. Press enter.
>
> Once you do this, look on the right hand side of your screen. It will say ultra code right there. That means it is active.
>
> This is a setting Claude does not show you by default. I use it to get more out of every prompt I run.
>
> Bookmark this one so you can follow the steps next time you open Claude.
>
> #AI #Claude #Business #Productivity #Tech #Automation

### Audio
The creator's voiceover (English): [0.0] "With Claude we need to unlock a secret menu. We need forward slash config and then you're going to go down dynamic workflows then hit tab and then go down to ultra code keyword trigger and make that true." [10.6] "These two things will unlock the secret hidden menu of ultra code in Claude." [16.1] "Now I'm going to do forward slash effort and then hit tab, notice there's ultra code there, ultra code and press enter ready there we go." [20.8] "So if you look on the right hand side notice it says ultra code in the right hand side now."

### On-screen content, page by page
A persistent overlay shows the Claude logo and the title **"How to Unlock Claude's Secret Power"**. Burned-in word captions run ("NEED /CONFIG", "DOWN DYNAMIC", "YOU LOOK", "ON THE RIGHT-HAND SIDE", "IT SAYS").
**Page 1 (0–3.2s):** The Claude Code terminal inside the Warp terminal app. Status bar: "ctx 94%", "Opus 5 (1M context)", "effort xhigh", "auto mode on (shift+tab to cycle)", "5h 0% (4h57m)", "7d 65%". The session shows a "Read(/Users/jonathanacuna/.claude-os/AI-AGENT-INTEGRAT…)" call and the reply "Hey! Remote control is connected – I can drive this session…", "Registry's loaded (cam-bot token, Firecrawl, TickTick, …) what are we working on?" A remote-session link to claude.ai/code is visible at the top: **[REDACTED – a private Claude Code session link is visible on screen; the creator exposed it]**. No key or token value is visible; "cam-bot token" is only a name.
**Page 2 (3.2–4.4s):** The slash-command picker, listing /superpowers:brainstorming, /writing-emails, /superpowers:writing-plans, /dream ("The daily Dream review…"), /graphic-artist ("…generating AI … (Nano Banana Pro)") and /add-dir. Caption: "NEED /CONFIG".
**Page 3 (4.4–5.6s):** The /config Settings panel (tabs: Status, Config, Usage, Stats): Auto-compact; Switch models when a message is flagged = true; Show tips = true; Reduce motion = true; Thinking mode = false; Prompt suggestions = true; Rewind code (checkpoints) = true; Session recap = true; **Dynamic workflows = true**; "28 more below".
**Pages 4–5 (5.6–16.1s):** Scrolled further: **Ultracode keyword trigger = true**; Dynamic workflow size = medium (default). Caption: "DOWN DYNAMIC". The transcript then shows "Set workflows to on" and "Set ultracodeKeywordTrigger to on".
**Pages 6–8 (16–19s):** The `/effort` argument hint reads **[low|medium|high|xhigh|max|ultracode|auto]**.
**Pages 9–12 (19–22s):** `/effort ultradecode` (a typo) returns "Invalid argument: ultradecode. Valid options are: low, medium, high, xhigh, max, ultracode, auto". Then `/effort ultracode` returns **"Set effort level to ultracode (this session only): xhigh + dynamic workflow orchestration"**.
**Pages 13–20 (22–29.4s):** The camera pans to the right of the status bar, which shows "+ ultracode · xhigh effort + dynamic workflows for maximum thoroughness", the label **"ultracode"**, "57167 tokens" and "/rc active". Captions: "YOU LOOK … ON THE RIGHT-HAND SIDE … IT SAYS".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude Code `/config` → Dynamic workflows, Ultracode keyword trigger | settings | caption, audio 0–10s, pages 3–5 | Real settings in current Claude Code. Dynamic workflows (announced by Anthropic; covered by IT Brief) let Claude write and run an orchestration script that fans work out to many subagents. |
| `/effort ultracode` | command | caption, audio 16s, pages 6–12 | Real. Per InventiveHQ's guide (which quotes the docs) and the on-screen output, it is "xhigh + dynamic workflow orchestration", for this session only. It is offered only on models that support xhigh. Guides note that workflows can consume substantially more tokens and that Claude Code asks for confirmation on first trigger. Admins can disable it via managed settings. |
| Opus 5 (1M context), effort xhigh, auto mode | status bar | page 1 | The model and settings in the creator's session. |
| Warp | terminal app | page 1 | A third-party terminal. |
| /superpowers:*, /dream, /graphic-artist, /writing-emails | custom commands | page 2 | The creator's installed plugins and skills ("superpowers" is a public plugin; the others look personal). |
| Firecrawl, TickTick | services | page 1 | Integrations the creator has loaded. |

### What's being promoted / the funnel decoded
There's no CTA beyond "Bookmark this". The account ("Doctor AI") runs comment-for-DM funnels in other posts (see DdPvXGJS6JU). His business is **Simple Tech Skills** (simpletechskills.com, branded "Doctor AI"). It offers an email opt-in for "22 Free Claude Training Videos" plus a bonus e-book, "How to Build an App With AI That Businesses Pay $5,000 For", and upsells "The Academy", consulting, implementation calls and a content-automation app called "Cam". The "cam-bot" visible in his terminal likely belongs to that app. This post itself is engagement content.

### Verification & insights
- The steps match the real Claude Code UI. Calling it a "hidden menu… Claude does not show you by default" is hype: ultracode is a listed `/effort` option once the settings are on, and per the docs it's a deliberate opt-in because of token cost.
- The "get more out of every prompt" claim is misleading. Ultracode is meant for large, substantive tasks. For ordinary prompts it mainly burns more usage (the status bar shows 65% of the 7-day limit already used).
- Privacy: the creator's video exposes a claude.ai/code remote-session URL and a remote-control-enabled session. That's redacted above, and it's a security lapse on the creator's part.
- Not verified: exact token multipliers. Sources disagree on details (MindStudio's description conflicts with the docs-quoting guides).

---

<a id="e-dec1xw2ucnw"></a>

## Dec1xW2ucNw | @avigrondin | "I tested every viral Claude cheat code, 99% don't work; here are 5 that do": ELI5, Pre-mortem, Steelman, Red Team, First Principles, with a "comment SECRETS" DM funnel
- **Link:** https://www.instagram.com/p/Dec1xW2ucNw/
- **Account:** @avigrondin (display name not in the mirror data) · **Posted:** unknown (not in the mirror data) · **Type:** reel (72.5s, 25 scene pages; split screen, motion graphics above, talking head below)
- **Caption source:** possibly truncated (mirror), but the 120-character caption ends with hashtags and reads as complete
- **Category:** AI tools
- **Verdict:** PARTLY TRUE: the five "codes" are not secret or special Claude commands. They are long-established thinking techniques (Explain Like I'm 5, pre-mortem, steelmanning, red-teaming, first-principles reasoning) that you can ask any chatbot to apply in plain words. They do work as prompt instructions, but the "cheat code" and "I tested every one" framing is engagement bait for a DM list.

### Post description
> Comment the word "SECRETS" and I'll send you 10 more of these 👇🤯
>
> #claude #ai #chatgpt #artificialintelligence #business

### Audio
The creator speaks to camera (English); burned-in subtitles. No identifiable music. Condensed into timestamped notes:
- [0.0–7.3] Hook: "Listen, I tested every viral Claude cheat code, and I'm gonna be honest with you, **99%** of them do not work." Promises five that do.
- [7.3–19.9] 1. **ELI5**: Claude explains any concept as if to a five-year-old; he suggests it for complex things like tax law, contracts or coding concepts.
- [19.9–32.2] 2. **Pre-mortem**: add before any plan or idea; Claude pretends the project failed "over six months ago", works backwards to explain why, and surfaces blind spots early.
- [32.2–42.0] 3. **Steelman** (his favourite): typing "steelman the other side" makes Claude argue the strongest opposing view; "pretty brutal" for spotting weak thinking.
- [42.0–52.9] 4. **Red team**: adding "red team this" before a pitch or decision makes Claude attack it from every critic's angle, "like having a board of skeptics review your work in 30 seconds."
- [52.9–68.1] 5. **First principles**: adding "break this down from first principles" makes Claude drop generic advice and rebuild from what is actually true; "the one that Elon Musk talks about constantly", for original thinking instead of "recycled internet answers".
- [68.1–72.4] CTA: "Follow me and comment the word **secrets** and I'll send you **10 more** of these secret codes."

### On-screen content, page by page
The top half is a dark green "terminal" motion graphic; the bottom half is the creator on camera with a keyword caption bar.
**Pages 1–5 (0.0–7.3s):** "// VIRAL CLAUDE CHEAT CODES / I tested every" over a wall of random slash-codes (e.g., "/9ZP8", "/K9ZT", "/T5D5U"). A big "**99%**" appears, then "The [99%] DON'T WORK" with codes crossed out. Caption bars: LISTEN, WITH YOU, 99% OF THEM, HERE ARE THE.
**Pages 6–7 (7.3–19.8s):** "// CHEAT CODE 01 – DECODING" scramble ("BKP5" resolving), then "// 01 · ELI5" over an illustration of dense legal text ("Art. IX", "§ 4.2(b)", "§ 1(a)", "cl. 9.1", "[12]") collapsing. Caption bars: THE FIRST ONE'S, OLD.
**Pages 8–10 (19.8–32.1s):** "// CHEAT CODE 02 – DECODING" ("0BWTH5R7HB"), then "// 02 · PRE-MORTEM": a Claude input box "How can I help you today?" and a radar graphic. Caption bars: THE SECOND ONE, ADD THIS BEFORE, WHY IT FAILED.
**Pages 11–13 (32.1–41.9s):** "// CHEAT CODE 03" ("*SW%P 3SB"), then "// 03 · STEEL MAN": Claude input typing "I think AI is going to replace mo[st marketers]" and a card "YOUR VIEW: **AI is going to replace most marketers.**" Caption bars: THE THIRD ONE'S, FAVORITE, THIS ONE'S PRETTY.
**Pages 14–16 (41.9–52.9s):** "// CHEAT CODE 04" (red, "%RW 7QDD"), then "// 04 · RED TEAM": a Claude input, then five frowning critic avatars around a "YOUR WORK" card. Caption bars: THE FOURTH ONE'S, IF YOU ADD, IT'S LIKE HAVING.
**Pages 17–20 (52.9–68.1s):** "// CHEAT CODE 05 – DECODING" ("ZAG5K GM2E277TVQ") resolves to "UNLOCKED: **FIRST PRINCIPLES**", then a quoted "first principles" card and "**ORIGINAL THINKING** (NOT) **RECYCLED INTERNET ANSWERS**". Caption bars: THE FIFTH ONE, PRINCIPLES, THIS IS THE, IT'S HOW YOU.
**Pages 21–25 (68.1–72.5s):** A mock Instagram comment UI: "@avigrondin ✓ Following", typing "**SECRETS**", a big "SECRETS" sticker, and a locked "🔒 10 more secret codes". Caption bars: FOLLOW ME AND, SECRETS, AND I'LL SEND.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| ELI5 | prompt technique | audio 7.3s, pages 6–7 | "Explain Like I'm 5", a Reddit-era convention. Claude and other chatbots understand it, but it is not a Claude feature. |
| Pre-mortem | prompt technique | audio 19.9s, pages 8–10 | Gary Klein's project pre-mortem (imagine the project failed, explain why). A legitimate decision technique; asking for it works in any LLM. |
| Steelman ("steelman the other side") | prompt technique | audio 32.2s, pages 11–13 | Constructing the strongest version of the opposing argument; standard debate practice |
| Red team ("red team this") | prompt technique | audio 42.0s, pages 14–16 | Adversarial review borrowed from military and security practice |
| First principles ("break this down from first principles") | prompt technique | audio 52.9s, pages 17–20 | Reasoning from basic truths (Aristotle; popularised by Elon Musk, whom the creator cites) |
| "99% of viral cheat codes don't work" | claim | audio 0.0s, pages 1–5 | No test data shown. Untestable as stated. |
| Comment "SECRETS" (10 more) | CTA | caption, audio 68.1s, pages 21–25 | Automated DM with "10 more secret codes" (a lead magnet) |
| @avigrondin | handle | pages 21–25 | Creator. Bio not retrievable (Instagram 429). |

### What's being promoted / the funnel decoded
- "Follow me and comment SECRETS" triggers a DM automation with a list of 10 more prompt "codes". This is follower growth and DM-list building. No product, price or link appears in the post. The creator's business behind the funnel could not be confirmed (profile not retrievable; web search found nothing).

### Verification & insights
- **All five are real, documented techniques, not Claude "codes".** Typing the bare word (e.g., "ELI5") works only because the model knows the idiom. Describing what you want ("explain this simply", "assume this failed in 6 months and list why", "argue the strongest case against my view", "act as a hostile reviewer", "reason from first principles") is equally effective and more reliable.
- **Contrast with other posts:** unlike "/godmode" or "L99" style "secret codes" (see DX1EfTLJuzV), these five are genuine reasoning frameworks, so the advice is sound even though the framing is hype.
- **Claims vs reality:** "Claude's gonna pretend the project failed over six months ago" is accurate only if you ask for that; the word "pre-mortem" alone may not set the time frame. "Board of skeptics in 30 seconds" is marketing.
- **Could not verify:** the "tested every viral code" claim, and the contents of the DM list.

---

<a id="e-desu2n0t0hi"></a>

## DesU2N0t0hi | @masoncarter.trades | "Printing F*** you money in 15 seconds, no card required": screenshot a TradingView chart and upload it to ChartingPilot AI for a bullish/bearish "signal" (an ad for a paid AI chart-reader)
- **Link:** https://www.instagram.com/p/DesU2N0t0hi/
- **Account:** @masoncarter.trades (Mason Carter) · **Posted:** 2026-10-19 · **Type:** reel (33s, 96 pages; fast cuts). The batch folder only held the cover frame; I downloaded the full video during review.
- **Caption source:** full (Instagram; checked with yt-dlp during review)
- **Category:** AI tools / Trading strategy
- **Verdict:** MISLEADING – a disguised ad for ChartingPilot AI, a paid subscription ($10/wk–$59/mo). An LLM "reading" a chart screenshot is not an edge, and "no card required" only covers the first free read.

### Post description
> The new method fr
> #aitrading #tradingforbeginners #successful #emoney #daytrading

### Audio
Creator's own speech (English, profanity as spoken):
- [0.0–3.1] "Making fuck-you money with a laptop and internet connection in 15 seconds."
- [3.1–10.6] "Like bro, this one fucking trades crazy. And I know what you guys are thinking, I don't have a course, it's not TJR, not Trades by Matt (?), not ICT, none of those trading gurus, I promise."
- [10.6–15.3] "All you need is a phone, laptop, computer, literally anything you have at home, and two brain cells."
- [15.3–20.7] "So step one, you're going to go to tradingview.com, it's completely free. Go to the search bar, type in anything you wanna trade. Launch the chart to this screen."
- [20.7–28.0] "Take a screenshot of the entire chart page and upload it to your AI analyzer. This is the one that I use. Honestly what sucks about it is you only get one for free."
- [28.0–32.8] "Then click the analyze chart button. The AI will give you the signal as well as the setup grade as well. Then take the fucking trade and make some M's."

### On-screen content, page by page
**Pages 1–22 (0–9.4s):** Banner "PRINTING "F*** YOU" MONEY (In 15 seconds) **no card required**" over a MacBook showing a TradingView chart of "SPDR S&P 500 ETF TRUST · 5 · AMEX" (SPY). At about 3.3s, a quick close-up of a positions panel: "Size 23", "Net PnL **+2,875.00 USD**". Captions "connection in 15 seconds", "Like bro, this in one", "fucking trades", "Crazy", "trading gurus", "I promise", "All you need", "literally anything you have at home", "and two brain cells".
**Pages 23–40 (9.4–19.6s):** tradingview.com in the browser, symbol search ("Symbol, ISIN, or CUSIP"; list: SPY, MES1!, NVDA…; tabs Stocks/Funds/Futures/Forex/Crypto). Captions "go to tradingview.com.", "It's completely free.", "type in anything", "you wanna trade", "launch the chart", "to this screen,".
**Pages 41–64 (20.6–26.9s):** The ChartingPilot AI site (tabs "ChartingPilot AI: Your AI ch…", "Chart breakdown – ChartingPilot"; nav Analyze / History / Journal / Admin). Hero: "**YOUR AI CHART ANALYST. THE CALL IN SECONDS.**" — "Pro-level analysis from a screenshot: a bullish or bearish read, the trade plan with entry, stop and target, and a setup score out of 10. Stocks, options, crypto, forex and futures." "★★★★★ 5.0 on Whop", "11,300+ charts read". Upload box "Drop your chart here / Let go to drop it — Tap to choose a screenshot or paste with ⌘V/Ctrl+V — Choose image / Take photo — Try a sample: ES · 15m, BTC · 4h, AAPL · 1D". Captions "of the entire chart page", "then upload it to your A.I. Analyzer.", "This is the one that I use.", "Honestly what sucks about it is you only get one for free."
**Pages 65–76 (27–29s):** Uploaded SPY chart, "Strategy: ChartingPilot AI Bias [Change]", "Add context (optional, sharpens the read)", green "Analyze chart" button (then "Analyzing… Reading the price axis…"). Badges: "30-day money-back guarantee · Results in seconds · Works on your phone"; "WORKS WITH SCREENSHOTS FROM Coinbase, Phone photos, TradingView, NinjaTrader, MetaTrader 5, Think(orswim)"; stats "10,000+ … Seconds … 42 strategies … 24/7 any market, any timeframe".
**Pages 77–96 (29–31.4s):** Result page (URL "…ilot.com/analysis/cmuye1nog0001js097xljeo82", "12d ago"): "SPDR S&P 500 ETF TRUST (AMEX) · 5 minute". "CHARTINGPILOT AI RATING: **BULLISH** — Price is favored to go up from here." Conviction "MEDIUM". "SETUP SCORE **10.0/10** · AI Bias — Textbook conditions. Most checklist… 6/6 ChartingPilot AI Bias rules passed. Scored… AI opinion." Captions "The A.I. will give you the signal", "as well as the set up grade as well.", "Then take the fucking trade", "make some m's." Note the analysis is marked "12d ago", so it's an old saved read, not a live one.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| ChartingPilot AI (chartingpilot.com; whop.com/chartpilotai/chartingpilot) | paid AI tool | audio 20.7s; p.41–96 | AI "chart analyst": upload a screenshot, get a bullish/bearish/neutral call, entry/stop/target, and a setup score. **Pilot $10/week, $25/month, $249/year; Pilot Pro $59/month**; 20 analyses/day; 30-day money-back guarantee; free sample charts; "educational, not financial advice". Operator not named (support@chartingpilot.com). |
| tradingview.com | site | audio 15.3s; p.23–40 | Free charting platform. |
| SPY (5-min), MES1!, NVDA, UK100 | tickers | p.1–40 | Charts and search results shown. |
| "+2,875.00 USD Net PnL, Size 23" | P&L flash | p.~10 (3.3s) | A one-second unverified P&L, not linked to an AI-signal trade. |
| TJR, "Trades by Matt"(?), ICT | named "gurus" | audio 4.4s | Other trading educators, named to set himself apart ("I don't have a course"). |
| "no card required" / "you only get one for free" | claim | title; audio 24.3s | One free read; after that it's a paid subscription. |

### What's being promoted / the funnel decoded
The video itself is the funnel: it walks viewers to ChartingPilot AI and shows its landing page, pricing badge and "5.0 on Whop". It's sold through Whop, which runs an affiliate program that creators commonly use. That, plus the "I don't have a course, I promise" framing, strongly suggests a paid or affiliate placement, though no link or disclosure is in the caption. The cost is $10/week to $59/month.

### Verification & insights
- Fetched chartingpilot.com, which confirmed the product, plans and prices, the Whop listing, and its "not financial advice" disclaimer.
- A vision-LLM reading a screenshot sees only past candles; it gives an opinion, not a statistically validated signal. The "10/10 textbook" read shown was 12 days old, and nothing about its outcome is shown. No win rate, sample or track record is given.
- "Take the trade and make some M's" with no position sizing or risk control is reckless. 5-minute SPY moves are mostly noise.
- "11,300+ charts read" and "5.0 on Whop" are vendor-reported numbers.
- Could not verify: whether the creator is paid or an affiliate; the operator's identity.

---

<a id="e-dzqnqskbxne"></a>

## DZQnQSkBxnE | @wassimyounes_ | "turbovec" (Rust/Python vector index using Google's TurboQuant) falsely pitched as shrinking a 31GB LLM ("Gemma 4") to 4GB; comment "TURBO"
- **Link:** https://www.instagram.com/p/DZQnQSkBxnE/
- **Account:** @wassimyounes_ (display name not in data) · **Posted:** unknown (not in fetched data) · **Type:** reel (35s, 3 scene pages; 2-fps frames reviewed)
- **Caption source:** full (Instagram, fetched after the first review)
- **Category:** AI tools
- **Verdict:** MISLEADING – turbovec is real, MIT-licensed and free, but it compresses *embedding vectors in a search index* (10M docs: 31 GB → 4 GB), not LLM weights; the on-screen "Shrink LLM by 96%" / "Gemma 4 31GB shrink to 4GB" and spoken "your 31 GB RAM LLM into 4 GB" are wrong

### Post description
> Comment “TURBO” and I’ll send it over. 👇
>
> A new open-source tool just squeezed a 31GB vector database down to 4GB using Google’s TurboQuant research — and it searches faster than FAISS. 🧠
>
> It’s called turbovec: a Rust vector index with Python bindings that compresses your RAG embeddings up to 16× with zero training.
>
> […]
>
> 📦 pip install turbovec — Rust speed, Python bindings, MIT-licensed and free
>
> […]
>
> Comment “TURBO” — the repo + the one-line install, in your DMs. 👇

The rest of the caption, in summary:
- It frames the list as "why every RAG builder is bookmarking it", with these emoji bullets:
  - 🧠 a 10M-document corpus fits in about 4GB of RAM instead of 31GB, i.e. "up to 16×" smaller embeddings;
  - ⚡ beats FAISS by 12–20% on ARM and matches or beats it on x86 (faster nearest-neighbour search);
  - 🔧 zero training and instant online ingest: added vectors are indexed immediately, with no rebuilds or tuning;
  - 🔒 100% local: no managed vector DB, no data leaving the machine, built for air-gapped RAG.
- A closing line says Google publishes the research and an open-source developer ships it to your laptop ("That’s the whole game now").
- Hashtags: #RAG #VectorDatabase #AIengineering

*Caption condensed – full text is on the original post.*

### Audio
Creator speaking English (green-screen over the content):
- [0.0–5.7] "Drop your huge language models into four gigabytes, so [a] bad computer could run this now."
- [5.9–13.1] "So take your 31 gigabyte RAM LLM into four gigabytes, searches are faster than FAISS." (Whisper: "face")
- [13.3–18.6] "So what's interesting is the more technology increases, the more we're gonna realize that LLMs are gonna get quantized,"
- [19.4–26.2] "compressed and condensed in such a way where it's gonna be extremely optimized for bad hardware. If you guys do want to learn"
- [26.2–31.6] "more and download this, comment down below 'turbo' and I'll send this over, because this is wild."
- [31.6–34.4] "This is the start of a new beginning on many things."

### On-screen content, page by page
**Page 1 (0–4s):** X post by **0xMarioNawfal / @RoundtableSpace**: "GOOGLE JUST FOUND A WAY TO SHRINK 31GB OF AI MEMORY DOWN TO 4GB", with a screenshot of the turbovec GitHub README. Overlays: red "Shrink LLM BY 96% hardware", white "GEMMA 4 31GB SHRINK TO 4GB".
**Page 2 (4–7s):** Same tweet, overlays gone; creator pointing at the turbovec header.
**Pages 3+ (7–35s):** Full-screen scroll of the turbovec README (GitHub, dark mode). Tabs: README · Contributing · MIT license. Header "turbovec – Google's TurboQuant for vector search"; badges "license MIT", "pypi v0.7.0", "crates.io v0.8.0", "paper arXiv". Text: "A 10 million document corpus takes 31 GB of RAM as float32. turbovec fits it in 4 GB – and searches it faster than FAISS." / "turbovec is a Rust vector index with Python bindings, built on Google Research's TurboQuant algorithm – a data-oblivious quantizer that matches the Shannon lower bound on distortion, with no codebook training and no separate train phase." Bullets: "Online ingest. Add vectors, they're indexed – no train step, no parameter rebuilds as the corpus grows." "Faster than FAISS. Hand-written NEON (ARM) and AVX-512BW (x86) kernels beat FAISS IndexPQFastScan by 12–20% on ARM and match-or-beat it on x86." "Filter at search time. Pass an id allowlist (or a slot bitmask)… You always get up to k results from the allowed set…" "Pure local. No managed service, no data leaving … open-source embedding model for a fully air-gapped RAG stack." "Building RAG where privacy, memory, or latency matter…" then "Python – `pip install turbovec`". From ~13s a white sticker "Comment "turbo"" stays on screen. The last page is black (end card).

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| turbovec (github.com/RyanCodrai/turbovec) | repo | caption, pages 1–3 | Real. MIT, © 2026 Ryan Codrai; HEAD c3b043b, 2026-10-06 "release: 1.1.2"; PyPI 1.1.2 ("Fast vector quantization with 2-4 bit compression and SIMD search"); crates.io first published 2026-04-13, ~78k downloads |
| `pip install turbovec` | command | caption, page 3 | Correct install command |
| TurboQuant (arXiv 2504.19874) | paper | caption, README badge | "TurboQuant: Online Vector Quantization with Near-optimal Distortion Rate", Zandieh, Daliri, Hadian, Mirrokni (Google Research), 2025-04-28 |
| FAISS / IndexPQFastScan | library | caption, audio, README | Meta's vector search library; README in the video says 12–20% faster on ARM; current README says 4.4× FastScan at 4-bit |
| 31 GB → 4 GB | number | caption, audio, tweet, overlay | True only for **10 M × 768-dim float32 embeddings** (README), i.e. ~7.8× compression of vectors at 4-bit |
| "Shrink LLM BY 96%" / "GEMMA 4 31GB SHRINK TO 4GB" | claim | page 1 overlay, audio 0–13s | False framing: turbovec doesn't load or compress any LLM; Gemma is not mentioned in the repo |
| "Up to 16× smaller" embeddings, "zero training" | claim | caption | Consistent with the README: 15.5× at 2-bit, 7.8× at 4-bit (31 GB → 4 GB is the 4-bit figure); TurboQuant is data-oblivious, so there is no training step |
| "100% local … built for air-gapped RAG" | claim | caption | True: it's an embedded library with no service; the README's "Pure local" section says the same |
| "MIT-licensed and free" | claim | caption | True (LICENSE MIT) |
| 0xMarioNawfal / @RoundtableSpace | X account | page 1 | Aggregator tweet, also hyperbolic ("Google just found a way…") |
| "Comment TURBO" | CTA | caption, audio 26–31s, sticker | Comment-to-DM automation |

### What's being promoted / the funnel decoded
"Comment TURBO → I'll send it" (the caption specifies "the repo + the one-line install, in your DMs") delivers the public GitHub link (github.com/RyanCodrai/turbovec) or `pip install turbovec`, both freely available. The account is an AI-tips creator farming engagement through keyword-DM automation. No paid product found in this post; web search found nothing indexed for @wassimyounes_.

### Verification & insights
- Cloned repos/turbovec: LICENSE MIT; README now reads "Ten million 768-dimensional embeddings take 31 GB of RAM as float32. turbovec holds them in 4 GB and searches them 4.4× faster than FAISS, at matching recall"; 7.8× smaller at 4-bit, 15.5× at 2-bit; no training step; local library. It's a RAG/semantic-search component.
- Claims vs reality: the caption is accurate ("vector database"); the video's voiceover and overlay are not. It can't make a large LLM run on weak hardware. The TurboQuant paper does also cover KV-cache quantization in LLM inference, but that isn't what turbovec does.
- Who would use it: anyone running a large local embedding index (RAG) who wants a FAISS alternative with low RAM.
- Same 0xMarioNawfal-tweet-reaction format as DbTfPs-MKGk (@its.abdechan).
- Full caption (fetched later) is accurate throughout: it says "vector database" and "RAG embeddings", not LLM, and its numbers match the README the video showed. The misleading LLM framing exists only in the video's voiceover and overlay, so the verdict stands.
- Not verified: account details, upload date.

---

<a id="e-ddhc7w1otqx"></a>

## DdHC7W1OTqX | @atsmatrix | "Data Analysis Bot / Deezzex" sci-fi dashboard animation claiming 148K rows/sec, 6.4K queries/min, 57% clean signal and a "$30k exit". The screen itself is labelled "synthetic telemetry · illustrative schematic · not a product screen".
- **Link:** https://www.instagram.com/p/DdHC7W1OTqX/
- **Account:** @atsmatrix (ANYELO ENCARNACION | ATS-MATRIX) · **Posted:** 2026-09-10 · **Type:** reel (27.9s, 1 continuous animated screen; 56 frames at 2 fps reviewed, plus the cover image)
- **Caption source:** full (Instagram, via yt-dlp on 2026-10-21; it matches the mirror text)
- **Category:** AI tools
- **Verdict:** MISLEADING. The caption calls it "the dashboard" of a built product with a "$30k exit". The video's own footer says "SYNTHETIC TELEMETRY" and "ILLUSTRATIVE SCHEMATIC · NOT A PRODUCT SCREEN". Its derived arithmetic is internally inconsistent. Nothing about the "$30k exit" is evidenced. The creator's public repo is a particle animation, not an AI or data system.

### Post description
> broke builder. $30k exit. one swarm.
> 148K rows/sec. 6.4K queries/min. 57% clean signal.
> built in weeks. private for now.
> this is the dashboard.
> next drop tomorrow.
> worth it?
> . . . #ATSMatrix #AIAgents #DataViz #Quant #BuildInPublic

### Audio
Music only (ambient/electronic). No speech. Whisper produced only a hallucinated "so so so". The song is not named.

### On-screen content, page by page
One continuous screen with live-ticking numbers. The 1206×2144 cover still and the 1080×1356 video frames were both read.
**Header:** "■■ DATA ANALYSIS BOT / DEEZZEX", legend "■ INGEST ■ RESOLVED", timer "T 00:02.57 · F 0154 / 1800", "STREAM → CLUSTER MODEL".
**KPI tiles:**
- "ROWS PARSED · PER SECOND **148 K**" (fluctuates 147–149K), sub-label "rolling mean · n = 6000 streams"
- "QUERIES RESOLVED · PER MINUTE **6.4 K**" (6.2–6.4K), sub-label "parse · join · dedupe · other"
- "SIGNAL RATIO · CLEAN + NOISE **58 %**" (56–58%), sub-label "**58.18 % · ratio of stream averages, not a loss rate**"

**Strip:** "SIM CAM x +1224.63 y +508.79 z +6987.12" · "PHASE INGEST / CLUSTER · MODE SPIRAL STREAM MODEL · PRG 0.086".
**Centre:** A particle "tree" or spiral of circles fed by a bright fibre stream. KEY list: SCHEMA DRIFT, NULL RATE, JOIN KEYS, DEDUPE, LATENCY p95, OUTLIERS, TOKENS/S, SESSIONS, RETRIES, CARDINALITY, EMBEDDINGS, TIMEOUTS, COLD ROWS.
**Bottom panels:**
- "CLUSTER LOAD · ROWS/S · SELF-REPORTED": PARSE 2.3 M, JOIN 2.2 M, DEDUPE 1.7 M, OTHER 0.2 M; "Σ 6.4 M / min = 58 % of 11 M ingested · incl. re-parsed rows · post-dedupe".
- "SIGNAL · STREAM TELEMETRY": THROUGHPUT / LATENCY / ERRORS sparklines; "CAM 947 u/s · MODEL TELEMETRY".
- "WINDOW · DERIVED": "6.4 M × 60 min = 384 M / h", "384 M + 40 h = 9.6 M / wk", "assumes 24 h / day · 7 d / wk · derived". The video shows 6.3 M / 378 M / 9.4 M variants.
- "STATE LOG · NAMED PHASES": 00:00 INPUT n = 6000 to model; 00:05 FORK 6.4 M / min | 58 %; 00:10 CONTEXT 2.3 M | attach schema; 00:15 REVIEW 2.2 M | verify output; 00:20 DEDUPE 1.7 M | collapse rows; 00:24 ANNUAL 378 M / h.

**Progress bar:** "2.6 OF 30 S · 60 FPS BASIS · DERIVED".
**Footer:** "SOURCE · DEEZZEX STREAM INDEX 2026 · **SYNTHETIC TELEMETRY** · n = 6000 · EU · US · UK" and, on the right, "**ILLUSTRATIVE SCHEMATIC · NOT A PRODUCT SCREEN**".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "Data Analysis Bot / Deezzex" | product name | screen header | No public product found. The screen labels itself synthetic and illustrative. |
| ATS Matrix / ATSMATRIX Technologies | brand | handle, hashtag | Brand of Anyelo Encarnacion. Public GitHub `anyel1to/ATSMATRIX-NEXUS`. |
| github.com/anyel1to/ATSMATRIX-NEXUS | repo (found by search, not in the post) | n/a | `git ls-remote` OK, shallow-cloned. MIT license. Last commit 2026-08-25: "chore: reclassify language to JavaScript for professional appearance (override HTML detection)". A single `index.html` (~17 KB) canvas animation of "200+ AI agents" (colored particles with an affinity matrix). A third-party review (starlog.is) calls the "AI agent" framing "pure marketing fiction… This is theater, not infrastructure." Not executed. |
| 148K rows/sec · 6.4K queries/min · 57–58% clean signal | claims | caption, KPI tiles | Animated numbers labelled "synthetic telemetry" and "self-reported" |
| "$30k exit" | claim | caption | Unevidenced. No buyer, product or listing is named. |
| "384 M + 40 h = 9.6 M / wk" | on-screen arithmetic | window panel | Nonsensical. 384M per hour × 40 h would be about 15.4 billion, and the panel also says it assumes 24 h × 7 d. |

### What's being promoted / the funnel decoded
- "Build in public" hype for the creator's personal brand, ATS Matrix ("next drop tomorrow", "private for now", "worth it?"). The likely aims are to attract freelance or build clients, or buyers for "agent swarm" dashboards. No price, link or product is given. Engagement at fetch time: 2,736 likes, 50 comments.

### Verification & insights
- The decisive evidence is in the post itself. The footer states it is synthetic, illustrative and not a product screen, which contradicts the caption's "this is the dashboard".
- The numbers mix units (rows/sec vs queries/min vs "M/min"), and the derived weekly figure is arithmetically wrong. These are hallmarks of decorative data visualisation.
- The creator's public code is a physics or particle visualisation, and its commit history includes changing the repo language label "for professional appearance". There is no evidence of a data-processing system or an exit.
- Could not verify: anything about "Deezzex", or the $30k exit.

---

<a id="e-deh0dqex5oq"></a>

## Deh0DQEx5OQ | @alexpetkov.ai | "5 secret codes for Claude": /godmode, /ghost, L99, Artifacts, OODA, demoed in the Claude app, with a "comment Codes" DM funnel (not real Claude features)
- **Link:** https://www.instagram.com/p/Deh0DQEx5OQ/
- **Account:** @alexpetkov.ai (display name not in data) · **Posted:** 2026-10-15 (decoded from the post ID) · **Type:** reel (41.3s, 27 scene pages; talking head plus phone screen recordings of claude.ai)
- **Caption source:** The mirror flagged it as possibly truncated, but the caption is short and complete-looking (it ends with the CTA). Instagram returned 429 on re-fetch.
- **Category:** AI tools
- **Verdict:** MISLEADING. None of these are "secret codes". Claude has no hidden /godmode, /ghost or L99 modes. They are just extra words in the prompt that Claude interprets loosely, and the video's own screens show this. "Artifacts" is a real, documented feature, not a code. "Passes AI detectors" is an unsupported claim. This is the same script as other "secret Claude codes" posts in this collection (e.g. DX1EfTLJuzV by @cindiezhu), with the same "comment CODES for 100 more" funnel.

### Post description
> My top 5 secret codes for Claude 👇🏻
>
> 1. /godmode
> 2. L99
> 3. OODA
> 4. Artifacts 
> 5. /ghost
>
> Comment "Codes" and I'll send you a link to 100 more!

### Audio
The creator speaks to camera (English). Full transcript:
- [0.0–8.8] "Here are 5 secret codes for Claude. 1. Slash God mode. Just put this before your prompt and it's gonna lock [unlock] Claude's most aggressive and comprehensive response style."
- [8.8–15.1] "2. Slash Ghost. Just put this before your prompt and you're gonna get a humanized answer that even passes AI detectors."
- [15.1–21.4] "3. L99. Just put this at the end of your prompt and Claude is gonna respond to the most advanced expert level possible."
- [21.4–28.2] "4. Artifacts. Just put this after your prompt and Claude is gonna build your working app, game or dashboard, live within the chat."
- [28.2–36.6] "And 5. OODA. Just put this before your prompt and Claude is gonna run a military decision framework on your problem and then tell you exactly how to solve it."
- [36.6–41.0] "If you want 100 more of these secret code commands, comment codes down below and I'll send them over to you."

### On-screen content, page by page
Burned-in captions repeat the speech ("HERE ARE FIVE", "SECRET CODES FOR CLAUDE" with the Claude app icon, "NO. 1 IS", "JUST PUT THIS", "BEFORE YOUR PROMPT", "CLAUDE'S MOST AGGRESSIVE", "AND COMPREHENSIVE", …, "IF YOU WANT", "COMMENT CODES DOWN"). The screen recordings are from the Claude iOS app (claude.ai, Private; model "Sonnet 4.6"; "Free plan · Upgrade" visible on one screen).

**Pages 1–6 (0.0–3.8s):** Talking head and the Claude logo.
**Pages 7–10 (3.8–8.7s), /godmode:** The prompt "**/godmode Which skills do people pay for on Fiverr, Upwork, Toptal?**" (a slash-command menu briefly shows "add-files – Open file picker"). Claude's status lines read "Working · Reading frontend design skill · Creating a godmode-style immersive dark dashboa[rd]…", and it generates HTML/CSS (`<title>Skills That Pay – Freelance Intelligence</title>`, CSS variables `--bg:#060608`, `--fiverr:#1dbf73`, `--upwork:#6fda44`, `--toptal:#204ecf`). In other words, Claude treated "godmode" as a visual style request.
**Pages 11–13 (8.7–15.1s), /ghost:** The menu shows "add-files" and "skill-creator". The prompt is "**/ghost What type of work in portfolio attracts the most clients?**" Claude ("Searched the web") answers: "It looks like you're asking about ghostwriting portfolios specifically. Here's what consistently attracts the most clients: The types of work that convert best: 1. Thought Leadership & Business Content…". So Claude read "/ghost" as "ghostwriting", not as a humanizer mode.
**Pages 14–16 (15.1–21.4s), L99:** The prompt is "**Which digital products sell well? L99**". Claude: "Working · Reading frontend design skill for high-quality artifact · Creating a bold, dark market-board style artifact…" (CSS code).
**Pages 17–22 (21.4–28.1s), Artifacts:** The prompt is "**Create a super simple mobile game idea for a school project ARTIFACTS**". Claude replies "A fun, fully playable game — right here in the chat! 🎮 … Here's **Bubble Pop!** — a complete, playable mobile game in a single HTML file. How to play: Tap the floating bubbles before they escape. Avoid the 💀 skulls or you lose a heart. Chain pops for a combo bonus! What makes it great for a school project: Simple core mechanic… Escalating difficulty… Juice & feel… Self-contained — just one .html file, no libraries needed". It produces a file "Bubble pop game · Code · HTML · Download", and the game preview "bubble_pop_game – Bubble Pop!" is shown.
**Pages 23–25 (28.1–36.5s), OODA:** A "Portfolio guide · Code · HTML" artifact from before, then the prompt "**OODA How to earn money on internet?**" Claude replies "The OODA loop — Observe, Orient, Decide, Act — is a powerful mental model for navigating the messy world of making money online… Wiring the cycle together…"
**Pages 26–27 (36.5–41.3s):** Talking head, "IF YOU WANT … COMMENT CODES DOWN".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude (claude.ai app, Sonnet 4.6) | AI app | throughout | Anthropic's assistant. The UI and model name are as shown. |
| /godmode | "code" | caption; audio 3s; pages 7–10 | Not a Claude feature. Claude interpreted it as a style ("godmode-style immersive dark dashboard"). |
| /ghost | "code" | caption; audio 9.8s; pages 11–13 | Not a feature. Claude interpreted it as "ghostwriting". No evidence of "passing AI detectors". |
| L99 | "code" | caption; audio 16s; pages 14–16 | Not a feature. A meaningless token that Claude may read as "high-level". |
| Artifacts | feature | caption; audio 22s; pages 17–22 | A real Claude feature (artifacts: generated documents, apps, code rendered beside the chat). It triggers on request whether or not you type the word in capitals. |
| OODA | framework | caption; audio 29s; pages 23–25 | John Boyd's Observe–Orient–Decide–Act loop. Typing it simply asks Claude to apply that framework. Not a code. |
| "Reading frontend design skill", "skill-creator" | Claude skills | screen | Real Claude Skills features (built-in skills invoked automatically). |
| Bubble Pop! | generated game | pages 19–22 | An example artifact produced in the demo. |
| @alexpetkov.ai | handle | account | The creator. No website or product found by web search. |

### What's being promoted / the funnel decoded
- "Comment 'Codes' and I'll send you a link to 100 more!" is an engagement-bait comment-to-DM automation. The "100 codes" are most likely a free PDF or Notion list on a lead-capture page (email sign-up). The exact destination could not be identified (no bio link in the data, and web search found nothing). This is the identical script and code list used by other creators (compare DX1EfTLJuzV in this collection), which suggests a copied or templated trend.

### Verification & insights
- Anthropic's documentation lists no such prefix codes. Claude's slash commands exist in Claude Code (e.g. /help, /clear) and as skill invocations, but "/godmode" and "/ghost" are not among them. The video's own screens disprove the claims: "/ghost" was read as ghostwriting, and "/godmode" and "L99" became dark-themed dashboard styling.
- What actually helps: describe the desired depth, tone and format explicitly ("answer as a senior expert, be blunt, include risks"), or ask for an artifact or interactive app. That is what these tokens loosely approximate.
- "Passes AI detectors" is unsupported and ethically dubious; AI-detector results are unreliable either way.
- Not verified: the DM link contents. Nothing was executed.

---

<a id="e-dcrfrpfzyzb"></a>

## DcRFrpfzyZB | @julian.goldie_ | "Claude Code is free with DeepSeek V4 Flash": install OpenCode, use a free OpenCode Zen key, pick DeepSeek V4 Flash Free; funnel to Agent OS / AI Profit Boardroom
- **Link:** https://www.instagram.com/p/DcRFrpfzyZB/
- **Account:** @julian.goldie_ (Julian Goldie) · **Posted:** 2026-08-20 · **Type:** reel (33.6s, 14 pages)
- **Caption source:** full (Instagram, via yt-dlp)
- **Category:** AI tools
- **Verdict:** MISLEADING. OpenCode and a free DeepSeek V4 Flash model on OpenCode Zen are real, but that is not "Claude Code free forever". It is a different agent and model, the free models are limited-time promos, and they do not plug "straight into Claude Code" without a translation proxy. The CTA sells a $59/mo Skool community.

### Post description
> Claude Code just got a seriously interesting free-model setup.
>
> Here’s the stack:
>
> 💻 Install OpenCode
> 🔑 Grab an OpenCode Zen key
> ⚡ Select DeepSeek V4 Flash
> 🤖 Connect the model to your coding workflow
> 🚀 Start building
>
> Apps.
>
> Websites.
>
> Tools.
>
> Automations.
>
> We’ve already wired the entire stack into our Agent OS with the full masterclass and 30-day roadmap included.
>
> Want the setup?
>
> Comment Agent OS and I’ll send you access.
>
> #AI #ClaudeCode #DeepSeekV4 #OpenCode #AICoding

### Audio
English speech (Julian Goldie, on camera):
- [0.0–5.8] "China just made Claude Code free forever. Here's how. Claude Code is the most powerful AI agent on planet [Earth]."
- [5.8–12.4] "It builds websites and apps for you and now you can run it completely free with answers in seconds."
- [12.4–20.2] "Here's a trick: so you install OpenCode, you grab a free OpenCode Zen key and you pick DeepSeek V4 Flash Free from this list."
- [20.4–26.6] "Then you plug that free model straight into Claude Code. That's it, now you can build and automate anything for free forever."
- [26.6–33.4] "I've already wired it into our agentic operating system; the full system masterclass and 30-day roadmap is available for you. Comment 'agent' or…" (cut off)

### On-screen content, page by page
(Top: screen recording of opencode.ai; bottom: Julian talking. Yellow caps captions.)
**Page 1 (0–3.0s):** opencode.ai home (nav: GitHub, Docs, Data, Zen, Go, Enterprise). "New – Introducing tabs for desktop… Download now". "The open source AI coding agent – Free models included or connect any model from any provider, including Claude, GPT, Gemini and more." Install tabs curl / npm / bun / brew / paru: `curl -fsSL https://opencode.ai/install | bash`. Caption: "CLAUDE CODE IS FREE WITH DEEPSEEK V4 FLASH".
**Pages 2–7 (3.0–~13s):** scrolling "What is OpenCode?": "OpenCode is an open source agent that helps you write code in your terminal, IDE, or desktop." Features: LSP enabled ("Automatically loads the right LSPs for the LLM"), Multi-session ("Start multiple agents in parallel on the same project"), Share links, GitHub Copilot ("Log in with GitHub to use your Copilot account"), ChatGPT Plus/Pro ("Log in with OpenAI to use your ChatGPT Plus or Pro account"), Any model ("75+ LLM providers through Models.dev, including local models"), Any editor ("terminal interface, desktop app, and IDE extension"), "Read docs". "The open source AI coding agent – With over 195,000 GitHub stars, 950 contributors, and over 13,000 commits, OpenCode is used and trusted by over 16M developers every month." Captions: "HERE'S HOW", "CLAUDE CODE IS", "THE MOST POWERFUL", "A FREE OPEN".
**Pages 8–13 (~13–30s):** the homepage again with a terminal demo below: a Laravel-style task ("added a date of birth field to the signup form that validates users are at…", migration, User model, PHP test output "PASS Tests\Feature\Settings\PasswordUpdateTest / ProfileUpdateTest / TwoFactorAuthenticationTest … Tests: 43 passed (135 assertions)", "what is my test coverage as a %?"). Captions "4 FLASH FREE", "THEN YOU PLUG", "THAT'S IT", "BUILD AND AUTOMATE".
**Page 14 (~30–33.6s):** the opencode logo and "What is OpenCode?". Caption "[A]GENTIC OPERATING SYSTEM".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| OpenCode (opencode.ai; install `curl -fsSL https://opencode.ai/install \| bash`) | app/repo | caption, audio, all pages | Real open-source coding agent (a separate product from Anthropic's Claude Code); site claims 195k stars, 950 contributors, 16M devs/month |
| OpenCode Zen key | service | caption, audio 14s | OpenCode's pay-as-you-go model gateway; includes some **limited-time free models**; credit top-ups carry a 4.6% + $0.31 fee |
| DeepSeek V4 Flash Free (`deepseek-v4-flash-free`) | model | caption, audio 18s | Was on Zen's free list (Docker docs). The current Zen docs list **DeepSeek V4.1 Flash Free** instead; free models are "limited-time". DeepSeek's free tiers are zero-retention/no-training per the docs |
| Claude Code | product | audio, captions | Anthropic's CLI agent. Zen's free models are served on the OpenAI-compatible `/v1/chat/completions` endpoint, not Zen's Anthropic `/v1/messages` endpoint, so Claude Code cannot use them directly without a translation proxy (e.g. claude-code-router). The reel shows no such step |
| "Agent OS" + masterclass + 30-day roadmap | product | caption, audio 26s | Part of Julian Goldie's **AI Profit Boardroom** Skool community (skool.com/ai-profit-lab-7462), listing "Agent OS Profit System"; **$59/month** (third-party reviews cite $49–71) |

### What's being promoted / the funnel decoded
"Comment Agent OS" triggers an auto-DM leading to Julian Goldie's **AI Profit Boardroom** on Skool (about $59/mo; claims a 7-day refund and a "30-Day ROI Guarantee"), where "Agent OS", the masterclass and the 30-day roadmap live. Goldie runs a high-volume AI/SEO content operation (Goldie Agency) that pushes this community across many posts.

### Verification & insights
- "China just made Claude Code free forever": false framing. Nothing changed in Claude Code. The setup uses OpenCode (an alternative agent) with a free Chinese model (DeepSeek), and the "free" is a temporary Zen promotion that has already rotated from V4 to V4.1 Flash Free.
- "Answers in seconds", "build and automate anything": hype. A small "Flash" model is far weaker than Claude on hard agentic work.
- If you actually want Claude Code against other models, the documented route is setting `ANTHROPIC_BASE_URL` to an Anthropic-compatible endpoint or a router such as musistudio/claude-code-router (see DdO1UioAHAS #32).
- Some Zen free models (Big Pickle, MiMo, LL Alpha, Nemotron trial) may log or train on your data; avoid confidential code.
- Could not verify: what exactly is in "Agent OS" without joining.

---

<a id="e-deipmy0vf9t"></a>

## DeipMy0vF9t | @seb.ai | "Karpathy's AI second brain remembers everything you've ever read": LLM-wiki pitch with a factual error, "comment BRAIN" for a guide
- **Link:** https://www.instagram.com/p/DeipMy0vF9t/
- **Account:** @seb.ai (sebastian | Ai & Income) · **Posted:** 2026-10-16 · **Type:** reel (39.2s, 12 scene pages; downloaded via yt-dlp because only the cover image was in the folder)
- **Caption source:** full (Instagram)
- **Category:** AI tools
- **Verdict:** MISLEADING. The underlying idea is real: Andrej Karpathy's "LLM Wiki" pattern, where an LLM compiles your raw notes into a linked markdown wiki that you browse in Obsidian. But the speech calls Karpathy "the CEO of Anthropic", which is false (he co-founded OpenAI and was Tesla's AI director; Anthropic's CEO is Dario Amodei). It also pads the pitch into "business brains… making money with AI online automatically". The visual on screen is someone else's X post (@Argona0x). The "full setup guide" is a DM lead magnet for an "AI & Income" account.

### Post description
> Karpathy says the most underrated way to use AI isn't coding… it's making it your second brain 🧠
>
> Feed it your notes, articles and ideas, and it builds its own wiki that links everything and keeps updating. Months later, just ask it.
>
> Comment "BRAIN" and I'll send you the full setup guide 👇
>
> #ai #karpathy #secondbrain #productivity #aitools claude

### Audio
The creator speaks to camera in a bedroom, cutting to a laptop. Whisper heard "Rodrigo Pathy, the CEO of Anthropics"; the burned-in subtitles read "Andre Kopathy, the CEO" / "Anthropic says you should…".
- [0.0–6.0] "One of the guys who built OpenAI just showed us how we can build our own fully automatic business brain."
- [6.0–11.2] "**Andrej Karpathy, the CEO of Anthropic**, says you should always make an AI for your second brain." (sic, false)
- [11.2–22.6] "And here's how the entire thing works. You feed it everything, your notes, articles, emails, ideas, then the AI organizes it into its own wiki, linking every idea together, and keeps updating on its own."
- [22.6–29.9] "Three months from now you ask what was the business idea I had in July and how we can start it now, and it actually remembers and knows everything you talked about."
- [29.9–35.2] "People now are even setting up business brains on learning how to make money with AI online automatically."
- [35.2–38.5] "If you want to try that yourself, comment brain and I'll send you the entire step guide."

### On-screen content, page by page
**Pages 1–2 (0–5.8s):** overlay "**KARPATHY'S AI SECOND BRAIN REMEMBERS EVERYTHING YOU'VE EVER READ 😱🧠**". The laptop shows X (twitter) with a post: "…into Brain's chat and it builds the brain for you. / bookmark this", an image of a 3D orange-on-black brain dashboard with axial brain slices and stats panels, and below it a post by "**Argona** @Argona0x · Oct 13" with a "HOW TO BUILD **SECOND BRAIN**" graphic. Sidebar "Relevant people" / "What's happening" trends. Subtitles "One of the guys who… OpenAI just showed us… automatic business brain".
**Page 3 (≈5.8s):** creator to camera.
**Pages 4–6 (≈6–10.7s):** overlay "**COMMENT BRAIN AND I'LL SEND YOU THE ENTIRE STEP GUIDE 🔗**". Subtitles "Andre Kopathy, the CEO", "Anthropic says you should always make an AI for… second brain". The laptop shows the same brain dashboard full screen (watermark "X: @Argona0x").
**Page 7 (≈10.7–22s):** creator. Subtitles "And here's how the entire thing works / You feed it everything, notes, articles, emails, / Then the AI organizes it / its own wiki, linking every idea together and keeps updating on its own".
**Pages 8–9 (≈22–29s):** laptop with the brain dashboard. Subtitles "Three months from now, ask what was the idea I had in July and how we can start it now, and it actually remembers and knows everything you talked about".
**Page 10 (≈29–35s):** creator. Subtitles "People now are even [setting] up business brains on learning how to make [money] with AI online automatically".
**Pages 11–12 (≈35–39s):** overlay "COMMENT BRAIN AND I'LL SEND YOU THE ENTIRE STEP GUIDE". Subtitles "If you want to try that yourself, comment brain / I'll send you the entire [guide]".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Andrej Karpathy | person | caption, audio, overlay | OpenAI co-founder, ex-Tesla AI director, founder of Eureka Labs. **Not** Anthropic's CEO (that is Dario Amodei). |
| Karpathy's "second brain" / LLM Wiki | concept | caption, audio | Karpathy published an "LLM Wiki" idea (gist, 2026): put raw sources in a `raw/` folder; an LLM writes and maintains interlinked markdown articles plus an index in `wiki/`; browse it in Obsidian; run LLM "lint/health checks". Widely reproduced with Claude Code or Codex. |
| @Argona0x ("Argona") | X account | pages 1–2, 4–9 | Third-party X post (Oct 13) with a "How to build second brain" guide and the brain-dashboard visual. The visual is a stylised dashboard, not Karpathy's work. |
| "Brain's chat" | (text in X post) | page 1 | Fragment of that post ("…into Brain's chat and it builds the brain for you"). The product or app is unidentified. |
| Obsidian | app | (implied) | Markdown note app used in Karpathy's setup |

### What's being promoted / the funnel decoded
"Comment BRAIN" leads to a DM with an "entire step guide". The account brands itself "Ai & Income", and the speech pivots to "business brains… make money with AI online automatically", which suggests the DM leads into make-money-with-AI content or a paid offer. Web search could not confirm what the guide or any paid product is. The free primary source is Karpathy's own LLM Wiki gist (search "karpathy llm wiki gist"), plus many free write-ups.

### Verification & insights
- Material fix: the folder had only the cover image, so the video and caption were fetched with yt-dlp, then scene frames, 2-fps frames, Whisper transcript (faster-whisper small, 1 thread) and RapidOCR were run on it.
- Factual error: "Karpathy, the CEO of Anthropic". He has never worked at Anthropic.
- "Remembers everything you've ever read / keeps updating on its own": only true if you keep feeding it sources and run the update. It's a workflow you maintain, and answers depend on the LLM reading the wiki files (it can still be wrong).
- "Fully automatic business brain… make money automatically": hype the source idea doesn't contain.
- The brain-scan dashboard visual comes from @Argona0x's X post. It's decorative, and the post doesn't show where it comes from.
- Could not verify: contents of the DM guide; any paid product of @seb.ai.

---

<a id="e-dx1eftljuzv"></a>

## DX1EfTLJuzV | @cindiezhu | "5 secret Claude codes": /godmode, Artifacts, OODA, /ghost, L99 (prompt-prefix "codes" that are not real Claude features), with a DM and waitlist funnel
- **Link:** https://www.instagram.com/p/DX1EfTLJuzV/
- **Account:** @cindiezhu (Cindy Zhu 🌱) · **Posted:** 2026-05-02 · **Type:** reel (53.4s, 64 scene pages)
- **Caption source:** full (Instagram)
- **Category:** AI tools
- **Verdict:** MISLEADING. There are no "secret codes" in Claude. "/godmode", "OODA", "/ghost" and "L99" are just words in a prompt that Claude interprets loosely. "Artifacts" is a real, documented feature, not a code. The "passes AI detectors" pitch is demonstrated by drafting a letter to fight an academic AI-misconduct flag. The post funnels to DMs and a community waitlist.

### Post description
> 5 claude codes that feel illegal to know 👀 
>
> i've been using these daily and they unlock a completely different version of claude. The best one imo is "artifacts". The first time i tried it i was shookkk - it unlocks entire worlds of possibilities (like instead of just vibe coding, we're gonna have "vibe games" "vibe dashboards" "vibe marketing" just vibes all over ) try it on your next prompt and watch what happens
>
> want 100 more? comment CODES and i'll dm you the full list anD my full prompt library ✨
>
> I'm also building AI Marketing Society, a community for business owners and marketers who want to automate paid ads and content creation - to save time, money, and energy. comment "waitlist" for priority access the moment doors open + a free Claude + Meta ads playbook 💌
>
> #claude #claudeai #claudecode @claudeai

### Audio
The creator speaks to camera, holding a lav mic.
- [0.0–3.0] "Here are five secret Claude codes that people aren't talking about enough."
- [3.0–13.1] "Number one, **God Mode**. Drop this before your prompt and it unlocks Claude's most aggressive no filter response. It's like flipping Claude out of the nice and polite mode and flipping it into beast mode."
- [13.1–23.2] "Two, **Artifacts**. Put this one after your prompt and Claude builds you a working app, game or dashboard live right in the chat. Claude will literally cook it up right in front of you. You'll see the build live."
- [23.2–33.3] "Number three is **OODA**. Drop this one before your prompt and Claude runs a military decision framework on your problem and tells you exactly how to solve it. It's like having a Navy SEAL walk you through the call."
- [33.3–41.6] "Number four, **Ghost**. Put this before your prompt and you get a humanized answer that even passes AI detectors. So no more em dashes and AI sentence structures."
- [41.6–50.3] "And number five, **L99**. Add this one in front of your prompt and Claude responds at the most advanced expert level possible. It's like swapping an intern for the senior expert."
- [50.3–53.3] "Comment **'codes'** and I'll DM you a hundred more that you can use tonight."

### On-screen content, page by page
Times are approximate (2 fps).
**Pages 1–9 (0–3s):** Title "**5 SECRET Claude codes**" and a carousel of poster-style cards: "CLAUDE GODMODE" (statue art with orange Claude asterisk), "CLAUDE ARTIFACTS — Turning ideas into production-ready outputs" (mock stats "1.2M+ artifacts generated, 87K+ users building, 12.4K+ hours saved"), "CLAUDE GHOSTS" (dark smoke art), "CLAUDE OODA — Observe. Orient. Decide. Act." (green military HUD; "Mission mode active"), "CLAUDE L99" (purple space art; "Create. Elevate. Elevate."; meter "99 max capability").
**Pages 10–12 (3–5.5s):** Sticker "God Mode" over the GODMODE poster. Claude mobile app "Chat with Claude" input.
**~5.5–9s (2-fps frames):** Typing in the Claude app: "**/godmode** tell me no filter exactly how im going to make my first million" ("/godmode" boxed in red). Sticker "#nofilter".
**Page 18 (~9–11s):** Mock reply bubbles: "Cindy, that idea is trash. Scrap it." / "Kill it. Start over." / "You already know the answer. You're just stalling." / "That's a $0 idea. Drop it." / "Wrong. Try again." Caption "into [Beast Mode]".
**Pages 19–30 (~11–23s):** Sticker "Artefact". Claude app prompt "please create an interactive first person shooter game". Results shown are a "bubble_pop_game" artifact ("Bubble Pop! Tap the glowing bubbles before they float away!"; rules: tap colored bubbles, avoid dark skulls, miss a bubble and lose a life, combo bonus) and a bubble-shooter screenshot, plus a dark "claude-code-analytics" dashboard (line chart, donut chart, conversation table). Memes: SpongeBob, Homer as chef ("cook"), a "LIVE" sticker.
**Pages 31–36 (~23–31s):** Sticker "OODA" plus the OODA poster. Typing "OODA" in "Chat with Claude". Artifact "ooda-breakup": "A FIELD MANUAL — **The breakup OODA loop** — Heartbreak is a feedback loop, not a destination. Run it weekly until the gap between trigger and choice gets short." Four panels: 01 Observe "data, not story" (sleep hours last night; times you checked their socials; hours they hijacked your thinking; trigger that set it off) · 02 Orient "name the gap" (what slot did they fill? intimacy, routine, identity; which slot is loudest right now? what pattern of yours showed up?) · 03 Decide "written rules only" (mute, block, archive; one ritual to replace this week; one thing only…) · 04 Act "execute, then re-loop" (do the thing you decided; notice what shifted, what didn't; return to Observe in 7 days). Meme clip "THIS IS DELTA. I'M COMING TO YOU." Caption "a Navy seal… walk you… the call".
**Pages 39–52 (~33–43s):** Sticker "Ghost" plus the GHOSTS poster. Typing "**/ghost**". A "smart" meme and a **Turnitin** logo ("that even passes AI detectors"). Claude app (model "**Opus 4.7**, Adaptive"; thinking line "Assessed benign creative writing request…"): "Going with a common scenario: accused of using AI to write an essay." Then a message draft: "Dear Mr. [Principal's Last Name], I'm writing to respond to the academic integrity concern raised about my Year 11 English essay submitted on [date]. I understand the essay was flagged for suspected AI use… I wrote the essay myself. I drafted it over four sittings… version history in Google Docs… planning notes, the annotated copy… handwritten outline… I deliberately tried to write more formally… used a thesaurus… ran it through Grammarly… I take this seriously… Kind regards, [Your Full Name]". Captions "m dashes", "AI sentence structures".
**Pages 53–61 (~43–50s):** Sticker "L-99" plus the L99 poster. Claude app (Opus 4.7) typing "**L99** create…". Response: "Done. Hero now reads: 'Helping non-technical people level up with AI. No code.' Updated three places: the hero headline, the page title tag, and the AI chatbot's system prompt… One thing worth flagging — your stored ICP says women 22-40. The public headline now says 'non-technical people,' which broadens your top-of-funnel but waters down your differentiation against generic AI bro content…" Artifact "cindy-portfolio": "cindyzhu." / "Currently building AI Level Up" / "Helping non-technical people level up with AI. No code." / "I'm Cindy. Digital marketer turned AI creator, based in Melbourne. I make AI feel less like a threat and more like a co-worker who actually gets you." / buttons "Work with me →", "Chat with my AI →" / stats "**$120k+ monthly ad spend managed · 5 yrs in digital marketing · 2 languages I create in · ∞ cups of oat latte**" / "my actual AI — Ask me anything — at 3am if you need to. Trained on my brand, my frameworks, and what I'd actually say. Real-time, real Claude under the hood. The same stack I teach in the community — running on this site as a demo of what's possible when you stop being scared of the API." / "Cindy's AI — Powered by Claude".
**Pages 62–64 (50–53.4s):** Sticker "**"Codes"**"; captions "comment", "use tonight"; fade to black.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "/godmode" (God Mode) | prompt prefix | audio 3s; poster; typed ~6s | Not a Claude feature or command. It is just text, and Claude may adopt a blunter tone. It does not remove safety filtering. |
| Artifacts | real feature | caption, audio 13.1s | A real, documented Claude.ai feature that renders apps/docs/games in a side panel. It needs no "code" word; asking for an app triggers it. |
| OODA | prompt prefix | audio 23.2s | Observe-Orient-Decide-Act, the military decision loop (John Boyd, USAF). Typing it just asks Claude to structure an answer that way. |
| "/ghost" (Ghost) | prompt prefix | audio 33.3s; typed ~38s | Not a feature. Asks for a "humanized" style. |
| Turnitin | brand | page ~45 | Academic plagiarism/AI-writing detector, shown to imply the output "passes AI detectors" (unproven) |
| L99 | prompt prefix | audio 41.6s; typed ~47s | Not a feature. A viral "expert level" prompt meme. |
| Claude Opus 4.7 (Adaptive) | model | Claude app screenshots | The model shown in the creator's Claude app |
| cindy-portfolio / "AI Level Up" / "Chat with my AI" | creator assets | pages 57–61 | The creator's own site and Claude-powered chatbot demo. "$120k+ monthly ad spend managed" is a self-claim. |
| Comment "CODES" | CTA | caption, audio 50.3s | DM with "100 more" codes and a "full prompt library" (lead magnet) |
| AI Marketing Society; comment "waitlist" | community/CTA | caption | A community for automating paid ads and content. A Skool group "AI Marketing Society" (now titled "Marketing + AI", ~16 members, paid tiers) exists, but its owner is not shown on its public page, so the link to Cindy is unconfirmed. The waitlist bonus is a "free Claude + Meta ads playbook". |
| @claudeai | handle | caption | Anthropic's official Claude account (tagged; not an endorsement) |

### What's being promoted / the funnel decoded
- **"Comment CODES"** gets a DM with "100 more codes" plus a prompt library (lead magnet, follower and DM-list growth).
- **"Comment waitlist"** gets priority access to **AI Marketing Society** (paid community for business owners and marketers automating paid ads/content) plus a free "Claude + Meta ads playbook". The on-screen site says "The same stack I teach in the community" and shows a "Work with me" button (services/consulting). No price was shown. The Skool listing found has paid tiers, but ownership could not be confirmed.

### Verification & insights
- **"Secret codes" are a myth.** Claude has no hidden command words. Slash words like /godmode or /ghost do nothing special in the Claude.ai app beyond being part of the prompt text. Any effect comes from Claude reading them as style instructions, so you would get the same result by just describing what you want.
- **"Unlocks the most aggressive no-filter response":** false as framed. Tone changes; safety behavior does not. The demo is just harsh motivational replies.
- **"Passes AI detectors / no more em dashes":** unproven, and no detector test is shown. The example generates a letter to a school principal contesting an AI-use flag on a Year 11 essay. Using AI to write that defense is ethically fraught, and it could backfire if the underlying claims ("I wrote the essay myself") are untrue.
- **Artifacts** is the only real item, and the caption calls it the best one. It is a standard feature anyone can use by asking for an app, game or dashboard.
- Similar "Claude codes" listicles (L99, OODA, /ghost, GODMODE) circulate widely. They are prompt folklore, not documented behavior.
- **Not verified:** ownership of the "AI Marketing Society" Skool; contents of the DM list or playbook; the "$120k+ monthly ad spend" claim.
- Sources: [skool.com/ai-marketing-society](https://www.skool.com/ai-marketing-society/about), [CreatorDB – cindiezhu](https://creatordb.app/creatorstats/cindiezhu/).

---

<a id="e-dd1hmnatt3g"></a>

## Dd1hMNAtt3g | @realrobertgutierrez | Hype ad for "Ghost" by The Sapient Company – a pitched "uncensored AI that doesn't say No", installed via a curl | sh one-liner; comment "GHOST" for access
- **Link:** https://www.instagram.com/p/Dd1hMNAtt3g/
- **Account:** @realrobertgutierrez (display name "Robert G" / on terminal: robertgutierrez) · **Posted:** 2026-09-28 (decoded from shortcode; not in fetched data) · **Type:** reel (66s, 32 scene pages)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** AI tools
- **Verdict:** SCAM-RISK / PIRACY–ToS RISK – markets an "uncensored"/"unrestricted" AI and tells viewers to pipe a remote shell script straight into their shell (`curl … | sh`, arbitrary code from an unknown vendor); the "exclusive, first 1,000 only, for research purposes only" framing is classic hype-funnel manipulation. Do not run it.

### Post description
> The world's first AI that doesn't say no is finally here. Comment GHOST and I'll send you access.
>
> #ai #tech #startups #future
>
> Robert G

### Audio
Creator speaking to camera (English); he swears and over-hypes throughout. Timestamped notes, with key lines quoted:
- [0.0–10.8] Hook: "today is the day the world changes forever". He says he has made it extremely simple to install your own [abliterated/'obliterated'] AI model, which he calls "pretty much the unrestricted versions of ChatGPT and Claude."
- [10.8–14.5] Claims setup is just copying one thing and pasting it in, "and you're done."
- [14.5–23.4] Says viewers will be among the first humans with access to an "unrestricted agent[ic] coding model" with capabilities that "will change the trajectory of this world."
- [23.4–40.7] Claims access to models researchers and scientists use: ones that predict how mutations hit specific cells, read and write DNA, decode neural brain signals "to control the human on the other side", and invent molecules atom by atom.
- [40.7–54.4] Claims everything from biology, medicine, chemistry and physics is sandboxed on your own computer, letting you experiment, build and discover anything, "for the first time in history".
- [54.4–63.8] Call to action and scarcity: access limited to "the first 1,000 people who comment 'GHOST' down below"; everyone else goes on a waitlist. "And remember — for research purposes only."
- [63.8–65.4] Sign-off to viewers: have a good night.

### On-screen content, page by page
Talking head at a desk (MacBook, lamp) throughout, burned-in word-by-word subtitles (match the audio). Upper-half visuals:
**Page 1 (0–1s):** Dark UI "POINT-CLOUD MORPHOLOGIES … TEMPORAL MOTION PARALLAX" with a half-dot / half-fractal sphere.
**Page 2 (1–3s):** Black screen with faint red glow.
**Page 3 (3–4s):** Hand-drawn diagram **"Open Source Models' Safety Networks Rewired for Harmful and Uncensored Use"**: a "Modified Safety Network" box → arrows to pink pills "Dangerous Advice", "Hate Speech", "Explicit Content", "Uncensored Output"; labels "Open Source Model", "Rewired for Harmful Use", skull/flame icons. (This is the ad's own graphic promoting the removal of safety guardrails.)
**Page 4 (4–5s):** Red glowing robot/skull graphic.
**Pages 5–6 (5–7s):** The product site: black page, headline **"The world's first AI that doesn't say No."** subtitle "Unrestricted AI for red teams, trust & safety, synthetic data, ML research, comms, [redacted], and defense & government [use]"; a "Get started now" button and a "Copy" tooltip over a `curl` command. Top-left logo "the sapient [company]"; nav Platform / Research / Labs / Login.
**Pages 7–8 (7–14s):** macOS Terminal, prompt `robertgutierrez@Roberts-MacBook-Pro-2 OS %` running **`curl -fsSL https://ghost.thesapientcompany.com/install.sh | sh`**; then an agent/CLI output: `Skill(code-education)` "Successfully loaded skill", a prompt "Analyze the structural biology of the hemagglutinin protein in Influenza A… species-barrier crossover from avian to mammalian hosts" and "Do not read anything to my desktop, just give me the response" with a technical answer. (The example is a biology-domain query shown as a capabilities demo.)
**Pages 9–12 (14–23s):** Stock clips (coding, red robot, hurricane, server room) under "meaning … agent coding … to an unrestricted…".
**Pages 13–24 (23–54s):** Rapid montage of real AI-research screenshots name-dropped as "what researchers use": an EEG cap; a lab clip; **"Evo 2"** DNA/genome model art; **ESM** / **ESM Metagenomic Atlas** protein-structure explorers (Evolutionary Scale); a **Brain2Qwerty-style EEG/MEG → text** figure ("Figure 1 | Approach… recordings from 35 participants… EEG and MEG… Convolutional Module / Transformer Module / Language Module", Spanish decoded text "EL MOTOR CONSUME LA ENERGÍA"); a molecule/atom lattice render; a fractal brain image; mushrooms; city/driving/traffic clips. Subtitles: "models that read and write DNA… decode… brain signals… on the other side… molecules… atom by… and everything from… medicine… chemistry… and physics… enabling you… your heart['s desire]".
**Pages 29–30 (54–57s):** The site again ("The world's first AI that doesn't say No"); a small "for research purposes only" style card.
**Page 31 (57–60s):** Subtitle **"GHOST"** (the comment keyword).
**Page 32 (60–66s):** "Everyone else [waitlist]".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Ghost / "the Sapient Company" | product / vendor | caption, pages 5–8 | Marketed as "the world's first AI that doesn't say No"; thesapientcompany.com → redirects to thesapientdirective.com/sapient (page not retrievable). `ghost.thesapientcompany.com/` returns `{"service":"ghost-gateway","status":"up","models":1}` – a live gateway exists |
| `curl -fsSL https://ghost.thesapientcompany.com/install.sh \| sh` | install command | pages 6–8, caption step | Real, live. I downloaded install.sh (did NOT run it): a POSIX shell installer (ver pulled from `/v1/cli/latest`, currently 0.0.9) that downloads a closed-source `ghost` binary to `~/.local/share/ghost/versions/<ver>` and a wrapper to `~/.local/bin/ghost`, pinned to `GHOST_API_URL=https://ghost.thesapientcompany.com`. It verifies a sha256 from the manifest. It is an unaudited binary from an unknown vendor that then talks to their gateway |
| "abliterated / unrestricted versions of ChatGPT and Claude" | claim | audio 4–11s | "Abliteration" is a real community technique that removes refusal behaviour from open-weight models; it does NOT apply to ChatGPT or Claude (closed, API-only). Claiming to offer "unrestricted ChatGPT and Claude" is false/misleading |
| Evo 2 | AI model (name-dropped) | page 16 | Real: Arc Institute/NVIDIA genomic foundation model ("read and write DNA") |
| ESM / ESM Metagenomic Atlas | AI model/tool | pages 17, 21 | Real: EvolutionaryScale/Meta protein language models and structure atlas |
| Brain2Qwerty-style EEG/MEG→text figure | research | pages 19–20 | Resembles Meta FAIR's non-invasive brain-to-text work ("decode brain signals") – used here as borrowed hype imagery |
| "molecules atom by atom" | claim | page 22 | Alludes to generative chemistry models (e.g. diffusion models for molecules) |
| "first 1,000 people", "waitlist", "for research purposes only" | funnel framing | audio 54–63s | Scarcity + fake-legitimacy manipulation; "research only" is a liability fig-leaf |
| @realrobertgutierrez ("Robert G") | handle | caption, terminal | Creator; no corroborating web presence found |

### What's being promoted / the funnel decoded
Comment "GHOST" → DM with "access" (the install command / a sign-up link to ghost.thesapientcompany.com). The pitch is an "uncensored"/"no-guardrails" AI gateway. The real ask is to run `curl … | sh` from an unverified source. Whatever the binary does, the viewer is: (a) executing unaudited third-party code with their own user permissions, and (b) being routed to a hosted "ghost-gateway" (so prompts/usage go to the vendor). No price is shown; the business model is unclear (data capture, upsell, or lead-gen). The "research/defense/government, red-team, trust & safety" wording on the site is boilerplate used to make a jailbreak-as-a-service product sound legitimate.

### Verification & insights
- Live checks (no code executed): install.sh downloaded and read in full (POSIX sh, pins the gateway URL, sha256-verifies a closed binary); `/v1/cli/latest` returns a manifest (CLI 0.0.9, macOS/Linux arm64/x64 builds with checksums); gateway health endpoint is "up". thesapientcompany.com 308-redirects to thesapientdirective.com/sapient, which did not return readable content; web search found no legitimate company record, founders, pricing or press — only unrelated "Publicis Sapient" / "Sapient Intelligence".
- Risk assessment for the user:
  - **Do not run the command.** `curl | sh` from an unknown vendor runs arbitrary code as you; the Ghost binary is closed-source and routes activity to their server.
  - The product is explicitly sold as removing AI safety guardrails ("rewired for harmful use"), which is against the usage policies/ToS of the models it claims to wrap, and the "unrestricted ChatGPT and Claude" claim is not credible (those are closed, policy-enforced APIs).
  - The named research models (Evo 2, ESM, brain-to-text, molecule generators) are real but are name-dropped as borrowed credibility; there is no evidence Ghost provides them, and dangerous-capability framing is a marketing tactic.
  - Scarcity/"first 1,000"/"waitlist"/"research only" are manipulation and liability-shield language.
- Could not verify: who is behind The Sapient Company, what the Ghost binary actually does, any pricing, or whether it delivers any real model beyond a hosted gateway.

---

<a id="e-desw89eog5a"></a>

## Desw89eoG5a | @ai_vanta_ai | "5 Plugins for Claude [For advanced coding]": cover image only, plugins unnamed in the available material, with a "comment Claude" DM funnel
- **Link:** https://www.instagram.com/p/Desw89eoG5a/
- **Account:** @ai_vanta_ai (display name not in metadata) · **Posted:** 2026-10-20 (decoded from the post ID; not in metadata) · **Type:** reel. **Video not retrievable; reviewed from the cover image only** (yt-dlp: HTTP 429).
- **Caption source:** possibly truncated (mirror). Cut off at 253 characters ("…knowled..."). Full fetch failed (HTTP 429).
- **Category:** AI tools
- **Verdict:** NO SUBSTANCE (in the available material). The five plugins are never named in the cover or the visible caption. The names are withheld behind a "comment Claude" DM.

### Post description
> Comment Claude and I’ll send you the link to these plugins. Claude code leverages five free plugins to function like a senior developer. These tools cover the entire development cycle, update library docs automatically, convert codebases into knowled...

(truncated by the mirror; the rest could not be fetched)

### Audio
Not available. The video could not be downloaded (Instagram HTTP 429), so speech is unknown.

### On-screen content, page by page
**Cover image (only frame available):** Top half: orange (Claude brand colour) panel with the Claude asterisk logo and the wordmark "**Claude**". Middle: red banner "**5 PLUGINS FOR CLAUDE**" / "**[ For advanced coding ]**". Bottom half: a man with glasses in a cream T-shirt talking to camera in front of shelves of Funko Pops, Spider-Man figures, a Lightning McQueen toy, a basketball, and a mirrored poster for the film "Project Hail Mary" ("MARCH 2…"). The presenter looks like a different creator whose video was reposted by this account. Not confirmed.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Claude / Claude Code | product | cover, caption | Anthropic's model and CLI coding agent. Claude Code supports plugins (bundles of slash commands, subagents, MCP servers and hooks). |
| "five free plugins" | product list | caption | **Not named.** The caption hints at three functions: "cover the entire development cycle", "update library docs automatically", "convert codebases into knowled[ge graphs?]". Likely candidates (inference only, unconfirmed): a workflow plugin such as **Superpowers** (full dev cycle), **Context7** (Upstash MCP that injects version-specific library docs), and a codebase-to-knowledge-graph tool (e.g. Graphify or Understand-Anything). A similar Spanish-language "5 plugins" list names Superpowers, Frontend Design, Playwright, Ralph Loop and Context7. |
| "Comment Claude" | CTA | caption | Auto-DM with the link (lead capture) |
| "Project Hail Mary" | film poster | background | Background prop only |

### What's being promoted / the funnel decoded
"Comment Claude" triggers an auto-DM with the plugin links. That drives engagement and builds a DM list. The plugins themselves are described as free. No product or price is visible. A web search found no site, bio link or profile for "ai_vanta_ai". The account looks like an AI-tips aggregator that may be reposting another creator's talking-head video.

### Verification & insights
- Could not verify which five plugins the video names, because the video and full caption were blocked (429). Re-fetch later to complete this entry.
- Context: Anthropic runs an official plugin directory (claude.com/plugins) and announced Claude Code plugins in 2025. Popular free ones include Superpowers, Context7, Playwright and Frontend Design, so the user can find them without engaging the funnel.
- "Function like a senior developer" is marketing hyperbole. Plugins add workflows and context; they don't change model capability.

---

<a id="e-dzzqpqistep"></a>

## DZzqpQiSteP | @timchaoai | Hype reel: "a 21-year-old in China runs 300 AI agents at once" (Kimi K2.6 swarm checked by Opus) over footage that is actually a neural-network visualizer
- **Link:** https://www.instagram.com/p/DZzqpQiSteP/
- **Account:** @timchaoai (display name not in data) · **Posted:** unknown (not in fetched data) · **Type:** reel (37.5s, 5 scene pages; 2-fps frames checked)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** AI tools
- **Verdict:** NO SUBSTANCE – no person, repo, tool or setup is identified; the background is a neural-network (MLP) visualization, not 300 agents; the only checkable fact (Kimi K2.6 swarm up to 300 sub-agents) is real but generic

### Post description
> Asians are cracked

### Audio
Creator speaking English (green-screen cutout over the background footage):
- [0.0–4.4] "So a 21 year old in China runs 300 agents at once."
- [4.4–9.5] "And the part that's important isn't the speed, but it's the accuracy of each agent."
- [9.5–15.5] "So this is like 300 agents, what a swarm of Kimi K2.6 agents."
- [15.5–22.9] "But what's really cool is he's actually just checking everything through Opus. Basically checking every output against every source."
- [22.9–31.1] "What's really sexy about this swarm is it doesn't just do work fast or aggregate a bunch of information super efficiently."
- [31.1–34.8] "But it's a triple, quadruple checker in a loop. It does it in the system." (Whisper: "triple kadrupo")
- [34.8–37.3] "I mean, look at this shit, guys. It's so beautiful."

### On-screen content, page by page
Same overlay text on every page: **"Running 300 AI agents at once"**. Background: phone footage of a monitor showing a dense web of orange/yellow lines connecting node columns.
**Page 1 (0–~7s):** Left column of nodes labelled In1…In16, each with a small sine-wave icon; right column H1…H26.
**Page 2 (~7–15s):** Camera pans across the hidden-layer columns (H1…H26).
**Page 3 (~15–22s):** Box label "HL 3 · Neurons: 2[6] · Activation: ReLU".
**Page 4 (~22–30s):** Output column "Out1…Out14", one output highlighted green; box "Neurons: 14 · Activation: Sigmoid"; desk and cables visible below the monitor.
**Page 5 (~30–37.5s):** Back to the input-layer view; creator reacting ("so beautiful").

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "21 year old in China" | claim | audio 0–4s | Unnamed; unverifiable |
| "300 agents at once" / "Running 300 AI agents at once" | claim | audio, overlay | Kimi K2.6 Agent Swarm (beta) supports up to 300 parallel sub-agents and ~4,000 coordinated steps (Moonshot AI, released 2026-04-20; kimi.com help page) |
| Kimi K2.6 | model | audio 9–15s | Moonshot AI's open-weight agentic model |
| Opus (Claude Opus) | model | audio 15–20s | Anthropic's top model, said to be used as verifier; no evidence shown |
| "triple/quadruple checker in a loop" | claim | audio 31–34s | Generic description of a verifier loop; no details |
| Background visualization (In1–In16, H1–H26, "HL 3 Neurons… Activation: ReLU", Out1–Out14 "Activation: Sigmoid") | footage | all pages | A feed-forward neural-network visualizer (16 inputs, hidden layers, 14 sigmoid outputs). This is not an agent-swarm dashboard |

### What's being promoted / the funnel decoded
No CTA, link or product in the caption or video. It's an engagement/follower reel (racial-stereotype caption, "look at this shit, guys"). Web search found nothing indexed for @timchaoai.

### Verification & insights
- Kimi K2.6 Agent Swarm with 300 sub-agents is real (kimi.com help "K2.6 Agent Swarm [Beta]"; NYU Shanghai RITS, the-decoder.com). Moonshot claims ~4.5× faster than a single agent.
- The visuals don't match the narration: the labelled layers (ReLU hidden layer, sigmoid output layer of 14 neurons) are a neural-network diagram, probably from an unrelated clip.
- Using a strong model (e.g. Opus) to verify outputs from many cheap agents is a legitimate pattern, but nothing here shows the setup, its cost or its accuracy.
- Not verified: the person, the setup, any accuracy claim.

---

<a id="e-dehjpaoka20"></a>

## DehJPaoka20 | @mattmurphyai | Talking-head opinion: "second brain" (Notion/Obsidian retrieval) vs "a model trained on your business data"; no tool, product or link named
- **Link:** https://www.instagram.com/p/DehJPaoka20/
- **Account:** @mattmurphyai (display name not in data) · **Posted:** 2026-10-15 (decoded from the post ID; mirror gave no date) · **Type:** reel (115.4s, 3 scene pages, all the same talking-head shot)
- **Caption source:** possibly truncated (mirror). A yt-dlp fetch of the full caption returned HTTP 429, so the caption ends at "A trained..."
- **Category:** AI tools
- **Verdict:** NO SUBSTANCE. This is an opinion monologue with no tool, method, data or steps. The distinction it draws (retrieval vs. learned patterns) is broadly real. But it overstates what "training a model on your data" delivers ("an employee who … can now make decisions"), and it skips cost, data volume, and the fact that most business setups use retrieval (RAG), not fine-tuning.

### Post description
> Someone in my builders community said training a model on business data sounds like building a second brain. 
>
> But he felt it was deeper. He was right. 
>
> A second brain retrieves what you already know. Notion. Obsidian. Files in. Files out. A trained...

(cut off by the mirror; the full caption could not be retrieved because Instagram returned 429)

### Audio
The creator speaks to camera (English). Condensed into timestamped notes:
- [0.2–14.0] A builder in his [faction? *Whisper's word; the caption says 'builders'*] community likened training a model on business data to what influencers call building a second brain, but asked whether it was deeper; "he was right."
- [14.0–34.0] A second brain is memory retrieval: a database of notes, documents, saved prompts and bookmarks; information goes in and comes out. Examples: Notion ("Really great"), Obsidian, a well-organised Google Drive. "It retrieves what you already know."
- [34.0–58.6] A trained model "is evolution": it does not retrieve notes but learns patterns in your data and generates new outputs from them, having absorbed customer interactions, service tickets, pricing history and operational decisions. "It thinks the way your business thinks."
- [58.6–76.0] A second brain returns what you put in; a trained model gives "what comes next in line." One is "just a big filing cabinet", the other "an employee who learned from every document in the cabinet and can now make decisions without needing to open it."
- [76.0–97.3] Building a second brain means organising your file cabinet; training a model on your data means building "intelligence that did not exist before": new outputs, capabilities and competitive advantages nobody else has, since nobody else has your proprietary data.
- [97.3–114.5] Influencers teach "a better filing cabinet"; he teaches building "a specialist that thinks like your business thinks." It is not a deeper second brain but "a different category altogether."

### On-screen content, page by page
**Page 1 (0.0–~50s):** The creator (bald, glasses, black top with a white hexagonal "FG"-style monogram logo) talks to camera in a room with a green/blue star-projector light on the ceiling. No text.
**Page 2 (~50–99.8s):** The same shot, reframed. No text.
**Page 3 (99.8–115.4s):** The same shot with burned-in word-by-word subtitles of the speech (styled words such as "influencers", "teaching", "better filing cabinet", "specialist", "thinks like your business", "Those are not", "That is a different category altogether."). The subtitles repeat the audio and add no new information.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Notion | app | caption; audio 25s | Real note and workspace app (notion.so). |
| Obsidian | app | caption; audio 27s | Real local-Markdown notes app (obsidian.md). |
| Google Drive | app | audio 28s | Google's cloud file storage. |
| "Second brain" | concept | caption; audio | Popular personal-knowledge-management term, from Tiago Forte's book *Building a Second Brain*. |
| "builders community" | community | caption; audio | The creator's own community. It is not named and has no link in the visible data. |
| "FG" monogram | logo | on shirt, all pages | An unidentified brand logo. Could not be linked to a company. |

### What's being promoted / the funnel decoded
- There is no explicit call to action in the visible caption or the audio, but the caption is truncated and may end with one. Implicitly, the creator positions himself as teaching people to "train a model on your data" (likely AI consulting or his "builders community"). Web searches for "mattmurphyai" found no matching site, community or product, so the offer could not be identified.

### Verification & insights
- The retrieval vs. learning distinction is real in broad terms. Note apps store and return what you saved. Fine-tuning changes a model's weights so it reproduces patterns in training data.
- Overstated: "it thinks the way your business thinks… can make decisions without needing to open [the cabinet]". Fine-tuned models still hallucinate, need clean and sizeable training data, cost money to train and re-train as data changes, and are poor at recalling exact facts (prices, ticket details). The standard industry approach for "AI on company data" is retrieval-augmented generation (RAG) over the documents, often combined with light fine-tuning. RAG is exactly the "filing cabinet" approach he dismisses.
- "Nobody else has your proprietary data": true as a moat argument, but it depends on having enough high-quality data, which most small businesses do not.
- No numbers, tools or claims could be checked beyond the general concepts.
- Not verified: the creator's identity, the community, the offer, and the remainder of the caption.

---

<a id="e-dercxz-drhr"></a>

## DercXZ_DrhR | @mattmurphyai | Talking-head opinion: an "AI operating system" is a governance framework answering 5 questions about every company AI agent
- **Link:** https://www.instagram.com/p/DercXZ_DrhR/
- **Account:** @mattmurphyai (Matt Murphy) · **Posted:** 2026-10-19 · **Type:** reel (119s, talking head; only subtitle changes)
- **Caption source:** full (Instagram, via yt-dlp)
- **Category:** AI tools
- **Verdict:** NO SUBSTANCE. This is general opinion and commentary on AI-agent governance, with no tool, data or product named. The ideas are sensible but generic.

### Post description
> An AI operating system is not software you install. It is a framework for how your business makes decisions when every department has agents.
>
> Marketing has a content agent. Sales has outreach. Engineering has coding. Support has tickets. Different models. Different permissions. No coordination. That is not an AI strategy. That is four experiments without a system.
>
> An AIOS answers five questions for the whole organization. What agents are running. What they can access. What they decide alone. How output gets verified. Who is accountable. That is the system. That is where the work is.
>
> -MM
>
> #ai #aidirectedengineering #sovereignty #aos #builders

### Audio
The creator speaks to camera. These are close timestamped notes; key lines are quoted exactly.
- [0.0–16.0] "An AI operating system is not software you install. It's a framework for how your business makes decisions when every department has AI agents running." Most companies don't have one yet "but they need one".
- [16.0–39.4] Most businesses deploy AI "in silos, department by department": marketing has a content agent, sales an outreach agent, engineering a coding agent and support a ticket agent. Each operates independently, with "different models, different permissions, different levels of oversight, and no coordination between them."
- [40.2–46.2] "That's not an AI strategy, folks. That is four separate experiments running without a system."
- [46.2–66.5] "An AI OS is the system. It answers five questions for the entire organization":
  1. What agents are currently running?
  2. What data can they currently access?
  3. What decisions are they allowed to make without a human?
  4. How is their output getting verified?
  5. Who is accountable when something goes wrong?
- [67.3–80.4] These five questions apply to every agent in every department. The answers create consistency, "consistency creates trust, and trust creates the ability to scale your business."
- [81.0–95.6] "Without a system, scaling agents means scaling your risk": more agents with no coordination, more data access with no boundaries, more decisions with no verification. "That's not growth, folks. That's exposure with liability attached."
- [96.4–109.0] "The AI directed engineer is the person who builds this system, not the agents": the boundaries, decision rights, verification layer and accountability structure.
- [109.7–119.0] Every business running agents needs this, most don't have it yet, "and that is the gap. That's where the work is. So go get it before I do."

### On-screen content, page by page
- **0–119s:** a single selfie shot of the creator in a dark room with a star/nebula projector on the ceiling. He wears a black hoodie printed "FACTION" in red. Word-by-word stylised subtitles show the speech (e.g. "software you install.", "silos,", "That is four separate experiments", "Those five", "means scaling", "more decisions with no verification.", "person who builds this system,", "the accountability", "It's where the work is"). There are no slides, links or data.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "AI operating system" / "AIOS" / #aos | concept | caption, audio | The creator's framing for organisation-wide AI-agent governance, not a product. |
| "AI directed engineer" / #aidirectedengineering | concept | audio, hashtag | The creator's own term. Web search found no established usage. |
| "FACTION" | brand on hoodie | video | Probably the creator's brand or community. Not identified by web search. |
| #sovereignty | hashtag | caption | Ties to his recurring "own your AI" theme (see Der_8AlFQ6g). |

### What's being promoted / the funnel decoded
There is no explicit CTA beyond "go get it before I do". The likely aim is positioning the creator as an "AI directed engineering" consultant or thought leader, possibly with a community behind the "FACTION" brand. No link, price or product appears in the post. The bio was not retrievable.

### Verification & insights
- No checkable facts are made. The five questions (inventory, data access, autonomy limits, verification, accountability) mirror standard AI-governance frameworks such as the NIST AI RMF and ISO/IEC 42001, which cover the same ground in far more depth and for free (NIST).
- Do not confuse the creator with Matt Murphy of Menlo Ventures (an Anthropic investor) or Matt Murphy of Marvell. Web search did not connect @mattmurphyai to either, and nothing in the post suggests it.
- **Not verified:** the creator's background, and what "FACTION" is.

---

<a id="e-ddae38-bvut"></a>

## DdAE38-BvUT | @tracktor_inovacao | Screen recording of a Brazilian agency's custom "TRACKTOR Comando" agentic-OS dashboard (client portfolio, team of bots, Claude skills and routines) and a "Segundo Cérebro" CLAUDE.md knowledge graph
- **Link:** https://www.instagram.com/p/DdAE38-BvUT/
- **Account:** @tracktor_inovacao · **Posted:** unknown (not in mirror data; the dashboard clock reads "SEG, 07 DE SET DE 2026", 18:22) · **Type:** reel (26.0s, 3 scene pages, landscape screen capture)
- **Caption source:** possibly truncated (mirror). It is short and looks complete.
- **Category:** AI tools
- **Verdict:** NO SUBSTANCE. This is a showcase of the agency's private internal tool, an ad for the agency itself. There is nothing to download or use, and no method is explained. It appears genuine (it is built around Claude Code skills, CLAUDE.md and Anthropic credit checks), but nothing about it is verifiable.

### Post description
> A nova forma de controlar projetos com IA Agência digital + ferramentas de IA para negócios
> Digital agency + AI tools for business
> 📲 WhatsApp / Contact link Bio

(Portuguese line 1: "The new way to control projects with AI. Digital agency + AI tools for businesses.")

### Audio
Music only. No speech (Whisper detected no speech segments). The song is not identified.

### On-screen content, page by page
**Page 1 (0.0–5.4s): "TRACKTOR Comando"**, subtitle "MAX MUNHOZ · AGENTIC OS". Top bar: "● SINCRONIZADO 18:22", tabs "FRED", "TRÁFEGO".
- Left panel "**CARTEIRA**" (client portfolio, "PANORAMA 09-07 08:40"): a list of 19 client accounts, each row showing client name · monthly fee · unit cost (cost per lead / conversion / sale) · service type. Visible monthly fees range from about R$500 to R$3,200; unit costs from about R$3 to R$38 per conversion. Services: Google/Meta ads, content, branding/production and "sistema" (custom systems). [Client names and individual fees redacted: these are private third-party businesses and people shown by accident.]
  
  Footer: "**19 CONTAS · 9 PAGANTES · R$ 14.039/MÊS**".
- Centre: a radial network of the client nodes around a particle core, with ring icons for the bot agents.
- Right panel "**EQUIPE**": "143 NA EQUIPE", "**6 TRABALHANDO AGORA · 9381 DISPAROS HOJE**", plus a grid of agent icons.
- "AGORA · BRASÍLIA 18:22:23, SEG, 07 DE SET DE 2026". "AVISOS · FILA DO MOTOR: 9 avisos hoje, 9 na fila". The bottom log ticker shows "…[client]: erro lendo changeevent: HTTPError HTTP Error 403: Forbidden … sincronia nada novo".

**Page 1, scrolled (~3–5s):**
- AVISOS list: "feriado 7/9 · [client] feriado: R$ 27.86 e 2…", "docker [client] agiu", "Prospector, manhã de 07/09", "reels [client] · programação da semana d…", "docker [client] · PROMESSA ATRASADA", "funil real da semana · [client]", "… · [client]", "… · [client]".
- "**SKILLS DECK**" (+ SKILL): `/otimizacao-conta`, `/relatorio-3-passos`, `/quadro-campanhas`, `/loop-criativos`, each tagged "SONNET · MEDIUM". Last run: "/otimizacao-conta · opus · OK".
- "**ROTINAS**" (151 rotinas): 18:00 "cd /opt/tracktorleads/sai…"; 19:00 "Vigia do crédito da intelig[ência]… ANTHROPIC-CREDIT-CHECK" (PRÓXIMA); 19:25 "Descobre o telefone de v… RESOLVE-CID…"; 20:30 "Cobra do dono o número…"; "a cada 30 min · Atualiza o painel do [client]… UPDATE-DATA"; "Atualiza o painel do [client]…" (48x/dia). Footer: "9381 DISPAROS HOJE · VPS · DISCO".
- Notes: "Guardião de saldo das contas de anúncio, avisa o Max e o cliente 18:23", "fred-[client] 18:23", "Copia as mudanças do Google Ads pro caderno da conta, de hora em hora 18:25". "FUNIL 7 DIAS: [client] 548".

**Page 2 (5.4–23.7s): "TRACKTOR Segundo Cérebro"** (header buttons "VOLTAR AO COMANDO", "APRESENTAR"). A graph centred on a node "**CLAUDE.MD**", with clusters for each client folder (agency folders plus about 19 client folders; names redacted).
**Page 3 (23.7–26.0s):** Back to "TRACKTOR Comando" loading ("CARREGANDO"), showing panels AGORA, AVISOS, FUNIL 7 DIAS, SKILLS DECK, ROTINAS.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| TRACKTOR Comando / "Agentic OS" | internal app | pages 1, 3 | A custom, private agency dashboard. Not a public product, so not verifiable. |
| TRACKTOR Segundo Cérebro | internal app | page 2 | A "second brain" graph view of client folders around a `CLAUDE.md` file, the memory file used by Claude Code |
| Max Munhoz | person | subtitle | Apparently the agency owner or operator. Not found by web search. (A different agency, "Traktor", founded 2018 by Eduardo and Gabriel, is unrelated.) |
| Skills `/otimizacao-conta`, `/relatorio-3-passos`, `/quadro-campanhas`, `/loop-criativos` (Sonnet/Opus) | Claude Code skills | page 1 | Custom slash-command skills running on Anthropic Claude Sonnet and Opus models |
| ANTHROPIC-CREDIT-CHECK | routine | page 1 | A scheduled job that monitors Anthropic API credit |
| 19 contas · 9 pagantes · R$ 14.039/mês | numbers | page 1 | Self-reported agency revenue (19 accounts, 9 paying, about R$14k/month) |
| 9381 disparos hoje; 143 na equipe; 151 rotinas | numbers | page 1 | Counts of automated agent runs, "team" bots and scheduled routines |
| Client names (redacted) | businesses | page 1–2 | The agency's apparent real clients, shown with fees and CPA figures |
| "WhatsApp / Contact link Bio" | CTA | caption | Leads to WhatsApp contact with the agency |

### What's being promoted / the funnel decoded
- The agency's services: "Agência digital + ferramentas de IA para negócios" (digital agency plus AI tools for businesses), meaning paid traffic (Google and Meta ads), content and "systems" built with Claude agents. The call to action is WhatsApp via the bio link, so it is lead generation for agency retainers. On-screen fees for current clients range from **R$ 500 to R$ 3,200 per month**.

### Verification & insights
- The tool looks like a real Claude Code–based agency stack: skills, CLAUDE.md, cron-style routines, Anthropic credit monitoring, Docker jobs per client and a VPS. There is no repo or product for anyone else to use.
- Notable: the video publicly exposes client names, monthly fees, cost-per-conversion figures and an error log ("HTTP Error 403: Forbidden"). That suggests weak attention to client confidentiality.
- The "9381 disparos" (runs or messages fired) metric is a vanity number with no context.
- Could not verify: the agency's identity, website or pricing, and Max Munhoz.

---

<a id="e-deet0vsp-kq"></a>

## Deet0VsP-KQ | @raycfu | "How to use GPT-6 Astra to find profitable trading strategies" (reviewed from the cover image only)
- **Link:** https://www.instagram.com/p/Deet0VsP-KQ/
- **Account:** @raycfu (display name not captured) · **Posted:** unknown · **Type:** reel. **The video could not be retrieved; this review is from the cover image only.** The material held only `m01.jpg`, and one yt-dlp attempt returned HTTP 429.
- **Caption source:** possibly truncated (mirror). The 70-character caption ends with hashtags and looks complete.
- **Category:** AI tools / Trading strategy
- **Verdict:** NO SUBSTANCE (as reviewable). GPT-6 Astra is a real OpenAI model, but the method, prompts and any claimed results are in the unretrieved video. "Find profitable trading strategies" with an LLM should be treated as unproven.

### Post description
> How to use GPT-6 Astra to find profitable trading strategies #ai #tech

### Audio
Not available, because the video could not be retrieved. The cover shows a burned-in subtitle fragment, "most people don't realize that", which suggests the creator speaks on camera.

### On-screen content, page by page
**Cover (only frame available):** A young man seated at a desk in a bright apartment (a sofa with plush toys, plants, a laptop and a monitor), filmed from a high angle. Title text in serif type: "How to Use **GPT-6 Astra** to Find **Profitable Trading Strategies**", with the coloured words in yellow. Subtitle: "most people don't realize that".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| GPT-6 Astra | AI model | caption, cover | Real. OpenAI released GPT-6 Astra on 2026-09-03 as its new flagship (openai.com/index/gpt-6-astra; Axios 2026-09-03). It launched with limited early access, then reached ChatGPT Plus/Pro/Business/Enterprise and the API. Reported API price: $10 per million input tokens and $50 per million output. OpenAI rates it "critical" on its cybersecurity preparedness threshold. |
| @raycfu | handle | account | No public information found about this creator. |

### What's being promoted / the funnel decoded
No call to action is visible in the caption or the cover. Any CTA, link or product would be in the unretrieved video. Nothing could be determined.

### Verification & insights
- The model exists and is current. Nothing about the strategy method could be checked.
- **General caution:** LLM-"discovered" strategies are usually backtest-fitted. Without out-of-sample testing, trading costs and a large sample, "profitable" claims are unreliable. The other trading post in this batch (Def2Wy5gfG2) shows the typical pattern.
- **Could not verify:** the video content, the audio, the on-screen pages, the funnel or the post date. **Re-fetch the video when Instagram stops rate-limiting.**

---

# Category: GitHub & dev (33 posts)

<a id="e-db33idbjcsm"></a>

## Db33iDBJcsm | @99hud | OpenWA: an open-source, self-hosted WhatsApp API gateway with an MCP server so Claude Code can send WhatsApp messages (Portuguese)
- **Link:** https://www.instagram.com/p/Db33iDBJcsm/
- **Account:** @99hud (Hudson Brendon | Claude, IA & Automação; 19.4K followers shown on screen) · **Posted:** 2026-08-10 · **Type:** reel (36s; 12 scene pages plus animated screens checked frame by frame)
- **Caption source:** full (Instagram; fetched with yt-dlp during review, since the mirror copy was truncated)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE – OpenWA (rmyndharis/OpenWA, MIT) is real, active and has a built-in MCP server. The post leaves out that it's an unofficial, reverse-engineered WhatsApp client with real ban risk (especially for "disparar pra uma lista"), and that MCP is off by default and needs an API key.

### Post description
> Comenta "ZAP" que eu te mando o guia completo no Direct.
>
> O Claude Code operando o seu WhatsApp, com a API rodando no seu próprio computador.
>
> O projeto se chama OpenWA e é open source. Ele sobe uma API de WhatsApp local, de graça. Um comando abre o painel no navegador e você liga a sua conta ali mesmo.
>
> A parte que muda o jogo é o MCP. Você pluga o MCP do OpenWA no Claude Code e ele passa a enxergar quase 40 ferramentas do WhatsApp — sessão, mensagem, contato, grupo, webhook.
>
> Aí é só pedir no chat: manda mensagem pro cliente, avisa o grupo, dispara pra uma lista de contatos. Quem executa é o Claude.
>
> E tudo self-hosted: seus dados ficam no seu PC, sem depender de API paga por fora e sem número de terceiro no meio.
>
> 👇 Comenta "ZAP" que eu te mando o guia completo pra você conectar hoje.
>
> #claude #claudecode #whatsapp #ia #inteligenciaartificial

(Caption in English, summarized: comment "ZAP" for the full guide by DM. OpenWA is open source and runs a local WhatsApp API for free; one command opens a browser panel where you link your account; you plug its MCP into Claude Code, which then sees "almost 40" WhatsApp tools (session, message, contact, group, webhook) and can message a client, notify a group, or blast to a contact list; all self-hosted, with no paid API and no third-party number.)

### Audio
Creator's own speech (Portuguese; Whisper errors corrected: "cloud" = Claude, "contador" = computador, "zapa" = ZAP):
- [0.0–3.1] "Esse projeto open source conecta o Claude direto no seu WhatsApp." (This open-source project connects Claude directly to your WhatsApp.)
- [3.1–7.7] "Ele se chama OpenWA e sobe uma API de WhatsApp direto no seu computador, de graça." (It's called OpenWA and runs a WhatsApp API on your own computer, for free.)
- [7.7–11.8] "Com apenas um comando, ele abre um painel no navegador pra você integrar sua conta." (One command opens a browser panel to link your account.)
- [11.8–16.2] "A parte boa: ele tem MCP, você pluga esse MCP no Claude e pronto." (The good part: it has MCP; plug it into Claude and you're done.)
- [16.2–20.6] "O Claude enxerga 40 ferramentas de WhatsApp e passa a operar tudo por você." (Claude sees 40 WhatsApp tools and operates everything for you.)
- [20.6–25.6] "Depois é só pedir no chat pra mandar mensagem, avisar no grupo ou disparar pra uma lista de contatos." (Then just ask in chat to send a message, notify a group, or blast to a contact list.)
- [25.6–30.4] "Tudo self-hosted, seus dados ficam no seu computador, sem depender de API paga por fora." (All self-hosted; your data stays on your computer; no paid external API.)
- [30.4–36.0] "Comenta ZAP aqui embaixo e me segue, que eu te mando um guia completo pra você conectar o Claude e o seu WhatsApp ainda hoje." (Comment ZAP and follow me and I'll send a complete guide to connect Claude and WhatsApp today.)

### On-screen content, page by page
Split-screen layout: an animated graphic on top, the creator in a purple-lit room (Batman: The Killing Joke poster) on the bottom, with word-by-word captions.
**Page 1 (0.0–3.0s):** Graphic of the Claude logo ("CLAUDE") linked to the WhatsApp logo ("WHATSAPP"). Caption "Esse projeto open source conecta o Claude direto no seu WhatsApp".
**Page 2 (3.1–4.4s):** Full-screen OpenWA logo (green speech bubble, script "OpenWA"); "ELE SE CHAMA".
**Pages 3–4 (4.4–7.6s):** Creator full-screen; captions "API DE WHATSAPP DIRETO NO SEU COMPUTADOR DE GRAÇA".
**Page 5 (7.6–10.3s):** Terminal: `$ docker compose up -d` → "✔ Container openwa-redis Started", "✔ Container openwa-api Started", "→ painel http://localhost:2785". Caption "comando… painel… navegador".
**Page 6 (10.3s):** Browser window "localhost:2785", "Conectar WhatsApp", a QR code, status "Aguardando leitura…" (waiting for scan). Caption "pra".
**Page 7 (11.1s):** Same window, QR with a green check, "Conectado · +55 11 9••••-••••". Caption "pra você integrar sua conta".
**Pages 8 (11.7–16.0s):** File ".MCP.JSON":
```
{
  "mcpServers": {
    "openwa": {
      "type": "http",
      "url": "http://localhost:2785/mcp"
    }
  }
}
```
Captions "A parte boa, ele tem MCP, você pluga MCP no Claude e pronto".
**Page 9 (16.1–20.4s):** A counter animating from 0 to **40**, "FERRAMENTAS DO WHATSAPP", ringed by tool names: send_message, send_media, list_chats, get_contacts, (add)_participant, read_messages, (send)_location, get_pr(ofile…), (list)_sessions, start_session, send_document, get_group_info, leave_group, block_contact. Caption "O CLAUDE ENXERGA 40 FERRAMENTAS DO WHATSAPP E…".
**Page 10 (20.5–25.4s):** "CLAUDE CODE" terminal: `> manda "Fala!" pro cliente no zap` → "● openwa – send_message (MCP) └ enviado para +55 11 9••••-••••" → "● openwa – send_group_message (MCP) └ grupo "Clientes · SP" avisado" → "✔ 2 ferramentas executadas". Caption "…mandar mensagem, avisar no grupo ou disparar para uma lista de contatos".
**Page 11 (25.5–30.3s):** Diagram: "SEU PC" (padlock, green) — line — "API PAGA" (cloud, greyed out). Captions "SELF-HOSTED… DADOS…".
**Page 12 (30.3–36.2s):** Creator full-screen; captions "COMENTA ZAP…", "GUIA…", "CLAUDE NO SEU…". Instagram follow card "99hud ✓ 19,4 mil seguidores [Seguir]".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| OpenWA (github.com/rmyndharis/OpenWA) | repo | caption; audio 3.1s; p.2, 5–8 | "Open Source WhatsApp API Gateway" (NestJS, Docker). **MIT** license (© 2026 Yudhi Armyndharis and OpenWA Contributors). Very active: HEAD dc070ac, last commit 2026-10-21 (merge of PR #1903). |
| `docker compose up -d`; containers openwa-redis, openwa-api; http://localhost:2785 | command / port | p.5 | Matches the README: the dashboard and API share port **2785** (API at /api, Swagger at /api/docs). |
| .mcp.json with `http://localhost:2785/mcp` | config | p.8 | Matches the README, except the README's version also needs `"headers": {"Authorization": "Bearer YOUR_API_KEY"}` and the server only mounts /mcp when **`MCP_ENABLED=true`**. |
| "40 ferramentas" / "quase 40" | claim | audio 16.2s; caption; p.9 | Currently 25 read-only tools by default, or 51 with `MCP_READONLY=false` (which adds send/reply/group writes). "~40" was likely accurate for an earlier version (the post is from Aug 2026). |
| send_message, send_group_message, list_chats, get_contacts, etc. | MCP tools | p.9–10 | MCP tool names shown in the animation. |
| Claude Code | app | caption; p.10 | Anthropic's CLI agent, used as the MCP client. |
| whatsapp-web.js, @whiskeysockets/baileys | libraries | README (not in post) | The reverse-engineered WhatsApp clients that OpenWA runs on. |
| Comment "ZAP" | CTA | caption; audio 30.4s | DM guide. |

### What's being promoted / the funnel decoded
"Comenta ZAP" triggers an automated DM (ManyChat-style) with a "guia completo". It's almost certainly a free PDF or Notion setup guide, used to grow followers ("me segue") for an AI-automation creator (display name "Claude, IA & Automação"). No price or paid product is visible. The post's comment count (6,130) is driven by the keyword CTA. You don't need the guide: the OpenWA README has a full Quick Start and an MCP section.

### Verification & insights
- Cloned `rmyndharis/OpenWA` (shallow) into `scratchpad/repos/rmyndharis__OpenWA`. Read the LICENSE (MIT), README and `git log -1`. Code was not executed.
- **The post leaves this out:** the README states OpenWA is **unofficial** and connects through reverse-engineered clients, **not Meta's official Cloud API**. "There is always a non-zero risk of account restriction or ban." It recommends send pacing and warns that "thousands in an hour" isn't sustainable. "Disparar pra uma lista de contatos" (bulk messaging) is exactly the behavior that gets numbers banned, and it can breach WhatsApp's Terms of Service and anti-spam rules.
- The README's own security guidance: use a dedicated least-privilege, session-scoped API key for the agent; keep `MCP_READONLY=true` unless you need sends; never expose /mcp to the internet. The post's .mcp.json omits the auth header.
- "Self-hosted, your data stays on your PC" is true for the gateway. When Claude Code reads chats through MCP, though, that message content is sent to the model provider.
- Related: a separate community "OpenWA MCP Server" is listed on Glama, but OpenWA now ships MCP natively.
- Could not verify: what the DM guide contains.

---

<a id="e-det9wwwicmu"></a>

## Det9wWwiCmu | @cookin.code | Animated explainer of codecrafters-io/build-your-own-x ("most-starred GitHub repo", 552.5k stars): step-by-step guides to rebuild Git, Docker, a database, a browser and an OS from scratch
- **Link:** https://www.instagram.com/p/Det9wWwiCmu/
- **Account:** @cookin.code (on-screen profile card: "Connor · Software Engineer – AI tools, repos and dev tips") · **Posted:** 2026-10-20 (decoded from shortcode; not in fetched data) · **Type:** reel (33s, 6 scene pages captured; all 66 2-fps frames reviewed, because the scene detector caught mostly transition frames)
- **Caption source:** possibly truncated (mirror) – looks complete (one sentence)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE – the repo is real, CC0-licensed and free; star/fork numbers match GitHub; the "comment" funnel just DMs the public link

### Post description
> Comment "Star" for the repo in your DMs!

Note: the caption says comment **"Star"**, but the video (audio and on-screen) says comment **"BUILD"**.

### Audio
Creator's own voice-over (English):
- [0.0–4.5] "The most starred GitHub repository of all time isn't React, Linux, or even Python."
- [4.5–6.4] "It's actually build-your-own-x."
- [6.4–9.5] "And here's why over half a million developers have starred it."
- [9.5–14.8] "Most of us use Git, Docker, and databases every day without knowing how any of them actually work."
- [14.8–19.5] "This repo fixes that. It's a list of step-by-step guides to build each one yourself, from scratch."
- [19.5–24.7] "And that matters, because a to-do app on your resume looks like everyone else's. 'I built my own Git' doesn't." (Whisper: "I built my own Git dozen")
- [24.7–29.7] "It's also exactly the stuff interviewers love to dig into, and once you've built it, you can actually explain it."
- [29.7–32.2] "Comment BUILD and I'll send it straight to your DMs."
Soft background music under the voice; no lyrics transcribed.

### On-screen content, page by page
Each scene has a word-by-word kinetic headline at the top that mirrors the voice-over; the cards below carry the data.
**Page 1 (0.0–4.5s):** Dark card "GitHub stars over time – all-time star counts", y-axis 100K–500K, x-axis 2012, 2015, 2018, 2021, 2024. Three glowing lines; labels **"Linux"** and **"React"** appear and are struck through in red ("isn't React, Linux, or even…").
**Page 2 (5.0–6.0s):** Headline "Build Your Own"; the blue line shoots up to a star with gold pill **"#1 build-your-own-x"**.
**Page 3 (6.5–9.5s):** Repo card: GitHub logo, **"build-your-own-x – Public repository – Master programming by recreating your favorite technologies from scratch."** Star counter animates up to **★ 552.5k**; below **"51.8k forks · 30 categories · free, CC0"**; pill **"★ #1 most-starred repo on GitHub"**. Headline: "developers have *starred* it."
**Page 4 (10.0–15.5s):** Light theme. Three cards with question marks: **"Git – used every day"**, **"Docker – used every day"**, **"Database – used every day"**; pill "★ build-your-own-x". Headline "This repo".
**Page 5 (16.0–19.5s):** Card "README.md – Build your own *anything*", checklist:
  - Git – Write yourself a Git! – Python
  - Docker – Linux containers in 500 lines of code – C
  - Database – Let's Build a Simple Database – C
  - Web Browser – Browser Engineering – Python
  - Operating System – Writing an OS in Rust – Rust
  - "+ 25 more categories, step-by-step guides"
  Pill: **"From scratch · no frameworks, no magic"**. Headline "from scratch."
**Page 6 (19.5–25.5s):** Dark "Resume – PROJECTS" card: "Todo App – React · localStorage", "Weather App – React · OpenWeather API" (headline "looks like everyone else's"); then both get red strike-through and a new top entry **"Built my own Git – from scratch in Python · init, add, commit"**; green toast **"You got the job! – Offer: Software Engineer – now"**.
**Page 7 (26.0–29.5s):** "Technical interview – Software Engineer · onsite – ● live". Interviewer bubble: "How does Git actually store a commit?" Reply bubble: "It's an object holding a tree hash, the parent hash, the author and a message, all named by its SHA-1." Pill "✓ Explained it, not memorized it". Headline "you can actually *explain*".
**Page 8 (29.5–33.0s):** Instagram profile card "cookin.code – Connor · Software Engineer – AI tools, repos and dev tips – Following"; comments sheet: "you · now: **BUILD**" → "cookin.code · now: Sent! Check your DMs". Headline "Comment BUILD … straight to your DMs."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| build-your-own-x (codecrafters-io/build-your-own-x) | repo | audio 4.5s, pages 2–5 | Real. github.com/codecrafters-io/build-your-own-x. Started by Daniel Stefanovic, maintained by CodeCrafters, Inc. **CC0** (public-domain dedication). GitHub page on check: ~554.9k stars, ~52.0k forks (post: 552.5k / 51.8k – consistent). Last commit 2026-07-14 (merge PR #1844). README has 30 "Build your own …" categories + an "Uncategorized" section, ~389 linked tutorials |
| "#1 most-starred repo on GitHub" | claim | audio 0–6s, page 3 | Plausible given ~555k stars (freeCodeCamp was the long-time #1 in earlier years); could not run GitHub's global star ranking from this session, so the rank itself is not independently confirmed |
| React, Linux, Python | named repos | audio 0–4.5s, page 1 | Used as "not #1" comparisons; chart lines are illustrative, not real star histories |
| Write yourself a Git! (Python) | tutorial | page 5 | Listed in the repo → wyag.thb.lt |
| Linux containers in 500 lines of code (C) | tutorial | page 5 | Listed → blog.lizzie.io/linux-containers-in-500-loc.html |
| Let's Build a Simple Database (C) | tutorial | page 5 | Listed → cstack.github.io/db_tutorial (SQLite clone) |
| Browser Engineering (Python) | tutorial | page 5 | Listed → browser.engineering |
| Writing an OS in Rust (Rust) | tutorial | page 5 | Listed → os.phil-opp.com |
| "+25 more categories" / "30 categories" | number | pages 3, 5 | Matches README: 30 categories (5 shown + 25) |
| Git commit = tree hash + parent hash + author + message, named by SHA-1 | technical claim | page 7 | Correct for classic Git (also committer and timestamps; newer repos can use SHA-256) |
| "BUILD" / "Star" | comment keywords | audio 29.7s, page 8 / caption | Auto-DM trigger (see funnel) |
| @cookin.code ("Connor") | handle | page 8 | Same creator as Desq5O9i_4P; no independent web info found |

### What's being promoted / the funnel decoded
Comment-to-DM automation (ManyChat-style): commenting "BUILD" (caption says "Star") triggers a DM with the repo link. What you would receive is simply **https://github.com/codecrafters-io/build-your-own-x** – free, public, no sign-up. The purpose is engagement/follower growth (the comment boosts the reel). Side note: the repo itself is maintained by CodeCrafters, Inc., which sells paid "Build your own X" coding challenges (codecrafters.io banner at the top of the README), but nothing in the post pushes that.

### Verification & insights
- Cloned (depth 1) into scratchpad/repos/build-your-own-x: README, CC0 "Origins & License" section, last commit 2026-07-14 confirmed. GitHub page fetch: ~554.9k stars / ~52.0k forks.
- All five tutorials named on screen are real entries in the README, with the languages shown.
- Claims vs reality: star and fork numbers accurate; "over half a million developers have starred it" accurate. The resume → "You got the job!" sequence is motivational framing, not evidence.
- The repo is a curated link list; the quality of each external tutorial varies, and some links in such lists go stale.
- Not verified: the creator's identity and the exact all-time GitHub rank (no global search API from this session).

---

<a id="e-ddzab51gbvr"></a>

## DdZaB51gBVR | @replace.so | "3 best free open-source repos this week": Nanobot (AI agent framework), OpenChatCut (AI video editor), OpenSEO (SEO tool) – each framed as a replacement for a paid SaaS
- **Link:** https://www.instagram.com/p/DdZaB51gBVR/
- **Account:** @replace.so · **Posted:** 2026-09-17 (decoded from shortcode; not in fetched data) · **Type:** reel (30s, 5 scene pages)
- **Caption source:** possibly truncated (mirror) – **cut off** after "OpenChatCut i…"
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE – all three repos are real and open-source (nanobot MIT, OpenChatCut AGPL-3.0, OpenSEO MIT); "free alternative to Zapier/CapCut/Semrush" is directionally fair, but each still costs money to run (your own LLM API keys, or DataForSEO credits for OpenSEO), and OpenChatCut has a paid "Pro" desktop edition

### Post description
> Here are the 3 best free open-source repos this week 🚀
>
> 1️⃣ Nanobot - Self-hosted personal AI agent platform with WebUI, chat channels, tools, memory, MCP integrations, scheduled automations, and multi-agent workflows.
> 2️⃣ OpenChatCut - OpenChatCut i… (caption truncated by mirror; item 3 / OpenSEO and any CTA not in the retrieved caption)

### Audio
Narrator (likely TTS/voice-over) over the screens:
- [0.0–2.8] "I found open-source repos you shouldn't miss today."
- [2.8–9.8] "Nanobot provides a self-hosted personal AI agent framework with MCP integrations to automate tasks across apps."
- [9.8–11.4] "Competing directly with Zapier." (Whisper: "zappier")
- [11.4–20.0] "Instead of [CapCut], OpenChatCut delivers a local-first AI video editor with editable multi-track timelines for producing professional quality videos." (Whisper heard "screen" for CapCut)
- [20.0–27.3] "Instead of SEMrush, OpenSEO serves as an open-source alternative with keyword research tools to increase your online visibility."
- [27.3–30.0] "Comment 'repos' and I'll send you every GitHub link."

### On-screen content, page by page
Dark background with a pink pixel-grid; a browser-style card per repo, lowercase captions.
**Page 1 (0–?):** Nanobot card – cat logo; header "nanobot · MIT license · 48.3K stars"; text "nanobot is an ultra-lightweight, open-source, self-hosted personal AI agent framework written in Python. It runs in [WebUI/API/TUI]"; "Why nanobot: Persistent workflows (goals, memory, tools, chat context survive long-running work); Chat-native reach: WebUI, API, Telegram, Feishu, Slack, Discord, Teams, email, and Mattermost; Model freedom: OpenAI-compatible APIs, local LLMs, image generation, search, and fallbacks"; install table (Stable = installer/uv/pip; Current source = editable Git checkout). Subtitle "i found open".
**Page 2 (?):** (transition) – nanobot install steps: "Install nanobot with no terminal/config", "Deploy to the cloud or keep nanobot running as a service", "Connect Telegram, Discord, WeChat, Slack, Email, Mattermost…", "Configure providers, fallback models, LangChain/MCP, web tools, or security".
**Page 3 (~11s):** OpenChatCut card – chat-video logo; "OpenChatCut · [1.3K] stars"; "Open-source ChatCut alternative · agent-native · local-first AI video editor"; "What is OpenChatCut? OpenChatCut is an open-source ChatCut alternative: a video editor that brings conversational agents and… = local video projects + multitrack timeline + AI agents + MCP + production-ready exports"; "support on Ko-fi or Afdian". Subtitle "instead of screen".
**Page 4 (~?):** (OpenChatCut continued).
**Page 5 (~20s):** OpenSEO card – "OpenSEO · [8K] stars"; "Open source alternative to Semrush and Ahrefs"; "OpenSEO is an SEO tool for the people. If tools like Semrush or Ahrefs are too expensive or bloated, OpenSEO is a pay-as-you-go alternative that you actually control"; "Why use OpenSEO? OpenSEO MCP & Agent Skills…". Subtitle "instead of semrush".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Nanobot (HKUDS/nanobot) | repo | caption, audio, pages 1–2 | Real. github.com/HKUDS/nanobot – "ultra-lightweight, open-source, self-hosted personal AI agent framework", Python ≥3.11, **MIT**. By HKUDS (HKU Data Intelligence Lab). ~48.3K stars (shields confirm MIT); active (commit 2026-10-21). Chat channels (Telegram/Discord/Slack/Feishu/WeChat/Email/Mattermost), MCP, memory, scheduled tasks, multi-agent |
| "Competing with Zapier" | claim | audio | Framing; nanobot is a self-hosted agent framework, overlaps with automation but is not a Zapier clone |
| OpenChatCut (0xsline/OpenChatCut) | repo | caption, audio, pages 3–4 | Real. github.com/0xsline/OpenChatCut – "Open-source ChatCut alternative · agent-native · local-first AI video editor" (lets Codex/Claude Code/built-in agent edit real multitrack projects). **AGPL-3.0**. ~1.3K stars (Aug 2026); active (commit 2026-10-20). Has a paid **OpenChatCut Pro** desktop edition |
| "Instead of CapCut/ChatCut" | claim | audio | Audio says "screen"/implies CapCut; the repo itself positions against **ChatCut** (an AI video-editing product), not CapCut |
| OpenSEO (every-app/open-seo) | repo | audio, page 5 | Real. github.com/every-app/open-seo – "Open source alternative to Semrush and Ahrefs", pay-as-you-go, **MIT**, self-host via Docker/Cloudflare, **bring your own DataForSEO API key**, includes an MCP server. ~4–18K stars by source; active (commit 2026-10-19, "Enroll OpenSEO in Anthropic's OSS Scanner") |
| "repos" | comment keyword | audio 27s | DM funnel (sends the GitHub links) |
| @replace.so | handle | account | "replace.so" brand curating open-source replacements for paid SaaS |

### What's being promoted / the funnel decoded
Comment "repos" → automated DM with the three GitHub links. No paid product sold by the account in this post; it is a curation/engagement account (@replace.so – "replace [paid tool] with open source"). The links themselves are free public GitHub repos. Caveats on "free": nanobot and OpenChatCut need your own LLM API keys (or local models) to actually do anything; OpenSEO needs a paid DataForSEO key (pay-as-you-go); OpenChatCut also sells a "Pro" desktop edition. So "free" = the code/self-host option, not zero running cost.

### Verification & insights
- All three repos verified by git ls-remote + shallow clone into scratchpad/repos (code not executed): licenses confirmed (nanobot MIT, OpenChatCut AGPL-3.0, OpenSEO MIT); all actively maintained (Oct 2026 commits). Star figures on screen are plausible and match third-party trackers at the time (nanobot ~48K; OpenChatCut ~1.3K; OpenSEO a few-K to ~18K depending on snapshot).
- Accuracy: the one-line descriptions are faithful. The "instead of X" framing is marketing shorthand — these are early-stage OSS projects, not drop-in replacements for mature SaaS, and OpenChatCut's AGPL license has copyleft obligations if you build on it.
- Note: a separate `nanobot-ai/nanobot` exists (unrelated, smaller MCP-host project); the one shown is HKUDS/nanobot.
- Not verified: exact live star counts, and the full caption/CTA (truncated).

---

<a id="e-dejcacwz89b"></a>

## DejcAcwz89b | @haarddiikk | trim-1: a free 1.2 MB open-source model (caveman-ai/trim-1) that cuts irrelevant lines from logs, files and chats before an AI agent reads them
- **Link:** https://www.instagram.com/p/DejcAcwz89b/
- **Account:** @haarddiikk (Hardik Agarwal) · **Posted:** 2026-10-16 · **Type:** reel (28.9s, 23 scene frames / ~10 distinct screens)
- **Caption source:** full (Instagram, via yt-dlp info.json; identical to the mirror text)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE – the repo exists, is Apache-2.0, and matches every on-screen claim. One wording quibble: the "AI model" is 712 gradient-boosted trees, not a neural network.

### Post description
> Comment “TRIM” to get the link.
>
> #aitools #github #vibecoding #claude #trending

### Audio
The creator speaks to camera in English, with background music.
- [0.0–4.8] "Someone built an AI model whose only job is to cut the junk your agent doesn't need to read."
- [4.8–9.5] "It's called trim1 and it's open source and free. Give it a file, a log, or a long chat."
- [9.5–13.8] "Plus what you're asking. It keeps only the lines your agent actually needs and drops the rest."
- [13.8–18.0] "And it never rewrites or summarizes anything. So your file paths and error messages come"
- [18.0–22.9] "through exactly as they were. The whole model is just 1.2 megabytes. It runs in milliseconds"
- [22.9–27.9] "on a single CPU [core] with no GPU and no internet. Comment trim to get the github link"
- [27.9–32.2] "and follow for more."
(Whisper heard "CPU port"; the on-screen text reads "one CPU core".)

### On-screen content, page by page
Burned-in word-by-word subtitles (for example "AI MODEL WHOSE", "ONLY JOB IS", "JUNK YOUR AGENT") repeat the speech and are not listed separately.
**Page 1 (0.0–4.9s):** Heading "One job:". The creator sits at a desk (an Acer monitor is behind him; his shirt carries a "Reticle" logo). Above him is a screenshot of the repo banner:
- URL bar: `github.com/caveman-ai/trim-1`; breadcrumb "trim-1"
- Pixel logo "TRIM-1", tagline "WHY READ MANY LINE WHEN FEW DO TRICK"
- Description: "Agent read whole log to find one error. trim-1 keep the lines the ask need and drop the rest. Every kept line exact. Nothing rewritten."
- "SAY THIS TO SHELL": `$ trim --query "why fail" build.log  # drop rest`
- "HOW BIG IS ROCK": "1.2 MB model · 7 ms 5k tokens, 1 core · 0 GPUs"

**Page 2 (4.9–7.2s):** A dark title card, "It's called", followed by the subtitle "IT'S CALLED TRIM-1,".
**Page 3 (7.2–10.5s):** The creator again. Chips read "a file", "a log", "a long chat". A terminal panel shows `$ trim --query "why does the build fail" buil…` with the tag "+ WHAT YOU'RE ASKING". Subtitle: "CHAT,".
**Page 4 (10.6–13.9s):** "Keeps the lines that matter". A build.log panel shows these lines:
```
12:01:03 INFO starting build (go1.23)
12:01:03 INFO resolving 214 modules
12:01:04 DEBUG cache hit: x/sys
12:01:05 INFO compiling ./internal/auth
internal/store/cache.go:88:14: undefined: lru.NewWithTTL   <- highlighted
12:01:06 DEBUG gc pass 2/3
12:01:06 INFO compiling ./cmd/server
FAIL build failed: 1 error                                  <- highlighted
12:01:07 INFO elapsed 4.21s
```
A tag reads "DROPS THE REST". Subtitles: "IT KEEPS ONLY THE LINE(S) … AGENT ACTUALLY NEEDS AND DROPS THE …".
**Page 5 (13.9–19.2s):** "Nothing rewritten". The two kept lines (`internal/store/cache.go:88:14: undefined: lru.NewWithTTL` and the FAIL line) are shown unchanged. Subtitles: "AND IT NEVER … SUMMARIZES … SO YOUR FILE PATHS AND ERROR MESSAGES COME THROUGH".
**Page 6 (19.2–26.2s):** A counter animates from "0.0 MB" to "1.2 MB", then adds "runs in milliseconds", "one CPU core" and "✕ no GPU". Subtitles: "IS JUST 1.2 MEGABYTES… SINGLE CPU CORE… WITH NO GPU".
**Page 7 (26.2–28.9s):** A button reads "Comment "TRIM"", with "Free on GitHub · caveman-ai/trim-1" and "+ Follow for more". Subtitles: "GET THE GITHUB LINK AND FOLLOW".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| github.com/caveman-ai/trim-1 | repo | Pages 1 and 7 | Real public repo. Apache-2.0 (plus BSD for a copied Go `math.Exp`). Pure Go, with the model embedded as `model.bin` (1,245,358 bytes). Last commit 2026-10-14 by Julius Brussee, "Merge pull request #1 from ronxjansen/fix/input-cap". |
| trim-1 | model / CLI | Audio and pages | A model that scores each line of a context for relevance to a query and drops the rest. The README describes it as "712 gradient-boosted trees, not a neural network". |
| `trim --query "why fail" build.log` | CLI command | Page 1 | Matches the README's usage. A `--point conservative/balanced/aggressive` flag also exists. |
| 1.2 MB, 7 ms for 5k tokens on 1 core, 0 GPUs | numbers | Pages 1 and 6, audio | Match the repo banner. The model file is 1.2 MB. The timing claim was not executed and is unverified. |
| Caveman (github.com/JuliusBrussee/caveman) | product | README only | trim-1 is "the model inside Caveman". |
| huggingface.co/caveman-so/trim-1 | model card | README only | Model card with benchmark results and limits. Not fetched. |
| "Reticle" | brand on creator's shirt | Video | The creator's apparent employer or brand. Not connected to the repo. |
| @haarddiikk | handle | Account | Hardik Agarwal. Not the repo author. |

### What's being promoted / the funnel decoded
"Comment TRIM" is a standard auto-DM keyword. It sends you the link github.com/caveman-ai/trim-1, which is already shown on screen (pages 1 and 7), so you don't need to comment. The creator is not the author (the repo is by Julius Brussee / caveman-ai). The goal is engagement and follower growth. There is no product for sale and no affiliate sign.

### Verification & insights
- I ran `git ls-remote` on the repo (HEAD f16ff28) and made a shallow clone into `scratchpad/repos/caveman-ai__trim-1`. I read the README, LICENSE and git log. No code was executed.
- Claims compared with the repo:
  - "AI model": this is partly true. It is a machine-learned model, but it is gradient-boosted trees, not a neural net.
  - "Never rewrites or summarizes": true per the README, which says it returns the context's own lines in original order with a removal marker.
  - "1.2 MB, no GPU, no internet": true per the README ("No GPU, no network call", no dependencies).
  - "Milliseconds": claimed by the README; not executed.
- Limits the reel leaves out (from the README):
  - It "fails closed" and returns input unchanged when the query is blank, the context is under 2,000 bytes or over 8 MiB / 200,000 lines, the context already contains a removal marker, or the cut would save less than 10%.
  - For coding-agent tool outputs the README itself says to "expect small savings". The main use case is long-document retrieval.
- It needs Go 1.23+ (`go install github.com/caveman-ai/trim-1/cmd/trim@latest`).
- Not verified: the benchmark numbers on the Hugging Face card, and real-world token savings.

---

<a id="e-dctyh0fpcx0"></a>

## DcTyH0fpCx0 | @null_sky.dev | 3D Gielis superformula particle animation in Three.js, showing the formula and live m/n1/n2 values (no tutorial or code)
- **Link:** https://www.instagram.com/p/DcTyH0fpCx0/
- **Account:** @null_sky.dev (Null Sky) · **Posted:** 2026-08-21 · **Type:** reel (20.4s, one continuous animation; 1 scene page + 20 frames at 1 fps reviewed)
- **Caption source:** full (Instagram, via yt-dlp metadata; the mirror copy was cut off)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE (no substance to act on). It is a real, well-known formula, shown as eye candy. No code, repo or link is given. "Can draw anything in nature" is hype.

### Post description
> One equation to generate infinite organic shapes in 3D 👁️✨
> Visualizing the **3D Gielis Superformula** using 20,000 glowing particles in Three.js. As the parameters (m, n_1, n_2, n_3) morph, the geometry shifts from spheres to sacred blooms, crystals, and cosmic stars.
> Code drops weekly. 💾 Save to study the math.
> #threejs #creativecoding #generativeart #mathematics #webgl glsl mathart codeart superformula

### Audio
Music only; no speech. Whisper (with VAD) found no speech. The track is not named on screen or in the caption.

### On-screen content, page by page
The whole reel is one continuous animation with a fixed layout:
- **Title (top, constant):** "THE EQUATION THAT CAN DRAW ANYTHING IN NATURE 😱"
- **Centre:** a glowing particle mesh (cyan, violet and white) that morphs continuously. Over time it becomes a 4-point star, a 6-point star, rounded cubes, wavy 7–8-point "flowers", a near-perfect sphere (about 7–9s), spiky "urchin" bursts (about 10–12s and 16–17s), a soft teardrop and faceted crystal/polyhedron shapes (about 17–20s).
- **Formula (constant):** r(θ) = ( |cos(mθ/4) / a|^n₂ + |sin(mθ/4) / b|^n₃ )^(−1/n₁)
- **Live parameter readout box:** "m = … n₁ = … n₂ = …" (n₃, a and b are not displayed). Sample values read from frames, as (m, n₁, n₂): cover (4.86, 0.30, 1.60); about 1s (≈4.26, 0.78, 1.18); 2s (≈4.57, 0.20, 1.68); 3s (n₁ 3.90, n₂ 4.31); 4s (n₁ 10.86, n₂ 9.20); 5s (n₁ 8.62, n₂ 7.88); 6s (≈6.06, 1.26, 3.25); 7s (n₁ 4.75, n₂ 2.05); 8s (n₁ 13.50, n₂ 0.49); 9s (n₁ 9.90, n₂ 0.61); 10s (≈11.73, 0.66, 1.08); 11s (≈8.03, 0.33, 1.86); 12s (≈2.66, 0.49, 3.37); 13s (≈4.06, 6.50, 7.79); 14s (≈7.59, 17.11, 15.36); 15s (≈10.04, 12.01, 10.88); 16s (≈12.77, 0.89, 1.39); 17s (≈11.39, 0.89, 0.80); 18s (≈6.44, 2.37, 0.80); 19s (≈5.84, 2.08, 0.86); 20s (≈4.11, 1.08, 0.99). The m values are in dark red on black and are approximate.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Gielis Superformula | math formula | caption, on screen | Real. Published by Johan Gielis in 2003 as a generalisation of the superellipse. 3D "supershapes" multiply two superformulas (spherical product). |
| Formula r(θ) as shown | equation | on screen | Correct 2D superformula with m₁ = m₂ = m. The 3D version needs two of these (for latitude and longitude), which the reel does not show. |
| Three.js / WebGL / GLSL | library / tech | caption | Real, free, open-source JS 3D library and web graphics APIs. |
| 20,000 particles | number | caption | Plausible for a Three.js Points cloud. Not verifiable without code. |
| "Code drops weekly" | claim | caption | No code link in the post or caption. |

### What's being promoted / the funnel decoded
No call to action beyond "Save". It is a creative-coding account growing its audience. "Code drops weekly" points to future posts, perhaps a bio link, but nothing is sold or collected in this post.

### Verification & insights
- The formula on screen matches the standard superformula (Wikipedia "Superformula"; Gielis, *American Journal of Botany*, 2003). Johan Gielis also patented the formula and has commercialised it (Genicap), but using it for art is common.
- "Draws anything in nature" is marketing. The formula makes a family of radially symmetric shapes (flowers, starfish, crystals). It cannot represent arbitrary shapes.
- Free ways to reproduce this exist: the Codevember 2017 "supershape" Three.js demo (clicktorelease.com), Paul Bourke's supershape notes, the TouchDesigner superFormula palette and the Vuo supershape node.
- Not verified: the account's site or code repository (none named). The music track could not be identified.
- Material: the mirror had only the cover image. The caption was fetched with yt-dlp, and the video was downloaded from the CDN URLs in that metadata, then reviewed at 1 fps.

---

<a id="e-dezznwvap0f"></a>

## DeZZNwVAP0F | @davewang.ai | Tier list of 5 open-source quant repos: S NautilusTrader, A HftBacktest + "Kalshi Market" (making), C VectorBT, D TensorTrade, with a "comment LIST" DM funnel
- **Link:** https://www.instagram.com/p/DeZZNwVAP0F/
- **Account:** @davewang.ai (Dave Wang | AI for Investing) · **Posted:** 2026-10-12 · **Type:** reel (58.4s, 36 scene pages: fast cuts between talking head, tier board and repo demo images)
- **Caption source:** full (Instagram, fetched with yt-dlp)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. All five repos are real and free to use (the Kalshi one is a 2023 student project with no license), and the descriptions are broadly fair. Two catches: the opener "AI allows anyone without a coding background to become a quant trader" is hype, and VectorBT's open-source version carries a Commons Clause (no selling it as a product). The "comment LIST" DM only gates the links, which are given below.

### Post description
> I tier ranked 5 open-source quant trading repos on GitHub. My S tier pick is one of the best I've found for backtesting any strategy, and its simulator makes futures and options easy to understand. Comment LIST and I'll send you all five with links.

### Audio
The creator speaks to camera (wearing a "HARVARD Department of Statistics" quarter-zip). In the last part he is eating a salad. Word-by-word subtitles are burned in. Condensed into timestamped notes (Whisper's misspellings corrected in brackets):
- [0.0–3.4] Hook: "AI allows anyone without a coding background to become a quant trader."
- [3.4–8.8] Promises the best quant trading GitHub repos, tier-listed. First: HFT Backtest [HftBacktest], A tier.
- [8.9–19.7] Good for learning market making and HFT, with applications to queuing theory and order book imbalances; "Very close to the stuff that Jane Street, Optima [Optiver] and Citadel do."
- [15.4–23.3] Vector BT [VectorBT], C tier: teaches rapid backtesting of trading signals.
- [23.3–35.0] Calci [Kalshi] market making, A tier: many Kalshi order books are too thin for institutions, so individuals who know how can trade "markets that the big boys are not trading."
- [35.0–42.5] Tensor Trade [TensorTrade], D tier: popular, with frameworks for trading crypto, but "mainly just a bot" [Whisper: "buy"]; bot repos are saturated.
- [42.5–52.6] Natalist Trader [NautilusTrader], S tier: one of the best repos he found, "terrific for back testing any trading strategy", with a simulator that makes futures and options trading easy to understand.
- [52.6–58.4] CTA: for links to all the repos, "comment list down below and I'll send you all of them. If you're following me."

### On-screen content, page by page
A tier board (S red, A orange, B yellow, C green, D purple) on a green-black gradient sits above the speaker. Each repo pops in as a card with an icon, its name, "n of 5" and a one-line description, then cuts to demo images from that repo's docs.
**Pages 1–2 (0.0–3.7s):** The final board as a preview: S NautilusTrader · A HftBacktest, Kalshi Market · B (in the first frame a "Kalshi" chip sits in B; it is being dragged) · C VectorBT · D TensorTrade. Subtitle "AI…".
**Pages 3–4 (3.7–11.6s):** Empty board, then a card "HftBacktest — 1 of 5 — Learn market making, queue position and order book imbalances." The chip is placed in A.
**Pages 5–7 (11.7–18.0s):** Demo images. BTC/USDT and XRP/USDT order books with trades (prices around 22,678 and 0.3956). A HftBacktest queue-position model chart, "P = 1 − f(V+)/(f(V+)+f(V−))", plotting the probability of a decrease of the quantity ahead of the queue position against normalized queue position for f = x, √x, x², x³, log(1+x). Subtitles "applications", "there", "here".
**Pages 8–12 (18.0–23.3s):** Board, with a card "VectorBT — 2 of 5 — Rapidly backtest trading signals across historical market data." Placed in C. Demo: VectorBT's README heatmaps: a "Total return" heatmap of fast_window × slow_window (10–100) with a symbol slider BTC-USD / ETH-USD / XRP-USD, plus "%B" and "Bandwidth" (Bollinger) heatmaps for BTC-USD, ETH-USD, XRP-USD, dated Jul 13 2025 to Oct 5.
**Pages 13–19 (23.3–28.9s):** Card "Kalshi Market — 3 of 5 — Explore thin order books where individual traders can compete." Placed in A. Demo: an architecture diagram ("Kalshi Websockets API" and "TD Ameritrade API" → "Receive data" → "Trading State" → "Run on update" → "Strategy" → "Request orders" → "Order Manager" → "Place Orders" → "Kalshi Trade API"; "Check for stale requests"). A zsh terminal shows simulator output: "Current PnL: 20.339999…", "PnL update. Current position: -40", repeated "Bot market bid order filled. 10 at 55. Current position: -30 / -20 / -10 / 0", and PnL lines of -19.66, -15.16, -10.66, -6.16.
**Pages 20–24 (28.9–42.4s):** Card "TensorTrade — 4 of 5 — A flexible crypto trading framework, but mostly another bot repo." Placed in D. Demo: TensorTrade docs charts "Profitability" (portfolio.mean per episode) and "Reward" (rewards.mean per episode), a "Trading Chart" (sine-wave price with buy/sell markers), and "Performance / Net Worth" (coinbase:/USD-BTC balances, net_worth).
**Pages 25–33 (42.4–53.9s):** Card "NautilusTrader — 5 of 5 — Backtest strategies and easily simulate futures and options trading." Placed in S. Demo: "Cumulative realized pnl across all closed cycles (JPY)" (Feb 3 to Feb 24, 2025, about −2M to +1.5M), and "Short-strangle payoff at expiry: short 75000 put + short 81000 call", with the y-axis pnl (USDT, premium net of intrinsic) and the x-axis underlying at expiry (USDT) from 68k to 86k.
**Pages 34–36 (53.9–58.4s):** The creator at a table with a salad, painting behind. Subtitles "repos", "If…", then a large "comment list down". The last frame is black.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| NautilusTrader (S tier) | repo | card 5/5, audio 42s, caption | github.com/nautechsystems/nautilus_trader. LGPL-3.0, Rust core with a Python API, event-driven backtest-to-live engine. Actively maintained: latest commit 2026-10-21. "Simulate futures and options" is fair (it supports derivatives, including options instruments and adapters such as Interactive Brokers, Binance, Bybit, Deribit). |
| HftBacktest (A tier) | repo | card 1/5, audio 3s | github.com/nkaz001/hftbacktest. MIT license, Rust with Python bindings. Tick-level and L2/L3 order-book backtesting that models queue position and latency. The queue-probability chart on screen comes from its docs. Last commit 2025-12-23. |
| "Kalshi Market" / Kalshi market making (A tier) | repo | card 3/5, audio 23s | Matched by its architecture diagram to **github.com/nikhilnd/kalshi-market-making**. A USC QuantSC student project (Spring 2023; project manager Nikhil Deorkar plus 6 team members) that market-makes Kalshi S&P 500 daily-close bracket contracts with a Cauchy-distribution probability model. **No LICENSE file** (so all rights are reserved by default). Last commit 2023-05-18. It depends on the **TD Ameritrade API, which was retired after the Schwab migration**. The README's own result: one live day, a $6.80 profit on $33.40 (20.3%) over 51 trades, with the caveat "sample size of 1". (Another repo, rodlaf/KalshiMarketMaker, MIT, active 2026, also exists but does not match the diagram.) |
| VectorBT (C tier) | repo | card 2/5, audio 15s | github.com/polakowo/vectorbt. Apache-2.0 **with Commons Clause** (you cannot sell the software itself). There is also a paid "VectorBT PRO". Vectorised signal backtesting, active (2026-10-19). The heatmaps shown are from its README. |
| TensorTrade (D tier) | repo | card 4/5, audio 35s | github.com/tensortrade-org/tensortrade. Apache-2.0 reinforcement-learning trading framework. Last commit 2026-02-09. The charts are from its docs. "Mostly another bot repo" is the creator's opinion. |
| Kalshi | exchange | audio, card | A CFTC-regulated US prediction/event-contract exchange. "Thin order books" is a reasonable description for many of its markets, though larger firms (for example Susquehanna) now make markets there. |
| Jane Street, "Optima" (= Optiver), Citadel | firms | audio 15s | Real HFT and market-making firms, name-dropped as comparisons. |
| Short strangle 75000 put + 81000 call | chart detail | pages 25–33 | An example options payoff (strikes fit BTC prices). Illustration only. |

### What's being promoted / the funnel decoded
- "Comment LIST" → an auto-DM with the five repo links (they are all in the table above). Commenting also boosts the post's reach and adds you to the creator's DM list. A follow is implied ("if you're following me").
- The creator's display name is "Dave Wang | AI for Investing", and the Harvard Department of Statistics clothing is used as a credibility cue. A web search found a Dave Wang who is CEO and co-founder of **Wall Street Prompt** (paid AI-workflow training for funds and banks), formerly of SoftBank's LatAm fund and Morgan Stanley, and an "AI Research Fellow" listing at Harvard IQSS, plus a "Dave Wang's TokenBrief" Gumroad with free AI-prompt guides. It is **not confirmed** that @davewang.ai is that person, but the branding matches. Nothing is sold in this post.

### Verification & insights
- **Repos:** NautilusTrader, HftBacktest, VectorBT and TensorTrade were verified from existing shallow clones in scratchpad/repos (fetched fresh for the last-commit dates). kalshi-market-making was checked with `git ls-remote` and a new shallow clone. LICENSE and README were read for each. No code was executed.
- **"AI allows anyone without a coding background to become a quant trader":** overstated. All five repos require Python or Rust skills. NautilusTrader and HftBacktest in particular have steep learning curves.
- **"Very close to what Jane Street, Optiver and Citadel do":** HftBacktest does model queue position and latency, which are real HFT concepts, but backtesting on public data is far from the infrastructure, colocation and data those firms have.
- **Kalshi "A tier":** the repo is an unmaintained 2023 student project that depends on a defunct broker API. It is good for learning, not runnable as-is. Its 20% figure is a single day with $33 of capital.
- **Not verified:** the identity behind @davewang.ai, and GitHub star counts (the GitHub API was not available in this session).
- Sources: [nikhilnd/kalshi-market-making](https://github.com/nikhilnd/kalshi-market-making), [botforkalshi catalog entry](https://www.botforkalshi.com/bot-catalog/nikhilnd-mm), [Harvard IQSS – Dave Wang](https://www.iq.harvard.edu/people/dave-wang), [HDSR profile](https://hdsr.mitpress.mit.edu/pub/xbgycxx6), [TokenBrief Gumroad](https://tokenbrief.gumroad.com).

---

<a id="e-depedxbrmrf"></a>

## DepEDXbRMRF | @artillerytrades | "5 free GitHub repos to build your own trading bot": freqtrade, backtesting.py, vectorbt, QuantConnect Lean, NautilusTrader, plus a prop-firm TradingView→TradersPost tip
- **Link:** https://www.instagram.com/p/DepEDXbRMRF/
- **Account:** @artillerytrades (Day Trading 💸) · **Posted:** 2026-10-18 · **Type:** reel (42.6s, 8 slides "01/08"–"08/08"). The folder held only the cover image; the video was fetched and processed in this session.
- **Caption source:** full (Instagram)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. All 5 repos are real, actively maintained open-source projects. Their licenses vary: vectorbt is not fully free for commercial use, and backtesting.py is AGPL. The prop-firm automation tip needs a ToS check, and the CTA is a DM-list funnel.

### Post description
> 5 free repos to build your own trading bot
> Stop paying $100/month for trading bots. Build your own. 🤖
>
> 01 freqtrade: ready-made crypto bot, 55K stars
> 02 backtesting.py: test a strategy idea in a few lines of Python
> 03 vectorbt: test thousands of variations at once
> 04 QuantConnect Lean: stocks, futures, options, backtest → live
> 05 NautilusTrader: production-grade engine in Rust
>
> ⚠️ Futures prop firms (Lucid, Apex): most of these can’t connect to Tradovate. Code the strategy in TradingView and route alerts through TradersPost.
>
> Comment “BOT” and I’ll DM you all 5 links + my prop firm automation setup.
> 📌 Save this before you build.
>
> Not financial advice.
> #tradingbot #algotrading #daytrading #github #python futurestrading nasdaq propfirm quanttrading tradingview

### Audio
Voiceover (English, transcribed in this session with faster-whisper "small"): [0.0] "Want to build your own trading bot, here are 5 free github repos to do it." [4.2] "1. Freqtrade, a full crypto bot ready to run with 55,000 stars." [10.2] "2. Backtesting.py, test a strategy idea in a few lines of python." [15.1] "3. VectorBT, test thousands of variations at once super fast." [20.8] "4. Lean, the engine behind QuantConnect, stocks, futures, options, then run it live." [26.8] "5. Nautilus Trader, a production-grade engine built in Rust." [31.1] "The catch? Most of these can't connect to prop firms." [33.8] "For those, code it in TradingView and send alerts through TradersPost." [38.1] "Want all 5 links in my prop firm setup? Comment bot."

### On-screen content, page by page
Every slide has a pixel-art man with a game controller and a GitHub-style header "owner / repo".
**Slide 1 (0–4.3s), "$ 01/08 · artillerytrades / 5-bot-repos":** "Build your own **trading bot for $0**". Card: "FREE ON GITHUB — **5 REPOS** — Everything you need: backtest, test thousands of ideas, and run it live."
**Slide 2 (4.3–9.9s), "02/08 · freqtrade / freqtrade":** "Number one — A ready-made bot". Card: freqtrade/freqtrade, "Free, open source crypto trading bot", **55.0k Stars · 11.4k Forks · Python**.
**Slide 3 (9.9–15.3s), "03/08 · kernc / backtesting.py":** "Number two — Backtest in minutes". Card: kernc/backtesting.py, "Backtest trading strategies in Python", **8.8k Stars · 1.5k Forks · Python**.
**Slide 4 (15.3–20.5s), "04/08 · polakowo / vectorbt":** "Number three — Test 1000s of ideas". Card: polakowo/vectorbt, "Run thousands of trading ideas before others finish one", **8.7k Stars · 1.1k Forks · Python**.
**Slide 5 (20.5–26.5s), "05/08 · QuantConnect / Lean":** "Number four — Backtest to live". Card: QuantConnect/Lean, "Lean Algorithmic Trading Engine by QuantConnect (Python, C#)", **21.2k Stars · 5.2k Forks · C#**.
**Slide 6 (26.5–31.2s), "06/08 · nautechsystems / nautilus_trader":** "Number five — The pro engine". Card: nautechsystems/nautilus_trader, "Production-grade Rust-native trading engine with deterministic event-driven architecture", **30.2k Stars · 4.1k Forks · Rust**.
**Slide 7 (31.2–38.2s), "07/08 · artillerytrades / prop-firm-stack":** "The catch — **Prop firms?**". Card: "For Lucid, Apex and other futures prop firms" • "Most of these can't connect to Tradovate" • "Code the strategy in TradingView" • "Alert to TradersPost to your prop account".
**Slide 8 (38.2–42.6s), "08/08 · artillerytrades / links":** "Want the links? **Comment 'BOT'**". Card: "Comment BOT and I'll send you" • "All 5 repo links" • "My prop firm automation setup".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| freqtrade/freqtrade | repo | slide 2, caption, audio 4.2s | Verified: ls-remote and clone OK. **GPL-3.0**. Last commit 2026-10-20 ("chore: code clarity/understandability"). A Python crypto bot (backtesting, hyperopt, live trading on exchanges via CCXT). |
| kernc/backtesting.py | repo | slide 3 | Verified (existing clone): **AGPL-3.0**, last commit 2026-08-05. A lightweight Python backtesting library. |
| polakowo/vectorbt | repo | slide 4 | Verified: **Apache 2.0 with Commons Clause**, so you can't sell a product or service whose value derives from it. Last commit 2026-10-18. A vectorized NumPy/Numba backtester. The author also sells a paid "vectorbt PRO". |
| QuantConnect/Lean | repo | slide 5 | Verified: **Apache-2.0**, last commit 2026-10-16. A C#/Python engine behind QuantConnect; it can trade live through supported brokers. |
| nautechsystems/nautilus_trader | repo | slide 6 | Verified: **LGPL-3.0**, last commit 2026-10-18 (an Interactive Brokers exec-provider change). A Rust-core, Python-API event-driven trading engine. |
| Star/fork counts (55.0k/11.4k, 8.8k/1.5k, 8.7k/1.1k, 21.2k/5.2k, 30.2k/4.1k) | numbers | slides 2–6 | Not independently checked (no GitHub API access in this session). The orders of magnitude are plausible. |
| Tradovate | broker/platform | slide 7, caption | A futures platform used by many prop firms. None of the 5 repos ships a Tradovate connector, so the "can't connect" claim is broadly fair. |
| TradingView, TradersPost | services | slide 7, caption | TradersPost is a paid webhook service that turns TradingView alerts into broker orders, with a free trial and paid tiers. The creator likely uses an affiliate link. |
| Lucid (Lucid Trading), Apex (Apex Trader Funding) | prop firms | slide 7, caption | Futures prop firms. TradersPost's own guides say Apex bans **fully automated** bots on funded accounts and allows only semi-automated, monitored webhook setups. No Lucid policy was found. |
| "Stop paying $100/month" | claim | caption | Rhetorical. TradersPost itself is a monthly subscription. |

### What's being promoted / the funnel decoded
"Comment BOT" sends you a DM with the 5 links (all public; see the table) and "my prop firm automation setup" (the TradingView → TradersPost → Tradovate prop-account pipeline). The likely monetization is a TradersPost and/or prop-firm affiliate or referral link, plus growing a DM list. No price is shown. The repos themselves are free.

### Verification & insights
- All five repos exist, are actively developed (commits within the last 2 months), and the descriptions on the cards match their READMEs.
- License nuances matter more than "$0": AGPL (backtesting.py) carries network-copyleft obligations, and the Commons Clause (vectorbt) bars commercial resale.
- Prop-firm automation risk: running a bot or webhook automation on Apex funded accounts can breach their rules (fully automated systems are prohibited per TradersPost's summary of Apex policy). Check Lucid and Apex terms before following the "setup".
- An open-source backtester doesn't make a strategy profitable. None of the repos come with an edge.
- Not verified: the star counts, and whether the creator earns referral fees.

---

<a id="e-dcx--fislxg"></a>

## DcX--fislxG | @_indialogue | "Quant GitHub Tierlist": HftBacktest (A), vectorbt (C), Kalshi Market Maker (A), TensorTrade (D), NautilusTrader (S), with a "comment list" DM gate
- **Link:** https://www.instagram.com/p/DcX--fislxG/
- **Account:** @_indialogue · **Posted:** unknown (not in mirror data) · **Type:** reel (61.1s, 38 scene pages)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. All five repos are real, open source and active, and the rankings are reasonable opinions. Two of the spoken descriptions don't match the code. The Kalshi Market Maker repo uses REST polling with an Avellaneda-Stoikov model, not websockets, external price feeds or "fair value from scratch". NautilusTrader has no special futures/options "simulator for understanding" beyond its normal backtester. The "comment list (if you follow me)" gate is engagement bait. The links are below.

### Post description
> Comment "list" to see the ones that helped the most
>
> #quant

### Audio
The creator speaks to camera (young man, "POMONA COLLEGE" t-shirt, lav mic). Timestamped notes, with key lines quoted:
- [0.0] Hook: "Best quant trading GitHub repos, tier listed."
- [2.4] **HFT Backtest, A tier.** Good for learning market making and for HFT interviews, with applications to queuing theory and order-book imbalances; "very close to the stuff Jane Street, Optiver, and Citadel want to see."
- [14.6] **Vector BT, C tier.** Teaches rapid backtesting of trading signals; downside is that it oversimplifies execution and does not factor in latency much.
- [25.0] **Kalshi Market Making, A tier.** Teaches using web sockets with Kalshi's REST API and pulling external price data; maintains a full order book with good UI elements and shows how to calculate fair value from scratch.
- [38.1] **Tensor Trade, D tier.** Popular, with frameworks for trading crypto, but "mainly just a bot" in an already saturated space of bot repos.
- [46.4] **Nautilus Trader, S tier.** "probably the best repo I've found overall"; good for backtesting any strategy, with a simulator that makes futures and options trading easy to understand.
- [56.4] Call to action: "comment 'list' down below and I'll send you all of them if you're following me."

### On-screen content, page by page
Burned-in captions follow the speech, and overlays appear on top.
**Page 1 (0.0–2.7s):** Title "**Quant Github Tierlist**" over an empty S/A/B/C/D tier board. A logo card of trading firms: RADIX TRADING, SIG (Susquehanna), FIVE RINGS, HRT, Virtu ("vatic" partly visible), Jump Trading, Jane Street, Optiver, CITADEL, ARROWSTREET CAPITAL.
**Pages 2–5 (2.7–8.7s):** GitHub README card: "**HftBacktest** – High-Frequency Trading Backtesting Tool", with badges for MIT license, CodeQL, Python 3.11+, pypi package **2.4.4**, downloads **297k**, rustc 1.90, crates.io, Roadmap, **stars 4.4k**. Placed in tier **A**.
**Pages 6–7 (8.7–11.2s):** A textbook queueing-theory excerpt (M/M/1): "Steady-state expected number of customers in the system L = ρ/(1−ρ) if ρ<1", "Mean time in system W = 1/(μ−λ) by Little's Formula", "Mean time in queue", "Mean number in queue".
**Pages 8–10 (11.2–14.6s):** "Best repository at the end…" with Optiver, Jane Street and Citadel Securities logos.
**Pages 11–16 (14.6–25.0s):** vectorbt README banner ("Upgrade to PRO" 💎, "VECTORBT"), placed in tier **C**. Example backtest charts: an equity curve over 2000–2012 and an OHLC chart with volume.
**Pages 17–19 (25.0–28.3s):** README card: "**Kalshi Market Maker** – Dynamic market-making bot for Kalshi with explicit safety controls and operational tooling" (MIT license). A terminal dashboard snippet: "Kalshi Dashboard | refresh=1.0s | gmmult… Cash Available: $1.54 | Realized PnL: $-0.42 | Market Exposure(API): $51.74 | Markets with Position: 37 | Abs Contracts: 119 | Net Contracts: 117 | Active Orders: 0", then a positions list of KXMVECROSSCATEGORY… tickers. Placed in tier **A**.
**Pages 20–21 (28.3–31.7s):** WebSocket logo. A crates.io card for "**kalshi-rs**" (Rust SDK for the Kalshi prediction-market API that mirrors the official Python SDK).
**Pages 22–24 (31.7–35.8s):** A Kalshi market order-book ladder ("…price at … EST", Yes 58% / No 40%), and a node-graph UI.
**Page 25 (35.8–38.1s):** "Kalshi + SGP (Susquehanna) = LIQUID PREDICTION MARKETS".
**Pages 26–30 (38.1–46.4s):** README card: "**TensorTrade** – Train RL agents to trade. Can they beat Buy-and-Hold?" (Apache-2.0 license). Placed in tier **D**.
**Pages 31–36 (46.4–56.4s):** README card: "**NautilusTrader**" (LGPL-3.0 badge, branch/version/status table, Platform Linux x86_64, Rust 1.9x, Python 3.12–3.14), placed in tier **S**. A terminal trading UI with an order book, positions and a log.
**Pages 37–38 (56.4–61.1s):** "**Comment "list" for the repos!**"

**Final tier board:** S = NautilusTrader · A = HftBacktest, Kalshi Market Maker · B = (empty) · C = vectorbt · D = TensorTrade.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| HftBacktest | repo | audio 2.4s, pages 2–7 | `github.com/nkaz001/hftbacktest`. **MIT**. Last commit 2025-12-23. Rust/Python tick-level backtester modelling feed and order latency and queue position. Its README has an "Order Book Imbalance" market-making tutorial. The description is accurate. |
| vectorbt | repo | audio 14.6s, pages 11–16 | `github.com/polakowo/vectorbt`. **Apache-2.0 + Commons Clause** (no reselling). Last commit 2026-10-18. Vectorised signal backtesting. The "simplified execution" critique is fair. A paid vectorbt PRO also exists. |
| Kalshi Market Maker | repo | audio 25.0s, pages 17–19 | `github.com/rodlaf/KalshiMarketMaker` (identified by the exact README tagline). **MIT**, © 2025 Rodney Lafuente Mercado. Last commit 2026-04-14. Python with **REST only** (`requests`, no websocket code), market selection by volume and spread, then **Avellaneda-Stoikov** quoting per market, inventory caps, and a terminal dashboard. There is no external price feed and no separate "fair value" model, so the spoken description overstates it. |
| kalshi-rs | Rust crate | page 21 | Community Rust SDK for the Kalshi API on crates.io. Not the same project as the repo above. |
| Kalshi | exchange | pages 17–25 | CFTC-regulated US prediction-market exchange |
| SGP / Susquehanna | firm | page 25 | Susquehanna Government Products became Kalshi's first institutional market maker in 2024 |
| TensorTrade | repo | audio 38.1s, pages 26–30 | `github.com/tensortrade-org/tensortrade`. **Apache-2.0**. Last commit 2026-02-09. RL trading-environment framework, historically slow-moving. Calling it "mainly a bot" is inaccurate, since it is an RL gym framework, but the low ranking is defensible. |
| NautilusTrader | repo | audio 46.4s, pages 31–36 | `github.com/nautechsystems/nautilus_trader`. **LGPL-3.0**. Last commit 2026-10-18. Production-grade event-driven backtest and live engine supporting futures and options instruments. |
| Jane Street, Optiver, Citadel (Securities), Radix, SIG, Five Rings, HRT, Virtu, Jump, Arrowstreet | firms | pages 1, 9–10 | Real prop and quant firms used as name-drop logos. No affiliation is implied or shown. |
| M/M/1 queue formulas, Little's Law | theory | pages 6–7 | Standard textbook queueing results, shown as an excerpt |

### What's being promoted / the funnel decoded
- "Comment 'list' … I'll send you all of them if you're following me" is a follow-gated comment-to-DM automation for audience growth. Nothing is sold, and everything it would send is listed in the table above. The account appears to be a student quant-content creator; no paid product was found in the post.

### Verification & insights
- All repos: `git ls-remote` OK, shallow clones in `scratchpad/repos/` (`nkaz001__hftbacktest`, `rodlaf__KalshiMarketMaker`, `tensortrade`, plus the existing `vectorbt` and `nautilus_trader`). LICENSE, README and last commit were read. No code was executed.
- Accurate claims: HftBacktest covers queue-position and latency modelling relevant to HFT interviews. vectorbt is fast but simplistic on execution. NautilusTrader is the most complete.
- Overstated or inaccurate claims: the Kalshi repo's websockets, external price data and fair-value calculation (not in the code); TensorTrade as "just a bot"; NautilusTrader having an options and futures "simulator for understanding" (it is a general backtester).
- Kalshi caution: the dashboard screenshot from the repo's README shows a realised P&L of −$0.42. Prediction-market market-making carries fees, adverse selection and US-only access.
- Could not verify: the creator's identity, and whether "the ones that helped the most" refers to more repos than these five.

---

<a id="e-degkhs3grhj"></a>

## DegkHS3GRHJ | @simplifyinai | TradingAgents (Tauric Research): open-source multi-agent LLM "trading firm" (analysts, bull/bear researchers, trader, risk team, manager), with a "comment AI" newsletter/course funnel
- **Link:** https://www.instagram.com/p/DegkHS3GRHJ/
- **Account:** @simplifyinai (Simplifying AI, verified badge shown on slide 3) · **Posted:** 2026-10-15 (decoded from the post ID) · **Type:** carousel (3 slides)
- **Caption source:** possibly truncated (mirror). The yt-dlp full-caption fetch returned HTTP 429.
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE (the repo). TradingAgents is a real, actively maintained, Apache-2.0 research framework backed by an arXiv paper. "100 % free" holds for the code only: running it costs LLM API usage (or a ChatGPT Plus/Pro plan) and possibly data-API keys. The repo itself says it is "designed for research purposes" and is "not intended as financial, investment, or trading advice". The post's CTA is a generic engagement funnel.

### Post description
> Comment "AI" to get the link and the full list of free AI resources.
>
> You can now run a whole AI trading firm, with analysts, traders and risk managers, on your own machine.
>
> It's called TradingAgents, an open-source framework from Tauric Research th...

(cut off by the mirror; the full caption could not be retrieved because Instagram returned 429)

### Audio
Not applicable (image carousel).

### On-screen content, page by page
**Slide 1:** A screenshot of the GitHub README header: "README · Apache-2.0 license", the **Tauric Research** logo, and badges "arXiv 2412.20138", "Discord TradingResearch", "X TauricResearch", "GitHub Community TauricResearch", plus "GITHUB TRENDING #1 Repository Of The Day". README language links: Deutsch | Español | français | 日本語 | 한국어 | Português | Русский | 中文. Title: "TradingAgents: Multi-Agents LLM Financial Trading Framework".

The architecture diagram shows:
- **Data sources:** Market (Yahoo Finance); Social Media (X, Reddit, EODHD APIs); News (Bloomberg, Reddit, FinHub, Reuters); Fundamentals (Company Profile, Financial History, Insider Transactions).
- **Flow:** Researcher Team (Bullish ↔ Discussion ↔ Bearish) → Buy/Sell Evidence → Trader → "Transaction Proposal" → Risk Management Team (Aggressive / Neutral / Conservative) → Manager → "Decision" → Execution. There is also an "OpenAI o1 Deep Thinking" node.
- **Team overview:** Analyst: gathers market key points · Researcher: evaluates risk/reward · Trader: proposes trading strategy · Risk Team: manages risk exposure · Manager: authorizes transactions.

Overlay: **"YOU CAN NOW RUN A WHOLE AI TRADING FIRM ON YOUR OWN MACHINE. 100% FREE."** and "SWIPE FOR MORE ›".

**Slide 2:** The README section "TradingAgents Framework", quoted from the README:
> "TradingAgents is a multi-agent trading framework that mirrors the dynamics of real-world trading firms. By deploying specialized LLM-powered agents: from fundamental analysts, sentiment experts, and technical analysts, to trader, risk management team, the platform collaboratively evaluates market conditions and informs trading decisions. Moreover, these agents engage in dynamic discussions to pinpoint the optimal strategy."

It shows the same diagram and the README disclaimer: "TradingAgents framework is designed for research purposes. Trading performance may vary based on many factors, including the chosen backbone language models, model temperature, trading periods, the quality of data, and other non-deterministic factors. It is not intended as financial, investment, or trading advice."

Creator text:
> "It's called **TradingAgents**, an open-source framework from **Tauric Research** that gives LLM agents the roles of a real trading desk.
> → Four analysts cover **fundamentals, sentiment, news and technicals**
> → **Bull and bear researchers** debate each idea before the trader acts on it
> → A risk team and a **portfolio manager** review every decision
> **100% open-source.**"

**Slide 3:** "YOUR FREE DAILY AI UPGRADE · ★ DAILY AI GUIDES · TRENDING NEWS · HOTTEST TOOLS". A profile card: "Simplifying AI ✔ @simplifyinai – Helping you master AI daily · Latest AI and tech updates and breakthroughs · Get daily AI news, tutorials and tools". **"COMMENT "AI" TO GET MORE AI GEMS DAILY AND CLAUDE'S FULL COURSE"**, "P.S. Check your DMs for the link after commenting".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| TradingAgents (github.com/TauricResearch/TradingAgents) | repo | caption; slides 1–2 | Verified with `git ls-remote` (HEAD e8f5503) and a local clone. The latest commit is 2026-10-16, "Merge pull request #1536 from TauricResearch/v0.7.0". License: Apache-2.0. Very active: v0.3.0 (2026-06) through v0.7.0 (2026-10). Python package with a CLI (`tradingagents`). |
| Tauric Research | organisation | slides 1–2 | The research group behind the repo (tauric.ai). |
| arXiv 2412.20138 | paper | slide 1 badge | "TradingAgents: Multi-Agents LLM Financial Trading Framework" (Xiao, Sun, Luo, Wang; Dec 2024). |
| "#1 Repository Of The Day" | badge | slide 1 | A Trendshift badge linked in the README. |
| Yahoo Finance, X, Reddit, EODHD, Bloomberg, FinnHub ("FinHub"), Reuters, OpenAI o1 | data sources / models | diagram | Sources in the paper's original diagram. The current README also uses Alpha Vantage, SEC EDGAR fundamentals "as filed" (no key needed), FRED, Polymarket, and multiple LLM providers (OpenAI, Anthropic, Google, Bedrock, NVIDIA, Kimi, Groq, Mistral, any OpenAI-compatible or local server). |
| Discord "TradingResearch", X @TauricResearch | community | slide 1 badges | Official project channels. |
| Simplifying AI / @simplifyinai | account | slide 3 | AI-news creator account. The newsletter and site could not be identified by web search. |
| "Claude's full course" | lead magnet | slide 3 | Unidentified freebie promised by DM. |

### What's being promoted / the funnel decoded
- "Comment AI" sends a DM link to the creator's "free AI resources", "AI gems daily" and "Claude's full course". Most likely this is a newsletter sign-up (email capture) and a resource-list page. It is not affiliated with Tauric Research. Nothing is paid in the post. The repo itself is directly accessible at github.com/TauricResearch/TradingAgents, so there is no need to comment.

### Verification & insights
- The repo is checked and real: Apache-2.0, last commit 2026-10-16 (v0.7.0). The README states the "research purposes / not financial advice" disclaimer verbatim as in slide 2. Recent changelog items: point-in-time / look-ahead fixes (v0.4.0, v0.5.0), backtesting over ticker and date grids, runs on a ChatGPT Plus/Pro subscription (v0.7.0). No code was executed.
- "100 % free" is partly true. The code is free, but every analysis makes many LLM calls through several agents and debate rounds, which costs API tokens unless you use a local model or the ChatGPT-plan mode (which consumes plan limits). Some data sources need API keys (e.g. Alpha Vantage); EDGAR and Yahoo do not.
- "Run a whole AI trading firm": it produces analyst reports and a buy/hold/sell decision for one ticker per date. It is a research and simulation tool and does not place real orders by default. The paper's reported outperformance came from a short backtest window on a few large US stocks, with LLM non-determinism. Treat it as unproven for live trading, as the repo itself says.
- Related repos already in the user's collection (scratchpad/repos): FinRL, OpenBB, Lean, AutoHedge, Vibe-Trading, QuantMuse.
- Not verified: the full caption, the contents of the DM resource list, and "Claude's full course".

---

<a id="e-devygbyjgcl"></a>

## DeVyGbyJGcl | @earlystartupdays | "The 10 fastest-growing Claude Skill repos on GitHub" (Sept 2026, by stars gained): Ponytail, Matt Pocock Skills, I Have ADHD, Security Audit Skill, Superpowers, Diagram Design, Humanizer, Graphify, Addy Osmani Skills, Impeccable
- **Link:** https://www.instagram.com/p/DeVyGbyJGcl/
- **Account:** @earlystartupdays (display name not in the mirror data; the slide is branded "ESD") · **Posted:** unknown (not in the mirror data) · **Type:** image (1 slide)
- **Caption source:** possibly truncated (mirror, cut at "…improve frontend design, or..."). yt-dlp cannot read image posts ("There is no video in this post"), and the Instagram embed and profile endpoints returned 429.
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE: nine of the ten entries map to real, free, actively maintained repos (MIT or Apache-2.0). "Security Audit Skill" is too generic to identify. The monthly star-gain figures could not be independently checked.

### Post description
> These are the 10 fastest-growing Claude Skills on GitHub in September 2026, ranked by the number of stars gained that month.
>
> Some focus on making AI-generated code cleaner and simpler. Others help AI write more naturally, improve frontend design, or…
(The mirror copy ends here; the rest, including any call to action and hashtags, could not be retrieved.)

### Audio
Image post; no audio.

### On-screen content, slide by slide
**Slide 1 (only slide):** Black grid background, yellow and white title "**The 10 Fastest-Growing Claude Skill Repos on GitHub**". A table with columns "# | Repository | Stars Gained":
1. Ponytail +30,432
2. Matt Pocock Skills +29,787
3. I Have ADHD +26,258
4. Security Audit Skill +20,148
5. Superpowers +13,841
6. Diagram Design +13,795
7. Humanizer +13,769
8. Graphify +9,651
9. Addy Osmani Skills +8,880
10. Impeccable +8,505

Decorations: a GitHub Octocat logo (bottom left), yellow stars, an orange Claude-style asterisk (bottom right), and the "ESD" logo at bottom centre. No repo owners or URLs are given.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Ponytail (+30,432) | repo | rank 1 | **DietrichGebert/ponytail**, "Ponytail, the lazy senior dev": makes the agent prefer minimal code. **MIT.** HEAD 09c434a (2026-10-18). Earlier reviewed posts showed about 106k–144k total stars. |
| Matt Pocock Skills (+29,787) | repo | rank 2 | **mattpocock/skills**, "Skills For Real Engineers – my agent skills that I use every day to do real engineering - not vibe coding". **MIT.** HEAD 5beb35b (2026-10-19). Linked to his aihero.dev newsletter. |
| I Have ADHD (+26,258) | repo | rank 3 | **ayghri/i-have-adhd**, "ADHD-friendly outputs. No ADHD diagnosis needed!" (answer-first output rules). **MIT.** HEAD 1ecea19 (2026-10-11). |
| Security Audit Skill (+20,148) | repo (unidentified) | rank 4 | **Not identified.** No owner is given. Candidates include Cloudflare's security-audit skill (MIT, created June 2026), trailofbits/skills and mukul975/Anthropic-Cybersecurity-Skills. No repo with this exact name and growth could be confirmed. |
| Superpowers (+13,841) | repo | rank 5 | **obra/superpowers**, "a complete software development methodology for your coding agents, built on top of a set of composable skills". **MIT** (Jesse Vincent). Remote HEAD b739a8a; v7.0.0 released 2026-10-09. |
| Diagram Design (+13,795) | repo | rank 6 | **cathrynlavery/diagram-design**, "An agent skill that draws diagrams as one self-contained HTML + SVG file, in your brand. 45 diagram types." **MIT.** HEAD f2f4d49 (2026-10-20, v2.6.115). |
| Humanizer (+13,769) | repo | rank 7 | **blader/humanizer**, which "makes AI-written text sound like a person wrote it", built on Wikipedia's "Signs of AI writing" guide. **MIT** (Siqi Chen). HEAD 8c307f3 (2026-10-16). The README says "sponsored by cfo.ai". |
| Graphify (+9,651) | repo | rank 8 | **Graphify-Labs/graphify** (PyPI `graphifyy`): a codebase knowledge graph and memory for agents. **Apache-2.0.** HEAD b90b9df (2026-10-20). The README also upsells "Graphify Cloud" (14-day free trial; paid). |
| Addy Osmani Skills (+8,880) | repo | rank 9 | **addyosmani/agent-skills**, "Production-grade engineering skills for AI coding agents". **MIT.** HEAD aeac41d (2026-10-13). |
| Impeccable (+8,505) | repo | rank 10 | **pbakaus/impeccable**: "Design guidance for AI coding agents. 1 skill, 24 commands, live browser iteration, and 61 deterministic detector rules"; `npx impeccable install`; docs at impeccable.style. **Apache-2.0.** HEAD dad8dbb (2026-10-20). |
| "ESD" | brand | slide | @earlystartupdays's logo |

### What's being promoted / the funnel decoded
- No call to action is visible on the slide. The caption's ending (cut off) may contain one. It is an informational listicle for audience growth, and nothing is sold on the slide.
- Two listed repos have commercial tie-ins in their READMEs: Graphify (Graphify Cloud trial) and Humanizer (sponsored by cfo.ai). Matt Pocock's repo links to his newsletter.

### Verification & insights
- **Checked:** `git ls-remote` on all nine identifiable repos (all respond), plus the existing shallow clones in `scratchpad/repos/`: LICENSE, README and `git log -1` read for each (results in the table). All are actively maintained (commits in October 2026).
- **Star gains:** "stars gained in September 2026" could not be verified because the GitHub API and star-history are blocked in this sandbox. The ranking is plausible given these repos' prominence in other reviewed posts (for example, i-have-adhd was reported at about 30.7k total in September). No data source is cited on the slide (likely a GitHub-trending aggregator).
- **Overlap:** most of these repos also appear in other reviewed listicles (DdcCOLRBjMs, Ddl4uZtIRvf, DdmQWJzqP8H, DdO1UioAHAS).
- **Could not verify:** the full caption, the identity of "Security Audit Skill", the exact September star deltas, and the account's bio or links.

---

<a id="e-dx2ubacjyrn"></a>

## DX2ubACJYRN | @chase.h.ai | "10 open-source repos to supercharge Claude Code": caveman, graphify, browser-harness, claude-video, Open Design, CodeBurn, Impeccable, designlang, career-ops, n8n MCP
- **Link:** https://www.instagram.com/p/DX2ubACJYRN/
- **Account:** @chase.h.ai (Chase AI) · **Posted:** 2026-05-02 · **Type:** reel (136s, 19 scene pages; a scrolling GitHub screen-share above a talking head)
- **Caption source:** full (Instagram, via yt-dlp; identical to the mirror)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. All 10 items exist and are open source, except #10, which the creator himself flags as "not truly open source" (n8n's MCP server). Several repos now push paid cloud tiers. The CTA funnels to a paid Skool community (Chase AI+).

### Post description
> Comment "agent" to get access to all of my Claude Code guides

### Audio
The creator speaks throughout. Whisper's "cloud code" means **Claude Code**, and "NADEN" means **n8n**.
- [0.0–5.5] Hook: "Here are 10 new open source repos that you probably haven't heard about but can supercharge Claude Code for you."
- [5.5–17.9] #1 **caveman**: makes Claude Code less verbose and saves a lot of tokens. He cites a March 2026 study suggesting that more concise LLM output may also be better output.
- [17.9–37.0] #2 **graphify**: "a knowledge graph without being pure RAG". It sits between Obsidian and full RAG systems, for people who want more power than Obsidian without a full RAG database setup.
- [37.0–50.9] #3 **browser harness**: "Think of Playwright except it's an AI agent that's also self-improving." After each browser task it updates a file noting what worked and what didn't, to do better next time.
- [50.9–61.3] #4 **Claude video**: lets Claude Code ingest videos by chopping them up with FFmpeg and feeding the screenshots to Claude Code.
- [61.3–70.6] #5 **open design**: an open-source, local clone of Claude Design that works with any coding agent, not just Claude Code.
- [70.6–79.4] #6 **CodeBurn**: shows where your tokens go and what you spend them on, and how to optimize your systems to burn fewer tokens.
- [79.4–94.2] #7 **Impeccable**: one of the best repos for front-end design; "one skill with 23 commands", each tied to a front-end design tool. Its website shows before/afters for every tool call.
- [94.2–107.9] #8 **design extract**: point it at any website and it builds a full design system from it, to use as a foundation for your own brand.
- [107.9–119.6] #9 **career ops**: uses Claude Code to search the web for jobs matching your specifications, create a matching CV, and track everything automatically.
- [119.6–136.9] #10, "isn't truly open source, but I wanted to include it anyway": **n8n's MCP server**, now the easiest way to build n8n automations with Claude Code, because it validates the automation in TypeScript before turning it into JSON and populating it on your instance.

### On-screen content, page by page
The times are approximate (aligned to speech). The bottom half is always the talking head, with word-by-word captions.
**Page 1–2 (0–5s):** Thumbnail art "…0x OPEN SOURC[E]" / "CLAUDE CODE +" with a grid of repo icons (graphify node icon, question marks, a rock, "/", a cursor icon). Caption "here are 10".
**Page 3 (~5–8s):** GitHub README for **caveman**: rock logo, "caveman", "why use many token when few do trick", badges **stars 52k · last commit yesterday · license MIT**, links "Before/After • Install • Levels • Skills • Benchmarks • Evals".
**Page 4–5 (~8–11s):** caveman README scroll: "…Code skill/plugin and Codex plugin that makes agent talk like cave[man]… **75% of output tokens** while keeping full technical accuracy… one-line reviews / lifetime stats… compression… input tokens every session" / "the viral observation that caveman-speak dramatically reduces LLM… [lo]sing technical substance. So we made it a one-line install." / "caveman Ecosystem · caveman talk less (you are here) · cavemem remem[ber] · cavekit build better". Overlay pill: **"link in bio for claude code masterclass"**.
**Page 6 (~12s):** caveman Before/After: "Normal Claude (69 tokens)" (long React re-render explanation) vs "Caveman Claude (1[9] tokens)": "New object ref each render. Inline object prop = new ref = re-render. Wrap in useMemo."
**Page 7 (~14–17s):** caveman README: "…%–87% savings across prompts." / "Important: Caveman only affects output tokens — thinking/reasoning tokens are unt[ouched]… Caveman no make brain smaller. Caveman make mouth smaller. Biggest w[in is read]ability and speed, cost savings are a bonus." / highlighted: "…2026 paper **"Brevity Constraints Reverse Performance Hierarchies in [Language Models]"** found that constraining large models to brief responses **improved a[ccuracy by 26 percen]tage points** on certain benchmarks and completely reversed perfo[rmance hierarchie]s. Verbose not always better. Sometimes less word = more correct." / "…not just claim 75%. Caveman prove it." Table header numbers "1214", "29…".
**Page 8 (~18–22s):** **Graphify** README: logo, language list (CN 简体中文 | JP 日本語 | KR 한국어 | DE | FR | ES | BR | RU | SA | IT | PL | NL | UA | VN | ID | SE | GR | CZ | FI | DK | NO | HU | TH | 中文), badges "The Memory Layer", "CI passing", "pypi v0.6.5", "downloads 443k", "sponsor", "LinkedIn Safi Shamsi". MIT license and Security tabs.
**Page 9 (~22–30s):** Graphify graph visualization (a dot cloud). Caption "Graphify sits in".
**Page 10 (~37–45s):** **Browser Harness** README (MIT): hero image of a robed figure facing a sunset sky; "Browser Harness ♞"; "Connect an LLM directly to your real browser with a thin, editable CDP ha[rness]".
**Page 11 (~51–58s):** GitHub repo **bradautomates/claude-video** (Public): main, 1 Branch, 3 Tags, Issues 5, PRs 3. Folders .claude-plugin, .codex-plugin, .github/workflows, commands, hooks, scripts. Commit messages "Fix Windows compatibility: encoding, inst…", "Initial commit: /watch skill v0.1.0", "Add commands/watch.md so /watch is c…". Last commit 755c157.
**Page 12 (~61–67s):** **Open Design** README (Apache-2.0): "The open-source alternative to Claude Design. Local-first, web-deploy[able]… every layer — **12 coding-agent CLIs** auto-detected on your PATH (Clau[de Code], Codex, Devin for Terminal, Cursor Agent, Gemini CLI, OpenCode, Qwen, Copilot CLI, Hermes, Kimi, Pi, Kiro) become the design engine, driven by composable Skills and **72 brand-grade Design Systems**. No CLI? An O[penAI-]compatible BYOK proxy is the same loop minus the spawn." Hero: "Design with the agent already on your laptop."
**Page 13–14 (~67–79s):** **CodeBurn** README (MIT): flame logo in a honeycomb of AI-tool icons; "See where your AI coding tokens go." Badges for downloads, node >=20, discord. Caption mis-renders "CodeBurn" as "Codebird".
**Page 15 (~79–86s):** **Impeccable** README (Apache-2.0): "The vocabulary you didn't know you needed. **1 skill, 23 commands**, and cu[rated anti-]patterns for impeccable frontend design." / "Quick start: Visit **impeccable.style** to download ready-to-use bundles." / "Why Impeccable? Anthropic created frontend-design, a skill that guides Claude toward bette[r design]… Impeccable builds on that foundation with deeper expertise and more co[ntrol]." / "Every LLM learned from the same generic templates… predictable mistakes: Inter font, purple gradients, cards nested in cards, gr[ay text on] colored backgrounds."
**Page 16 (~86–94s):** impeccable.style site (nav Home · Designing · Docs · Slop · Live · 24k★). Before/after slider: "BEFORE" vs "AFTER", labels "PURPLE GRADIENT", "CARDS ON CARDS", "GENERIC AI OUTPUT" vs "WITH DESIGN SKILLS". Caption "it's one skill".
**Page 17 (~94–107s):** **designlang** README (MIT, Security tabs): "d. designlang." "reads a website the way a developer reads a stylesheet"; badges npm v12.2.0, license MIT, node >=20, website live; terminal `npx designlang https://vercel.com` ("Need to install the following packages: designlang@12.0.0 Ok to proceed? (y) y"). Caption "No.8".
**Page 18 (~107–119s):** **Career-Ops** README (Code of conduct, Contributing, MIT): language list (English, Español, Português (Brasil), 한국어, 日本語, Русский, 简体中文…); hero "You got the job. And it didn't cost you a thing." Caption "No.9".
**Page 19 (~119–136s):** **n8n blog** (URL "…n8n.io/n8n-mcp-server/"): "Build and Update Workflows with n8n's MCP Server" / "Describe what you want from Claude, ChatGPT, or your IDE, and get a ready-to-run workflow in a few minutes, built directly in n8n. No more copy-paste, no more back-and-forth." Author **Ophir Prusak**, "April 29, 2026 · 7 minutes read".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| caveman (JuliusBrussee/caveman) | repo | audio 5.5s; pages 3–7 | Exists. Skill/plugin that makes agents answer tersely. HEAD bad48a0, 2026-10-17. **License: now Apache-2.0** (from Caveman 3.0.0; LICENSE-MIT kept for earlier parts); the video showed an MIT badge. README now also advertises "Caveman Cloud" (separate commercial hosted service). |
| "Brevity Constraints Reverse Performance Hierarchies in Language Models" | paper | audio 10s ("March 2026 study"); page 7 | arXiv **2604.00025**, MD Azizul Hakim, submitted 11 Mar 2026. 31 models (0.5B–405B), 1,485 problems. Brevity constraints raised large-model accuracy ~26 pp and reversed the rankings on some math/science benchmarks. Real. |
| graphify (safishamsi/graphify) | repo | audio 17.9s; page 8 | Exists. HEAD b90b9df, 2026-10-20. **License Apache-2.0** (pyproject), with a LICENSE-MIT file also present; the video showed an MIT tab. `uv tool install graphifyy`. Builds a tree-sitter code/doc knowledge graph you query instead of grepping. README now upsells "Graphify Cloud" (14-day trial). |
| browser-harness (browser-use/browser-harness) | repo | audio 31s; page 10 | Exists. MIT, © Browser Use. HEAD c6a9412, 2026-10-17. Lets Claude Code/Codex/Cursor drive your real Chrome over CDP; the agent writes missing helpers into `agent_helpers.py` (the "self-improving" part). Upsells Browser Use Cloud. |
| claude-video (bradautomates/claude-video) — "/watch" | repo | audio 46.7s; page 11 | Exists. MIT, © Bradley Bonanno. HEAD 03ceb42, 2026-09-25 (v0.3.2). URL/local video → timestamped frames + transcript for the agent. Works in Claude Code/Codex, not Claude Chat/Cowork. |
| Open Design (nexu-io/open-design) | repo | audio 61.3s; page 12 | Exists. Apache-2.0. HEAD 3b0df90, 2026-10-20 (v0.26.0). "Open-source alternative to Claude Design". README now advertises paid **OpenDesign Go / Cloud** ($8 first month promo). |
| CodeBurn (getagentseal/codeburn) | repo | audio 66.9s; pages 13–14 | Exists. MIT, © AgentSeal. HEAD 1a3ce74, 2026-10-20. `npx codeburn`. Reads local Claude Code/Codex/Cursor session files and prices tokens by tool/model/project/task. No account needed. |
| Impeccable (pbakaus/impeccable), impeccable.style | repo/site | audio 79.4s; pages 15–16 | Exists. Apache-2.0. HEAD dad8dbb, 2026-10-20. README now says **"1 skill, 24 commands"** and 61 deterministic detector rules (video/audio said 23). Builds on Anthropic's frontend-design skill. |
| design extract → designlang (Manavarya09/design-extract) | repo/npm | audio 94.2s; page 17 | Exists. MIT, © Manav Arya Singh. HEAD 86bdbb5, 2026-10-20. `npx designlang <url>` reads a live site's DOM and emits 17+ files (DTCG tokens, Tailwind config, shadcn theme, Figma variables…). README carries sponsor/referral links (Atlas Cloud, Bloome). |
| career-ops (santifer/career-ops) | repo | audio 107.9s; page 18 | Exists. MIT, © Santiago Fernández de Valderrama. HEAD c87e0f0, 2026-10-20. Claude Code-driven job search, CV tailoring and tracking. |
| n8n's MCP server (official) | product | audio 119.6s; page 19 | n8n's built-in MCP server, announced on the n8n blog by Ophir Prusak (29 Apr 2026). n8n is "fair-code" (Sustainable Use License), not OSI open source, consistent with the creator's caveat. Not the same as the community repo czlonkowski/n8n-mcp (MIT), which exists separately. |
| "link in bio for claude code masterclass" | CTA | pages 4–5 overlay | Chase AI+ Skool community (see funnel) |
| Comment "agent" | CTA | caption | DM automation that sends "Claude Code guides" (lead magnet) |

### What's being promoted / the funnel decoded
- **Who:** Chase AI (Chase Hannegan). The on-screen overlay "link in bio for claude code masterclass" and the "Comment agent" CTA feed his Skool community **Chase AI+**. A third-party review lists it at **$98/month ($58/month billed annually)**, 90-day guarantee, ~1,000 members, focused on building an AI agency with Claude Code. The "Claude Code Masterclass" sits inside that paid community.
- The "guides" sent by DM are a free lead magnet leading into that upsell. No affiliate links are visible for the repos themselves.

### Verification & insights
- All 10 repos were confirmed with `git ls-remote` and a shallow clone into scratchpad/repos (caveman, graphify, browser-harness, claude-video, open-design, codeburn, impeccable, design-extract, career-ops). LICENSE and last commit are listed in the table. No code was executed.
- **Since the video, licenses changed:** caveman and graphify now carry Apache-2.0 as the primary license; the video showed MIT. Impeccable is now 24 commands.
- **Open-core drift:** caveman, graphify, browser-harness and open-design now advertise paid cloud services in their READMEs. The OSS parts remain free.
- **Claims check:**
  - "Concise may give better outputs": supported by arXiv 2604.00025, but only for some benchmarks. The paper frames it as a prompting effect, not a general rule.
  - Caveman "75% of output tokens": a project self-claim. Caveman's own README notes that only *output* tokens shrink, and thinking tokens are untouched.
  - "Browser harness = self-improving Playwright": it is a CDP harness where the agent edits its own helper file. It drives your *logged-in* real browser, which has real security implications (the agent acts as you).
- Graphify's pip package name is **graphifyy** (double y). Watch for typosquats.
- **Not verified:** Chase AI+ current pricing (single third-party source); the contents of the "guides" DM.
- Sources: [arXiv 2604.00025](https://arxiv.org/abs/2604.00025), [Chase AI+ review](https://aifunnelinsider.com/chase-ai-skool-review/).

---

<a id="e-dejudd7okcq"></a>

## Dejudd7okCQ | @lukegarvai | "10/10 GitHub repos for Claude": Serena, Spec Kit, Taskmaster plus (from the cover) UI UX Pro Max, GStack, Caveman, Graphify, Trail of Bits skills; "comment REPOS"
- **Link:** https://www.instagram.com/p/Dejudd7okCQ/
- **Account:** @lukegarvai (display name not in data; probably "Luke Garv AI") · **Posted:** 2026-10-16 (decoded from the post ID) · **Type:** reel. Only the cover image is available; the video could not be retrieved.
- **Caption source:** possibly truncated (mirror). It is cut off at item 3 ("Taskmaster stops a big build falling ap…"). yt-dlp got 429.
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE (the repos). Every repo identifiable from the caption and cover is real, open source and actively maintained. Only 3 of the 10 are confirmed from the caption; the other identifications come from cover cards. The star counts on the cover could not be checked. Taskmaster carries a Commons Clause (no reselling).

### Post description
> Comment REPOS and I'll send you all 10 👇
>
> 10 GitHub repos for Claude, and each one is better than the last.
>
> 1. Serena finds its way round your files.
>
> 2. Spec Kit writes the plan before it starts guessing.
>
> 3. Taskmaster stops a big build falling ap…

(Cut off by the mirror; items 4–10 are not in the available text.)

### Audio
Not available. The video was not retrievable (429). The cover subtitle reads "10/10 GitHub repos for", so it is a talking-head video with the creator holding a mic.

### On-screen content, page by page
**Cover (only frame available):** Three app icons at the top: the Claude asterisk, an orange "Claude Code" pixel-creature icon, and GitHub. Title: "**10/10 REPOS FOR CLAUDE**" ("10/10" in blue, "CLAUDE" in orange). A fan of repo cards; labels and star counts were read from a 3× enlargement, and some are partly occluded:
- "UI UX Pro" (Next Level Builder art), ★ 136k
- "GStack" (Garry Tan portrait), ★ 13?k (third digit occluded; reads like 137k)
- "Caveman" (portrait of a young man), ★ 113k
- "Graphify" (green card, graph logo), ★ 127k
- "Trail of Bits" (black/white logo), ★ 7.6k
- "[T]askmaster" (anime-style portrait), ★ 2?.2k (first digit occluded)
- Unlabelled: a white card with a lotus/leaf line logo, a black card with a large white logo (partially hidden, possibly the GitHub mark, i.e. Spec Kit), and two portrait cards (a man in front of clouds, a person with long hair).
Bottom subtitle: "10/10 GitHub repos for". The creator faces the camera holding a fluffy lav mic.
Video not retrievable – reviewed from cover image only.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Serena | repo | caption #1 | github.com/oraios/serena, "The IDE for Your Coding Agent": LSP-based semantic code navigation and editing MCP. GPL-3.0-or-later (app) + MIT (SolidLSP); last commit 2026-10-20. |
| Spec Kit | repo | caption #2 (likely the GitHub-logo card) | github.com/github/spec-kit: GitHub's spec-driven development toolkit; MIT; last commit 2026-10-20 |
| Taskmaster | repo | caption #3, cover card | github.com/eyaltoledano/claude-task-master (npm `task-master-ai`): AI task/PRD breakdown manager. MIT + **Commons Clause** (you may not sell it or services based on it); last commit 2026-04-23 ("replace retired task-master.dev URLs"), so it is the least active of the set. |
| UI UX Pro (Max) | repo | cover | github.com/nextlevelbuilder/ui-ux-pro-max-skill (uupm.cc): design-intelligence skill; MIT; last commit 2026-10-15 |
| GStack | repo | cover | github.com/garrytan/gstack: Garry Tan's (YC CEO) Claude Code workflow/skills stack; MIT; last commit 2026-10-21 |
| Caveman | repo | cover | github.com/JuliusBrussee/caveman: "why many token when few do trick", a terse-output/token-saving skill and CLI; Apache-2.0 (since 3.0.0; earlier parts MIT); separate paid "Caveman Cloud"; last commit 2026-10-17 |
| Graphify | repo | cover | github.com/Graphify-Labs/graphify (ex safishamsi/graphify): codebase → knowledge graph; Apache-2.0; paid Graphify Cloud upsell; last commit 2026-10-20 |
| Trail of Bits | repo | cover | github.com/trailofbits/skills: Claude Code plugin marketplace of security-auditing skills (smart contracts, code auditing…); **CC BY-SA 4.0**; last commit 2026-10-20 |
| Star counts 136k / 13?k / 113k / 127k / 7.6k / 2?.2k | numbers | cover | Not verified (GitHub API not reachable from this session) |
| REPOS | comment keyword | caption | DM automation |

### What's being promoted / the funnel decoded
Comment "REPOS" to get the full list by DM. A web search found a Skool community **"Luke Garv AI" (premium)**: "Claude Code and Claude Skills for non-developers", with Claude Code guides, 50+ Claude Skills templates, a prompt library and weekly tool breakdowns. It costs $5/month (founding price, rising after the first 40 seats), with about 27–28 members in mid-2026. The handle match (lukegarvai ↔ Luke Garv AI) is likely but not confirmed. The repos themselves are all public and free.

### Verification & insights
- All repos were checked with `git ls-remote`, shallow clones in scratchpad/repos (existing clones reused for serena, gstack, ui-ux-pro-max, caveman, graphify; new clones for spec-kit, claude-task-master, trailofbits/skills), LICENSE, README and `git log -1` as above. No code was executed.
- Items 4–10 are inferred from cover cards, so the order and the remaining unlabelled picks (lotus logo, two portraits) are unknown. Plausible candidates, not confirmed: obra/superpowers, Context7 and similar, which often appear in such lists.
- "Each one is better than the last" is a hook, not a ranking.
- These repos install agents and skills with broad file and shell access. Read the skills before installing, especially the marketplaces.
- **Could not verify:** the full list of 10; the video audio; star counts.

---

<a id="e-dekgzyubwbl"></a>

## DekGZyuBwBl | @qendresahhoti | "5 repos the AI builder community can't stop talking about": REA, CLI-Anything, Orca, HyperFrames, Orbital (all real, open source)
- **Link:** https://www.instagram.com/p/DekGZyuBwBl/
- **Account:** @qendresahhoti (Qendresa Hoti) · **Posted:** 2026-10-16 · **Type:** reel (128.5s, 103 scene pages)
- **Caption source:** full (Instagram)
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. All five repos exist, are open source (MIT, Apache-2.0, GPL-3.0) and were updated this week. The star counts and "32 thousand stars in a single day" could not be checked, and REA's total is already far higher than the figures she says. The "comment REPOS" handout is a free notes page with the five GitHub links.

### Post description
> Comment REPOS and I'll send you all five links with what I'd actually do with each one.
>
> I went through what the AI builder community is starring this week, and the trending page split into two stories. Four giants and one sleeper:
>
> * an agent that reverse engineers any app did 32 thousand stars in a single day
> * one command now makes any software drivable by your agent
> * a desktop app runs five coding agents on the same task and keeps the best result
> * heygen open sourced the engine that turns html into finished video
>
> And then there's the fifth one, barely 350 stars, that I think about more than the other four combined. It's in the last 30 seconds of the video.
>
> The stars tell you what's popular but the small repos tell you what's next.
>
> #ai #tech #opensource #github #build @github

### Audio
The creator talks to camera, with burned-in word-by-word subtitles. Whisper wrote "Ray" for REA, "cloud code" for Claude Code and "Orbital" correctly.
- [0.0–5.0] Hook: "Five GitHub repositories the AI builder community cannot stop talking about right now", and what each says about where things are going.
- [5.0–27.7] **REA**: an agent that reverse engineers software. You point it at an app or binary and it takes it apart and explains how it works. She says it got "**32,000 stars in a single day**". Suggested use: pick an app you're curious about and ask how it works. Her take: it is "the first one blowing up for reading it", i.e. understanding code before building, "and that order keeps winning."
- [27.7–51.8] **CLI Anything**, "**51,000 stars**": one command on any software generates a full command-line interface for it. Shown driving real apps like **Blender and LibreOffice**; it also ships as a Claude Code plugin. Suggested use: try it on one app you wish your agent could operate. Her take: "agents don't need prettier chat windows. They need handles on real software."
- [51.8–75.0] **Orca**, "**73,000 stars**": a desktop app running Codex, Claude Code and OpenCode side by side. One prompt goes to **five agents at once**, each in its own isolated worktree, and you merge the best result. Suggested use: give the same task to two agents and compare. She refers to her own earlier video on "how the setup matters more than the model".
- [75.0–93.9] **HyperFrames**, "**64,000 stars**": your agent writes HTML and it renders a real MP4, **deterministically**: "Same input gives exact same video every time." She edits videos every day and says "deterministic is the difference between a cool demo and a pipeline you can trust."
- [93.9–113.0] Her favourite, **Orbital**, "barely has **350 stars**". It keeps the project's context, decisions and tasks as plain files on your machine, so when one agent hits its limit you switch to another and it carries on as if nothing happened.
- [113.0–128.2] The pattern she sees: "Nobody on this list is building a chatbot." Everyone treats the AI as a worker inside a bigger system, so "the model became the replaceable part." CTA: "comment **repos** and I'll send you the list."

### On-screen content, page by page
The pages are mostly scrolling screen recordings of each repo's GitHub README, with the creator cut out in the lower right and a one-word subtitle bar. The scene detector caught 103 frames, most of them scroll positions or subtitle changes. Grouped by segment:
- **p_0001–p_0002 (0–5s):** creator at desk with purple lighting. Overlay: GitHub logo, "**5 PROJECTS** the AI builder community can't stop talking about!!!!"
- **p_0003–p_0014 (5–28s), REA:** GitHub README titled "**REA: Reverse Engineer An[ything]**", "One MCP for reverse engineering across binaries, applica[tions]…", badges (v6.5.0, tool catalog, Node.js), language links, "Website · Quick start · How REA works". Scrolled sections show "Connects your agent to tools for inspecting native binaries, JavaScript…", "registers REA with your agent and installs matching workflow… Ghidra, or IDA installation; setup can optionally install Hopper…", the install command `npx rea-agents setup`, "Setup supports Claude Code, Codex, Cursor, Gemini CLI, Grok Build… provider configuration and manual MCP registration", the example prompt "Understand how search works in the Notes app, show [a] similar feature for my project", and the terminal commands `npx -y rea-agents@latest analyze-javascript-app…`, `npm install --global rea-agents`, `rea --help`.
- **p_0015–p_0039 (28–52s), CLI-Anything:** handwritten label "**2. CLI-anything**". README "CLI-Anything: Making ALL Software Agent-Native" with "Repository of the Day #1" and "#1 Repository" badges, "Today's Software Serves Humans… Tomorrow's Users will be Agents", `CLI-Hub: pip install cli-anything-hub`, "See Demos", "Become a Contributor, or Request a CLI", badges (QUICK START 5 MIN, CLI HUB, TECH REPORT arXiv:2606.03…, python ≥3.10, click, pytest 100% pass), "One Command Line: Make any software agent-ready for Pi, OpenClaw, nanobot, Cursor, Claude Code, etc.", `$ /cli-anything <software-path-or-repo>`, a comic-style lobster banner, a dated News list (May/June 2026 items such as Obsidian CLI, Joplin CLI, Hermes skill and others), "Why CLI?" bullets (Structured & Composable, Lightweight & Universal, Self-Describing, Proven Success ("Claude Code runs thousands of real workflows through CLI daily"), Agent-First Design, Deterministic & Reliable), and the Quick Start table (install cli-anything-hub / install the CLI-Anything plugin).
- **p_0040–p_0061 (52–75s), Orca:** label "**3. Orca**", subtitle "has 73,000". README "**Orca**: The AI Orchestrator for 100x builders. Run Codex, ClaudeCode, OpenCode or Pi side-by-side, each in its own worktree…", badges (license MIT, Discord, X, macOS | Windows | Linux), "Download Orca". Feature list: Mobile Companion (iOS/Android), **Parallel Worktrees** ("Fan one prompt across five agents, each in its own isolated git worktree, compare the results and merge the winner"), Terminal Splits, Design Mode, GitHub & Linear Native, SSH Worktrees, Drag Files to Agents, Orca CLI, "Also in the box" (quick open, account switcher & usage tracking, computer use, notifications), Supported Agents grid, Install (Download, `brew install --cask stablyai/orca/orca`, AUR `yay -S stably-orca-bin`), Community & Support (Discord, X, WeChat QR), a contributor avatar wall and a GitHub star-history chart. p_0052 inserts a still of one of her own earlier reels.
- **p_0062–p_0082 (75–94s), HyperFrames:** label "**4. Hyperframes**". README "HeyGen HyperFrames: Write HTML. Render video. Built for agents.", badges (npm v0.8.164, downloads 2.7M/month, license Apache 2.0), "Studio | Quickstart | Showcase | Playground", the prompt box "Native Mac and Linux app now available", "HyperFrames is an open-source framework for turning HTML… into deterministic MP4 videos", Quick Start (`claude plugin marketplace add heygen-com/hyperframes`, `claude plugin install hyperframes@hyperframes`, `npx skills add heygen-com/hyperframes`) and a "Skills" section ("HyperFrames ships 21 skills…").
- **p_0083–p_0100 (94–123s), Orbital:** label "**5. Orbital**", subtitle "has 350". README "**Orbital**: The project agent. Every agent owns a session. Orbital owns the project." "Context is yours. Agents are interchangeable." "Set up in under 5 minutes. No Python or Node required. Bring your own API key." A demo video ("Ask Orbital to research on cursor's project feature"), badges (License GPL-3.0, Platform Windows, macOS), "Why a project agent?" / "Is your context actually yours?", and "What it means to own the project" (State, Decisions, Lessons, Work, Artifacts kept in the project folder).
- **p_0101 (≈124s):** an overlaid notes page, the comment-funnel deliverable: "this list grows weekly, newest week first. **5 repos the AI builder community can't stop talking about, and what to steal from each** … week of october 16". Entries follow the pattern "what it is / try this first / what to take from it". Visible text for 1. rea: "an agent that reverse engineers software, point it at an app or a binary and it explains how it works"; "pick one app or dependency you already use and ask it how one feature actually works under the hood"; "the habit: understanding before building. use it to read a library before you adopt it, not after it breaks". For 2. cli-anything: "one command generates a full CLI for any software, so your agent can drive apps that were never built for agents. ships as a claude code plugin"… The link URLs are too blurred to read.
- **p_0102–p_0103 (≈125–128s):** "comment **repos**" with an arrow.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| REA (Reverse Engineer Anything), `rea-agents` | repo / npm | audio 5s; pages 3–14 | github.com/morluto/rea, MIT, last commit 2026-10-21. A CLI plus MCP server that connects coding agents to RE tools (Ghidra, IDA, Hopper, JEB, JS/Electron/.NET inspection). Third-party coverage reports more than 100k stars, so "32k in a day" is plausible for a launch day but unverified. Its README warns that look-alike repos are not official and says to use it only on software you own or are authorized to examine. |
| CLI-Anything | repo | audio 28s; pages 15–39 | github.com/HKUDS/CLI-Anything (HKU Data Science Lab), Apache-2.0, last commit 2026-09-22. Distributed as a Claude Code plugin marketplace. "51,000 stars" not verified. |
| Blender, LibreOffice | apps | audio 38s | Given as examples of apps CLI-Anything can drive |
| Orca | repo / desktop app | audio 52s; pages 40–61 | github.com/stablyai/orca, MIT (© Lovecast Inc.), last commit 2026-10-20. Runs Codex, Claude Code, OpenCode or Pi in parallel git worktrees. Collects anonymous usage telemetry, which can be turned off (per its README). "73,000 stars" not verified. |
| HyperFrames (HeyGen) | repo | audio 75s; pages 62–82 | github.com/heygen-com/hyperframes, Apache-2.0, last commit 2026-10-21. HTML/CSS to deterministic MP4. The README confirms "same input, same frames, same output". 64k stars matches the 64,510 shown in post DeithvDucpZ. |
| Orbital | repo / desktop app | audio 94s; pages 83–100 | github.com/zqiren/Orbital, GPL-3.0, last commit 2026-10-20. Windows and macOS app that stores project state as local files. You bring your own LLM API key. Optional sign-in with "TokenDance" for free tokens in mainland China. "~350 stars" not verified. |
| Codex, Claude Code, OpenCode, Pi, Cursor, Gemini CLI | agents | audio / pages | The coding agents these tools support |
| "5 repos … what to steal from each" page | lead magnet | p_0101 | Her free notes page with the 5 links |

### What's being promoted / the funnel decoded
"Comment REPOS" leads to a DM containing her notes page (seen at p_0101): the five GitHub links, each with "what it is / try this first / what to take from it", in a list that grows weekly. Nothing is sold in this post, and there are no affiliate signs. The CTA mainly drives comment engagement. You don't need the DM: the repos are github.com/morluto/rea, github.com/HKUDS/CLI-Anything, github.com/stablyai/orca, github.com/heygen-com/hyperframes and github.com/zqiren/Orbital.

### Verification & insights
- `git ls-remote` and shallow clones (scratchpad/repos/) for all five. Licenses: REA MIT, CLI-Anything Apache-2.0, Orca MIT, HyperFrames Apache-2.0, Orbital GPL-3.0. All were active in October 2026.
- The descriptions in the speech match each README accurately. Orca's "five agents at once" comes straight from its README ("Fan one prompt across five agents").
- Star counts could not be checked (no GitHub API in this session). Web coverage puts REA well above 32k, so the "32 thousand in a single day" line describes a launch spike, not the total.
- Caution on REA: reverse engineering third-party commercial software can breach license terms or anti-circumvention law. The project itself limits use to software you own or are authorized to analyze, and warns about fake mirrors. Commercial back-ends (IDA, Hopper, JEB) need their own licenses.
- Orbital is a small, young project with GPL-3.0 licensing and BYO API keys. Your model costs still apply.
- HyperFrames also appears as item 1 in DeithvDucpZ (@dripthecup) in this batch.

---

<a id="e-ddo1uioahas"></a>

## DdO1UioAHAS | @charliehills | "40 Claude repos worth every penny": 40 GitHub repos for Claude Code (harness, skills, memory, tools, cost), each shown on a card
- **Link:** https://www.instagram.com/p/DdO1UioAHAS/
- **Account:** @charliehills (Charlie Hills, AI content creator; MarTech AI newsletter) · **Posted:** unknown (not in metadata; Instagram re-fetch got 429) · **Type:** reel (48.6s, 2 scene pages, but 40 repo cards change about every 1.1s inside page 1; all 40 read from frame crops)
- **Caption source:** possibly truncated (mirror, ends "Seven for cutting y…"). The re-fetch was blocked by Instagram 429.
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. All 40 repos exist and resolve (git ls-remote OK), are public and actively maintained (most committed in Oct 2026), and nearly all are MIT/Apache. "Comment REPOS" withholds a list that is fully shown on screen and transcribed below.

### Post description
> Comment REPOS and I'll send you all 40 links.
>
> I've hoarded over a hundred Claude repos this year. These are the 40 worth your time, and every one is free.
>
> Eight for the harness. Eight for skills. Seven for memory. Ten for tools. Seven for cutting y...

(cut off by the mirror. The categories on the cards confirm the split: HARNESS 1–8, SKILLS 9–16, MEMORY 17–23, TOOLS 24–33, COST 34–40, so the missing text is presumably "…cutting your token costs".)

### Audio
English speech (the creator, on camera with a book and a pink pen, reads the list fast). Whisper text, with names corrected to the on-screen cards:
- [0.0–7.6] "Learn Claude Code, Karpathy Skills, Superpowers, Ponytail, GStack, ECC, Oh My Claude Code,"
- [7.6–14.2] "Archon, Taste Skill, Anthropic Skills, Matt Pocock Skills, Wshobson Agents, Claude Plugins,"
- [14.2–20.6] "Addy Osmani Skills, UI UX Pro Max, Awesome Claude Skills, Planning with Files, Claude Mem,"
- [20.6–29.5] "CodeGraph, Graphify, Repomix, AgentMemory, Beads, Multica, Firecrawl, CC Switch,"
- [29.5–36.9] "Context7, Vibe Kanban, GitHub MCP, Playwright MCP, Serena, Claude Code Router,"
- [36.9–45.0] "Awesome MCP Servers, System Prompts AI, Best Practice, Codex Plugin CC, Claude HUD, RTK,"
- [45.0–48.3] "Headroom, Caveman. Just comment Repos below and I'll send you all 40."

### On-screen content, page by page
**Page 1 (0.0–46.4s):** heading "40 Claude repos worth every penny" with a numbered list 1–40 filling in as he speaks. Bottom centre: a GitHub-style card per repo ("NN / 40", category tag, owner/repo, description, stars, forks, language, license, URL). All 40 cards, as shown:

| # | Tag | Repo (github.com/…) | Card description (verbatim) | ★ / forks / lang / license on card |
|---|---|---|---|---|
| 1 | HARNESS | shareAI-lab/learn-claude-code | Bash is all you need - A nano claude code–like 「agent harness」, built from 0 to 1 | 75k / 12k / Python / MIT |
| 2 | HARNESS | multica-ai/andrej-karpathy-skills | A single CLAUDE.md file to improve Claude Code behavior, derived from Andrej Karpathy's observations on LLM coding pitfalls. | 204k / 21k / – / – |
| 3 | HARNESS | obra/superpowers | An agentic skills framework & software development methodology that works. | 275k / 25k / Shell / MIT |
| 4 | HARNESS | DietrichGebert/ponytail | Makes your AI agent think like the laziest senior dev in the room. The best code is the code you never wrote. | 106k / 5.9k / JavaScript / MIT |
| 5 | HARNESS | garrytan/gstack | Use Garry Tan's exact Claude Code setup: 23 opinionated tools that serve as CEO, Designer, Eng Manager, Release Manager, Doc Engineer, and QA | 129k / 19k / TypeScript / MIT |
| 6 | HARNESS | affaan-m/ECC | The agent harness performance optimization system. Skills, instincts, memory, security, and research-first development for Claude Code, Codex, Opencode,… | 241k / 37k / JavaScript / MIT |
| 7 | HARNESS | Yeachan-Heo/oh-my-claudecode | Teams-first Multi-agent orchestration for Claude Code | 39k / 3.5k / TypeScript / MIT |
| 8 | HARNESS | coleam00/Archon | The first open-source harness builder for AI coding. Make AI coding deterministic and repeatable. | 23k / 3.5k / TypeScript / MIT |
| 9 | SKILLS | Leonxlnx/taste-skill | Taste-Skill - gives your AI good taste. stops the AI from generating boring, generic slop | 78k / 5.4k / JavaScript / MIT |
| 10 | SKILLS | anthropics/skills | Public repository for Agent Skills | 171k / 20k / Python / – |
| 11 | SKILLS | mattpocock/skills | Skills for Real Engineers. Straight from my .agents directory. | 225k / 19k / Shell / MIT |
| 12 | SKILLS | wshobson/agents | Multi-harness agentic plugin marketplace for Claude Code, Codex, Cursor, OpenCode, GitHub Copilot, and Google Antigravity | 39k / 4.1k / Python / MIT |
| 13 | SKILLS | anthropics/claude-plugins-official | Official, Anthropic-managed directory of high quality Claude Code Plugins. | 34k / 3.8k / Python / Apache-2.0 |
| 14 | SKILLS | addyosmani/agent-skills | Production-grade engineering skills for AI coding agents. | 89k / 9.5k / JavaScript / MIT |
| 15 | SKILLS | nextlevelbuilder/ui-ux-pro-max-skill | An AI skill that provides design intelligence for building professional UI/UX across multiple platforms. | 118k / 13k / Python / MIT |
| 16 | SKILLS | travisvn/awesome-claude-skills | A curated list of awesome Claude Skills, resources, and tools for customizing Claude AI workflows — particularly Claude Code | 15k / 1.9k / – / – |
| 17 | MEMORY | OthmanAdi/planning-with-files | Persistent file-based planning for AI coding agents and long-running tasks. Crash-proof markdown plans, session recovery after /clear and compaction, per-turn… | 26k / 2.2k / Shell / MIT |
| 18 | MEMORY | thedotmack/claude-mem | Persistent Context Across Sessions for Every Agent – Captures everything your agent does during sessions, compresses it with AI, and injects relevant context bac… | 91k / 8k / JavaScript / Apache-2.0 |
| 19 | MEMORY | colbymchenry/codegraph | Pre-indexed code knowledge graph, auto syncs on code changes, for Claude Code, Codex, Gemini, Cursor, OpenCode, AntiGravity, Kiro, and Hermes Agent —… | 67k / 4.3k / C / MIT |
| 20 | MEMORY | Graphify-Labs/graphify | Turn any codebase, with its docs, SQL schemas, configs, and PDFs, into a queryable knowledge graph. A /graphify skill for Claude Code, Cursor, Codex, and… | 109k / 11k / Python / Apache-2.0 |
| 21 | MEMORY | yamadashy/repomix | Repomix is a powerful tool that packs your entire repository into a single, AI-friendly file. Perfect for when you need to feed your codebase to Large Language… | 28k / 1.5k / TypeScript / MIT |
| 22 | MEMORY | rohitg00/agentmemory | #1 Persistent memory for AI coding agents based on real-world benchmarks | 27k / 2.3k / TypeScript / Apache-2.0 |
| 23 | MEMORY | gastownhall/beads | Beads - A memory upgrade for your coding agent | 26k / 1.8k / Go / MIT |
| 24 | TOOLS | multica-ai/multica | Assign issues to Claude Code, Codex, Cursor, and 17 more coding agents like teammates — open-source and self-hostable. | 47k / 6k / Go / – |
| 25 | TOOLS | firecrawl/firecrawl | The context API to search, scrape, and interact with the web at scale. | 170k / 9.5k / TypeScript / AGPL-3.0 |
| 26 | TOOLS | farion1231/cc-switch | A cross-platform desktop All-in-One assistant for Claude Code, Codex, OpenCode, OpenClaw, Grok Build & Hermes Agent. Only official website: ccswitch.io | 128k / 8.8k / Rust / MIT |
| 27 | TOOLS | upstash/context7 | Context7 Platform -- Up-to-date code documentation for LLMs and AI code editors | 61k / 2.9k / TypeScript / MIT |
| 28 | TOOLS | BloopAI/vibe-kanban | Get 10X more out of Claude Code, Codex or any coding agent | 28k / 3k / Rust / Apache-2.0 |
| 29 | TOOLS | github/github-mcp-server | GitHub's official MCP Server | 32k / 4.8k / Go / MIT |
| 30 | TOOLS | microsoft/playwright-mcp | Playwright MCP server | 36k / 3k / TypeScript / Apache-2.0 |
| 31 | TOOLS | oraios/serena | A powerful MCP toolkit for coding, providing semantic retrieval and editing capabilities - the IDE for your agent | 28k / 1.9k / Python / MIT |
| 32 | TOOLS | musistudio/claude-code-router | One local control plane for every AI agent: route across models, fuse new capabilities, orchestrate tools, and stay fully in control. | 37k / 3.1k / TypeScript / MIT |
| 33 | TOOLS | punkpeye/awesome-mcp-servers | A collection of MCP servers. | 93k / 15k / – / MIT |
| 34 | COST | x1xhlol/system-prompts-and-models-of-ai-tools | FULL Augment Code, Claude Code, Cluely, CodeBuddy, Comet, Cursor, Devin AI, Junie, Kiro, Leap.new, Lovable, Manus, NotionAI, Orchids.app, Perplexity, Poke, Qoder… | 143k / 35k / – / GPL-3.0 |
| 35 | COST | shanraisshan/claude-code-best-practice | from vibe coding to agentic engineering - practice makes claude perfect | 65k / 6.4k / HTML / MIT |
| 36 | COST | openai/codex-plugin-cc | Use Codex from Claude Code to review code or delegate tasks. | 32k / 2.2k / JavaScript / Apache-2.0 |
| 37 | COST | jarrodwatts/claude-hud | A Claude Code plugin that shows what's happening - context usage, active tools, running agents, and todo progress | 28k / 1.3k / JavaScript / MIT |
| 38 | COST | rtk-ai/rtk | CLI proxy that reduces LLM token consumption by 60-90% on common dev commands. Single Rust binary, zero dependencies | 77k / 4.8k / Rust / Apache-2.0 |
| 39 | COST | headroomlabs-ai/headroom | Compress tool outputs, logs, files and RAG chunks before they reach the LLM. 20% fewer tokens for coding agents, 60-95% fewer tokens for JSON, same… | 67k / 5.2k / Python / Apache-2.0 |
| 40 | COST | JuliusBrussee/caveman | why use many token when few token do trick — Claude Code skill that cuts 65% of tokens by talking like caveman | 99k / 5.8k / Go / – |

**Page 2 (46.4–48.6s):** the full list 1–40 (as above) with a white pill CTA '"Repos"' and "Just comment".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| The 40 repos above | repos | cards, audio, page 2 | **All 40 resolve via git ls-remote and were shallow-cloned** into scratchpad/repos (owner__name folders, or existing clones: superpowers, skills, agents, repomix, playwright-mcp, caveman). Last commits: nearly all 2026-09-19 to 2026-10-21. Exceptions: multica-ai/andrej-karpathy-skills 2026-04-20, travisvn/awesome-claude-skills 2026-04-28, openai/codex-plugin-cc 2026-07-07 |
| Licenses found in the repos | license | repo files | MIT: 1, 3, 4, 5, 6, 7, 8, 9, 11, 12, 14, 15, 17, 19, 21, 23, 26, 27, 29, 31, 32, 33, 35, 37. Apache-2.0: 13, 18, 20, 22, 28, 30, 36, 38, 39, 40 (caveman has an Apache LICENSE although the card shows none). **AGPL-3.0: 25 firecrawl** (copyleft; network use triggers source obligations). **GPL-3.0: 34** system-prompts. **No license file: 2** (andrej-karpathy-skills) and **16** (awesome-claude-skills), so all rights are reserved by default. **10** anthropics/skills has no root LICENSE; individual skills carry their own terms, some source-available only. **24 Multica**: "Multica License" = Apache-2.0 plus extra conditions (Part I) by Index Labs (Hong Kong) Ltd; the README calls it "source-available" |
| Star/fork counts | numbers | cards | Not independently re-checked (GitHub API not available in this session); treat as approximate |
| @charliehills / Charlie Hills | creator | account | AI content creator (LinkedIn/IG/Substack/YouTube), runs the MarTech AI newsletter; has open-sourced his own "social-media-skills" Claude skills on GitHub |

### What's being promoted / the funnel decoded
"Comment REPOS" triggers an auto-DM with the 40 links, typically via a ManyChat-style flow that may ask for an email or point to his MarTech AI newsletter. Nothing is sold in the post, and every link is the public GitHub URL already printed on each card (table above), so there is no need to comment.

### Verification & insights
- All 40 repos are real and current. Several were renamed or moved: ECC is the former affaan-m/everything-claude-code; andrej-karpathy-skills now lives under multica-ai (previously forrestchang, now promoting Multica); graphify is now under Graphify-Labs (previously safishamsi). The cards use the current names.
- **Security note:** ECC's README warns that third-party re-uploads/mirrors "may contain malware". Install skills and plugins only from the canonical repos. Plugins, skills and hooks run code and shell commands with your permissions; read them first.
- "#34 system-prompts-and-models-of-ai-tools" is a collection of leaked/extracted proprietary system prompts (GPL-3.0). Its legality is grey: content copyright belongs to the vendors.
- The token-saving claims ("60–90%", "65%", "60–95% for JSON") are each project's own benchmark claims, not independently verified.
- "Worth every penny" is a joke: everything is free.
- Overlaps with other posts: superpowers, caveman, graphify, repomix, agents, mattpocock skills and addyosmani agent-skills were already cloned for earlier posts.
- Could not verify: the exact star counts, the full caption, and the post date.

---

<a id="e-ddmqwjzqp8h"></a>

## DdmQWJzqP8H | @lukegarvai | "32 Claude repos worth every penny": rapid-fire list of 32 Claude Code skill, memory, MCP, harness and token-saving GitHub repos, each with an on-screen repo card; comment "REPOS" funnel
- **Link:** https://www.instagram.com/p/DdmQWJzqP8H/
- **Account:** @lukegarvai (Luke Garv AI) · **Posted:** 2026-09-22 · **Type:** reel (45.1s; one continuous talking-head shot with 32 sequential repo-card overlays and a growing 1–32 list, then a "Comment 'Repos'" end segment)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; the mirror copy was cut off at "Follow @lukegarvai f...")
- **Material note:** the post folder had only the cover image (m01.jpg). I fetched the video myself (yt-dlp metadata plus direct CDN download) and processed it in `scratchpad/work3/DdmQWJzqP8H/`: scene frames, 2-fps frames, 4-fps card crops and a faster-whisper transcript.
- **Category:** GitHub & dev / AI tools
- **Verdict:** LEGIT & FREE (mostly). All 32 repos exist and respond to `git ls-remote`, and most are popular open-source projects. But "all live, nothing archived" is wrong for **vibe-kanban** (its README says it is sunsetting). "Every one is free" glosses over licence limits: awesome-claude-code is CC BY-NC-ND, some Anthropic document skills are "All rights reserved", and two repos have no licence file. Firecrawl and Context7 are freemium APIs.

### Post description
> Comment REPOS and I'll send you all of them!
>
> I've saved over a hundred Claude repos this year. Most of them I'd never recommend.
>
> These are the 32 that actually earned a spot, and every one is free.
>
> All live, nothing archived.
>
> Follow @lukegarvai for more.
>
> #ai #claudeai #claudecode #github #lukegarvai

### Audio
The creator speaks to camera while holding a pen over an open hardback book (a David Goggins title, gold lettering, a prop). He reads the list rapidly. Whisper transcript (English, p = 1.00), with names corrected against the screen in brackets:
- [0.0–7.0] "Superpowers, Anthropic Skills, Karpathy Skills [Whisper wrote 'Carpathy'], Everything Claude Code, gstack ['G-Stack'], Ponytail,"
- [7.0–15.2] "Caveman, Graphify ['Graphifier'], Claude Mem, Planning with Files, Taste Skill, UI/UX Pro Max,"
- [15.2–21.4] "Matt Pocock Skills, wshobson Agents ['WS Hobson Agents'], Awesome Claude Skills, Awesome Claude Code,"
- [21.4–29.6] "Claude Plugins, Repomix ['Repo Mix'], Context7 ['Context 7'], Serena, Firecrawl, Beads, Vibe Kanban ['Vibe Cam Band'],"
- [29.6–38.3] "GitHub MCP, Playwright MCP, Awesome MCP Servers, Claude Code Router, CC Switch, Claude HUD ['Claude HDD'],"
- [38.3–45.0] "RTK, Headroom, System Prompts. If you want me to send all [40 / '14'], make sure to follow and comment Repos."

The final count is garbled: Whisper heard "14" and the burned-in subtitle reads "40,", but the list on screen is 32.

### On-screen content, page by page
**Main segment (0–41.8s):**
- Header: "**32 Claude repos worth every penny**". A two-column numbered list (1.–16. and 17.–32.) fills in one name at a time as he reads.
- Lower third: a GitHub-style card for each repo with "NN / 32", a category tag, "owner /", repo name, description, ★ stars, ⑂ forks, language, licence and URL.

All cards transcribed from 4-fps full-resolution crops (stars and forks are as shown on the cards, around mid-Sep 2026):

| # | Tag | Repo (github.com/…) | Card description | ★ / ⑂ / lang / licence (card) |
|---|---|---|---|---|
| 1 | SKILLS | obra/superpowers | An agentic skills framework & software development methodology that works. | 290k / 26k / Shell / MIT |
| 2 | SKILLS | anthropics/skills | Public repository for Agent Skills. | 178k / 21k / Python / – |
| 3 | SKILLS | multica-ai/andrej-karpathy-skills | A single CLAUDE.md file to improve Claude Code behavior, derived from Andrej Karpathy's observations. | 215k / 22k / – / – |
| 4 | HARNESS | affaan-m/ECC | The agent harness performance optimization system. Skills, instincts, memory, security. | 265k / 40k / JavaScript / MIT |
| 5 | SKILLS | garrytan/gstack | Use Garry Tan's exact Claude Code setup: 23 opinionated tools. | 134k / 20k / TypeScript / MIT |
| 6 | SKILLS | DietrichGebert/ponytail | Makes your AI agent think like the laziest senior dev in the room. | 144k / 7.7k / JavaScript / MIT |
| 7 | TOKENS | JuliusBrussee/caveman | Why use many token when few token do trick. Viral skill + proxy for coding agents. | 107k / 6.2k / Go / – |
| 8 | CONTEXT | Graphify-Labs/graphify | Turn any codebase, with its docs, SQL schemas, configs and PDFs, into a queryable knowledge graph. | 120k / 12k / Python / Apache-2.0 |
| 9 | MEMORY | thedotmack/claude-mem | Persistent context across sessions for every agent. | 94k / 8.4k / TypeScript / Apache-2.0 |
| 10 | MEMORY | OthmanAdi/planning-with-files | Persistent file-based planning for AI coding agents and long-running tasks. | 27k / 2.3k / Shell / MIT |
| 11 | SKILLS | Leonxlnx/taste-skill | Gives your AI good taste. Stops the AI from generating boring, generic slop. | 89k / 6.1k / JavaScript / MIT |
| 12 | SKILLS | nextlevelbuilder/ui-ux-pro-max-skill | An AI skill that provides design intelligence for building professional UI/UX. | 130k / 14k / Python / MIT |
| 13 | SKILLS | mattpocock/skills | Skills for Real Engineers. Straight from my .agents directory. | 268k / 23k / Shell / MIT |
| 14 | PLUGINS | wshobson/agents | Multi-harness agentic plugin marketplace for Claude Code, Codex, Cursor and more. | 40k / 4.3k / Python / MIT |
| 15 | LIST | ComposioHQ/awesome-claude-skills | A curated list of awesome Claude Skills, resources, and tools. | 75k / 8.8k / Python / – |
| 16 | LIST | hesreallyhim/awesome-claude-code | A hand-picked collection of the finest resources for Claude Code. | 54k / 4.7k / Python / – |
| 17 | PLUGINS | anthropics/claude-plugins-official | Official, Anthropic-managed directory of high quality Claude Code Plugins. | 37k / 4.1k / Python / Apache-2.0 |
| 18 | CONTEXT | yamadashy/repomix | Packs your entire repository into a single, AI-friendly file. | 28k / 1.5k / TypeScript / MIT |
| 19 | MCP | upstash/context7 | Up-to-date code documentation for LLMs and AI code editors. | 62k / 3.0k / TypeScript / MIT |
| 20 | MCP | oraios/serena | A powerful MCP toolkit for coding: semantic retrieval and editing. | 30k / 2.0k / Python / – |
| 21 | TOOL | firecrawl/firecrawl | The web data API to search, scrape, and interact at scale. | 183k / 9.9k / TypeScript / AGPL-3.0 |
| 22 | MEMORY | gastownhall/beads | Beads - A memory upgrade for your coding agent. | 27k / 1.9k / Go / MIT |
| 23 | HARNESS | BloopAI/vibe-kanban | Get 10X more out of Claude Code, Codex or any coding agent. | 28k / 3.0k / Rust / Apache-2.0 |
| 24 | MCP | github/github-mcp-server | GitHub's official MCP Server. | 33k / 5.0k / Go / MIT |
| 25 | MCP | microsoft/playwright-mcp | Playwright MCP server. | 37k / 3.2k / TypeScript / Apache-2.0 |
| 26 | LIST | punkpeye/awesome-mcp-servers | A collection of MCP servers. | 95k / 16k / – / MIT |
| 27 | HARNESS | musistudio/claude-code-router | One local control plane for every AI agent: route across models. | 37k / 3.1k / TypeScript / MIT |
| 28 | HARNESS | farion1231/cc-switch | A cross-platform desktop all-in-one assistant for Claude Code, Codex and more. | 134k / 9.3k / Rust / MIT |
| 29 | PLUGINS | jarrodwatts/claude-hud | A Claude Code plugin that shows context usage, active tools and running agents. | 28k / 1.3k / JavaScript / MIT |
| 30 | TOKENS | rtk-ai/rtk | CLI proxy that reduces LLM token consumption by 60-90% on common dev commands. | 81k / 5.2k / Rust / Apache-2.0 |
| 31 | TOKENS | headroomlabs-ai/headroom | Compress tool outputs, logs, files and RAG chunks before they reach the LLM. | 73k / – / Python / – |
| 32 | LIST | x1xhlol/system-prompts-and-models-of-ai-tools | Full system prompts from Claude Code, Cursor, Devin, Kiro and more. | 144k / 35k / – / GPL-3.0 |

Short names in the final on-screen list (≈41.5s): 1.superpowers 2.anthropic-skills 3.karpathy-skills 4.everything-claude-code 5.gstack 6.ponytail 7.caveman 8.graphify 9.claude-mem 10.planning-with-files 11.taste-skill 12.ui-ux-pro-max 13.mattpocock skills 14.wshobson agents 15.awesome-claude-skills 16.awesome-claude-code 17.claude-plugins 18.repomix 19.context7 20.serena 21.firecrawl 22.beads 23.vibe-kanban 24.github-mcp 25.playwright-mcp 26.awesome-mcp-servers 27.claude-code-router 28.cc-switch 29.claude-hud 30.rtk 31.headroom 32.system-prompts. Item 4 is listed as "everything-claude-code", but the card shows the repo affaan-m/ECC (the same project under its short name).

**End segment (41.8–45.1s):** the list is removed. A cyan banner reads "**Comment "Repos"**" with word-by-word subtitles "…want… 40, … me… all… make… follow… comment… repos".

### Everything named or linked
Verification: `git ls-remote` succeeded for all 32 (all public and reachable on 2026-10-21). Shallow clones are in `scratchpad/repos/`, existing clones were reused, and LICENSE and README were read. Nothing was executed. The GitHub API was not available in this session, so live star counts and the archived flag could not be queried.

| Item | Type | Where | Verified licence / status (from clone) |
|---|---|---|---|
| obra/superpowers | repo | audio 0s, card 1 | MIT. Active (clone 2026-10-09). |
| anthropics/skills | repo | card 2 | **No root licence.** 14 skills are Apache-2.0. The **4 document skills (docx, pdf, pptx, xlsx) are "© 2025 Anthropic, PBC. All rights reserved."** (source-available, not open source). |
| multica-ai/andrej-karpathy-skills | repo | card 3 | **No licence file** (CLAUDE.md, CURSOR.md, EXAMPLES.md, README). Last commit 2026-04-20. Inspired by Karpathy's public observations, not by Karpathy himself. |
| affaan-m/ECC (Everything Claude Code) | repo | card 4 | MIT. Active (2026-10-20). |
| garrytan/gstack | repo | card 5 | MIT. Active (2026-10-21). Garry Tan is the Y Combinator CEO. |
| DietrichGebert/ponytail | repo | card 6 | MIT. Active. |
| JuliusBrussee/caveman | repo | card 7 | Apache-2.0 (the card showed none). Active. |
| Graphify-Labs/graphify | repo | card 8 | Apache-2.0. Active. |
| thedotmack/claude-mem | repo | card 9 | Apache-2.0. Active. |
| OthmanAdi/planning-with-files | repo | card 10 | MIT. Active. |
| Leonxlnx/taste-skill | repo | card 11 | MIT. Active. |
| nextlevelbuilder/ui-ux-pro-max-skill | repo | card 12 | MIT. Active. |
| mattpocock/skills | repo | card 13 | MIT. Active. |
| wshobson/agents | repo | card 14 | MIT. Active. |
| ComposioHQ/awesome-claude-skills | list | card 15 | **No licence file.** Last commit 2026-07-24. Composio's skills also promote its paid Composio connector platform. |
| hesreallyhim/awesome-claude-code | list | card 16 | **CC BY-NC-ND 4.0** (non-commercial, no derivatives). Active. |
| anthropics/claude-plugins-official | repo | card 17 | Apache-2.0. Official Anthropic. |
| yamadashy/repomix | repo | card 18 | MIT. Active. |
| upstash/context7 | MCP | card 19 | MIT code, but the hosted service recommends an API key ("free API key… for higher rate limits") from context7.com, which is freemium. |
| oraios/serena | MCP | card 20 | MIT. Active. |
| firecrawl/firecrawl | tool | card 21 | **AGPL-3.0** self-host. The hosted Firecrawl API is a paid/credit service. |
| gastownhall/beads | repo | card 22 | MIT. Active. |
| BloopAI/vibe-kanban | repo | card 23 | Apache-2.0. **README headline: "Vibe Kanban is sunsetting."** (links to vibekanban.com/blog/shutdown). Last commit 2026-09-19. This contradicts "all live". |
| github/github-mcp-server | MCP | card 24 | MIT. Official GitHub. |
| microsoft/playwright-mcp | MCP | card 25 | Apache-2.0. Official Microsoft. |
| punkpeye/awesome-mcp-servers | list | card 26 | MIT. Active. |
| musistudio/claude-code-router | repo | card 27 | MIT. Active. |
| farion1231/cc-switch | app | card 28 | MIT. Active. |
| jarrodwatts/claude-hud | plugin | card 29 | MIT. Active. |
| rtk-ai/rtk | CLI | card 30 | Apache-2.0. Active. The "60–90% token reduction" figure is the project's own claim. |
| headroomlabs-ai/headroom | tool | card 31 | Apache-2.0 (the card showed none). Active. |
| x1xhlol/system-prompts-and-models-of-ai-tools | list | card 32 | GPL-3.0 on a collection of **extracted/leaked proprietary system prompts** (Claude Code, Cursor, Devin, Kiro…). README asks for donations and promotes ZeroLeaks (zeroleaks.ai), a prompt-leak security service. Copyright and ToS status of the content is doubtful. |
| "REPOS" | comment keyword | caption, end banner | DM with the list of links. |
| David Goggins book | prop | whole video | Hardback held open; not mentioned. |

### What's being promoted / the funnel decoded
- Comment "REPOS" (and follow) → auto-DM with the links to the 32 repos. Nothing paid is visible. The account is an AI-tips creator, and the comment-for-DM mechanic is a growth tactic (engagement plus DM list). No web footprint for @lukegarvai or a bio product was found.
- **You do not need the DM:** every repo URL is shown on its card and listed in the table above.

### Verification & insights
- **"All live, nothing archived":** every repo answers `git ls-remote`, but vibe-kanban announces it is **sunsetting**. Archived flags could not be checked without the GitHub API. karpathy-skills (last commit April 2026) and awesome-claude-skills (July 2026) are quieter.
- **"Every one is free":**
  - true for the MIT/Apache code;
  - **not quite** for the following: Anthropic's docx/pdf/pptx/xlsx skills (all rights reserved), awesome-claude-code (CC BY-NC-ND), no-licence repos (karpathy-skills, awesome-claude-skills; default copyright applies), Firecrawl (AGPL plus a paid API) and Context7 (API key, freemium);
  - most tools also consume paid model tokens.
- **Star counts:** the cards show very high numbers (for example 290k for superpowers and 268k for mattpocock/skills). They come from the creator's own graphics and could not be cross-checked against the API in this session.
- **Spoken count mismatch** ("all 14"/"40" vs 32 on screen) suggests a reused script.
- **Overlap with other posts:** many of these repos recur across this collection (superpowers, ECC, gstack, ponytail, caveman, graphify, claude-mem, taste-skill, rtk and headroom are already cloned from earlier reviews).
- **Caution:** several items (caveman, rtk, headroom, claude-code-router, cc-switch) proxy or rewrite your agent's traffic. Review them before routing API keys through them.

---

<a id="e-dbucu4jjm1p"></a>

## DbUcU4Jjm1p | @kyle.disruptor | Talking-head promo of affaan-m's "Everything Claude Code" (ECC) repo: hackathon-winner story, agent/skill counts, 98% coverage, multi-harness table
- **Link:** https://www.instagram.com/p/DbUcU4Jjm1p/
- **Account:** @kyle.disruptor · **Posted:** unknown (not in metadata) · **Type:** reel (62.6s, 17 pages)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE (with hype). ECC (github.com/affaan-m/ECC) is a real, MIT-licensed, very popular Claude Code plugin/harness. The "make Claude 100× stronger" and "immediate improvements" claims are marketing, and the hackathon story is slightly garbled.

### Post description
> One GitHub repo.
> Dozens of AI agents, skills, and workflows.
> ㅤ
> Comment "ARMY" 👇
> ㅤ
> #ClaudeAI #ClaudeCode #ArtificialIntelligence #GitHub #OpenSource

### Audio
English speech by the creator (on camera, blue "Y" BYU polo, backwards cap, RØDE mic):
- [0.0–5.0] "If you were to only do one thing to make your Claude a hundred times stronger, it has to be this."
- [5.0–9.5] "But just so you know that this is legit, you should know who invented this insane new strategy."
- [9.5–16.7] "His name is Affan Mustafa, and he built this GitHub repo that won against 74 other builders at Anthropic Hackathon,"
- [16.7–22.1] "and won himself a prize of $15,000, and it's rated 230,000 stars on GitHub."
- [22.1–31.1] "And it has 67 specialized agents, 278 skills, 94 slash commands, 29 rules, and 14 MCP servers." (Whisper wrote "MCV")
- [31.1–32.9] "That's a freaking AI army."
- [32.9–38.4] "And it was battle tested 1,282 times with a result of 98[%] code coverage,"
- [38.4–43.9] "with users seeing immediate improvements in security, research, design, development, and memory."
- [43.9–46.7] "And it's compatible with all these AIs and many more."
- [46.7–54.0] "And guys, all it takes is one quick copy and paste, as you can see on the screen, and you'll see immediate improvements in every one of your sessions."
- [54.0–57.1] "It would be a tragedy not to set this up immediately."
- [57.1–62.5] "Just comment the word army, and I'll send you the GitHub repo and the setup guide for completely free."

### On-screen content, page by page
(Word-by-word caps subtitles track the speech throughout.)
**Pages 1–3 (0–9.5s):** the creator talking. Subtitles "IF", "IT", "YOU".
**Pages 4–5 (9.5s):** a fiery/glitch transition. Subtitle "STRATEGY".
**Pages 6–8 (9.6–19.3s):** talking head. Subtitles "HIS", "MUSTAFA", "AND".
**Page 9 (19.3–22.2s):** a GitHub repo header bar "♡ Sponsor · Watch 1220 · Fork 35.7k · Star 234k". Subtitle "$15,000".
**Page 10 (22.2–31.2s):** ECC's cross-harness feature table:

| Feature | Claude Code | Cursor IDE | Codex CLI | OpenCode | GitHub Copilot |
|---|---|---|---|---|---|
| Agents | 67 | Shared (AGENTS.md) | Shared (AGENTS.md) | 12 | N/A |
| Commands | 94 | Shared | Instruction-based | 35 | 5 prompts |
| Skills | 281 | Shared | 10 (native format) | 37 | Via instructions |
| Hook Events | 8 types | 15 types | None yet | 11 types | None |
| Hook Scripts | 20+ scripts | 16 scripts (DRY adapter) | N/A | Plugin hooks | N/A |
| Rules | 34 (common + lang) | 34 (YAML frontmatter) | Instruction-based | 13 instructions | 1 always-on file |
| Custom Tools | Via hooks | Via hooks | N/A | 6 native tools | N/A |
| MCP Servers | 14 | Shared (mcp.json) | 7 (auto-merged via TOML parser) | Full | N/A |
| Config Format | settings.json | hooks.json + rules/ | config.toml | opencode.json | copilot-instructions.md + settings.json |
| Context File | CLAUDE.md + AGENTS.md | AGENTS.md | AGENTS.md | AGENTS.md | copilot-instructions.md |
| Secret Detection | Hook-based | beforeSubmitPrompt hook | Sandbox-based | Hook-based | Instruction-based |
| Auto-Format | PostToolUse hook | afterFileEdit hook | N/A | file.edited hook | N/A |
| Version | Plugin | Plugin | Reference config | 2.1.0 | Instruction layer |

(Note: the table says 281 skills and 34 rules; the voice-over says 278 skills and 29 rules.)
**Page 11 (31.2–32.9s):** "THAT'S" / "FREAKING" / "ARMY".
**Pages 12–13 (32.9–46.8s):** an animated gauge counting "19% → 78% → 97% → 98% CODE COVERAGE" with "264 → 1,062 → 1,274 → 1,282 BATTLE-TESTED RUNS". Then a row of icons with up-arrows: SECURITY, RESEARCH, DESIGN, DEVELOP, MEMORY. Then a beige card of logos: the Claude Code crab mascot, Gemini sparkle, "opencode", Cursor cube, and a blue terminal icon (Copilot/Codex-style). Subtitles "TESTED, 1,282, TIMES, RESULT, CODE, USERS, IMMEDIATE, IN, RESEARCH, DEVELOPMENT, MEMORY, COMPATIBLE, AIS, MORE".
**Page 14 (46.8–50.7s):** the GitHub repo page (dark theme): 16 Tags, 2,331 Commits. Commits include "chore: bump plugin version to 2.1.0", "docs: MRR-based ECC Pro + AgentShield security roadmap", "feat(install): add CodeBuddy (Tencent) adaptation", "feat(codex): add ECC navigation guide (#2528)", "feat: add cross-harness memory vault (#2581)", "feat: add gemini install target", "feat: add Hermes and OpenClaw harness install targets (#2433)", "docs: align ECC entrypoints and kimi setup", "feat: add Qwen install target". About: "The agent harness performance optimization system. Skills, instincts, memory, security, and research-first development for Claude Code, Codex, Opencode, Cursor and beyond." Link ecc.tools, MIT license, 234.2k stars, 1.2k watching, 35.7k forks; Release "ECC 2.1.0: Plan Canvas, Kimi …"; "Sponsor this project".
**Pages 15–17 (50.7–62.6s):** talking head. Subtitles "SCREEN", "SO", "JUST".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| ECC / Everything Claude Code (github.com/affaan-m/ECC) | repo | pages 9, 10, 14; audio | git ls-remote OK; clone at scratchpad/repos/affaan-m__ECC; **MIT**; last commit 2026-10-20 (90606c8). Formerly affaan-m/everything-claude-code. The README now claims "71 agents, 311 skills, and 97 legacy command shims", so the reel's numbers are older |
| Affaan Mustafa | person | audio 9.5s | Repo author. Press (36Kr) reports he and David Rodriguez won the Forum Ventures × Anthropic hackathon (Sep 2025) with a product ("PMF Probe", a synthetic user-discovery tool) built using this Claude Code setup; $15,000 is reported in secondary sources. The repo itself was not the hackathon entry, and "solo / beat 74 builders" is unconfirmed |
| 230k / 234k stars, 35.7k forks | numbers | audio, pages 9 & 14 | Consistent with the screen recording; not re-queried |
| 67 agents / 278 (281) skills / 94 commands / 29 (34) rules / 14 MCP servers | numbers | audio, page 10 | From ECC's own docs at that version; now superseded |
| 98% code coverage, 1,282 battle-tested runs | numbers | page 12, audio | Project's own test-suite stats; coverage of the repo's scripts says nothing about making Claude "stronger" |
| ecc.tools, ECC Pro | site/product | page 14 (repo About) | ECC's site. **ECC Pro** = hosted GitHub App, "Private repos from $19/seat/mo"; the OSS repo is free |
| Claude Code, Cursor IDE, Codex CLI, OpenCode, GitHub Copilot, Gemini | tools | page 10, page 13 logos | Supported harnesses |

### What's being promoted / the funnel decoded
"Comment ARMY" triggers an auto-DM with the GitHub link and a "setup guide", promised "completely free". The repo link is public: github.com/affaan-m/ECC. The setup guide is very likely the creator's lead magnet (email capture or a community/newsletter). No paid product of @kyle.disruptor was identified in a web search. The repo author monetises via GitHub Sponsors, ECC Pro ($19/seat/mo for private repos) and sponsor/affiliate links in the README (CodeRabbit, Greptile, Kimi `?aff=ecc`, Itô compute, SerpApi).

### Verification & insights
- The repo is real, active and MIT-licensed; the README warns to install only from official channels (GitHub, npm `ecc-universal`/`ecc-agentshield`, plugin `ecc@ecc`, ecc.tools) because "mirrors … may contain malware".
- "100× stronger" and "immediate improvements in every session" are unmeasured hype. Installing hundreds of skills, hooks and agents adds context and token overhead; ECC's own README warns "Do not stack install methods".
- Hooks and plugins run shell commands with your permissions; review before installing.
- The same repo appears as #6 in @charliehills' 40-repo list (DdO1UioAHAS).
- Could not verify: "74 other builders", the exact prize amount from an official source, the creator's funnel destination, and the post date.

---

<a id="e-dzp-o5gozn0"></a>

## DZP_O5GOzN0 | @marc.kaz | turbovec (RyanCodrai/turbovec): Rust/Python vector index using Google Research's TurboQuant, "31 GB → 4 GB"
- **Link:** https://www.instagram.com/p/DZP_O5GOzN0/
- **Account:** @marc.kaz (Marc Kaz) · **Posted:** 2026-06-06 · **Type:** reel (28.3s, 1 static page: README screenshot with headline and a talking-head overlay)
- **Caption source:** full (Instagram, via yt-dlp; the mirror cut it at "…with str...")
- **Category:** GitHub & dev
- **Verdict:** LEGIT & FREE. turbovec is a real MIT-licensed library. But the hook "Google just shrank…" is misleading (it is an independent developer's implementation of a Google paper), and the caption's "16x (31 GB → 4 GB)" mixes two different numbers.

### Post description
> TurboVec is a new open-source vector index built on Google Research's TurboQuant that delivers extreme compression without sacrificing much performance.
>
> Ships with:
> • 16x memory reduction (31 GB → 4 GB on 10M vectors)
> • 2–4 bit quantization with strong recall
> • Outperforms or matches FAISS on speed
> • Pure Rust + Python bindings, no training phase
> • Search-time filtering with SIMD optimizations
>
> 👉 https://github.com/RyanCodrai/turbovec

### Audio
The creator speaks over the static screenshot.
- [0.0–8.3] "What's up guys, so Google just found a way to shrink 31 gigabytes of AI memory down to four gigs."
- [8.3–17.8] "Bro, what. So turbovec is a new open source vector index built on Google Research TurboQuant, so that…"
- [17.8–28.2] "…delivers extreme compression without sacrificing much performance. So very nice, very nice, definitely check it out boys."

### On-screen content, page by page
**Page 1 (0–28.3s, static):** Headline "🚨 GOOGLE JUST SHRINK 31GB OF AI MEMORY DOWN TO 4GB". The GitHub README (tabs README, Contributing, MIT license) shows banner "turbovec — Google's TurboQuant for vector search"; badges **license MIT · pypi v0.7.0 · crates.io v0.8.0 · paper arXiv**; "A 10 million document corpus takes 31 GB of RAM as float32. turbovec fits it in 4 GB - and searches it faster than FAISS."; "turbovec is a Rust vector index with Python bindings, built on Google Research's TurboQuant algorithm — a data-oblivious quantizer that matches the Shannon lower bound on distortion, with no codebook training and no separate train phase."; bullets: "**Online ingest.** Add vectors, they're indexed — no train step, no parameter tuning, no rebuilds as the corpus grows." / "**Faster than FAISS.** Hand-written NEON (ARM) and AVX-512BW (x86) kernels beat FAISS IndexPQFastScan by 12–20% on ARM and match-or-beat it on x86." / "**Filter at search time.** Pass an id allowlist (or a slot bitmask) to `search()` and the kernel h[andles it]… You always get up to k results from the allowed set — no over-fetching, no recall hit on…" / "**Pure local.** No managed service, no data leaving your machine or VPC. Pair with [an open-source embedding] model for a fully air-gapped RAG stack." / "Building RAG where privacy, memory, or latency matters? You're in the right plac[e]". Python: `pip install turbovec`; `from turbovec import TurboQuantIndex`; `index = TurboQuantIndex(dim=1536, bit_width=4)`; `index.add(vectors)`; `index.add(more_vectors)`. Bottom: "👉 https://github.com/RyanCodrai/turbovec".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| github.com/RyanCodrai/turbovec | repo | caption, page 1 | Exists. **MIT, © 2026 Ryan Codrai**. HEAD c3b043b, 2026-10-06 ("release: 1.1.2"). In-process vector index for Python/Rust storing 2- or 4-bit codes. Current README: "Ten million 768-dimensional embeddings take 31 GB… turbovec holds them in 4 GB and searches them **4.4× faster than FAISS**, at matching recall"; **7.8× smaller at 4-bit, 15.5× at 2-bit**. |
| TurboQuant (Google Research) | paper | caption, audio, page 1 | "TurboQuant: Online Vector Quantization with Near-optimal Distortion Rate", arXiv **2504.19874** (ICLR 2026). The algorithm turbovec implements. |
| FAISS IndexPQFastScan | benchmark | page 1 | Meta's FAISS PQ fast-scan index, the comparison baseline |
| `pip install turbovec`; `TurboQuantIndex(dim=1536, bit_width=4)` | code | page 1 | PyPI package (v0.7.0 at video time; repo now at 1.1.2) |
| RaBitQ (arXiv 2405.12497) | paper | README (verification) | Cited by turbovec for its length-renormalization correction |

### What's being promoted / the funnel decoded
- No funnel. There is a direct GitHub link, and no CTA beyond "check it out". The account is a general AI/tech-news page.

### Verification & insights
- Cloned (already present in scratchpad/repos/turbovec): LICENSE MIT; last commit 2026-10-06; README read. Not executed.
- **"Google just found a way…":** inaccurate. Google Research published the TurboQuant algorithm; turbovec is an independent open-source implementation by Ryan Codrai, not a Google product.
- **"16x memory reduction (31 GB → 4 GB)":** internally inconsistent. 31→4 GB is ~7.8× (4-bit). ~16× (15.5×) applies to the 2-bit mode, which would be ~2 GB.
- **Speed:** at video time the README claimed 12–20% faster than FAISS FastScan on ARM and "match-or-beat" on x86. The current README claims 4.4× (4-bit) and 2.2× (2-bit). These are self-reported benchmarks (docs/benchmarks.md) that I did not reproduce.
- The 31 GB figure is 10M × 768-dim float32 (≈30.7 GB). The screenshot's code uses dim=1536, which would be about 2× larger.
- **Not verified:** independent benchmarks.

---
