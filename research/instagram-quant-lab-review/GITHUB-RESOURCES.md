# Reputable GitHub Projects for the Lab

Compiled 2026-10-19. **61 repositories checked in this pass**, plus the ones already verified in `DATA-SOURCES.md` and `REPORT.md`. For each one I:
- confirmed it exists with git
- read its LICENSE file directly
- took its last commit date from the repo

Star counts couldn't be checked (the GitHub API is blocked in the review sandbox), so popularity notes below are general reputation, not numbers. **Nothing was installed or run.** Treat this as a vetted shortlist to pilot, not a guarantee of quality.

**Choosing:**
- **Prefer active projects:** commits within the last few months.
- **Prefer permissive licenses:** MIT, Apache-2.0, BSD.
- **Copyleft is fine for personal use:** GPL and AGPL are fine as long as you never distribute or host them for others.
- **Read the license before any commercial use** of "source-available" code: Commons Clause, BSL, custom licenses.

Items already covered in `DATA-SOURCES.md` and `REPORT.md` are only cross-referenced here.

---

## 1. Second brain: memory, knowledge base, RAG

### Agent memory servers (the "shared brain" layer)
| Repo | License | Last commit | What it is |
|---|---|---|---|
| `garrytan/gbrain` | MIT | 2026-10-19 | **Recommended in the plan.** Markdown-in-git brain, Postgres index, HTTP MCP with per-agent tokens. Pre-1.0. |
| `vectorize-io/hindsight` | MIT | 2026-10-16 | **Recommended as optional.** Automatic agent memory (recall/retain), Postgres + pgvector, MCP per bank. v1.0. |
| `mem0ai/mem0` | Apache-2.0 | 2026-10-14 | Widely used memory layer for LLM apps; self-hostable server plus a hosted version |
| `letta-ai/letta` | Apache-2.0 | 2026-10-18 | Formerly MemGPT. Stateful agents with self-editing memory; runs as a server. |
| `getzep/graphiti` | Apache-2.0 | 2026-10-19 | **Temporal knowledge graph** for agent memory: tracks how facts change over time. Has an MCP server. |
| `topoteretes/cognee` | Apache-2.0 | 2026-10-16 | Turns documents into a knowledge graph plus vectors for agent memory |
| `basicmachines-co/basic-memory` | **AGPL-3.0** | 2026-10-18 | Local Markdown knowledge base exposed to Claude over MCP; simple and Obsidian-compatible |
| `modelcontextprotocol/servers` | Apache-2.0 (moving from MIT) | 2026-10-11 | Official reference MCP servers, including a simple **memory** (knowledge-graph) server, filesystem, git, and fetch |

### Retrieval / RAG engines (search over large document collections)
| Repo | License | Last commit | What it is |
|---|---|---|---|
| `HKUDS/LightRAG` | MIT | 2026-10-14 | Lightweight graph-plus-vector RAG; good results, easy to self-host |
| `microsoft/graphrag` | MIT | 2026-10-08 | Microsoft's graph-based RAG. Strong for "what are the themes across all my research" questions; costly to index. |
| `infiniflow/ragflow` | Apache-2.0 | 2026-10-19 | Full RAG application with deep document parsing (tables, layouts) |
| `run-llama/llama_index` | MIT | 2026-10-14 | The standard Python framework for building custom RAG pipelines |

### Personal knowledge apps (the human-facing side; all self-hostable)
| Repo | License | Last commit | Notes |
|---|---|---|---|
| `khoj-ai/khoj` | AGPL-3.0 | 2026-08-01 | Self-hosted AI "second brain" app: chat with your notes and documents, works with local models |
| `Mintplex-Labs/anything-llm` | MIT | 2026-10-15 | All-in-one desktop/server app: chat with documents, agents, local or hosted models |
| `open-webui/open-webui` | Custom (BSD-style + **branding clause**) | 2026-10-16 | Popular chat UI for local models. You may not remove its branding except in small deployments (≤50 users), which is fine for a personal lab. |
| `ollama/ollama` | MIT | 2026-10-17 | Runs local LLMs and **embedding models**. The piece that keeps your brain's data inside the lab. |
| `logseq/logseq`, `siyuan-note/siyuan`, `TriliumNext/Trilium` | AGPL-3.0 | Oct 2026 | Open-source note apps, alternatives to Obsidian (which is free but closed source) |
| `foambubble/foam` | MIT | 2026-10-12 | Markdown knowledge base inside VS Code; works on the same files as Obsidian |
| `kepano/obsidian-skills` | MIT | 2026-09-15 | Agent skills for Obsidian Markdown, Bases and Canvas (by Obsidian's CEO); what claude-obsidian builds on |

### Capture tools (getting things in)
| Repo | License | Last commit | What it captures |
|---|---|---|---|
| `paperless-ngx/paperless-ngx` | GPL-3.0 | 2026-10-19 | Scanned documents and PDFs, with OCR, tagging and search. A good home for statements and paperwork. |
| `karakeep-app/karakeep` | AGPL-3.0 | 2026-10-18 | Bookmarks, links and notes, with AI tagging. A place to save Instagram-style finds going forward. |
| `ArchiveBox/ArchiveBox` | MIT | 2026-10-18 | Archives full copies of web pages, so links you save don't disappear |

**How these fit the plan:**
- The plan stays **GBrain + Markdown repo** (optionally + Hindsight).
- **Graphiti** and **Letta** are the strongest alternatives if you want a temporal knowledge graph or self-editing agent memory.
- **Ollama** provides the local embeddings and models.
- **Karakeep** solves the "I saved it on Instagram and lost the link" problem from this project.

---

## 2. Neural networks for markets: forecasting and ML

| Repo | License | Last commit | What it is |
|---|---|---|---|
| `amazon-science/chronos-forecasting` | Apache-2.0 | 2026-10-05 | Amazon's pretrained time-series foundation models (Chronos / Chronos-Bolt); forecasts without training |
| `google-research/timesfm` | Apache-2.0 | 2026-09-29 | Google's time-series foundation model |
| `SalesforceAIResearch/uni2ts` | Apache-2.0 | 2026-06-02 | Salesforce's Moirai foundation models |
| `time-series-foundation-models/lag-llama` | Apache-2.0 | 2025-06-06 | Probabilistic forecasting foundation model; **quieter now** |
| `shiyu-coder/Kronos` | MIT | 2026-04-13 | Finance-specific foundation model trained on candlestick data *(see REPORT.md)* |
| `Nixtla/neuralforecast` | Apache-2.0 | 2026-10-14 | 30+ neural forecasting models (N-BEATS, N-HiTS, TFT, PatchTST…) behind one API |
| `Nixtla/statsforecast` | Apache-2.0 | 2026-10-15 | Fast classical baselines (ARIMA, ETS, Theta). **Always compare neural models against these.** |
| `unit8co/darts` | Apache-2.0 | 2026-10-16 | Friendly all-in-one forecasting library, classical and neural |
| `sktime/sktime` | BSD-3 | 2026-10-18 | scikit-learn-style toolkit for time-series ML |
| `autogluon/autogluon` | Apache-2.0 | 2026-10-18 | AutoML, including AutoGluon-TimeSeries, which wraps Chronos |
| `thuml/Time-Series-Library` | MIT | 2026-04-18 | Research benchmark library from Tsinghua: reference implementations of the latest architectures |
| `AI4Finance-Foundation/FinRL` | MIT | 2026-10-14 | Deep reinforcement learning for trading. A research sandbox, like TensorTrade. |
| `AI4Finance-Foundation/FinGPT` | MIT | 2026-09-23 | Open financial LLMs and fine-tuning recipes (sentiment, forecasting) |
| `microsoft/qlib` | MIT | 2026-10-08 | Full AI quant platform: data, factors, models, backtest *(see DATA-SOURCES.md)* |
| `stefan-jansen/machine-learning-for-trading` | MIT | 2026-10-18 | Companion code to *Machine Learning for Algorithmic Trading*. **The best single learning resource** on this list: hundreds of notebooks from data to deep learning, done carefully. |

**The honest rule for neural nets on prices:** published results are usually on easier data (energy, traffic) than markets. Use foundation models as **features or baselines**, and always benchmark against `statsforecast` and a naive "tomorrow = today" model on out-of-sample data, with costs included.

---

## 3. Trading frameworks, strategy libraries and evaluation

### Backtest / live engines
| Repo | License | Last commit | Best for |
|---|---|---|---|
| `nautechsystems/nautilus_trader` | LGPL-3.0 | Oct 2026 | Professional event-driven backtest-to-live, multi-asset *(REPORT.md)* |
| `QuantConnect/Lean` | Apache-2.0 | Oct 2026 | Mature multi-asset engine; can run locally *(REPORT.md)* |
| `freqtrade/freqtrade` | GPL-3.0 | 2026-10-19 | The most popular open-source **crypto** bot: backtest, hyperopt, live, plus FreqAI for ML |
| `jesse-ai/jesse` | MIT | 2026-10-17 | Clean crypto research and live framework |
| `hummingbot/hummingbot` | Apache-2.0 | 2026-09-22 | Market-making and arbitrage bots across CEX/DEX |
| `stefan-jansen/zipline-reloaded` | Apache-2.0 | 2026-10-17 | Maintained version of Quantopian's Zipline; good for equity factor research |
| `pmorissette/bt` | MIT | 2026-10-17 | Simple portfolio/allocation backtesting |
| `robcarver17/pysystemtrade` | GPL-3.0 | 2026-10-16 | Rob Carver's real systematic futures system (author of *Systematic Trading*). Excellent for trend-following and risk management. |
| `edtechre/pybroker` | Apache + **Commons Clause** | 2026-08-27 | ML-oriented backtester; free to use, not to resell |
| `mementum/backtrader` | GPL-3.0 | **2023-04-19** | Classic and widely taught, but **unmaintained**; prefer the others for new work |

### Evaluation, risk and portfolio
| Repo | License | Last commit | What it does |
|---|---|---|---|
| `ranaroussi/quantstats` | Apache-2.0 | 2026-09-27 | Performance tearsheets (Sharpe, drawdowns, monthly returns) |
| `stefan-jansen/alphalens-reloaded` | Apache-2.0 | 2026-10-17 | **Factor/signal analysis.** Tells you if an indicator actually predicts returns before you build a strategy. |
| `stefan-jansen/pyfolio-reloaded` | Apache-2.0 | 2026-10-17 | Portfolio and risk analysis |
| `PyPortfolio/PyPortfolioOpt` | MIT | 2026-07-07 | Portfolio optimization (mean-variance, HRP, Black-Litterman) |
| `dcajasn/Riskfolio-Lib` | BSD-3 | 2026-10-04 | Advanced risk-based portfolio optimization (CVaR, drawdown, risk parity) |

### Strategy collections (study, don't trust)
| Repo | License | Last commit | Notes |
|---|---|---|---|
| `freqtrade/freqtrade-strategies` | GPL-3.0 | 2026-09-08 | Community crypto strategies for freqtrade, all testable. Most will not survive honest testing; that's the lesson. |
| `je-suis-tm/quant-trading` | Apache-2.0 | 2024-04-14 | Readable Python implementations of classic strategies (pairs, MACD, Bollinger, etc.); quiet but useful for learning |

**Avoid:** `hudson-and-thames/mlfinlab`. The public repo is stuck at **2021** and is under a **proprietary license agreement**, not open source; the library became a paid product. Use `machine-learning-for-trading` and Marcos López de Prado's published papers for the same techniques (triple-barrier labeling, purged cross-validation).

---

## 4. Data streams (live, real-time)

| Repo | License | Last commit | What it does |
|---|---|---|---|
| `ccxt/ccxt` | MIT | 2026-10-18 | Unified REST + websocket access to 100+ crypto exchanges *(DATA-SOURCES.md)* |
| `bmoscon/cryptofeed` | **AGPL-3.0** + attribution term | 2026-10-18 | Normalized real-time crypto feeds (trades, books, funding) from many exchanges, with built-in writers to databases |
| `tardis-dev/tardis-node` | MPL-2.0 | 2026-10-16 | Real-time and historical crypto market-data replay (Tardis's own feeds need a paid key) |
| `databento/databento-python`, `alpacahq/alpaca-py`, `ib-api-reloaded/ib_async` | Apache / Apache / BSD | 2025–2026 | Live stock, futures and options streams *(DATA-SOURCES.md)* |
| `Finnhub-Stock-API/finnhub-python` | Apache-2.0 | 2026-06-24 | Client for Finnhub (vendor with a free tier: real-time US quotes, news, fundamentals) |
| `quixio/quix-streams` | Apache-2.0 | 2026-10-15 | Python stream processing on Kafka: compute indicators live as ticks arrive |
| `bytewax/bytewax` | Apache-2.0 | 2026-10-16 | Python stream-processing framework (Rust core) |
| `nats-io/nats-server` | Apache-2.0 | 2026-10-15 | Lightweight message bus to pass live data between your lab's VMs and agents |

**Simple lab streaming setup:** exchange or broker feeds (ccxt / cryptofeed / ib_async) → NATS (one message bus) → indicator workers (talipp for incremental indicators) → QuestDB (storage) → agents and dashboards subscribe. Start without the bus (one Python process writing to QuestDB) and add NATS only when several VMs need the same live data.

---

## 5. Curated "awesome" lists (for further discovery)

| Repo | License | Last commit | Notes |
|---|---|---|---|
| `wilsonfreitas/awesome-quant` | none stated | 2026-09-13 | **The** standard index of quant libraries and data sources, by language |
| `georgezouq/awesome-ai-in-finance` | CC0 | 2026-09-08 | AI/ML-in-finance projects, papers and courses |
| `grananqvist/Awesome-Quant-Machine-Learning-Trading` | none stated | 2025-05-21 | Papers, courses and code for ML in trading; quieter now |
| `ai-boost/awesome-harness-engineering` | CC0 | Oct 2026 | Agent harness and memory patterns *(REPORT.md, V10)* |

A curated list only means *someone* linked it. Apply the same checks (license, recent commits, real code, honest README) to anything you pick from them.

---

## 6. If you only start with a handful

1. **Learn properly:** `stefan-jansen/machine-learning-for-trading`.
2. **Test indicators before strategies:** `alphalens-reloaded` (does the signal predict anything?), then `quantstats` for results.
3. **Engine:** `nautilus_trader` (multi-asset) or `freqtrade` (crypto-only, fastest to get running).
4. **Forecasting baseline vs. neural:** `statsforecast` vs. `chronos-forecasting` / Kronos, through `neuralforecast` or `darts`.
5. **Second brain:** `gbrain` + `ollama` (local embeddings), with `graphiti` or `letta` as alternatives to evaluate.
6. **Live data:** `ccxt` / `ib_async` into QuestDB; add `nats-server` when more than one machine needs the stream.
