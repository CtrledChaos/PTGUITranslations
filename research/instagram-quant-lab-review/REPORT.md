# Instagram Saves → Quant Lab: Reviewed & Ranked

**35 posts reviewed** (20 videos, 13 image posts/carousels, 2 posts only partly retrievable), compiled 2026-10-18.

**How each post was checked**
- Every video was downloaded, transcribed and broken into one frame per second. Every frame and every carousel slide was viewed, with crops for small text.
- Every repo named was confirmed with git, shallow-cloned, and its LICENSE, README and commit history read. **No downloaded code was executed**, except the Clip 1 repo's own test suite.
- Products were checked by web search.
- Star counts come only from screenshots, because the GitHub API was blocked in the review sandbox.

**Not fully retrieved**
- `Dd2iE-vjl1-` (a "Top 15 finance GitHub repos" carousel): the slides couldn't be fetched.
- `Dd2f6r5BfAy`: only the cover image could be fetched.

---

## The short version: what's worth your time

### Tier 1: free, open source, directly useful for the lab (start here)

| What | Why | License | From post |
|---|---|---|---|
| **NautilusTrader** – `nautechsystems/nautilus_trader` | Production-grade backtest→live engine (Rust core, Python API, IBKR/crypto adapters) | LGPL-3.0 | DcD1vwCtGGX, DegcLifkzmE |
| **skfolio** – `skfolio/skfolio` | Portfolio optimization + walk-forward / purged CV, sklearn-style. Highest value per hour of effort | BSD-3 | DcD1vwCtGGX |
| **OpenBB** – `OpenBB-finance/OpenBB` | Open financial data platform; has an MCP server, so Claude can query it directly | Apache-2.0 | DegcLifkzmE |
| **Free long-history data** – Dukascopy (`dukascopy-node`), HistData (`FX-1-Minute-Data`), Hyperliquid SDK, Polymarket `py-clob-client` | 10+ yrs of 1-min FX for free; crypto perps + prediction-market APIs | MIT / Apache-2.0 | DeloQPzgbtw |
| **CFTC COT data** – `cot_reports` | Free weekly positioning data, one pip install | MIT | DemXvfSjwCM |
| **TradingAgents** – `TauricResearch/TradingAgents` | Multi-agent LLM research desk (analysts / debate / risk), paper-backed, runs with local Ollama | Apache-2.0 | DegkHS3GRHJ |
| **Kronos** – `shiyu-coder/Kronos` | Open foundation model for OHLCV forecasting (AAAI 2026); small models run on CPU | MIT | DcD1vwCtGGX |
| **Vibe-Trading** – `HKUDS/Vibe-Trading` | LLM research workspace + "Alpha Zoo" of 462 prebuilt factors (Qlib-158, Alpha-101, GTJA-191) | MIT | DcD1vwCtGGX |
| **claude-obsidian** – `AgriciDaniel/claude-obsidian` | Persistent, cited research memory for Claude Code (all tests passed when run here) | MIT | Defw9ggACu1 (Clip 1) |
| **MinerU** – `opendatalab/MinerU` | PDF → markdown/JSON incl. tables & formulas; for feeding papers/filings into the lab | Apache-2.0 + terms | DeCKnW0DAGc |
| **superpowers** – `obra/superpowers` | Claude Code plugin: brainstorm→plan→TDD→review discipline | MIT | DeRgmkvIkP4 |
| **SkillOpt** – `microsoft/SkillOpt` | Auto-improves Claude skill files against held-out evals; learns from past sessions | MIT | DbEK3bustQ7 |

### Tier 2: real and usable, but niche, early, or needing caveats

| What | Note | From post |
|---|---|---|
| **OpenAlice** – `TraderAlice/OpenAlice` | Local AI trading orchestrator with human-approved execution; AGPL, live trading is beta | DatpvftE-Iq |
| **qanat** – `fidetolabs/qanat` | Point-in-time financial data as an MCP server; MIT, beta | DeUE0tQPmgX |
| **Indra OCR** – `datalab-to/indra` | Fast CPU OCR (code Apache-2.0, weights have a revenue-capped license) | DeosAIWFZN2 |
| **TensorTrade** – `tensortrade-org/tensortrade` | RL trading sandbox; experiment only. Its own results lose money after 0.1% fees | DemfalkFKqU |
| **QF-Lib** – `quarkfin/qf-lib` | Event-driven backtester with good tearsheets (found behind a misattributed image) | Dd4JGF1lIhA |
| **Hindsight, OpenRig, OpenChamber** | Agent memory / run Claude Code + Codex as a team / remote GUI for agents on a headless server | DeCKnW0DAGc, DenP7kUD3Az |
| **Also verified real (from a list we couldn't fully read):** `microsoft/qlib`, `QuantConnect/Lean`, `virattt/ai-hedge-fund` | All active, permissive licenses | Dd2iE-vjl1- |

### Tier 3: ideas and reference material worth keeping (no install)

- **Research pipeline:** idea → rules → code → backtest → in/out-of-sample → Monte Carlo → live. Use SSRN as a free strategy-paper source. *(Dd4QRzpFM00)*
- **Config-driven signal scanner:** rules across sector ETFs, alerts to Slack. Rebuildable in pandas in an afternoon. *(DenSGzckhBw)*
- **Peer groups by revenue reality, not SIC codes:** better screens and comparables. *(DeUE0tQPmgX)*
- **Agent folder pattern:** PROMPT.md / handovers / KNOWLEDGE.md / **evals the agent can't edit** / skills. *(DenJITWMbi2)*
- **Project memory files:** README / STATUS / progress / decisions. A lighter version of Clip 1. *(DYYaA1LKtoO)*
- **Claude Code project-structure cheat sheet:** a useful layout, but several details on it are wrong (see entry). *(DdtaUOCNmNs)*
- **Paper → strategy → backtest:** the free version of what Astral charges $30/mo for is Claude Code + vectorbt/LEAN. *(Ddei3-cy1cC)*
- **Strategies to test, not trust:**
  - 9 EMA + VWAP intraday *(DekhFIbgQTO)*
  - "midday sell" EURUSD *(DemxOm_AS9a)*
  - Gartley 222 *(DejYce1ADfB)*
  - Each entry has the recovered rules plus how to test them honestly.

### Tier 4: skip

- **Misrepresented:**
  - **DemHMk4AOWB:** a PS4 game port narrated as an "AI memory layer"; fabricated.
  - **DeEtB78jJtu:** "AI Omarchy"; a real desktop distro wrapped in hype, and not suited to a headless server.
- **Data-snooping hype:** **DekL5L-gzAy**, "8 million tests, 19 patterns survived". The held-out year was used to pick the winners.
- **Generic prompts / pop-psych / funnels:**
  - DeY-l9KjXVd
  - Dea-ayyDW8t (fake "Buffett system")
  - DeRXBt_kxDh
  - Dem60yJDELo
  - Del5xpMtE-t (strategy names only)

---

## Patterns across the batch

1. **Most posts are lead funnels.** About 20 of 35 end in "comment X and I'll DM you." In every case checked, the thing they DM is either already public (a GitHub link) or the entry point to a paid course, newsletter or community. You never need to comment; the repo names are in this document.
2. **Repo-spotlight accounts don't check what they post.** @repopicks narrated an OCR tool as an LLM runner and a game port as AI memory. Always open the actual repo.
3. **The tools are often better than the posts.** TensorTrade, NautilusTrader and OpenBB are legit even when the post's code is broken, its charts are mockups, or its "BREAKING" is about a 2019 library.
4. **Trading-result red flags seen here:**
   - P&L cards where the "best day" is bigger than the whole month
   - 56% win rate on 71 trades presented as an edge
   - an NVDA buy-and-hold rally presented as a bot's backtest
   - a sine-wave test chart shown as performance

   Treat every strategy claim as a hypothesis and test it with realistic costs and out-of-sample data.

## Suggested starter stack for the lab (all free)

1. **Data:**
   - OpenBB (equities, macro, fundamentals)
   - Dukascopy / HistData (FX history)
   - `cot_reports` (positioning)
   - a recorder for Hyperliquid if you want crypto perps
2. **Research and validation:**
   - pandas + vectorbt or backtesting.py for fast idea tests
   - skfolio for portfolio construction and walk-forward / purged CV
3. **Engine:** NautilusTrader once an idea survives. The same code runs in backtest, paper and live via IBKR.
4. **AI layer:**
   - Claude Code + superpowers
   - claude-obsidian as research memory, with MinerU to ingest papers
   - TradingAgents / Vibe-Trading as experimental research assistants
5. **Experiments:** Kronos forecasts as a feature, benchmarked against naive baselines.

---

# Full entries

Ordered by usefulness. Each entry has the detailed verification, claims vs. reality, the creator's agenda, and lab-use notes.


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

---

## Defw9ggACu1 | claude-obsidian: Claude Code plugin that builds a cited, linked Obsidian wiki ("AI second brain")
- **Link:** https://www.instagram.com/reel/Defw9ggACu1/
- **Posted by:** Nathan Hodgson (@nathanhodgson.ai), 2026-10-15, 59 s
- **Method:** full download, Whisper transcript, every frame reviewed, repo cloned and test suite run

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

---

## Dem60yJDELo | "Company brain / context package": a whiteboard pitch for connecting Claude Code to an org knowledge base, aimed at AI consultancies
- **Link:** https://www.instagram.com/p/Dem60yJDELo/
- **Account:** @lostandlucky · **Type:** video (57s)
- **Category:** USELESS / REPACKAGED
- **Lab value:** LOW – a generic consulting concept with no tool, repo or method named; the underlying idea (an agent with a curated knowledge base) is already common and better covered by real open-source projects.

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
