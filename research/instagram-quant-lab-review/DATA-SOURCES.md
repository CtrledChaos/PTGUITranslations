# Market Data Sources & Indicator Libraries for the Lab

Compiled 2026-10-19 for a self-hosted Python quant lab.

**How this was verified**
- **Every open-source library listed was checked with git:** it exists, its LICENSE file was read, and its last commit date was taken from the repo.
- **Official data endpoints were contacted directly** to confirm they respond.
- **What was not verified:** history depths and free-tier limits that come from provider documentation are marked *(per provider docs)*. They change often, so check them before you depend on them.

---

## 1. How to judge whether a data source is "reputable"

Rank sources by who produces the data, best first:

1. **Official / primary:** the regulator, central bank, statistics agency, or the exchange itself (SEC, FRED, Treasury, ECB, CFTC, Binance's own archive). These are the most trustworthy and are usually free.
2. **Licensed vendors:** companies that redistribute exchange data under license (Databento, Polygon, Tiingo, Norgate, Tardis.dev, Kaiko, Coin Metrics). Paid, or free tiers with limits. Fine for serious research.
3. **Brokers:** IBKR, Alpaca and OANDA give you data as an account holder. Good for live and recent data, often thinner for deep history.
4. **Unofficial / scraped:** yfinance (scrapes Yahoo), Stooq, random CSV dumps. Fine for quick ideas, **not** for anything you'd bet money on without cross-checking.

**Three traps that ruin backtests (and that free data almost always has)**
- **Survivorship bias.** Free stock data usually only includes companies that still exist. Delisted and bankrupt stocks are missing, so every backtest looks better than reality. Fixing this needs a vendor that includes delisted names (e.g. Norgate, CRSP via a university, some Databento/Polygon datasets).
- **Look-ahead in fundamentals.** Earnings get revised. You need the value *as it was known on that date* ("point-in-time"). SEC EDGAR filings are point-in-time by filing date; most free fundamental APIs are not.
- **Adjustments.** Splits and dividends must be handled consistently. Store raw prices plus corporate actions, and adjust yourself.

---

## 2. Data sources by asset class

### US & global stocks / ETFs
| Source | Type | Cost | What you get | Python access (license, last commit) |
|---|---|---|---|---|
| **SEC EDGAR** | Official | Free (requires a User-Agent header with your email) | All filings, XBRL financial facts, insider Form 4, 13F holdings. Point-in-time by filing date. *Endpoint verified live.* | `edgartools` (MIT, 2026-10-18) |
| **Interactive Brokers API** | Broker | With account; real-time needs market-data subscriptions | Real-time and historical bars across stocks, futures, options, FX, bonds | `ib_async` (BSD-2, 2025-12-06) |
| **Alpaca** | Broker | Free with account (IEX feed); full SIP feed paid *(per provider docs)* | US stocks/ETFs bars, trades, quotes; also crypto | `alpaca-py` (Apache-2.0, 2026-10-16) |
| **Databento** | Licensed vendor | Pay-per-use; free starter credit *(per provider docs)* | Exchange-direct tick/order-book data for US equities, futures and options. Very high quality. | `databento-python` (Apache-2.0, 2026-09-22) |
| **Polygon.io** | Licensed vendor | Free tier (delayed, limited); paid tiers | US stocks, options, indices, FX, crypto | `polygon-io/client-python` (MIT, 2026-10-16) |
| **Tiingo** | Licensed vendor | Free tier with limits | EOD prices back decades, IEX intraday, news, crypto | `tiingo-python` (MIT, 2025-06-22) |
| **Alpha Vantage** | Vendor | Free tier is very limited *(per provider docs)* | Prices, fundamentals, FX, some indicators server-side | `alpha_vantage` (MIT, 2026-07-26) |
| **yfinance (Yahoo)** | Unofficial scrape | Free | Prices, basic fundamentals, option-chain snapshots. Breaks occasionally, so don't use it as your only source. | `yfinance` (Apache-2.0, 2026-10-18) |
| **Kenneth French Data Library** | Academic | Free | Fama-French factors and portfolio returns, back to the 1920s. The standard benchmark for factor research. *Verified live.* | download CSVs; `pandas-datareader` also reads it |
| **Stooq** | Unofficial | Free | EOD history for many global markets. *Didn't respond from the review sandbox; treat as a backup source.* | CSV download |

### Crypto
| Source | Type | Cost | What you get | Python access |
|---|---|---|---|---|
| **Binance Data Vision** (data.binance.vision) | Official exchange archive | Free | Daily and monthly bulk files of klines (bars), trades and aggTrades for spot and futures. The best free deep crypto history. Use is governed by Binance's "Vision Dataset Terms" (read them). *Verified live.* | `binance/binance-public-data` download scripts (no license file in the repo; data is under Binance's terms) |
| **CCXT** | Library for 100+ exchanges' public APIs | Free | One API for OHLCV, order books, trades and funding rates across exchanges. Use it for recent data and live feeds. | `ccxt` (MIT, 2026-10-18) |
| **Hyperliquid API** | Official exchange | Free | Perps market data and trading. Native candles only cover the recent window, so record your own history. | `hyperliquid-python-sdk` (MIT, 2026-06-04) |
| **Deribit API** | Official exchange | Free public endpoints | BTC/ETH **options** (including implied vol) and futures. The main crypto-options venue. *Verified live.* | REST/WebSocket; CCXT supports it |
| **Coin Metrics Community** | Data vendor (free tier) | Free, **non-commercial** (CC BY-NC 4.0, per its repo license) | On-chain network metrics (active addresses, fees, supply, etc.) plus reference rates. *API verified live.* | `coinmetrics/data` CSVs (2026-05-24); community API |
| **DefiLlama** | Open aggregator | Free | DeFi TVL, protocol revenue, stablecoin supply, DEX volumes. *Verified live.* | REST API (`api.llama.fi`) |
| **Tardis.dev** | Licensed vendor | Paid (some free sample days) | Tick-level order-book and trade history from major crypto exchanges, for serious microstructure research | `tardis-python` (MPL-2.0, 2026-09-28) |
| **CoinGecko** | Aggregator | Free tier with tight rate limits | Prices, market caps, coin metadata. *Responded with a rate-limit, so it's alive.* | REST API |

### Forex
| Source | Type | Cost | What you get | Python/JS access |
|---|---|---|---|---|
| **Dukascopy** | Swiss bank/broker feed | Free | Tick and 1-minute FX, metals, CFDs going back many years. *Verified live.* | `dukascopy-node` (MIT, 2026-07-24) |
| **HistData** | Free archive | Free | 1-minute FX bars, 2000s onward | `FX-1-Minute-Data` (Apache-2.0, 2025-05-04) |
| **ECB reference rates** | Official | Free | Daily euro reference FX rates. *Verified live.* | ECB data API (`data-api.ecb.europa.eu`) |
| **OANDA / IBKR** | Broker | With account | Live and historical FX | OANDA v20 API; `ib_async` |

### Rates, macro & economic data
| Source | Type | Cost | What you get |
|---|---|---|---|
| **FRED** (St. Louis Fed) | Official | Free API key | 800k+ US and international series: rates, inflation, employment, credit spreads. Python: `fredapi` (Apache-2.0, 2026-01-28). *Timed out from the sandbox only; widely used.* |
| **US Treasury** | Official | Free | Daily par yield curves, bill rates. *Verified live.* |
| **ECB / BIS / IMF / OECD / World Bank** | Official | Free | Euro-area, global banking, cross-country macro |
| **CFTC Commitments of Traders** | Official | Free | Weekly futures positioning by trader type. Python: `cot_reports` (MIT, last commit 2023-12-30, so stable but quiet). |
| **EIA** | Official | Free API key | Oil, gas and power inventories and production; the key inputs for energy trading |

### Futures & options
- **Databento:** exchange-direct CME futures and options (paid, pay-per-use). The most reputable affordable option.
- **IBKR:** futures and options history and live data with an account.
- **Deribit:** crypto options (free).
- **CFTC COT:** positioning (free).
- **Equity option chains:** free sources (yfinance) give **today's snapshot only**. Historical options data is almost always paid (Databento, Polygon, ORATS, CBOE DataShop).

### All-in-one front door
- **OpenBB** (Apache-2.0, 2026-10-18): one Python and MCP interface over many of the providers above. You plug in your own API keys and it normalizes the output. Good as the lab's single data entry point; your Claude agents can query it over MCP.
- **findatapy** (Apache-2.0, 2026-07-02): a similar unified downloader, strongest for FX and macro.

---

## 3. Indicator libraries (open source)

| Library | License | Last commit | Notes |
|---|---|---|---|
| **TA-Lib** (C core) + **ta-lib-python** | BSD | 2026-10-15 / 2026-10-17 | The industry standard: ~150 indicators plus candlestick patterns, fast C code. Older installs needed the C library built separately. |
| **pandas-ta-classic** | MIT | 2026-10-18 | The maintained continuation of pandas-ta, with 130+ indicators as pandas methods. **The original `twopirllc/pandas-ta` GitHub repo no longer exists**, and its PyPI package is a beta with no license listed, so use this fork instead. |
| **ta** (bukosabino) | MIT | 2026-03-18 | Simple pandas-based library, ~40 common indicators, easy to read |
| **Stock.Indicators** (.NET) + **stock-indicators-python** | Apache-2.0 | 2026-10-16 / 2026-10-04 | Well-tested, documented math, 200+ indicators (the Python wrapper needs the .NET runtime) |
| **talipp** | MIT | 2025-09-09 | **Incremental** indicators that update one bar at a time, ideal for live trading where you don't recompute history |
| **polars_ta** | MIT | 2026-02-11 | Indicators for Polars DataFrames, fast on large universes |
| **vectorbt** | Apache-2.0 + **Commons Clause** (no reselling) | 2026-10-18 | Vectorized backtesting with built-in indicators; free to use, not to resell |
| **smart-money-concepts** | MIT | 2026-04-03 | ICT-style order blocks, fair value gaps, liquidity. Lets you *test* the ICT claims from the videos. |
| **tsfresh** | MIT | 2026-07-06 | Automatically extracts hundreds of statistical features from time series, for ML models |
| **Qlib** (Microsoft) | MIT | 2026-10-08 | Full quant research platform with the **Alpha158/Alpha360** factor libraries |
| **Tulip Indicators** (C) | LGPL | 2024-01-08 | Fast and stable, but no recent updates |
| **finta** | LGPL | 2022-07-24 | **Stale**; avoid for new work |

**Recommendation:**
- **Main library:** TA-Lib for speed and standard definitions, plus pandas-ta-classic for breadth.
- **Live and streaming:** talipp.
- **ML features:** Qlib's Alpha158 or tsfresh.
- **Consistency matters more than which library you pick.** Implementations differ slightly (e.g. RSI smoothing), so pick one per indicator and use it everywhere: backtest and live alike.

---

## 4. Where to store it (self-hosted)

| Store | License | Best for |
|---|---|---|
| **Parquet files + DuckDB** | MIT (DuckDB, 2026-10-18) | Simplest start: bulk history in Parquet, queried with SQL. No server needed. |
| **QuestDB** | Apache-2.0 (2026-10-16) | Fast time-series server for tick and streaming data |
| **TimescaleDB** (Postgres extension) | Mixed Apache-2.0 / Timescale License (2026-10-16) | If you already run Postgres (e.g. for the second brain); some advanced features are under the non-Apache license |
| **ArcticDB** (Man Group) | **Business Source License 1.1**, converts to Apache-2.0 two years after each release | Built for DataFrame time series at hedge-fund scale. Read the "Additional Use Grant" in its license before any commercial use. |

**Suggested lab setup:**
- **Raw downloads:** kept as Parquet, partitioned by `source/asset_class/symbol/year`, and never edited.
- **Clean, adjusted data:** a second layer built from the raw files.
- **Queries:** DuckDB.
- **Tick and live streams:** QuestDB, added later if needed.
- **Sources log:** one record per dataset (vendor, license, date pulled, known gaps) in the second brain's `research/` folder, so every agent knows where each number came from and what it's allowed to be used for.

---

## 5. Start-here shortlist (all free)
1. **Stocks:** SEC EDGAR (`edgartools`) + IBKR or Alpaca for prices, with yfinance only as a cross-check.
2. **Crypto:** Binance Data Vision bulk files for history, CCXT for live and other exchanges, DefiLlama + Coin Metrics Community for on-chain/DeFi.
3. **FX:** Dukascopy + HistData.
4. **Macro / rates:** FRED + Treasury + CFTC COT.
5. **Factors:** Kenneth French library.
6. **Indicators:** TA-Lib + pandas-ta-classic (+ talipp for live).
7. **Storage:** Parquet + DuckDB.
8. **Front door:** OpenBB, so every agent queries data the same way.

**When to pay:** if a strategy survives free-data testing and you're about to risk money, re-test it on vendor data that includes delisted stocks (survivorship-free) and real costs. Databento, Norgate and Polygon are the reputable, reasonably priced options; check their current pricing.
