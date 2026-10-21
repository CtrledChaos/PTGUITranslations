# Batch 3, part 05 of 06: full entries

This part continues the full entries in category order. The summary table and cross-cutting findings are in part 00, and the complete single document is research/instagram-quant-lab-review/BATCH3-REPORT.md.

<a id="e-demrbpwcemc"></a>

## DemrBpwCemC | @quantfinancetogo | Quant Finance From Scratch Part 26: the size factor (small minus big), with a simulation and real-world post-1981 decay
- **Link:** https://www.instagram.com/p/DemrBpwCemC/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-17 · **Type:** reel (98.3s; one continuous animated screen with about 11 sections. The scene detector caught only 2 frames, so I reviewed it from the 2-fps frames.)
- **Caption source:** full (Instagram, via yt-dlp. The mirror had cut it off at about 250 characters.)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – accurate, carefully caveated factor-investing education. The simulation is labelled as assumed numbers and the hook chart as schematic. Nothing is sold.

### Post description
> ➡️ Part 26 of Quantitative Finance From Scratch: the size factor.
>
> A company's size on the stock market is its market value, the share price times the number of shares. The classic size portfolio buys the smallest stocks, sells the largest and rebalances once a year.

- Simulation (500 stocks, 50 years, assumed numbers): with the built-in premium on, the size portfolio earns **3.0 % a year (t 2.21)**.
- From an assumed publication year the premium is switched off (an assumption of the model, not a result); afterwards it earns **-0.2 % a year (t -0.11)**.
- The model shows how the method works, not what real markets will pay; the hook chart is a schematic, not real data.
- Real markets: the effect weakened sharply after publication in the early eighties; researchers still debate whether a small premium remains.
- "Education only, not financial advice."
- Hashtags: #quantfinance #sizefactor #factorinvesting #python #finance

*Caption condensed – full text is on the original post.*

### Audio
Narration in English. It runs about 160 words, so these are close notes with the key lines quoted.
- [0–8] "One of the most famous effects in finance nearly vanished right after it was discovered. It's called the size factor. Quantitative finance from scratch part 26."
- [8–18] Size = market value = share price × number of shares. Small caps have low market value; large caps have high market value.
- [18–26] "In 1981, researchers found small companies had earned more than large ones over decades, even after adjusting for their market risk."
- [26–34] "Quants turned this into a factor. Rank all stocks by size, buy the smallest group, sell the largest, and rebalance every year."
- [34–42] Why it might work: small companies are "riskier, harder to trade and less researched", so investors may want extra return.
- [42–51] "In our simulation, the size portfolio earns 3% a year with a t-statistic of 2.2 until the effect is published and no clear premium afterwards."
- [51–63] Real markets: the effect became much weaker soon after publication. "From the early 80s on, small US stocks earned little or no more than large ones on average", though researchers still debate whether a small premium remains.
- [63–75] Size became a standard factor in 1993, when Fama and French added it to their three-factor model next to market and value. "It helps explain why small stocks tend to rise and fall together."
- [75–84] In practice: get exposure through small-cap funds or ETFs, or as one tilt among several factors in a long-short portfolio.
- [84–97] Summary: small companies have tended to earn more, "But since the early 80s, the effect has been weak and uncertain." "Follow for more if you want to properly learn quantitative finance."

### On-screen content, page by page
The fixed header reads "QUANT FINANCE FROM SCRATCH", "PART 26", "Size Factor", "small companies have tended to beat big ones", with a part selector 13–26. The fixed footer reads "simulated market, assumed numbers · education only · not financial advice". Each section shows a chart panel above a `size.py` code panel ("python · running").
**Section 1 (0–5s) "small vs large – schematic, not data":** "small companies vs large companies". Dots are sized by market value; the y-axis is "value of 1 invested"; the x-axis runs "decades before / 1981 / later". Labelled "schematic, not real data · log scale".
**Section 2 (5–10s) "after 1981 – the gap stops growing":** The small and large lines diverge, then run parallel after a "DISCOVERED" marker at 1981, labelled "GAP STOPS GROWING".
**Section 3 (10–15s) "size – market value = price × shares":** "market value: how big a company is on the stock market", with a "one share" bar.
**Section 4 (15–20s) "small caps, large caps – low or high market value":** "SMALL CAPS: LOW MARKET VALUE", a curve of 500 simulated companies sorted by market value.
**Section 5 (20–30s) "found in 1981 – even after market risk":** Average return plotted against market risk (beta). Small stocks sit "SMALL: ABOVE THE LINE" of what is "explained by risk".
**Section 6 (30–35s) "the size factor – buy small, sell large":** "BUY THE 50 SMALLEST" is highlighted on the sorted curve (smallest to largest).
**Section 7 (35–45s) "why could it work? – risk, trading, research":** Three panels: "riskier" (wider return spread), "harder to trade" (large vs small bid-ask gap), "less researched" (many vs few analysts). Caption: "investors may want extra return".
**Section 8 (45–55s) "our run – simulated, seed 26":** Output of `$ python size.py`: "3.0%/year, t 2.21 (years 1 to 25)" and "-0.2%/year, t -0.11 (years 26 to 50)". A cumulative chart marks "published (assumed)" at year 25. Bars: 3.0% vs -0.2% per year.
**Section 9 (55–65s) "after publication – much weaker":** "US size premium per month (published research)": **about 0.30% (1926 to 1981) → about 0.08% (1982 to 2017)**, labelled "LITTLE OR NO MORE".
**Section 10 (65–80s) "three factor model – market, size, value":** "three factor model (1993)". "return = α + s·size", with "size = small minus big (SMB)". This expands to "return = α + b·market + s·size + h·value". Label: "RISE AND FALL TOGETHER".
**Section 11 (80–85s) "in practice – fund or one tilt":** Two options: "small cap fund or ETF (long only)", or "long short: one tilt among several" (market, size, value, momentum).
**Section 12 (85–98s) "size – part 26":** Recap chart labelled "SMALL TENDED TO EARN MORE" and "SINCE THE EARLY 80s: WEAK, UNCERTAIN".

**Code (`size.py`, 15 lines, shown but not executed):** It simulates 500 stocks with log market value `m = rng.normal(0, 1.5, 500)` and an assumed publication year `pub = 25`. Each of 50 yearly rebalances computes a size z-score. A premium `p = .012 * (y < pub)` (1.2% per unit z, switched off after year 25) drives returns `r = np.expm1(rng.normal(-p * z, .3))`. The portfolio holds the 50 smallest minus the 50 largest. Market value then follows returns. The script prints the mean per year and t-stat (mean / sd × √n) before and after publication. The seed is `default_rng(26)`.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Size factor / SMB (small minus big) | concept | Throughout | Standard equity factor. |
| 1981 discovery | paper | Audio 18s, section 5 | Rolf Banz (1981), "The relationship between return and market value of common stocks", *Journal of Financial Economics*. Not named in the post; this is the well-known source. |
| Fama & French three-factor model, 1993 | paper | Audio 63s, section 10 | Fama & French (1993), "Common risk factors in the returns on stocks and bonds", *JFE*. Correct. |
| 0.30%/month (1926–1981) vs 0.08%/month (1982–2017) | numbers | Section 9 | Labelled "published research". They are consistent in magnitude with SMB from the Ken French data library and with published post-discovery studies. I did not recompute them. |
| 3.0%/yr t 2.21; -0.2%/yr t -0.11 | simulation output | Section 8, caption | Model output with an assumed premium switch-off. Not executed, so unverified, but the caption is explicit that the drop is built in. |
| Parts 13–26 series | series | Header | The creator's numbered "Quant Finance From Scratch" series. |

### What's being promoted / the funnel decoded
There is no CTA beyond "Follow". No link, product, course or comment keyword appears. It looks like a pure education series, and I found no monetisation in the post.

### Verification & insights
- The facts check out: Banz 1981, Fama-French 1993, and the post-publication weakening of the size premium (a well-documented, debated finding).
- Caveats the post already states: the simulation's before/after split is assumed, not discovered.
- Context it does not mention: later research (for example Asness et al., "Size Matters, If You Control Your Junk", 2018) argues the size premium reappears after controlling for quality. That is relevant to its "debate whether a small premium remains" line.
- Related: the next part, 27 (Deo-i-zCdMb), covers the full Fama-French model.
- Not verified: the exact 0.30% / 0.08% figures and their source paper.

---

<a id="e-dedydilictv"></a>

## DedydiLiCtv | @quantfinancetogo | "Quant Finance From Scratch, Part 23: Mean Reversion": AR(1) spread simulation, half-life, regression t-test (−2.9 limit), z-score rule, post-publication decay, with a 16-line Python script on screen
- **Link:** https://www.instagram.com/p/DedydiLiCtv/
- **Account:** @quantfinancetogo (display name not in data) · **Posted:** 2026-10-14 (decoded from the post ID) · **Type:** reel (142.7s; 2 scene-detector pages, but it is one continuous animated explainer with about 20 distinct panels, reviewed from the 2-fps frames)
- **Caption source:** possibly truncated (mirror). The yt-dlp full-caption fetch returned HTTP 429.
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. This is an accurate, honest educational explainer. The simulation numbers are internally consistent. It explicitly warns about trading costs, out-of-sample decay, regime shifts, and spurious mean reversion in short samples. All data is simulated ("education only · not financial advice"), and there is no sales funnel.

### Post description
> ➡️ Quantitative Finance From Scratch, Part 23: Mean Reversion.
>
> Mean reversion means that a quantity which moves far from its long run average tends to drift back toward it. A single stock price behaves much like a random walk, but spreads, ratios an...

(cut off by the mirror; the full caption could not be retrieved because Instagram returned 429)

### Audio
Narration (English, a voice-over that may be synthetic) over background music. Condensed into timestamped notes:
- [0.0–8.2] Hook: "What is the mean reversion strategy?", why it is one of the best-known quant ideas, "And is it even profitable?" Series title: Quantitative finance from scratch, part 23.
- [8.2–29.4] Definition: a quantity far from its long-run average tends to drift back over time. Not everything does: a single stock price behaves much like the random walk from part 2, with no average to return to. It shows up more in spreads, ratios and rates (the gap between two related stocks, interest rates, volatility).
- [29.4–38.9] Forces that pull back: traders buy cheap and sell expensive, central banks steer interest rates, and calm usually returns after a panic.
- [38.9–51.4] Simplest model: each day the distance from the average shrinks by a fixed share, plus a random shock. The time for half the distance to disappear is the half-life; short half-life means strong pullback.
- [51.4–67.2] Test: regress today's change on yesterday's distance from the average (as in part 21); a negative slope means pullback. Pure chance often looks like a pull, so quants use a stricter t-statistic limit of "about minus three instead of minus two."
- [67.2–77.1] Simulation: a spread with a built-in 10-day half-life is estimated at 9.5 days, with t ≈ −6, far beyond the limit.
- [77.1–86.0] Basic rule: measure the z-score (standard deviations from the average) and bet on a move back when it is large.
- [86.0–100.9] Where institutions look: pairs of related stocks, an index vs its futures, currency pairs far from long-run levels over several years, related-commodity spreads (crude oil vs fuels made from it), and interest rate spreads.
- [100.9–122.1] Profitable? "It can be, but only if the pull is real," strong enough to beat trading costs and still present in data not used for testing. Studies find many published edges shrink once widely known. The average can shift, a past pull can vanish, and a spread can keep widening into large losses before coming back.
- [122.1–131.6] Short samples can make a pure random walk look mean-reverting: in their test, three months of a pure random walk typically showed a half-life of about 10 days.
- [131.6–141.2] Summary: a pullback toward an average that quants model, measure (half-life) and test. CTA: "Follow for more if you want to properly learn quantitative finance."

### On-screen content, page by page
Every panel has the fixed header "QUANT FINANCE FROM SCRATCH ▌ · PART 23 · **Mean Reversion** · the pull back to the average", a series selector (13 … 22, **23** highlighted), and the footer "simulated spread, assumed numbers · education only · not financial advice". From about 10s, a code editor ("meanreversion.py", python) under the chart types out the script line by line, in sync with the narration.

**Panel 1 (0.0–5.5s), hook:** A simulated spread is drawn live with a z readout ("z = −0.59 … −1.60 … −2.95 … −1.36", "distance from the average") and "half life = 10 d" ("built into this spread"). The axis runs z −2 to +2 with a "long run average" line. Callouts: "Z −2.95: FAR FROM THE AVERAGE", then "THIS SWING: HALF THE GAP GONE IN 7 DAYS". Footnote: "one simulated spread · day 31 of 140 shown · half life 10 days". A "KEY IDEA – MEAN REVERSION – the pull back to the average" card is shown.
**Panel 2 (~5.5–8s), title card:** "QUANTITATIVE FINANCE" with a bundle of random-walk lines.
**Panel 3 (~8–15s), "mean reversion · far away, then back":** A ball in a bowl ("average"), labels "FAR AWAY" → "DRIFTS BACK", above a simulated spread ("one simulated spread, 300 days"; "white line: long run average").
**Panel 4 (~15–29s), "where it shows up · spreads, rates, volatility":** "A SINGLE STOCK PRICE – NO AVERAGE TO RETURN TO" ("random walk (part 2)") next to three mean-reverting mini-charts: "spread of two stocks", "interest rate", "volatility", tagged "PULLED BACK TO AN AVERAGE".
**Panel 5 (~29–39s), "why it pulls back · three forces":** "traders buy cheap, sell expensive" (scale icon); "central banks steer interest rates" (bank icon); "calm returns after a panic" (decaying wave).
**Panel 6 (~39–51s), "the simplest model · half life = 10 days":** "gap today = **0.933** × gap yesterday + **shock**"; "every day 6.7 % of the gap disappears". Bars halve ("gap", "1/2", "1/4", "1/8") with a "HALF LIFE = 10 DAYS" label, plus a faster curve "SHORT HALF LIFE (3 DAYS): STRONG PULL".
**Panel 7 (~51–59s), "testing the pull · stricter limit ≈ −2.9":** A scatter of "↑ today's change" vs "yesterday's distance from the average →" ("1,007 days of the simulated spread"), with a fitted line "SLOPE −0.070: A PULL BACK".
**Panel 8 (~59–67s), same heading:** A histogram "2,000 PURE RANDOM WALKS, NO PULL" of t-statistics, overlaid on a dashed "normal curve (part 22)"; "34 % LOOK LIKE A PULL AT −2"; "STRICTER LIMIT ≈ −2.9".
**Panel 9 (~67–77s), "our run · simulated, seed 23":** Terminal output: `$ python meanreversion.py` / `slope -0.070, t statistic -6.05` / `half life: built 10, found 9.5 days`. Labels "BUILT IN: HALF LIFE 10 DAYS", "FOUND: 9.5 DAYS", "T = −6.05 FAR BEYOND THE LIMIT".
**Panel 10 (~77–86s), "z score · distance in standard deviations":** "z = (spread − average) / standard deviation"; output `z score today: -0.52`; ±2 bands with the breaches marked; "BEYOND ±2 ON 5.1 % OF DAYS: RULE EXPECTS A MOVE BACK".
**Panel 11 (~86–101s), "where institutions look · illustration":** Five tiles: "pairs of related stocks", "index vs its futures", "currency pairs, over years" (Ⓐ Ⓑ), "crude oil vs fuels", "interest rate spreads".
**Panel 12 (~101–114s), "is it profitable? · three conditions":** "SO IS IT PROFITABLE?", then the checklist "the pull is real" ✓, "strong enough to beat trading costs" ✓ (bars "pull" vs "costs"), "still there in unseen data" ✓ (bars "test" vs "unseen"). A chart "published return signals, average of 97": bar "before" vs "after publication", animated to "**−58 %**", with a faint source note (≈ "study of 97 signals (2016)").
**Panel 13 (~114–122s), "the limits · what can go wrong":** "the average can shift", "the pull can vanish", "the gap can keep widening" ("large losses").
**Panel 14 (~122–132s), same heading:** "A PURE RANDOM WALK, 63 DAYS, NO PULL AT ALL"; "ITS FITTED HALF LIFE: 9.8 DAYS"; "TYPICAL RESULT OF 2,000 SUCH TESTS: ABOUT 10 DAYS".
**Panel 15 (~132–142.7s), "mean reversion · part 23" summary:** "A PULL BACK TOWARD AN AVERAGE" · "MODEL IT" · "HALF LIFE 9.5 DAYS" · "TEST IT: T −6.05 < −2.9".

**Final code on screen (meanreversion.py, 16 lines, read from the frames; not executed), excerpt:**
```
rng = np.random.default_rng(23)
days, phi = 252 * 4, .5 ** (1 / 10)   # half life 10
for d in range(1, days):   # pull back plus a shock
    x[d] = phi * x[d - 1] + rng.normal(0, 1)
u = x[:-1] - x[:-1].mean()   # yesterday's distance
v = np.diff(x)   # today's change
b = (u * v).sum() / (u * u).sum()   # the slope
t = b / np.sqrt((e @ e) / (days - 3) / (u @ u))
hl = np.log(2) / -np.log(1 + b)   # half life
z = (x - x.mean()) / x.std()   # the z score
```
The omitted lines import numpy, initialise the spread `x = np.zeros(days)` (average 0), compute the residual `e = v - v.mean() - b * u` ("what the line misses"), and print "slope …, t statistic …", "half life: built 10, found … days" and "z score today: …". Inputs: seed 23, 1,008 days (252 × 4), φ = 0.5^(1/10), shocks N(0, 1). Printed results shown on screen: slope −0.070, t statistic −6.05, half life found 9.5 days, z score today −0.52.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Mean reversion / AR(1) / Ornstein–Uhlenbeck-style model | concept | all | Standard. "gap today = φ × gap yesterday + shock" is an AR(1) process. Half-life = ln2 / −ln(φ). |
| 0.933, "6.7 % of the gap disappears daily" | number | panel 6 | Correct: 0.5^(1/10) = 0.9330, so 1 − 0.933 = 6.7 %. |
| Slope −0.070, t −6.05, half-life 9.5 days | numbers | panel 9; audio 67s | Internally consistent: ln2 / −ln(1 − 0.070) ≈ 9.55 days. The true slope is φ − 1 = −0.067. Not executed. |
| "Stricter limit ≈ −2.9 / about −3" | number | panel 8; audio 64s | Matches the Dickey–Fuller 5 % critical value with a constant (≈ −2.86). The "−2" normal cut-off is wrong for this test, as the video says. |
| "34 % look like a pull at −2" | number | panel 8 | Plausible under the Dickey–Fuller distribution. Not executed. |
| "Beyond ±2 on 5.1 % of days" | number | panel 10 | Plausible for a roughly normal z (≈4.6 %). Not executed. |
| "Published return signals, average of 97 … −58 %" | study | panel 12; audio 109s | Matches McLean & Pontiff (2016), *Journal of Finance*, "Does Academic Research Destroy Stock Return Predictability?": 97 anomalies, returns ≈ 58 % lower post-publication (≈ 26 % lower out-of-sample). |
| Random walk, 63 days → fitted half-life 9.8 days, typical ≈ 10 days | numbers | panel 14; audio 125s | Illustrates small-sample bias toward finding mean reversion (a real, known effect). Not executed. |
| Parts 2, 21, 22 of the series | cross-refs | audio | The earlier episodes: random walk, regression, normal curve. |
| NumPy | library | code | Real open-source Python library. |
| @quantfinancetogo | handle | account | The series account. No website or product found by web search. |

### What's being promoted / the funnel decoded
- Only "Follow for more if you want to properly learn quantitative finance." No comment-to-DM, product, link or course is visible. The truncated caption could hide a CTA, but nothing in the video suggests one.

### Verification & insights
- Math checked by hand, not by running the code. φ = 0.5^(1/10) gives exactly the "0.933 / 6.7 %" shown. The regression in lines 7–11 is ordinary least squares of Δx on de-meaned lagged x, and the t-statistic uses n − 3 degrees of freedom. The half-life formula on line 12 matches the standard ln2 / −ln(1 + b). The printed results (−0.070, −6.05, 9.5) agree with each other.
- The claim that "even pure chance often looks like a pull … use about −3" is correct: this is the Dickey–Fuller / ADF unit-root test, whose 5 % critical value is about −2.86 (with a constant). Real quants use ADF or KPSS tests, the Engle–Granger or Johansen cointegration tests for pairs, and Hurst exponents.
- The −58 % post-publication decay is real (McLean & Pontiff 2016).
- The warnings are appropriate: costs, out-of-sample testing, shifting means, spreads widening into large losses (e.g. the LTCM-style "convergence trade" blow-ups), and spurious results in short samples.
- Not covered: transaction costs or borrow costs aren't quantified, and there is no real-market backtest. That is by design, since this is a concept lesson.
- Could not verify: the full caption (429), and the exact source line under "−58 %" (too small to read; it appears to say a 2016 study of 97 signals).

---

<a id="e-deswk28re6i"></a>

## DeSWK28Re6i | @quantfinancetogo | "Quant Finance From Scratch, Part 18: Fat Tails": Black Monday 1987 (−22.6%) under a bell curve (once every 1.83e+110 years) vs a Student-t fat-tail model (once every 216 years), with simulation code
- **Link:** https://www.instagram.com/p/DeSWK28Re6i/
- **Account:** @quantfinancetogo · **Posted:** 2026-10-09 (decoded from the shortcode) · **Type:** reel (91.3s; animated explainer, 1 scene page + continuous animation reviewed at 2 fps)
- **Caption source:** possibly truncated (mirror)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct, honest explainer of fat tails. The numbers reproduce exactly from the shown code. Assumptions are flagged ("ASSUMPTION", "our fat-tailed curve is an assumption too").

### Post description
> ➡️ Quantitative Finance From Scratch, Part 18: Fat Tails
>
> On Black Monday in 1987, the Dow fell 22.6% in a single day. The bell curve says that should never happen.
>
> Real prices make big moves far more often than the bell curve from part 4 predicts. ...

(Cut off by the mirror. The rest was not retrievable because Instagram returned 429.)

### Audio
Narration by the creator, condensed to timestamped notes with key lines quoted:
- [0.0] Hook: "On Black Monday in 1987, the Dow fell 22.6% in a single day. The bell curve says that should never happen."
- [6.8] "Quantitative finance from scratch, part 18. Today is about fat tails."
- [10.9] Real price changes make big moves much more often than the bell curve (normal distribution) from Part 4 predicts. The bell curve puts most days near the average and makes big moves extremely rare; a fat-tailed curve has more weight at its far edges, so extreme days happen far more often, even with the same volatility (Part 7).
- [31.0] Simulation: 100 years of trading run twice, both with a swing of about 1% a day (a typical day moves about 1% up or down), once with a bell curve and once with fat tails.
- [41.6] The bell curve gives zero days moving more than 5%; the fat-tailed model "about 70". (The machine transcript wrote "70%". The screen shows **74 days**.)
- [48.4] At the assumed 1% a day, Black Monday was more than 22 swings. The bell curve expects such a day once in a number of years "with more than 100 zeros"; the fat-tailed model about once in 200 years.
- [62.6] Why it matters for risk: "A risk model built on the bell curve calls crashes almost impossible."
- [68.6] Caveat: the fat-tailed curve is an assumption too, and in this run its wildest day jumps 36%. "Every model of the tails is a guess about rare days."
- [79.1] Answer: Black Monday is impossible "only on a bell curve"; with fat tails it is a rare day the model expects about once in 200 years.
- [87.7] CTA: "Follow to really learn quantitative finance."

### On-screen content, page by page
Constant frame: "QUANT FINANCE FROM SCRATCH PART 18 / **Fat Tails** / big moves, more often than the bell curve", series bar 13–21 with 18 highlighted, footer "simulated returns, assumed numbers · education only · not financial advice".

- **0–7s:** "DOW JONES · BLACK MONDAY 1987 – schematic path, real one-day drop". A counter runs from −0.5% to "**−22.6% since Friday's close**" (axis: Fri close → Monday, 19 Oct 1987 → Mon close), with the stamp "−22.6% in a single day". A mini chart, "our models, 1% a day · log scale", shows bell curve vs fat tails and "BLACK MONDAY −22.6%" far outside the bell curve. A "KEY IDEA – FAT TAILS – BIG MOVES, MORE OFTEN" card follows.
- **~10–17s:** "Fat tails · today" and "big moves, more often · than the bell curve (AS IN PART 4)": the two density curves.
- **~20–31s:** "the bell curve · normal distribution": "MOST DAYS WITHIN 1%: 68%", then "**MOST DAYS WITHIN 1%: 68% VS 82%**", "SAME VOLATILITY: 1% A DAY (AS IN PART 7)", "**OVER 5%: 0 VS 74 DAYS**", and "fat tails: weight at the edges · log scale".
- **~35–45s:** "assumed numbers · 100 years, 1% a day" / "SIMULATED · ASSUMED NUMBERS / 100 YEARS, TWICE / 1% A DAY". Mirrored histograms, "once with each model · **25,200 days each**".
- **~45–50s:** Terminal "bell: swing 1.00%, 0 days over 5%, worst −4.1%". Two 100-year return strips: bell curve "**0** days over 5%, WORST −4.1%" and fat tails with a count climbing to "53…" partway through (year 75), ending at 74. Fat-tail worst: "**WORST −25.5%**". Caption: "bell curve: 0 days over 5% · in 100 years".
- **~50–62s:** "Black Monday: 22.6 swings · Dow, 19 October 1987": "**z = 0.226 / 0.01 = 22.6**". A log chart "chance per day" (1 in 100 down to 1 in 100 trillion) vs "swings down (1 swing = 1% a day)". Terminal results: "**bell: a day like that every 1.83e+110 years**" and "**fat: a day like that every 216 years**". Captions "bell curve: every 1.83e+110 years · assumed 1% a day" and "fat tails: every 216 years".
- **~62–68s:** "risk models · built on the bell curve": a histogram "days per 0.25% (log scale), simulated" with "Black Monday" far left at −25%.
- **~68–79s:** "an assumption too · wildest day +36.4%": "fat tails, simulated, all 100 years" stamped "**ASSUMPTION**", "**WILDEST DAY +36.4%**", "WORST −25.5%".
- **~79–91s:** "Fat Tails – rare days, still part of the model": "**So was Black Monday impossible?**" with the bell vs fat strips and a −22.6% bar. "BELL CURVE: EVERY 1.83e+110 YEARS / FAT TAILS: EVERY 216 YEARS", then "the answer · about once in 216 years" and "follow to really learn quant finance".

Final code (`fattails.py`, 17 lines). Excerpt of the core logic:
```
days, swing = 252 * 100, .01      # assumed: 1% a day
bell = rng.normal(0, swing, days)
fat = rng.standard_t(3, days) * swing / 3**.5
for name, r in ("bell", bell), ("fat", fat):
    big = (abs(r) > 5 * swing).sum()   # 5 swings
z = .226 / swing                  # Dow, 19 Oct 1987: -22.6%
p_bell = math.erfc(z / 2**.5) / 2
p_fat = .5 - (math.atan(z) + z/(1 + z*z)) / math.pi
for name, p in ("bell", p_bell), ("fat", p_fat):
    years = 1 / p / 252
```
The rest: it imports `numpy` and `math` and seeds `np.random.default_rng(18)`. The fat-tailed returns are a Student-t with 3 degrees of freedom, rescaled by `3**.5` to the same 1 % swing. The first loop prints each model's swing, the number of days over 5 % and the worst day (`f"{name}: swing {r.std():.2%}, {big} days over 5%, worst {r.min():.1%}"`; on screen "bell: swing 1.00%, 0 days over 5%, worst −4.1%", fat tails 74 days and worst −25.5 %). The second loop prints how often a Black-Monday-sized day occurs (`f"{name}: a day like that every {years:.3g} years"`; on screen "every 1.83e+110 years" for the bell curve and "every 216 years" for fat tails).

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Black Monday, 19 Oct 1987, Dow −22.6% | event / number | audio 0s; screen | Correct (DJIA −22.61%, the largest one-day % drop) |
| Bell curve / normal distribution | concept | audio; screen | Standard |
| Fat tails: Student-t with 3 degrees of freedom, scaled to unit variance | model | code | `standard_t(3)/√3` has standard deviation 1. `p_fat` is the exact closed-form tail of that scaled t3 (checked by hand: p ≈ 1.85e-5/day → about 215–216 years). |
| 68% vs 82% within 1%; 0 vs 74 days over 5%; worst −4.1% vs −25.5%; wildest +36.4% | numbers | screen | Reproduced exactly with the shown code (seed 18). The "53" was a mid-animation count. |
| 1.83e+110 years (bell) vs 216 years (fat) | numbers | screen; audio | Correct for the stated assumptions |
| Parts 4 and 7 | cross-references | audio | Earlier episodes in the series (bell curve, volatility) |

### What's being promoted / the funnel decoded
No funnel. The only CTA is "Follow to really learn quantitative finance". There is no link, product or comment keyword. Same series as DeY9P8_CpfW (Part 21) and DeWlPe2id2c (Part 20).

### Verification & insights
- I re-ran my own transcription of the on-screen code. It gave bell: 1.00% swing, 0 days over 5%, worst −4.1%; fat: 1.00%, **74** days, worst −25.5%, best +36.4%. That matches the screen. The spoken "about 70" rounds the 74.
- Accurate framing: the 216-year figure depends entirely on the assumed t3 tail and a 1% daily volatility. In 1987 the volatility just before the crash was higher. The video says so itself ("every model of the tails is a guess").
- This is good education on why VaR models with a normal assumption understate crash risk.
- Not verified: the rest of the cut-off caption.

---

<a id="e-deo-i-zcdmb"></a>

## Deo-i-zCdMb | @quantfinancetogo | Quant Finance From Scratch Part 27: the Fama-French three-factor model, with a simulation showing CAPM "alpha" of 7.9% shrinking to -0.9%
- **Link:** https://www.instagram.com/p/Deo-i-zCdMb/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-18 · **Type:** reel (104.1s; one continuous animated screen with about 11 sections, reviewed from the 2-fps frames)
- **Caption source:** full (Instagram, via yt-dlp. The mirror had cut it off.)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – correct, well-sourced factor-model education. It uses a clearly labelled simulation and sells nothing.

### Post description
> ➡️ Part 27 of Quantitative Finance From Scratch: the Fama-French three factor model.
>
> The market beta alone (parts 14 and 15) explains stock returns only in part, so Fama and French added two more factors, size (part 26) and value (part 25).

- The model was introduced in 1993 in the Journal of Financial Economics ("Common risk factors in the returns on stocks and bonds").
- A factor is the return of one portfolio minus another: small minus big (SMB) and high minus low (HML, cheap minus expensive).
- Regression: a stock's return above the risk-free rate = alpha + a beta times each factor's return + an error term for the stock's own swings. Alpha is what the three factors cannot explain.
- Simulation: nine portfolios, three simulated factors, 50 years of monthly returns, assumed numbers, true alpha zero. With the market alone, the small value portfolio shows an **alpha of 7.9 % a year** and the market explains only **46 %** of its ups and downs.
- With all three factors its **alpha drops to -0.9 % a year**, close to the built-in zero; the model explains **90 %**, and the regression finds betas of **1.00, 1.00 and 0.96**.
- The structure is built into the model, so it "shows how the method works and makes no claim about real markets."
- Real data: the three factors explain much of the differences in average returns, but not all. In Fama-French's 1996 tests, short-term return continuation (momentum) stayed unexplained, and they later added two more factors.
- Eugene Fama shared the 2013 Nobel Memorial Prize in Economic Sciences with Lars Peter Hansen and Robert Shiller "for their empirical analysis of asset prices".
- "Education only, not financial advice."
- Hashtags: #quantfinance #famafrench #factorinvesting #python #finance

*Caption condensed – full text is on the original post.*

### Audio
Narration in English, about 190 words, given as close notes with key lines quoted.
- [0–8] "Eugene Fama won a Nobel Prize, and together with Kenneth French, he explained stock returns with just three factors… Quantitative Finance from Scratch, Part 27."
- [9.9–25] Market beta (part 14) explains returns only in part, so they added size (part 26) and value (part 25).
- [25–36] "A factor is the return of one portfolio minus another. Small minus big takes small stocks minus big ones. And high minus low takes cheap stocks minus expensive ones."
- [36–54] The regression: excess return = alpha + beta × each factor + error. "Each beta is the stock's sensitivity or exposure to one factor, and alpha is the part of the return that the three factors can't explain."
- [54–62] Simulation: nine portfolios with built-in betas on three simulated factors over 50 years; true alpha is zero.
- [62–72] Market alone (CAPM): the small value portfolio "seems to earn an alpha of 7.9% a year, and the market explains only 46%".
- [72–84] All three factors: alpha drops to −0.9%, close to zero; the model explains 90%; the regression recovers betas "about one each".
- [84–93] "That is why fund managers are judged by their exposure to these factors as well, because once size and value are included, much of what looked like alpha often disappears."
- [93–103] Summary, then "Follow to really learn quantitative finance."

### On-screen content, page by page
The fixed header reads "QUANT FINANCE FROM SCRATCH · PART 27 · Fama-French Model · market, size and value explain returns", with a part selector 14–27. The footer reads "simulated market, assumed numbers · education only · not financial advice". Each section has a chart above a `fama_french.py` code panel.
**Section 1 (0–5s) "market only – CAPM, one beta":** The hook. Average return per year (5–15%) is plotted against market beta (0.5–1.5). The "small value portfolio" sits far above the CAPM line. Labelled "simulated, nine portfolios, 50 years".
**Section 2 (5–10s) "three factors – market, size, value":** Card "KEY IDEA: Fama-French Model". During the animation the panel briefly shows "alpha +3.9%, explained (R²) 66%". This is an in-between animation value, not a result.
**Section 3 (10–25s) "one beta: only part – two more factors":** Scatter of the small-value portfolio's monthly returns against the market ("ONE BETA (PART 14)"). Bar: "market explains 46%". Label: "TWO MORE FACTORS".
**Section 4 (25–35s) "what is a factor? – one portfolio minus another":** "factor = portfolio A − portfolio B". Panels: "SMALL MINUS BIG" (small − big) and "HIGH MINUS LOW", each with a cumulative-return line.
**Section 5 (35–45s) "the regression – alpha + betas + error":** "R − r_f = α + β_M (R_M − r_f)", building up to "+ β_SMB·SMB + β_HML·HML + ε".
**Section 6 (45–55s) "beta = exposure – one beta per factor":** Three scatter fits labelled β_M (market), β_SMB (size, SMB) and β_HML (value, HML). Label: "ALPHA = WHAT THE FACTORS CAN'T EXPLAIN".
**Section 7 (55–65s) "our simulation – simulated, seed 27":** A 3×3 grid of 3D bars ("average return per year (column height)"). Size beta and value beta each run 0 → 1. Labels: "MARKET BETA = 1 FOR ALL" and "50 YEARS, MONTHLY".
**Section 8 (65–75s) "market only – CAPM regression":** Small value portfolio: **alpha +7.9%, explained (R²) 46%**. The other portfolios also sit above the CAPM line.
**Section 9 (75–85s) "all three factors – Fama-French regression":** Points line up on the "predicted by three factors" / "perfect fit" line. Small value portfolio: **alpha −0.9%, explained (R²) 90%**. Label: "CLOSE TO THE BUILT-IN 0".
**Section 10 (85–95s) "what looked like alpha – size and value exposure":** A waterfall titled "small value portfolio: what looked like alpha". **CAPM alpha +7.9% → size exposure −3.7% → value exposure −4.9% → market −0.2% → −0.9%.** Labels: "JUDGED BY FACTOR EXPOSURE", then "MOST OF THE ALPHA DISAPPEARS". The arithmetic checks: 7.9 − 3.7 − 4.9 − 0.2 = −0.9.
**Section 11 (95–104s) "Fama-French model – part 27":** Recap of the equation, labelled MARKET BETA, SIZE BETA, VALUE BETA, "WHAT IS LEFT: ALPHA".

**Code (`fama_french.py`, about 16 lines, shown but not executed):** The seed is `default_rng(27)`. It uses `months = 600` (50 years). The monthly factor premia are market .5%, SMB .2%, HML .3%, with volatilities 4.5/3/3%. Nine portfolios take size and value betas from a {0, .5, 1} grid, and every market beta is 1. Each portfolio adds its own N(0, 2%) noise. The script then runs OLS twice, with the market only (CAPM) and with all three factors, and prints annualised alpha (12 × intercept), R² ("fit") and the betas.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Fama & French (1993), "Common risk factors in the returns on stocks and bonds", *Journal of Financial Economics* | paper | Caption | Correct citation. |
| Fama-French 1996 tests, momentum unexplained | paper | Caption | Fama & French (1996), "Multifactor explanations of asset pricing anomalies", *Journal of Finance*. Correct: momentum is the noted failure. |
| "Later added two more factors" | fact | Caption | The Fama-French five-factor model (2015) adds profitability (RMW) and investment (CMA). Correct. |
| 2013 Nobel: Fama, Hansen, Shiller, "for their empirical analysis of asset prices" | fact | Caption, audio | Correct. |
| SMB, HML, CAPM, alpha, beta, R² | concepts | Throughout | Standard. |
| 7.9% / 46% → −0.9% / 90%; betas 1.00, 1.00, 0.96 | simulation output | Sections 8–10, caption | Model output. Not executed, so unverified. The numbers are internally consistent. |
| Parts 14, 15, 25, 26 | series cross-references | Caption, audio | Earlier parts of the same series (part 26 = DemrBpwCemC). |

### What's being promoted / the funnel decoded
There is no CTA beyond "Follow" and no link, product or keyword. It is a free education series.

### Verification & insights
- All historical and academic facts check out (1993 JFE paper, 1996 momentum anomaly, the five-factor extension, the 2013 Nobel co-laureates and citation).
- The simulation is honest about being built to recover its own parameters, so it demonstrates the method, not evidence.
- The practical takeaway is accurate: factor regressions are how fund "alpha" is stress-tested. Kenneth French's free data library provides the real factor series.
- Not verified: the printed regression outputs (code not run).

---

<a id="e-detlvaecmn0"></a>

## DetLvaeCMn0 | @neuron.machinelearning | 5 ML models on S&P 500 data (1999–2018): Random Forest, XGBoost, GARCH, K-means, Isolation Forest, and "always up" beats both direction models
- **Link:** https://www.instagram.com/p/DetLvaeCMn0/
- **Account:** @neuron.machinelearning ("NEURON" brand; display name not in fetched data) · **Posted:** 2026-10-20 (worked out from the shortcode; `upload_date` missing) · **Type:** carousel (7 slides)
- **Caption source:** possibly truncated (mirror). The re-fetch with yt-dlp was blocked by the sandbox permission policy, so it was not run.
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – an honest educational carousel. Its key result is that ML direction prediction lost to the naive baseline. One arithmetic slip and some small backtest caveats.

### Post description
> 5 machine learning models, run on real S&P 500 data from 1999 to 2018. Here's what actually happened 📈
>
> 	1.	Random Forest: 54.1% at predicting if the index is higher in 5 days
> 	2.	XGBoost: 50.3%, with early stopping at round 121
> 	3.	GARCH(1,1): caugh...

- The mirror cuts the caption off at "caugh..." and the remaining items and hashtags are missing.

### Audio
None (image carousel).

### On-screen content, page by page
Every slide has "NEURON" at top left, an "n/7" counter, and the footer "@neuron.machinelearning · real S&P 500 data 1999-2018".
**Slide 1:** "MACHINE LEARNING models for FINANCE". The creator takes a mirror selfie. Tags: python, sklearn, xgboost, arch, (numpy, pandas partly hidden). Thumbnails of the charts from slides 2–6 and the formulas ŷ = (1/B)Σ_b T_b(x); σ²_t = ω + αε²_{t−1} + βσ²_{t−1}; F_m = F_{m−1} + η h_m; s(x) = 2^{−E[h(x)]/c(n)}. Subtitle "5 models · real S&P 500 data · real results". "swipe →".
**Slide 2, "1. RANDOM FORESTS":**
- Formula ŷ(x) = (1/B)Σ_{b=1}^{B} T_b(x). Variance formula ρσ² + ((1−ρ)/B)σ².
- Text: "An ensemble of 300 decision trees… Workhorse of credit risk: scorecards and loan-default models."
- Setup: "every S&P 500 day, six features, one question: higher in 5 days? Trained on 1999–2012, tested on 2013–2018." It "ranks the distance to the 50-day average first. Test accuracy: 54.1%."
- Feature-importance chart (mean decrease in impurity), in order: dist_sma50 (~0.21), rsi_14, ret_5d (~0.18), vol_20d (~0.16), volume_z (~0.15), ret_1d (~0.11).
- Code: `y = (close.shift(-5) > close).astype(int)`; `cut = int(len(X) * 0.7)  # TEMPORAL split`; `RandomForestClassifier(n_estimators=300, max_depth=5, min_samples_leaf=50, oob_score=True)`.
- Chart: out-of-bag error vs n_estimators, falling from ~0.463 to ~0.448 at 300 trees.
**Slide 3, "2. XGBOOST":**
- Text: "Gradient boosting… each new tree fits what the ensemble still gets wrong. The second derivative of the loss sizes every leaf's step. Default tool in systematic quant…"
- Code: `xgb.XGBClassifier(n_estimators=400, learning_rate=0.03, max_depth=4, subsample=0.8, colsample_bytree=0.8, early_stopping_rounds=50)`.
- Logloss chart: train falls from ~0.69 to ~0.61, validation flat at ~0.675, early stop at about 121.
- Formulas F_m(x) = F_{m−1}(x) + η h_m(x); L = Σ_i l(y_i, ŷ_i) + Σ_k Ω(f_k).
- Text: "Validation loss stopped improving at round 121… That gap is the model memorising one good year. Test accuracy on 2013–2018: 50.3%."
**Slide 4, "3. GARCH(1,1)":**
- Formula σ²_t = ω + αε²_{t−1} + βσ²_{t−1}. Chart "volatility clusters" (|daily return| % vs GARCH volatility %, 2000–2018, spike about 2008).
- Text: "Fitted on 5,000 real days: α = 0.10, β = 0.885. So 98.7% of yesterday's risk carries into today. Peak: 5.47% daily volatility on 16 Oct 2008. Median day: 0.92%." Also: "still the default on risk desks for VaR and option pricing."
- Code: `from arch import arch_model`; `r = 100 * close.pct_change().dropna()`; `arch_model(r, vol="GARCH", p=1, q=1).fit()`.
**Slide 5, "4. K-MEANS":**
- Objective: arg min_μ Σ_{k=1}^{3} Σ_{x∈C_k} ||x − μ_k||².
- Features: "20-day return and the 20-day volatility. Three clusters fall out on their own."
- Chart: S&P 500 coloured by regime. Pills: "calm · 66.5% of days", "normal · 30.8% of days", "stress · 2.8% of days".
- Text: "The stress regime lights up 2002, 2008 and 2011… Funds use regimes like these for risk-on / risk-off allocation."
- Code: `StandardScaler().fit_transform(df[["ret_20d","vol_20d"]])`; `KMeans(n_clusters=3, n_init=10)`.
**Slide 6, "5. ISOLATION FOREST":**
- Formula s(x) = 2^{−E[h(x)]/c(n)}. Chart "days the forest isolated fastest", with 50 anomalous days clustered in late 2008, plus a few in 2001–02 and 2011.
- Text: it is used in "AML and market surveillance". "On daily return, volatility and volume, it flagged 50 days (1%). The five most abnormal are all autumn 2008, led by −9.03% on 15 Oct 2008." Also: "Unusual is not the same as criminal: a human still reviews every flag."
- Code: `IsolationForest(n_estimators=300, contamination=0.01)`, fitted on `["ret_1d","vol_20d","volume_z"]`; `flags = iso.predict(df) == -1`.
**Slide 7, "THE VERDICT":**
- Text: "Both direction models lost to the dumbest rule on 2013–2018: "always say up" scored 59.9%. Random forest 54.1%, XGBoost 50.3%."
- Bar chart "5-day direction, out of sample": 59.9 / 54.1 / 50.3, with a 50% "coin flip" line.
- Text: "Predicting direction is the hard part. That is finance."
- CTA box: "Comment FINANCE – I'll DM you the code for all 5 models". "save this 📌".

### Everything named or linked
| Item | Type | Where | What it really is (verified) |
|---|---|---|---|
| scikit-learn (RandomForestClassifier, KMeans, IsolationForest, StandardScaler) | library | slides 1, 2, 5, 6 | Standard open-source ML library. The parameters shown are valid. |
| xgboost | library | slides 1, 3 | Real. `early_stopping_rounds` in the constructor is valid in xgboost ≥1.6. |
| arch (`arch_model`) | library | slides 1, 4 | Kevin Sheppard's Python ARCH/GARCH package. Usage is correct. |
| −9.03% on 15 Oct 2008 | number | slide 6 | Correct: the S&P 500 fell about 9.03% that day, its worst day of 2008. |
| Peak vol on 16 Oct 2008; median 0.92% | numbers | slide 4 | Plausible, not recomputed. |
| α = 0.10, β = 0.885 → "98.7%" | numbers | slide 4 | Inconsistent as printed: 0.10 + 0.885 = 0.985. The 98.7% is probably from unrounded α. |
| 59.9% / 54.1% / 50.3% | numbers | slides 2, 3, 7, caption | Not executed, so unverified. A ~60% up-week rate for 2013–18 is plausible for that bull market. |
| Regime split 66.5 / 30.8 / 2.8% | numbers | slide 5 | Not executed, so unverified. |

### What's being promoted / the funnel decoded
"Comment FINANCE" gets a DM with "the code for all 5 models". No product, price or link is shown. The account is an ML-education brand ("NEURON"), and a web search found no product or website for @neuron.machinelearning. The comment gate exists for engagement. Every model is fully reproducible from the snippets on the slides plus standard S&P 500 price data, so there is no need to engage.

### Verification & insights
- The slides honestly report a negative result: random forest at 54.1% and XGBoost at 50.3% both lose to always predicting "up" (59.9%). Accuracy also isn't profit; no returns or costs are shown.
- Caveats: the 5-day target windows overlap, and there is no gap between train and test, so a few days of label leakage happen at the split. K-means and Isolation Forest are fit on the full 1999–2018 sample, so they "find" crises in hindsight. That's fine for description, but not a tradable signal.
- "1999–2018" is a stale window. It ends before 2020 and 2022.
- The claims "default on risk desks", "default tool in systematic quant" and "workhorse of credit risk" are broadly fair generalisations.
- Not verified: the full caption, the DM'd code, and all model outputs (no code was run).

---

<a id="e-dewlpe2id2c"></a>

## DeWlPe2id2c | @quantfinancetogo | "Quant Finance From Scratch, Part 20: Backtesting": data-mining demo where the best of 498 momentum rules on a no-edge simulated market makes +11% in-sample, then −28% out-of-sample, plus classic backtest mistakes
- **Link:** https://www.instagram.com/p/DeWlPe2id2c/
- **Account:** @quantfinancetogo · **Posted:** 2026-10-11 (decoded from the shortcode) · **Type:** reel (97.7s; animated explainer, 2 scene pages + continuous animation reviewed at 2 fps)
- **Caption source:** possibly truncated (mirror)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct, honest lesson on overfitting and data mining. The numbers reproduce exactly from the shown code.

### Post description
> ➡️ Quantitative Finance From Scratch, Part 20: Backtesting.
>
> A backtest tests a trading strategy on historical data, as if you had used it back then, to see whether it would have made money and how much risk it took along the way. Portfolio managers,...

(Cut off by the mirror. The rest was not retrievable because Instagram returned 429.)

### Audio
Narration by the creator, condensed into timestamped notes:
- [0.0] Hook: "A trading rule can look profitable on paper and still be worthless." The video explains what backtesting is and why it matters.
- [7.1] Series title: Quantitative finance from scratch, part 20.
- [9.2] A backtest runs a trading strategy on historical data as if used back then, to see whether it would have made money and how much risk it took. Portfolio managers, analysts and quant researchers run backtests before real money goes into an idea.
- [23.9] Split the past in two: build the rule on one part (in sample), then test it on later, unseen data (out of sample); "The out of sample result is the fairer check."
- [35.4] Search the past hard enough (e.g. machine learning trying thousands of rules) and you will find patterns even in pure noise; many are statistical chance and do not repeat. Trying rule after rule until one looks good is called data mining.
- [52.6] Demo: "We test 498 rules on a simulated market with no edge at all. The best one makes 11% in sample," and loses 28% on unseen data.
- [64.2] Even a properly backtested result only describes the past; markets change, so a long-working pattern can stop working.
- [71.3] Classic mistakes: look-ahead bias (using information not known at the time), survivorship bias (testing only companies that still exist), and leaving out trading costs (makes every rule look better).
- [86.6] Conclusion: a backtest "only tells the truth when it never sees the future, includes the cost, and holds up on data it has never seen."
- [94.0] CTA: "Follow to really learn quantitative finance."

### On-screen content, page by page
Constant frame: "QUANT FINANCE FROM SCRATCH PART 20 / **Backtesting** / testing a rule on the past", series bar 13–21 with 20 highlighted, footer "simulated market, assumed numbers · education only · not financial advice".

- **0–6s (hook):** "**+25%** best rule, first 5 years · in sample" over a fan of equity curves ("498 rules on a simulated market with no edge · 167 drawn"; year 1 → year 5). This is the leader's peak partway through the run. It then becomes "**+11%** in sample · rank 1 → **−28%** out of sample · rank 460", "BEST OF 498 RULES", "**RANK 460 OF 498 RULES**" (year 1 → 5 → 10), then a "KEY IDEA – BACKTESTING – testing a trading rule on the past" card.
- **~10–17s:** "a backtest · a rule on historical data": "historical data · simulated price, 10 years", "HISTORICAL DATA / AS IF BACK THEN", "one rule, played day by day".
- **~20s:** "before real money · managers, analysts, quants": PORTFOLIO MANAGERS / ANALYSTS / QUANT RESEARCHERS → IDEA.
- **~25–33s:** "split the past in two · build in sample": "BUILD THE RULE HERE" (years 1–5), with years 5–10 shaded.
- **~35–52s:** "many rules, one past · a market with no edge": "rules tried: 15 … 410 … **498**", "best so far: **+11%**", "MACHINE LEARNING: THOUSANDS OF RULES", "PURE NOISE: A MARKET WITH NO EDGE", "first 5 years · the same past for every rule". Then "new data" with all the top rules turning red: "**ON NEW DATA: −18.5% ON AVERAGE**".
- **~55–64s:** "498 rules · simulated, no edge" and "BEST IN SAMPLE: +11%". Terminal: "**498 rules, best: rise 36 days**". Caption "best in sample: +11% · first 5 years".
- **~64–71s:** "only the past · markets change": a sine "A PATTERN THAT WORKED FOR YEARS" then noise that "STOPS WORKING" ("later · a changed market"; labeled schematic).
- **~71–86s:** "classic mistakes · look-ahead, survivors, costs", three panels:
  - **LOOK-AHEAD BIAS** ("today / tomorrow – used before it was known")
  - **SURVIVORSHIP BIAS** ("only the survivors"; grid of crossed-out squares)
  - **TRADING COSTS** ("without costs it looks better")
- **~86–98s:** "Backtesting – honest only on unseen data", "in sample +11% · out of sample −28%", with the checklist "✓ never sees the future ✓ includes the costs ✓ holds up on unseen data", then "follow to really learn quant finance".

Final code (`mining.py`, 17 lines), excerpt:
```
rng = np.random.default_rng(20)
ret = rng.normal(0, .01, 2520)          # 10 years, no edge
price = np.cumprod(1 + ret)
d = np.arange(251, 2520)                # same days for all rules
n = (d < 1260).sum() - 1                # in sample: 5 years
for look in range(2, 251):              # 2 to 250 days back
    up = price[d - 1] > price[d - 1 - look]
    for kind, hold in ("rise", up), ("fall", ~up):
        g = np.cumprod(1 + ret[d] * hold)
        test[kind, look] = g[n], g[-1] / g[n]
```
The omitted lines import numpy, create the empty `test` dict, pick the rule with the highest in-sample growth (`max(test, key=lambda r: test[r][0])`) and print the rule count, the best rule's kind and lookback ("… rules, best: … days"), then its in-sample and out-of-sample returns as signed percentages. Parameters: seed 20, daily returns N(0, 0.01) over 2,520 days (10 years), lookbacks 2–250 days, "rise" and "fall" variants (498 rules), in sample = first 1,260 days. Printed result: "498 rules, best: rise 36 days", in sample +11%, out of sample −28%.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| 498 rules (249 lookbacks × "rise"/"fall") | number | audio 54s; screen | Correct count from the code |
| Best rule "rise 36 days": +11% in-sample, −28% out-of-sample, rank 460/498 | numbers | audio; screen | Reproduced exactly with the shown code (seed 20) |
| "On new data: −18.5% on average" (top rules) | number | screen ~50s | Shown on screen. Not separately recomputed. |
| In-sample / out-of-sample, data mining, look-ahead bias, survivorship bias, trading costs | concepts | audio; screen | Standard and correctly defined |

### What's being promoted / the funnel decoded
No funnel. The only CTA is "Follow to really learn quantitative finance". There is no link, product or comment keyword. Same series as DeY9P8_CpfW (Part 21) and DeSWK28Re6i (Part 18).

### Verification & insights
- I re-ran my own transcription of the on-screen code and got "498 rules, best: rise 36 days, in sample +11%, out of sample −28%", identical to the video. The rules use only past prices (`price[d-1]` vs `price[d-1-look]`), so the demo itself has no look-ahead bias.
- One nuance: the simulated market has no drift and no edge, so a −28% out-of-sample result is also just noise. The lesson is that the in-sample winner tells you nothing, not that it will systematically lose.
- This is a useful counterweight to posts in this batch that show unvalidated "winning" ML backtests (for example DeYY5HZE0o8's mock +312%).
- Not verified: the rest of the cut-off caption.

---

<a id="e-dewmjvvoyz0"></a>

## DeWMjVvoYZ0 | @neuron.machinelearning | "8 Algorithms You Need": eight scikit-learn classifiers on the same make_moons data with test accuracies (linear 80.0% to neural net 90.8%) and full code
- **Link:** https://www.instagram.com/p/DeWMjVvoYZ0/
- **Account:** @neuron.machinelearning (brand "NEURON.") · **Posted:** 2026-10-11 (decoded from the shortcode) · **Type:** reel (45.1s; animated explainer, 1 scene page + continuous animation reviewed at 2 fps)
- **Caption source:** possibly truncated (mirror)
- **Category:** Quant & data (ML education)
- **Verdict:** LEGIT & FREE. An accurate, honest comparison on a toy dataset with complete, runnable code. Nothing is sold.

### Post description
> 8 machine learning algorithms. Same data. Same test. 🧠
>
> Linear and logistic regression draw one straight line: ~80%.
> KNN, SVM, trees, forests, boosting and neural networks bend the boundary: up to 90.8%.
>
> Every boundary in this video is real, compute...

(Cut off by the mirror. The rest was not retrievable because Instagram returned 429.)

### Audio
Narration by the creator (burned-in word-by-word subtitles match), word for word:
- [0.0] "Eight algorithms you need to know. Same data, same test."
- [4.0] "Linear regression draws one straight line."
- [7.0] "Logistic regression turns it into a probability."
- [11.0] "K-nearest neighbors asks its 15 closest points." (Whisper wrote "Canearest".)
- [15.0] "An SVM finds the widest possible margin."
- [19.0] "A decision tree asks yes or no questions, boxes."
- [23.0] "A random forest lets 100 trees vote."
- [26.0] "Boosting adds trees that fix the last mistakes."
- [30.0] "A neural network bends the line any way it needs."
- [33.0] "Straight lines, about 80%. The flexible ones, up to 91."
- [39.0] "No best algorithm, only the right one for your data."
- [42.0] "Follow for more."

### On-screen content, page by page
Constant header: "NEURON. · SCIKIT-LEARN · MACHINE LEARNING · ALGORITHMS · **8 Algorithms *You Need***". A 4×2 grid of decision-boundary plots (two-moons data, blue vs orange) fills in one panel at a time, with a code editor `eight_algos.py` typing below.
- **0–4s:** Title, grid outline.
- **4–7s:** Linear Regression, labeled "one straight line".
- **7–11s:** Logistic Regression, labeled "soft = unsure" (a probability shading).
- **11–15s:** K-Nearest Neighbors (curved boundary).
- **15–19s:** SVM (circle highlight, curved boundary).
- **19–23s:** Decision Tree, with a box-shaped boundary and an example split "x < a? y > b?".
- **23–26s:** Random Forest, with a small tag "[number unreadable at this resolution] trees vote" (the narration says 100, which is the scikit-learn default).
- **26–30s:** Boosting.
- **30–33s:** Neural Network.
- **33–39s:** Accuracy badges appear (red for the straight-line models, green for the rest): **Linear 80.0% · Logistic 81.6% · KNN 90.4% · SVM 89.2% · Decision Tree 88.4% · Random Forest 88.8% · Boosting 88.8% · Neural Network 90.8%**. Subtitles: "Straight lines: about eighty percent."
- **39–42s:** "No best algorithm. Only the right one for your data." The terminal shows `$ python eight_algos.py` with the same 8 scores.
- **42–45s:** End card "NEURON – **Follow for more** – DAILY ML VIDEOS WITH REAL CODE".

Code on screen (18 lines), excerpt:
```
X, y = make_moons(1000, noise=0.3, random_state=0)
Xtr, Xte, ytr, yte = train_test_split(X, y, random_state=0)
mlp = nnet.MLPClassifier((32, 32), max_iter=2000, random_state=0)
models = {
  "linear":   lm.RidgeClassifier(),        # least squares
  ...
  "neural":   mlp}
for name, m in models.items():
    print(f"{name:9} {m.fit(Xtr, ytr).score(Xte, yte):.1%}")
```
The omitted lines are four scikit-learn imports (`make_moons`, `train_test_split`, `linear_model as lm`, `neighbors`, `svm`, `tree`, `ensemble as ens`, `neural_network as nnet`) and six more model entries: `"logistic": LogisticRegression()`, `"knn": KNeighborsClassifier(15)`, `"svm": SVC()`, `"tree": DecisionTreeClassifier(max_depth=5)`, `"forest": RandomForestClassifier(random_state=0)`, `"boosting": GradientBoostingClassifier(random_state=0)`. The loop fits each model on the training split and prints its test accuracy: linear 80.0%, logistic 81.6%, knn 90.4%, svm 89.2%, tree 88.4%, forest 88.8%, boosting 88.8%, neural 90.8%.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| scikit-learn | library | screen tag; code | Real, free (BSD). All the classes used exist with these arguments. |
| make_moons(1000, noise=0.3) | dataset | code | A synthetic 2-D toy dataset, not real-world data |
| "Linear regression" = RidgeClassifier | model | code; audio | Least-squares classification. Fair to call it a linear-regression classifier. |
| 8 accuracies (80.0 / 81.6 / 90.4 / 89.2 / 88.4 / 88.8 / 88.8 / 90.8%) | numbers | screen; caption ("~80%", "up to 90.8%") | Consistent with the caption. Not re-run because scikit-learn is not installed in this environment. Plausible for this noise level. |
| "100 trees vote" | detail | audio 23s | Correct: the scikit-learn default is n_estimators=100. |

### What's being promoted / the funnel decoded
No funnel. The CTA is "Follow for more – daily ML videos with real code". There is no link, comment keyword or product in the visible material. Same creator as DeRNXXMoH-- (neural network from scratch, Part 1).

### Verification & insights
- The code is complete and uses standard scikit-learn APIs. The results could not be re-run because scikit-learn is not installed here.
- The fair caveat is spelled out ("No best algorithm"). On a 2-D toy set, the 1–2 point differences between KNN, SVM, forest and MLP are within noise for a 250-point test split.
- Not verified: the rest of the cut-off caption ("Every boundary in this video is real, compute…").

---

<a id="e-defcbkaivma"></a>

## DeFCbkaiVMa | @quantfinancetogo | "Quant Finance from scratch" Part 14: market beta explained with a simulated market, three stocks (beta 0.5/1/2) and a 13-line numpy script
- **Link:** https://www.instagram.com/p/DeFCbkaiVMa/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-04 · **Type:** reel (118s, about 9 animated pages; scene detection caught only 1, so pages were reconstructed from the 2-fps frames)
- **Caption source:** full (Instagram, re-fetched with yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – a correct textbook explanation of beta (Cov/Var), the Fama-French factors and the CAPM link, using honest simulated data; nothing is sold

### Post description
> ➡️ Quant Finance from scratch part 14: market beta
>
> Step 1, a simulated market and three stocks: the market moves about 1 % on a typical day (15.9 % a year). Three stocks follow it with betas of 0.5, 1 and 2, each with its own random push of 0.7 % a day.

- **Step 2, beta in plain words:** a stock's sensitivity, or exposure, to the market factor, and a measure of risk, because it shows how strongly the stock swings relative to the market, in step with it. On the **122,149** simulated days when the market fell about 1 %, the three stocks fell **0.5 %, 1.0 % and 2.0 %** on average; on days it rose about 1 % they rose as much.
- **Step 3, the slope:** plot every day with the market's move across and the stock's move up. Beta is the slope of the best-fit line, computed as **Cov(stock, market) / Var(market)**. Over **10,000** simulated years it measures **0.50, 1.00 and 2.00**, exactly the built-in betas. Real betas have to be estimated like this from past returns.
- **Step 4, many betas:** a factor model gives one beta per factor. The Fama–French three-factor model (Journal of Financial Economics, **1993**) adds firm size and book-to-market (value) to the market factor; later videos cover them. In everyday use "beta" almost always means the market beta.
- **Why it matters:** in Part 11, mixing many assets averaged their own pushes away while the shared market swing stayed. Beta measures how much of this systematic risk a stock carries, so a big equal mix of beta-2 stocks still swings about twice as much as the market.
- **CAPM** (William Sharpe, Journal of Finance, **1964**): higher beta means higher expected return; that is the next episode.
- "This video is for education only, and nothing in it is financial advice."
- **Hashtags:** #quantfinance #beta #capm #finance python

*Caption condensed – full text is on the original post.*

### Audio
Creator voice-over (English, about 230 words; condensed timestamped notes with key lines quoted):
- [0.0–10.7] Hook: "What does the Greek letter beta mean in finance?" It is one symbol but tells you a lot about risk. "Quantitative finance from scratch, part 14."
- [11.6–21.5] Definition: "Beta is a stock's sensitivity or exposure to the market factor and a measure of risk", showing how strongly the stock swings relative to the market, in step with it.
- [21.5–32.3] The simulated market "moves about 1% on the typical day", and three stocks follow it "with built-in betas of a half, one and two. Each with its own random push."
- [32.3–45.2] When the market falls 1%, the beta-2 stock "falls about 2% on average and one with a beta of a half only about half a percent". It works the same way on up days.
- [45.2–66.2] Put every day on a map (market across, stock up). "Each stock forms a tilted cloud and the slope of the line that fits it best is its beta." The program computes it as the covariance of stock and market divided by the market's variance; over 10,000 simulated years it measures exactly the built-in betas (0.5, 1 and 2).
- [66.2–79.1] There is a beta for every factor, and "the model of Fama and French adds betas for company size and value", to be covered in later videos. Plain "beta" almost always means the market beta.
- [79.1–100.9] Why it matters: in Part 11, mixing assets averaged away their own pushes, but the shared market swing stayed. Beta measures how much of that swing a stock carries, so "even a big mix of beta two stocks swings about twice as much as the market does." In the CAPM, "the higher the beta, the higher the expected return", which is the next episode.
- [100.9–116.6] Recap: beta is "how strongly a stock moves with the market", so a beta of two means about twice the market's move. It matters because it shows how much of the market's risk you carry, "the one risk no diversification can remove". CTA: "Follow to really learn quantitative finance."

### On-screen content, page by page
Every page has the same frame. The header reads "QUANT FINANCE FROM SCRATCH" with "PART 14" at top right, below it a row of episode tabs 13–21 with 14 highlighted, and a code editor pane titled `beta.py` in the bottom half. The footer on every page reads "simulated stocks · education only · not financial advice". Each page also has a caption bar with a left label and a right label.
**Page 1 (0–8s):** Title "What Beta Means", subtitle "one market, three simulated stocks". A scatter-cloud animation, then a glowing β symbol. Card: "KEY IDEA – Beta". Bar: "one market, three stocks" / "market across, stock up". The editor behind the card shows the finished code.
**Page 2 (~8s):** Intro card "QUANTITATIVE …" (series title animation, with a small price-line graphic).
**Page 3 (12–32s):** Title "Beta", subtitle "how strongly a stock moves with the market". Tags: "SENSITIVITY", "EXPOSURE TO THE MARKET", "A MEASURE OF RISK". Animated price paths (y-axis 90–110 around 100) for market, beta 0.5, beta 1 and beta 2. Bars: "sensitivity to the market / simulated day 6 … 55", then "market, then betas 0.5, 1, 2 / simulated day 79 … 104". The code is typed line by line (the full code is under page 9).
**Page 4 (32–45s):** Strip plots on a −2% to +2% axis. "the market falls 1 %": market −1.0%, beta 0.5 −0.5%, beta 1 −1.0%, beta 2 −2.0% (bars "on average" / "beta 2: about −2 %"). Then "the market rises 1 %" with the label "122,550 DAYS THE MARKET ROSE ABOUT 1 %": +1.0%, +0.5%, +1.0%, +2.0% ("beta 2: about +2 %"). Code lines 9–10 (the d and u lines) are highlighted.
**Page 5 (45–54s):** "every day is a dot" with "market across, stock up". Three scatter clouds (beta 0.5, beta 1, beta 2), x-axis "across: market's move", y-axis "up: stock's move". Fitted white lines are then added, with the bar "slope of the best line = beta".
**Page 6 (54–66s):** Formula card "β = Cov(stock, market) / Var(market)", with "Cov: moving together" and "Var: market alone" shown as bar pairs. Results "= 0.50", "= 1.00", "= 2.00". Bar: "beta = Cov / Var" with "over 10,000 simulated years", then "measured 0.50, 1.00, 2.00". Console output:
```
> beta  measured  -1 % day  +1 % day
> 0.5   0.50      -0.5%     +0.5%
> 1     1.00      -1.0%     +1.0%
> 2     2.00      -2.0%     +2.0%
```
**Page 7 (66–79s):** "one beta per factor" with "market, size, value". A diagram connects market, size and value to "stock" through arrows labelled "β market", "β size" and "β value". Labels: "FAMA AND FRENCH, 1993: MARKET, SIZE, VALUE" and "LATER VIDEOS: SIZE AND VALUE".
**Page 8 (79–100s):** "the risk that stays" with "own pushes average away". A beta-2 scatter beside an inset "part 11: risk of a mix" (a decaying curve labelled "the market part stays"). Lines "2x" and "1x", with "market part only". Bars "market swing" against "big mix of beta 2 stocks", labelled "2x" and "beta 2: about 2x the market". Then a "CAPM" tag with "higher beta, higher expected return".
**Page 9 (100–118s):** Title "What Beta Means", subtitle "the slope of a stock against the market". Box "WHAT DOES BETA MEAN?": "1 How strongly it moves with the market." "2 Beta 2: about twice the market's move." "3 The risk no mix can remove." Bars "the answer" with "how strongly, with the market", then "the risk no mix removes", then "follow to really learn quant finance".

Final code shown in `beta.py` (read from the frames):
```python
import numpy as np
rng = np.random.default_rng(14)
n = 10000 * 252                                   # 10,000 years
m = rng.normal(0, 0.01, n)                        # the market
print("beta  measured  -1 % day  +1 % day")
for b in (0.5, 1, 2):                             # built-in beta
    own = rng.normal(0, 0.007, n)                 # own push
    s = b * m + own                               # the stock
    d = s[abs(m + 0.01) < 0.001].mean()           # -1 % day
    u = s[abs(m - 0.01) < 0.001].mean()           # +1 % day
    cov = ((s - s.mean()) * (m - m.mean())).mean()
    beta = cov / m.var()                          # the slope
    print(f"{b:<6}{beta:<10.2f}{d:+.1%}{u:+10.1%}")
```

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Beta = Cov(stock, market) / Var(market) | formula | caption Step 3, audio 54–60s, page 6 | The standard OLS slope definition of market beta. Correct. |
| Market sd 1%/day = 15.9%/yr | number | caption, audio, code (`0.01`) | 0.01 × √252 = 15.87%. Correct. |
| Betas 0.5, 1, 2; own push 0.7%/day | parameters | caption, code | Simulation inputs. |
| 10,000 simulated years (10000 × 252 days) | parameter | caption, page 6, code | Simulation length. |
| 122,149 days market fell ~1%; 122,550 days market rose ~1% | number | caption (fell); page 4 (rose) | Counts of simulated days with the market within ±0.1% of −1% or +1%. Plausible: about 4.8% of 2.52M normal draws fall in each window. |
| Measured 0.50 / 1.00 / 2.00; −0.5/−1.0/−2.0% and +0.5/+1.0/+2.0% | results | page 6 console, caption | These follow from the construction. |
| Fama & French three-factor model (J. Financial Economics, 1993) | paper | caption, audio, page 7 | Real: Fama & French, "Common risk factors in the returns on stocks and bonds", JFE 33 (1993). Factors are market, size (SMB) and value (HML, book-to-market). |
| CAPM, William Sharpe (J. of Finance, 1964) | paper | caption, page 8 | Real: Sharpe, "Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk", J. Finance 19(3), 1964. |
| "Part 11" (risk of a mix / diversification) | series reference | caption, audio, page 8 | An earlier episode in the same series (not reviewed here). |
| numpy (`np.random.default_rng(14)`) | library | code | Standard Python library. Seed 14 = the episode number. |
| @quantfinancetogo | handle | account | Educational quant-finance reel series. No product is visible. |

### What's being promoted / the funnel decoded
No funnel. The only call to action is "Follow to really learn quantitative finance". Nothing is sold, no comment keyword is used and no link is given. A web search found no product or course tied to the account.

### Verification & insights
- The math was checked and is correct. Beta is the regression slope Cov/Var. The annualisation 1% × √252 ≈ 15.9% is right. A portfolio of beta-2 stocks keeps beta 2, so its systematic volatility is about twice the market's.
- Both citations are accurate (Fama-French 1993 JFE; Sharpe 1964 J. Finance).
- Caveat the video states itself: the betas are built in, so recovering them exactly is by construction. Real betas are estimated with noise, drift over time, and depend on the window, the frequency and the market proxy.
- The seed and code are fully shown on screen, so the result can be reproduced. This entry does not run it.
- The "122,149" figure in the caption (fell) and "122,550" on screen (rose) are two different counts, not a contradiction.
- Same series as DeG3qGCirGO (Part 15, the CAPM).

---

<a id="e-dernxxmoh--"></a>

## DeRNXXMoH-- | @neuron.machinelearning | "Let's build a neural network from scratch, Part 1/10: The Neuron": a "ride my bike?" neuron (inputs 1.0/0.7/0.0, weights 0.8/0.5/−1.5, bias −0.4 → 0.75; rain → −0.75) with numpy code
- **Link:** https://www.instagram.com/p/DeRNXXMoH--/
- **Account:** @neuron.machinelearning (brand "NEURON.") · **Posted:** 2026-10-09 (decoded from the shortcode) · **Type:** reel (45.1s; animated explainer, 1 scene page + continuous animation reviewed at 2 fps)
- **Caption source:** possibly truncated (mirror)
- **Category:** Quant & data (ML education)
- **Verdict:** LEGIT & FREE. A correct beginner explainer of a single neuron (weighted sum plus bias). The arithmetic checks out. No funnel.

### Post description
> Let's build a neural network from scratch. 🧠 Part 1/10: the neuron.
>
> Should I ride my bike today?
>
> ■ Inputs: sunny 1.0 · warm 0.7 · rain 0.0
> ■ Weights: how much each input matters (rain: −1.5!)
> ■ Bias: the neuron's baseline mood (−0.4)
> ■ Multiply, ad...

(Cut off by the mirror. The rest was not retrievable because Instagram returned 429.)

### Audio
Narration by the creator (burned-in subtitles match), word for word:
- [0.0] "Let's build a neural network from scratch. 10 parts, part one, the neuron."
- [6.0] "A neuron takes a few inputs and turns them into one number."
- [10.9] "Should I ride my bike today? Sunny 1, warm 0.7, rain 0."
- [17.1] "Each input gets a weight. How much it matters? Rain matters a lot and negatively."
- [23.4] "Plus a bias, the neuron's baseline mood."
- [27.5] "Multiply, add it all up. And we get 0.75. Positive, let's ride."
- [34.3] "Now it rains, minus 0.75. Stay home."
- [39.5] "That's one neuron."
- [40.8] "Part two, why it needs an activation function."

### On-screen content, page by page
Constant header: "NEURON. · PART 1/10 · LET'S BUILD A NEURAL NETWORK · FROM SCRATCH · **The *Neuron***".
- **0–5s (hook):** The finished diagram. Inputs 1.0 (sunny ☀), 0.7 (warm 🌡), 0.0 (rain ☁), with weights ×0.8, ×0.5, ×−1.5 into Σ, bias "b = −0.4", output **0.75** → green "**RIDE ✓**". The full code is shown.
- **~5–10s:** Diagram builds. Caption "many inputs → one number". Σ shows **−0.40** (bias only).
- **~13–17s:** "Sunny: one. Warm: point seven. Rain: zero." Code line `inputs = [1.0, 0.7, 0.0]  # sunny, warm, rain`.
- **~17–23s:** Weights drawn (rain edge in red). "Rain matters a lot, and negatively." Code `weights = [0.8, 0.5, -1.5]  # how much each matters`.
- **~23–27s:** "the neuron's baseline mood". `bias = -0.4  # baseline mood`.
- **~27–34s:** "and we get zero point seven five". Box "WEIGHTED SUM z = Σᵢ wᵢxᵢ + b". Terminal `$ python neural_net.py` → `0.75`, then `0.7499999999999999` (np.dot version).
- **~34–39s:** Rain input switches to 1.0. A worked line "1·0.8 + 0.7·0.5 + 1·(−1.5) − 0.4 = −0.75". Σ shows **−0.75** → red "**STAY HOME**". Terminal adds `-0.7500000000000001`.
- **~39–41s:** "That's one neuron."
- **~41–45s:** End card "NEXT · PART 2 – **Activation functions** – FOLLOW THE SERIES · 10 PARTS".

Full code on screen (`neural_net.py`):
```
import numpy as np
# Part 1: a single neuron
inputs  = [1.0, 0.7, 0.0]          # sunny, warm, rain
weights = [0.8, 0.5, -1.5]         # how much each matters
bias    = -0.4                     # baseline mood
output = bias
for x, w in zip(inputs, weights):
    output += x * w                # weigh every input
print(output)
print(np.dot(inputs, weights) + bias)     # same, one line
inputs[2] = 1.0                           # now it rains
print(np.dot(inputs, weights) + bias)
```

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Neuron = weighted sum + bias, z = Σ wᵢxᵢ + b | concept | audio; screen | Correct (a perceptron or linear unit before activation) |
| 0.8·1 + 0.5·0.7 − 1.5·0 − 0.4 = **0.75**; with rain = **−0.75** | numbers | audio; screen; caption | Arithmetic checked by hand. Correct. The floating-point outputs 0.7499999999999999 and −0.7500000000000001 are normal float rounding. |
| numpy (np.dot) | library | code | Real |
| Part 2: activation functions; 10-part series | series | end card; audio 40.8s | The creator's upcoming episodes |

### What's being promoted / the funnel decoded
No funnel. The CTA is "follow the series · 10 parts". There is no link, keyword or product. Same creator as DeWMjVvoYZ0.

### Verification & insights
- The math and code are correct. Strictly, "positive → ride" already acts as a step-activation threshold, which is what Part 2 is set up to explain.
- This is standard beginner material. The same content is in free resources such as 3Blue1Brown's neural network series and Karpathy's "micrograd".
- Not verified: the rest of the cut-off caption.

---

<a id="e-deg3qgcirgo"></a>

## DeG3qGCirGO | @quantfinancetogo | "Quant Finance from scratch" Part 15: the CAPM derived from a simulated market (8 stocks, betas 0 to 1.4) with a 16-line numpy script
- **Link:** https://www.instagram.com/p/DeG3qGCirGO/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-05 · **Type:** reel (94.5s, about 10 animated pages; scene detection caught only 1, so pages were reconstructed from the 2-fps frames)
- **Caption source:** full (Instagram, re-fetched with yt-dlp after one 429)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – a correct explanation of the CAPM with honest assumed numbers and accurate Nobel and paper citations; nothing is sold

### Post description
> ➡️ Quant Finance from scratch part 15: the CAPM (Capital asset pricing model)
>
> There is a lot of discussion in science ongoing whether it is still a good estimate for expected returns or too simple with just 1 factor (market). Still its crucial to understand the concept itsself.

- **Step 1, simulated market (assumed numbers, not forecasts):** risk-free asset pays **3 %** a year; the market pays **5 %** more on average, with swings of **15.9 %** a year.
- **Step 2:** eight stocks with betas from **0 to 1.4**, each also with swings of its own, unrelated to the market.
- **Step 3, two of them:** beta **0.4** with big own swings (**20 %**) and beta **1.2** with small ones (**9 %**). Both swing about **21 %** a year in total, yet earned **5.3 %** and **9.3 %** on average.
- **Step 4, mixing:** a mix of **100** stocks like the first still earns **5.1 %** but swings only **6.7 %**. As in Part 11, own swings average out in a mix while the market's swing stays; beta measures the asset's sensitivity to market movements.
- **Step 5, the line:** the eight average returns lie on a straight line against beta, **3.1 % + 5.1 %** per step of 1 in beta. That is the CAPM equation: "expected return = risk-free rate + beta x (market's expected return - risk-free rate)". For beta 1.2 it gives 3 % + 1.2 × 5 % = **9 %**, close to the 9.3 % measured.
- **Nobel:** Sharpe shared the **1990** Nobel Memorial Prize in Economic Sciences with Harry Markowitz and Merton Miller, his part for the theory of asset pricing (the CAPM). The committee notes several researchers developed it independently in the mid-1960s and names his essay "Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk" (Journal of Finance, **1964**) as his pioneering achievement.
- "This video is for education only, and nothing in it is financial advice."
- **Hashtags:** #quantfinance #capm #beta #finance python

*Caption condensed – full text is on the original post.*

### Audio
Creator voice-over (English, about 270 words; condensed timestamped notes with key lines quoted):
- [0.0–9.1] Hook: "William Sharp[e] won a Nobel Prize for this equation. It links a stock's risk to the return you can expect." "Quantitative finance from scratch, part 15."
- [9.1–23.3] Simulated market: a risk-free asset pays 3% a year and the market 5% more, with swings of about 16%. Eight stocks follow it with betas from zero to 1.4, plus own swings unrelated to the market.
- [23.3–37.7] Two stocks: beta 0.4 with big own swings and beta 1.2 with small ones. Both swing about 21%, "yet the high beta one earns about 9%, the low beta one only 5%."
- [37.7–50.1] As Part 11 showed, own swings average out in a mix: 100 stocks like the low-beta one still earn 5% but swing only 7, so those swings "earn nothing extra", while the market swing stays, which is what beta measures.
- [50.1–68.1] All eight on a map (beta across, return up) land on a straight line from 3%, rising 5% per step of beta. "That is the CAPM equation": expected return equals the risk-free rate plus beta times the market's extra return.
- [68.1–83.4] "A beta of 1.2 gives 9%, close to what we measured." The CAPM gives a single stock's expected return from its beta, meaning its average over many years. Here the rule was built in; "Real betas and returns must be estimated from data."
- [83.4–93.3] Recap: own swings can be mixed away, "so only beta gets paid", and expected return is a straight line in beta. CTA: "Follow to really learn quantitative finance."

### On-screen content, page by page
Every page has the same frame. The header reads "QUANT FINANCE FROM SCRATCH" with "PART 15" at top right, below it a row of episode tabs 13–21 with 15 highlighted, and an editor pane titled `capm.py`. The footer on every page reads "simulated stocks, assumed numbers · education only · not financial advice".
**Page 1 (0–8s):** "The Nobel Prize Equation", subtitle "eight simulated stocks, one line". Formula "E(R) = R_f + β(R_m − R_f)". A strip chart of expected return (0–10%) against beta (0, 0.5, 1.0) with a line through the eight clouds. Card "KEY IDEA – CAPM – Capital Asset Pricing Model". Bar: "eight stocks, one line" with "beta across, return up".
**Page 2 (~8–12s):** Card "QUANTITATIVE FINANCE FROM SCRATCH", "PART 15 · THE CAPM".
**Page 3 (12–20s):** "The CAPM", subtitle "expected return from beta". Tag "SIMULATED · ASSUMED NUMBERS". Tiles "3 % risk-free", "+5 % more on average" and "16 % swings a year", over an animated bar chart of yearly returns. Bar: "a simulated market" with "risk-free 3 %, market +5 %".
**Page 4 (20–23s):** "MARKET PART" grid of rows: market, β 0, β 0.2, β 0.4, β 0.6, β 0.8, β 1.0, β 1.2, β 1.4. Bar: "eight stocks follow it" with "betas 0 to 1.4".
**Page 5 (23–37s):** "two of the eight stocks" with "beta 0.4 and beta 1.2". Two boxes split into market and own bars, labelled "BETA 0.4" and "BETA 1.2". Console "> risk 21% 21%" with "both swing about 21 %". Then "> return 5.3 % 9.3 %", green return bars "5.3 %" and "9.3 %", and the bar "same risk, different return" with "return 5.3 % against 9.3 %".
**Page 6 (37–50s):** "own swings average out" with "as in part 11". The risk curve falls against stocks in the mix (1, 10, 50, 100). "4 stocks" gives "12 %". "100 stocks like the low beta one" gives "7 %" risk and "5.1 %" return. Console "> mix 7% 5.1%". Bars "a mix of 100 stocks" with "swing 7 %, return 5.1 %", then "the market part stays" with "what beta measures".
**Page 7 (50–60s):** "eight stocks on one map" with "beta across, return up". Eight dots from about 3% at beta 0 to about 10% at beta 1.4. Console "> line 3.1% + 5.1% x beta". Bar "a line from 3 %, +5 % per beta"; the 3% intercept is marked.
**Page 8 (60–72s):** Box "THE CAPM EQUATION": "expected return = risk-free rate + β × market's extra return". Tiles "3 % risk-free rate" and "5 %" (market's extra return). Then "BETA 1.2" with the bar "beta 1.2 gives 9 %".
**Page 9 (72–83s):** "E(R) = R_f + β(R_m − R_f)". Example "β 0.8 → 7.0 %" on the line. Bars "expected return from beta" with "for any single stock", then "in real markets" with "estimated from data" (noisy dots around the line).
**Page 10 (83–94s):** "The Nobel Prize Equation", subtitle "where the equation comes from". Box "WHERE DOES THE EQUATION COME FROM?": "1 Own swings can be mixed away." "2 Only beta gets paid." "3 Expected return is a straight line in beta." Bars "the answer" with "only beta gets paid", then "follow to really learn quant finance".

Final code shown in `capm.py` (read from the frames; 16 lines). Excerpt of the core logic:
```python
safe, premium, swing, years = .03, .05, .159, 10000
beta = np.arange(8) / 5                      # eight betas
own_swing = [.18, .1, .2, .06, .15, .12, .09, .05]
market = rng.normal(premium, swing, years)
own = rng.normal(0, own_swing, (years, 8))
stocks = safe + beta * market[:, None] + own
ret, risk = stocks.mean(0), stocks.std(0)
slope, start = np.polyfit(beta, ret, 1)
mix_own = rng.normal(0, own_swing[2], (years, 100))
mix = safe + beta[2] * market + mix_own.mean(1)
```
The rest: the first two lines import NumPy and seed the generator with `np.random.default_rng(15)`. Four print lines then output the risk of stocks 2 and 6 (`risk {risk[2]:.0%} {risk[6]:.0%}`, shown on screen as "risk 21% 21%"), their returns (`return {ret[2]:.1%} {ret[6]:.1%}`, "return 5.3 % 9.3 %"), the 100-stock mix's swing and return (`mix {mix.std():.0%} {mix.mean():.1%}`, "mix 7% 5.1%") and the fitted line (`line {start:.1%} + {slope:.1%} x beta`, "line 3.1% + 5.1% x beta").

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| CAPM: E(R) = R_f + β(R_m − R_f) | formula | caption, audio, pages 1/8/9 | The standard Capital Asset Pricing Model. Correctly stated. |
| Risk-free 3%, premium 5%, market swing 15.9%/yr, 10,000 years | parameters | caption, page 3, code | Assumed inputs, explicitly not forecasts. |
| 8 betas 0, 0.2 … 1.4; own swings .18, .1, .2, .06, .15, .12, .09, .05 | parameters | code, page 4 | Simulation inputs. |
| Beta 0.4 (own 20%) / beta 1.2 (own 9%): risk 21% / 21%, return 5.3% / 9.3% | results | caption, page 5 | Consistent: √((0.4·0.159)² + 0.2²) ≈ 21.0% and √((1.2·0.159)² + 0.09²) ≈ 21.1%. Expected returns 5% and 9%; the sample means carry noise. |
| Mix of 100 beta-0.4 stocks: 6.7% swing (shown as 7%), 5.1% return | results | caption, page 6 | Consistent: √(0.0636² + 0.02²) ≈ 6.7%. |
| 4-stock mix: 12% risk | number | page 6 | A point on the diversification curve. |
| Fitted line 3.1% + 5.1% × beta | result | caption, page 7 | The regression recovers the built-in 3% + 5% × beta. |
| β 0.8 → 7.0% | example | page 9 | 3% + 0.8 × 5% = 7%. Correct. |
| William Sharpe; 1990 Nobel Memorial Prize with Harry Markowitz and Merton Miller | person/fact | caption, audio 0s | True. The 1990 Sveriges Riksbank Prize went to Markowitz, Miller and Sharpe, Sharpe's share for the CAPM. The audio calls it a "Nobel Prize" and the caption correctly says "Nobel Memorial Prize". |
| "Capital Asset Prices: A Theory of Market Equilibrium under Conditions of Risk", J. Finance 1964 | paper | caption | Real: J. Finance 19(3):425–442, 1964. |
| "Part 11" | series reference | caption, audio, page 6 | An earlier diversification episode. |
| @quantfinancetogo | handle | account | Educational series; also posted DeFCbkaiVMa (Part 14). |

### What's being promoted / the funnel decoded
No funnel. The only call to action is "Follow to really learn quantitative finance". There is no link, comment keyword or product.

### Verification & insights
- The numbers were recomputed from the stated parameters and the volatility figures match. The CAPM statement and the Nobel and paper facts are accurate.
- The video is honest that "the rule was built in": the stocks are generated as safe + beta × market + own. A straight line coming out is therefore by construction and does not test the CAPM.
- Empirically, the single-factor CAPM fits real data poorly. The security market line is too flat (the low-beta anomaly; Black, Jensen & Scholes 1972; Fama & French 1992). That is why multi-factor models exist. The caption itself notes the ongoing debate.
- The caption gives the mix swing as 6.7% and the screen rounds it to "7 %". The spoken "Sharp" is a transcription of "Sharpe".
- Nothing could not be verified.

---

<a id="e-derz-unoycl"></a>

## Derz_uNoyCl | @neuron.machinelearning | "Zero to ML Engineer" game-map roadmap: 4 worlds over 6 months (Python→Git→SQL→NumPy/Pandas → Linear Algebra→Statistics→scikit-learn→Validation → PyTorch→CNNs→Transformers→MLflow → FastAPI→Docker→Cloud → boss), 4 projects, "comment ROADMAP"
- **Link:** https://www.instagram.com/p/Derz_uNoyCl/
- **Account:** @neuron.machinelearning (NEURON) · **Posted:** 2026-10-19 (decoded from the post ID; not in metadata) · **Type:** reel (16.1s, 2 pages; an animated level-unlock from LVL 00/16 to 16/16)
- **Caption source:** possibly truncated (mirror). Cut off at 253 characters ("…World 2 · Classi..."). Full fetch failed (HTTP 429).
- **Category:** Quant & data (ML career/learning roadmap)
- **Verdict:** LEGIT & FREE. A sensible, standard ML-engineer curriculum. The full list is on screen, so the "comment ROADMAP" DM only adds the per-level resource links. "6 months" is optimistic for a beginner.

### Post description
> Comment “ROADMAP” and I’ll DM you the full ML Engineer roadmap, with a free resource for every level. 🎮
>
> Zero to ML Engineer in 6 months. 4 worlds, 15 levels, 1 final boss.
>
> 🟠 World 1 · Foundations: Python, Git, SQL, NumPy & Pandas
> 🟠 World 2 · Classi...

(truncated by the mirror; the rest could not be fetched)

### Audio
No speech (Whisper found 0 speech segments). Background music/sound effects only; the track is not identified on screen or in the visible caption.

### On-screen content, page by page
A game-style level map in a dark card (snake path from bottom left "START" up to "BOSS").
**Page 1 (0.0–11.6s), locked state:** progress bar "**LVL 00/16 · 0 XP**". "FINAL BOSS" in red. Every node has a padlock; a "YOU" marker sits at START. The map, bottom to top:
- **WORLD 1 · MONTH 1-2 · FOUNDATIONS:** Python (Py) → Git (git) → SQL (SQL) → NumPy & Pandas (pd)
- **WORLD 2 · MONTH 3 · CLASSIC ML:** Linear Algebra (Ax) → Statistics (σ²) → scikit-learn (sk) → Validation (CV)
- **WORLD 3 · MONTH 4-5 · DEEP LEARNING:** PyTorch (∇) → CNNs (conv) → Transformers (attn) → MLflow (log)
- **WORLD 4 · MONTH 6 · SHIP IT:** FastAPI (API) → Docker ([ ]) → Cloud (☁) → **BOSS: ship a live model**
- "**4 PROJECTS TO BUILD**": PROJECT 1 House Price Predictor · PROJECT 2 Churn Model + API · PROJECT 3 Image Classifier · PROJECT 4 Live ML System. Orange button: "**Comment "ROADMAP" for free resources**".
(Between the two pages, the 2-fps frames show the nodes unlocking one by one with check marks and the XP bar filling.)
**Page 2 (11.6–16.1s), completed state:** Header "**Zero to ML Engineer**" · "NEURON @neuron.machinelearning" · "Clear every level in 6 months, beat the boss, ship real models". Bar "**LVL 16/16 · 2000 XP**". "BOSS DEFEATED"; "YOU" at the boss node. All nodes and all 4 projects have check marks.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Python, Git, SQL, NumPy & Pandas | skills/tools | World 1; caption | Standard foundations (all free and open source) |
| Linear Algebra, Statistics, scikit-learn, Validation (cross-validation) | skills/tools | World 2 | Classic ML core. scikit-learn is the standard open-source library. |
| PyTorch, CNNs, Transformers, MLflow | skills/tools | World 3 | Deep learning (PyTorch, Meta/Linux Foundation, BSD license) plus experiment tracking (MLflow, Databricks, Apache-2.0) |
| FastAPI, Docker, Cloud | tools | World 4 | Model serving (FastAPI, MIT), containerisation, cloud deployment |
| 4 projects | list | bottom panel | House Price Predictor (regression) · Churn Model + API (classification plus serving) · Image Classifier (CNN) · Live ML System (end-to-end) |
| 16 levels / 2000 XP | numbers | progress bar | 15 skill nodes + 1 boss = 16. XP is decorative. |
| Comment "ROADMAP" | CTA | page 1 button; caption | Auto-DM with "a free resource for every level" |

### What's being promoted / the funnel decoded
"Comment ROADMAP" triggers an auto-DM with the same roadmap plus one free learning resource per level. That builds engagement and a DM list. The account's bio (per a prior review, DeQuUyPo8pR) links to its free "NEURON" machine-learning practice web app. No paid product or price was found. The full roadmap content is already captured above, so the user doesn't need to engage.

### Verification & insights
- The sequence matches common, well-regarded ML-engineer paths (e.g. the "Made With ML" MLOps course, fast.ai, roadmap.sh's AI/ML roadmaps). Free, high-quality resources per world: Python/SQL (CS50P, SQLBolt), math (3Blue1Brown, Khan Academy, "Mathematics for ML" book), classic ML (scikit-learn docs, Andrew Ng's ML Specialization, auditable for free), deep learning (fast.ai, Karpathy's Zero to Hero, PyTorch tutorials), MLOps (Made With ML, MLflow and FastAPI docs, Docker docs).
- "6 months" is a marketing number. For someone starting from zero, this list usually takes longer, especially the math. Job-ready "ML engineer" roles also tend to expect software-engineering depth and data engineering.
- Not verified: the actual resource links sent in the DM (deliberately not requested), and the rest of the caption.

---

<a id="e-derehucn9iy"></a>

## DerEhUCN9iy | @fidetolabs.math | Animated chart: fractional differencing (d = 0.24) passes the ADF stationarity test while keeping 89% of the series' memory
- **Link:** https://www.instagram.com/p/DerEhUCN9iy/
- **Account:** @fidetolabs.math (no display name returned) · **Posted:** 2026-10-19 · **Type:** reel (8.1s, one animated chart page)
- **Caption source:** full (Instagram, via yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct visual summary of a standard technique (López de Prado's fractional differentiation). It is educational, with no CTA.

### Post description
> In trading, fractional differencing makes price data stable without throwing away its long-term history. Standard models often subtract yesterday's price from today's price, which makes the data easy to analyze but wipes out all long-term price memory. Fractional differencing changes the price data just enough to pass statistical tests while keeping most of its historical trend. Traders use this tool to create models that read stable data without losing track of where prices came from.
>
> #mathforquants #mathfortraders #quanttrading

### Audio
No speech. There is a faint music or ambient track only; Whisper found 0 speech segments. The song is not identifiable.

### On-screen content, page by page
There is one page, animated from 0 to 8.1s.
- Header: "@fidetolabs.math", **"Fractional differencing"**, "KEEP THE MEMORY, PASS THE TEST", with the formula **w(k) = −w(k−1)·(d − k + 1)/k**. Legend: "THE 5% BAR" (dashed red), "ADF STATISTIC" (white), "MEMORY KEPT" (green).
- **Big counter (top left)** as d animates: "360 sessions, one series" → **97%** "of the series still there" (d = 0.12) → **66%** (d = 0.42) → **27%** (d = 0.71) → **8%** (d = 1.00; "what returns leave you") → ending at **89%** "AT 0.24 OF A DIFFERENCE".
- **Top chart:** "THE SAME SERIES, DIFFERENCED d TIMES", standardised (−3 to +3), "ONE SERIES, 360 SESSIONS". It shows how the trending price path becomes noise-like as d rises to 1.00.
- **Bottom chart:** "WHAT IT COSTS TO PASS THE TEST". The x-axis is "HOW MUCH OF A DIFFERENCE" from 0.00 to 1.00. The left axis is the ADF statistic (0 to −12) with a shaded band, "MEAN OF 150 WALKS". The right axis is memory kept (0–100%). The red dashed line is "−2.86 · THE 5% BAR". The green memory curve passes 89% at d = 0.24 (where the ADF line crosses −2.86), 54% at d = 0.50 and 8% at d = 1.00. A marker reads "d = 0.24".
- Footer: "in trading: difference a price just enough to pass, then keep the memory a whole difference throws away."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Fractional differencing | technique | caption, page | Fixed-width or expanding-window fractional differentiation, popularised for finance by Marcos López de Prado, *Advances in Financial Machine Learning* (2018), ch. 5. |
| w(k) = −w(k−1)(d − k + 1)/k | formula | page | Correct recursive weights of the binomial expansion of (1 − B)^d, with w0 = 1. |
| ADF statistic, −2.86 "5% bar" | test / number | page | Augmented Dickey-Fuller test. −2.86 is the standard 5% critical value with a constant and large sample, so it is correct. |
| d = 0.24 → 89% memory; 0.50 → 54%; 1.00 → 8% | numbers | page | "Memory kept" is probably the correlation with the original series. Computed on "150 walks" of 360 sessions, i.e. simulated data, not a real asset. |
| @fidetolabs.math | account | page | A math-for-traders explainer account. No product shown. |

### What's being promoted / the funnel decoded
Nothing. There is no CTA or link; it is a pure educational post.

### Verification & insights
- The formula and the ADF critical value are correct. The pattern (minimum d to pass ADF often well below 1, keeping high correlation to the original price) matches López de Prado's published findings, where many futures series need d below about 0.6.
- The numbers come from simulated random walks ("mean of 150 walks"). On real assets the minimum d differs per series and must be re-estimated, and using the whole sample to choose d adds look-ahead bias.
- The caption's wording ("pass statistical tests while keeping most of its historical trend") is a fair lay summary.
- Free reference implementations exist, for example in the open-source mlfinlab (older versions) or by hand with the formula shown.

---

<a id="e-dessenqi0tk"></a>

## DesSEnqI0tk | @neuron.machinelearning | "A neural network from scratch, 50 lines of NumPy": a 2-64-64-3 ReLU/softmax MLP (4,547 weights) learns 3 interleaved spirals in 2,000 steps, 34% guess to 100% train / 99.8% on 600 unseen points
- **Link:** https://www.instagram.com/p/DesSEnqI0tk/
- **Account:** @neuron.machinelearning (NEURON) · **Posted:** 2026-10-19 (decoded from the post ID; not in metadata) · **Type:** reel (50.1s, 6 scene pages plus continuous animation; read from the 2-fps frames)
- **Caption source:** possibly truncated (mirror). Cut off at 253 characters ("…Then sof..."). Full fetch failed (HTTP 429).
- **Category:** Quant & data (ML education)
- **Verdict:** LEGIT & FREE. Correct from-scratch implementation. Architecture and weight counts verified by arithmetic. The accuracy figures are plausible (not executed). The "comment code" DM is redundant because the code is on screen.

### Post description
> A neural network from scratch. No PyTorch, no TensorFlow, just 50 lines of NumPy. 🧠
>
> The task: three spirals wound into each other. No straight line can ever separate them.
>
> What happens in 2,000 steps:
> → Forward: multiply, add, ReLU, twice. Then sof...

(truncated by the mirror; the rest could not be fetched)

### Audio
Creator voice-over:
- [0.0–5.0] "A neural network from scratch. No PyTorch, no TensorFlow, 50 lines of NumPy."
- [5.8–10.0] "Three spirals, wound into each other. No straight line can ever separate them."
- [10.7–17.0] "Two inputs, two hidden layers of 64, three outputs, 4,547 random weights."
- [17.8–22.7] "Forward: multiply, add, ReLU, twice. Then softmax turns three scores into probabilities."
- [23.5–27.9] "Right now it's guessing. This point gets 34%, a coin with three sides."
- [28.7–33.0] "Backward: the error flows back through every layer. The chain rule hands each weight its share."
- [33.8–37.4] "One step downhill, then 2,000 more. Watch the boundaries bend."
- [38.2–41.5] "Inside, the network folds the plane until the spirals pull apart."
- [42.2–48.0] "99.8% on 600 points it never saw. Comment **code** for the file."

### On-screen content, page by page
Layout: "NEURON." logo, a progress bar with 8 dots, a locked badge "🔒 how accurate at the end?" (top right), a visual panel (top), and a code editor "**spiral_nn.py · 50 lines · NumPy**" (bottom) whose highlighted lines change with a "line x–y" tag.
**Page 1 (0–~5s):** Glowing network diagram. Code being typed: `import numpy as np`, `rng = np.random.default_rng(…)`, `# 1. data: three spirals wound…`, `def spirals(n=200, …`. Card "**133 neurons · 4,547 weights · pure NumPy**". Layer labels "2 in · 64 · ReLU · 64 · ReLU · 3 · softmax".
**(~5–10s) "line 5-13":** Panel "**600 points · 3 classes**": three coloured spirals (blue, orange, white). Code `def spirals(n=200, k=3, noise=0.2)` builds each arm from `r = np.linspace(0.05, 1, n)`, `t = np.linspace(c*4, (c+1)*4, n) + rng.normal(0, noise, n)`, points `(r·sin t, r·cos t)`. Then `X, y = spirals()` (training) and `X_test, y_test = spirals()` (a second, unseen draw).
**(~10–17s) "line 16-20":** `def layer(n_in, n_out): return rng.normal(0, np.sqrt(2/n_in), (n_in, n_out)), np.zeros(n_out)` (He initialisation); `W1,b1 = layer(2,64)`, `W2,b2 = layer(64,64)`, `W3,b3 = layer(64,3)`. A counter shows "2,303 random weights" while counting up, plus a heat-map thumbnail of W2.
**(~17–23s) "line 22-27":** `def forward(X)`: `h1 = max(0, X@W1+b1)`, `h2 = max(0, h1@W2+b2)`, `s = h2@W3+b3`, a stable softmax. Badges "W1 · ReLU", "W2 · ReLU", "W3 · softmax".
**Pages 2–3 (23.5–38.2s) "line 32-33":** Decision regions over the spirals: "**GUESSING · 42% right**", a probe point "**34% for the right class**", stamp "**IT'S JUST GUESSING**". Then "line 36-41" (backward pass): network glows red, gradient bars "∂L/∂W1, ∂L/∂W2, ∂L/∂W3", label "error = p − truth".
**Page 4 (38.2–42.1s) "line 29-45":** Panel "hidden layer 2 · 64 dims → 2D (PCA)" vs "input space", "step 0". Training loop highlighted.
**(~38–42s):** Trained boundaries. Side panel "**STEP 2,000 · LOSS 0.024 · TRAIN ACC 100.0%**" plus a falling loss curve.
**Page 5 (42.1–46.5s) "line 49-50":** "NEW POINTS" counter climbing ("79.6%" mid-count) to "**99.8%** · 600 never seen · step 2,000". Probe panel "same point, trained: orange 0.1% · blue 0.1% · white 99.9%".
**Page 6 (46.5–50.1s):** "spiral_nn.py · 50 lines · NumPy only" with the full lower half of the listing (lines 27–50) readable. Excerpt (≤10 lines):
```python
lr = 0.05
for step in range(2001):
    h1, h2, p = forward(X)
    loss = -np.log(p[np.arange(len(y)), y]).mean()
    d = p.copy(); d[np.arange(len(y)), y] -= 1; d /= len(y)
    dW3, db3 = h2.T @ d, d.sum(0)
    d = (d @ W3.T) * (h2 > 0)
    ...
        P -= lr * G
```
**What the full listing does (described, not copied):** generates 3 noisy spiral arms of 200 points each for train and test; He-initialises a 2→64→64→3 MLP; forward pass with two ReLU layers and a numerically stable softmax; cross-entropy loss; manual backprop (softmax-CE gradient `p − onehot`, ReLU masks `(h>0)`, `dW = hᵀ·d`, `db = Σd`); plain full-batch gradient descent at lr = 0.05 for 2,001 steps over all six parameter arrays; prints step, loss and train accuracy every 500 steps; finally prints "accuracy on 600 new points" (`test_acc` = argmax of forward(X_test) vs y_test).

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| spiral_nn.py (50 lines, NumPy only) | code | editor | The creator's script, sent by DM on "comment code". Most of it is legible on screen (described above). |
| 2-64-64-3 MLP, ReLU, softmax | architecture | audio 10.7s; diagram | Verified: 133 neurons = 2+64+64+3; weights = (2·64+64)+(64·64+64)+(64·3+3) = 192+4,160+195 = **4,547** ✓ |
| Three-spiral dataset, 600 points, noise 0.2 | data | code lines 5–13 | Classic non-linearly-separable toy (the CS231n "spiral" example) |
| lr = 0.05, 2,000 steps | hyperparameters | code | Full-batch gradient descent |
| 34% / 42% initial; loss 0.024, 100% train; 99.8% test | numbers | audio 23.5s and 42.2s; panels | Plausible (random init ≈ 1/3 per class; spirals are easily fit by a 64-64 MLP). **Not executed – unverified.** |
| PyTorch, TensorFlow | frameworks | caption, audio | Named as not used |
| Comment "code" | CTA | audio 42.2s | Auto-DM with the file |

### What's being promoted / the funnel decoded
"Comment code" sends spiral_nn.py by DM. That drives engagement and a DM list for the NEURON account, whose bio (per a prior review, DeQuUyPo8pR) points to its free NEURON ML-practice web app. No paid product was found. The code is essentially reproduced above, so the DM isn't needed.

### Verification & insights
- Read the code on screen (not run). The math is correct: the softmax-cross-entropy gradient, ReLU masks, He init and a stable softmax (subtracting the row max).
- The 99.8% test figure is believable here because the test set comes from the *same* generator and noise level as training (a separate draw, not a different distribution). It shows interpolation on a toy problem, not real-world generalisation.
- The "2,303 random weights" counter is a mid-animation value on its way to 4,547.
- Better-known free sources: Stanford CS231n "Putting it together: Minimal Neural Network Case Study" (the same spiral task, also in NumPy), Karpathy's micrograd.
- Not verified: the rest of the caption and the exact first ~4 lines of the file (partly obscured).

---

<a id="e-deulwiyikqz"></a>

## DeUlwIYikQz | @quantfinancetogo | Quant Finance from Scratch Part 19: value at risk (VaR) on 100 simulated years of fat-tailed days, with a 16-line NumPy script (99% VaR 2.7% vs bell-curve 2.3%; expected shortfall 4.2%)
- **Link:** https://www.instagram.com/p/DeUlwIYikQz/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-10 · **Type:** reel (112.9s, 2 scene pages; one continuous animation, reviewed from 2-fps frames)
- **Caption source:** full (Instagram, fetched with yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct textbook explanation of VaR and expected shortfall. Every number on screen and in the caption reproduces exactly from the on-screen code. Nothing is sold.

### Post description
> ➡️ Quantitative Finance from Scratch, part 19: value at risk (VaR).
>
> Value at risk is the maximum loss that a portfolio should not exceed over a chosen period, with a chosen probability called the confidence level, under normal market conditions.

- Example: a 1-day VaR of 2% at 99% means the loss of a single day stays below 2% on 99 days out of 100.
- Method: sort many past days from worst loss to best gain and draw the line where only one day in a hundred is worse.
- Use: banks, fund managers and risk teams use it daily to sum up thousands of positions in one number and to set risk limits; J.P. Morgan popularised it in the 1990s.
- Setup: simulated market with assumed numbers, 100 years of trading days, about 1% a day, with the fat tails from part 18.
- Results: 99% one-day VaR from the simulated days 2.7%; the same swing on a bell curve gives 2.3%, crossed on 396 days instead of the promised 252. At 99.9%: 5.9% vs 3.0%, with the bell line crossed on 186 days instead of about 25.
- "The dangerous problem": VaR says where the worst day in a hundred begins, not how bad it gets. Past the line, the average loss was 4.2% and the worst day lost 21.5%; that average is expected shortfall, which bank supervisors also moved toward for market risk after the financial crisis.
- Disclaimer: education only, not financial advice.
- Hashtags: #quantfinance #valueatrisk #riskmanagement #finance #python

*Caption condensed – full text is on the original post.*

### Audio
English voice-over by the creator over quiet background music (no identifiable song). Condensed into timestamped notes:
- [0.0–8.6] Hook: "This one number measures the risk of your portfolio and banks and funds all over the world rely on it." It is called value at risk and "has one dangerous problem."
- [8.6–10.9] Series title: "Quantitative finance from scratch, Part 19."
- [10.9–30.3] Definition: the maximum loss a portfolio or investment should not exceed over a set period, with a fixed probability (the confidence level), under normal market conditions. You choose both: the period can be 1 day, 10 days or a year; the confidence level is often 95 or 99%.
- [30.3–42.4] Example: a 2% VaR over one day at 99% means that on 99 days out of 100 a single day's loss stays below 2%.
- [42.4–54.7] Method: take many past days, sort them from worst loss to best gain, and draw the line where only 1 day in 100 is worse; that line is the VaR.
- [54.7–73.1] Use: banks, fund managers and risk teams use it daily; it turns thousands of positions into one number readable at a glance and sets risk limits for a trader or trading desk. JP Morgan popularised it in the 1990s, and it spread across the industry.
- [73.1–91.2] The problem: VaR "tells you where the worst one day in 100 begins and nothing about how bad that day gets." It also trusts the past and the model; with a bell-curve assumption, extreme days come more often than promised, like the fat tails from part 18.
- [91.2–101.4] Fix: risk managers add expected shortfall, the average loss on the days past the line.
- [101.4–111.2] Wrap-up: VaR sums up a portfolio's risk in one number (the loss on a bad day) with a blind spot beyond the line; ends "So to really learn quantitative finance." (The sentence is cut off at the end of the video. Other posts in the series end "Follow to really learn quantitative finance.")

### On-screen content, page by page
The layout is fixed throughout: header "QUANT FINANCE FROM SCRATCH ▌ · PART 19", title "Value at Risk", subtitle "one number for a bad day" (it changes to "one number, with a blind spot" at the end), and episode tabs 13–21 with 19 highlighted. Below that sit a chart panel, a caption bar, a code editor `valueatrisk.py` ("python · running" / "done"), and the footer "simulated returns, assumed numbers · education only · not financial advice". The scene detector caught only 2 pages (p_0001 at 0s, and p_0002, a near-black transition frame), so the segments below come from the 2-fps frames.

**Segment 1 (0–8s), hook:** A histogram "one day of the portfolio · squeezed scale", with the x-axis running −20, −10, −3, −1, 0 %, +1, +3, +10, +20, labelled "loss" on the left and "gain" on the right. A big counter animates (0.9 % → 1.9 % → 2.7 %) with the tag "ONE DAY · 99 % · SIMULATED". A lower panel shows "the same days, 100 years in a row" as a blue return series, with "line −2.7 %". Labels "VALUE AT RISK" and "1 DAY IN 100 IS WORSE". Pop-up: "KEY IDEA — VALUE AT RISK — one number for a bad day".
**Segment 2 (~10–24s):** Histogram labelled "MAXIMUM LOSS". Caption bars read "the maximum loss · over a period", then "not exceeded with 99 % · over one day", with tags "PERIOD: ONE DAY" and "CONFIDENCE LEVEL: 99 %". The code begins to type.
**Segment 3 (~24–30s), "you choose · period and confidence level":** Selector chips: period "1 DAY / 10 DAYS / 1 YEAR", confidence level "95 % / 99 %". Small bars, "one bar = one simulated day".
**Segment 4 (~30–42s), "example: 2 % at 99 %, one day · textbook example":** "VaR = 2 %", tag "EXAMPLE", "one day · 99 %". A grid of 100 squares labelled "example: 100 days".
**Segment 5 (~42–54s), "sort the past days · worst loss to best gain":** "worst 1 % of days, enlarged", "25,200 simulated days". Then "SORTED: WORST LOSS TO BEST GAIN", a sorted curve from the worst loss to the best gain.
**Segment 6 (~55–67s), "used every day · banks and funds", then "risk limits · trader or trading desk":** Tags "BANKS", "FUND MANAGERS", "RISK TEAMS". Day chips Mon–Fri and "2.7 % — ONE NUMBER · 99 % · ONE DAY". A bar "value at risk used" against a red "limit" marker, noted "schematic, no real limits", with "TRADER" and "TRADING DESK".
**Segment 7 (~67–73s), "J.P. Morgan, 1990s · then the whole industry":** A timeline 1990 / 1994 / 1998 with "J.P. MORGAN: DAILY RISK REPORT", "OCT 1994: RISKMETRICS PUBLISHED" and "WIDELY ADOPTED". Small print: "sources: Holton 2002, Finger 2001" (read from an enlarged frame; the last character is faint).
**Segment 8 (~73–81s), "the dangerous problem · 1 day in 100 beyond the line":** The left tail is shaded red. Tags "1 DAY IN 100 · 252 OF 25,200 DAYS" and "BEGINS HERE: 2.7 %".
**Segment 9 (~81–91s), "trusts the past · and the model", then "bell line crossed more often · 396 days, not 252":** Tags "THE PAST", "A MODEL", "FAT TAILS · PART 18". A blue bell curve is drawn over the histogram: "HISTORY: 2.7 %" vs "BELL CURVE: 2.3 %". Output lines: "> days past it: history 252, bell 396" and "> days past it: history 26, bell 186". Footnote: "promised: 252 days (1 in 100) and 25 days (1 in 1,000) in 100 years".
**Segment 10 (~91–101s), "expected shortfall · a second number":** Tag "EXPECTED SHORTFALL" over the red tail.
**Segment 11 (~101–113s), "value at risk · 2.7 % · and a blind spot":** "2.7 % VALUE AT RISK" and "4.2 % BEYOND THE LINE: EXPECTED SHORTFALL", with the tail labelled "BLIND SPOT". Subtitle "one number, with a blind spot".

**Final code on screen (`valueatrisk.py`, 16 lines, read from the last frame), excerpt:**
```
import numpy as np
rng = np.random.default_rng(19)
days, swing = 252 * 100, .01  # assumed: 1% a day
market = rng.standard_t(3, days) * swing / 3**.5
loss = -market  # fat tails, as in part 18
for level, swings in (.99, 2.326), (.999, 3.09):
    history = np.quantile(loss, level)
    bell = swings * market.std()  # same swing
tail = loss[loss > np.quantile(loss, .99)]
```
The omitted lines (9–13, 15–16) are print statements. For each level (99% with 2.326 bell multiplier, 99.9% with 3.09) they print the historical VaR and the bell-curve VaR as percentages (`{:.1%}`), then the number of days past each line ("days past it: history …, bell …"). Lines 15–16 print the average and worst loss past the 99% quantile ("past 99%: average loss …, worst …"). Inputs: seed 19, 25,200 days (252 × 100), 1% daily swing, Student-t with 3 degrees of freedom scaled by 1/√3. Printed results: 99% VaR history 2.7%, bell 2.3%; days past it 252 vs 396; 99.9% VaR history 5.9%, bell 3.0%; days past it 26 vs 186; past 99% average loss 4.2%, worst 21.5%.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Value at risk (VaR) | concept | title, caption, audio | Standard definition, correctly stated (a quantile of the loss distribution over a horizon at a confidence level). |
| Expected shortfall (ES / CVaR) | concept | caption, audio 91s, segments 10–11 | Correct: the average loss beyond the VaR line. Basel's FRTB (finalised 2016/2019) replaced 99% VaR with 97.5% ES for market-risk capital, which matches "bank supervisors also moved toward it… after the financial crisis". |
| J.P. Morgan, daily risk report; RiskMetrics, Oct 1994 | history | caption, audio 67s, segment 7 | Correct. J.P. Morgan's "4:15 report" (Weatherstone) dates from around 1990, and the RiskMetrics technical document was made public in October 1994. |
| "Holton 2002, Finger 2001" | sources | segment 7 (tiny print) | Glyn Holton wrote a well-known history of VaR (2002). "Finger" is most likely Chris Finger of RiskMetrics. The exact Finger work was not identified. |
| 99% VaR 2.7% vs bell 2.3%; days past it 252 vs 396; 99.9%: 5.9% vs 3.0%, 26 vs 186 days; tail average 4.2%, worst 21.5% | results | caption, screen | **Reproduced exactly** by re-typing the 16 on-screen lines and running them locally (my own transcription, no downloaded code). |
| 25,200 days = 252 × 100; seed 19; Student-t with 3 degrees of freedom scaled to 1% a day; z-values 2.326 and 3.09 | parameters | code, segment 5 | Assumed simulation inputs, as the post states. 2.326 and 3.09 are the correct normal 99% and 99.9% quantiles. |
| Part 18 (fat tails) | series reference | caption, audio, tags | An earlier episode of the same series. |

### What's being promoted / the funnel decoded
Nothing is sold. The only call to action is the (cut-off) spoken "…to really learn quantitative finance", the series' standard "follow" line. There is no comment keyword, link, product or affiliate. Same account and series as DeD3ruoCXGg (Part 13), DeFCbkaiVMa (Part 14), DeG3qGCirGO (Part 15) and Debex7eiZZu (Part 22). The sister account is @machinelearningtogo.

### Verification & insights
- **Code check:** my transcription printed `99% VaR: history 2.7%, bell 2.3%`, `days past it: history 252, bell 396`, `99.9% VaR: history 5.9%, bell 3.0%`, `days past it: history 26, bell 186` and `past 99%: average loss 4.2%, worst 21.5%`. That is identical to the caption and the screen.
- **Small discrepancy:** at 99.9% the screen says "history 26", while the promised count is "about 25" (25.2). This is a rounding and quantile artefact, not an error.
- **Accuracy:** the explanation is correct. The "historical simulation" method shown (sort past days, take a quantile) is one of three standard VaR methods, alongside parametric/variance-covariance and Monte Carlo. The bell-curve comparison correctly shows that normal-based VaR understates fat-tailed risk.
- **Caveats the post itself states:** simulated data with assumed numbers, and education only. Real VaR also depends on window length, volatility clustering, and position mapping.
- **Not verified:** which Finger publication is cited.

---

<a id="e-deljvbkihq-"></a>

## DeljvbKIhQ- | @neuron.machinelearning | 9 classic ML algorithms run on the same scikit-learn toy dataset, with a test-accuracy leaderboard (neural net 91.6% wins)
- **Link:** https://www.instagram.com/p/DeljvbKIhQ-/
- **Account:** @neuron.machinelearning (Neuron. Machine Learning) · **Posted:** 2026-10-17 · **Type:** reel (96.1s; one continuous animated screen with 11 sections, reviewed from the 2-fps frames)
- **Caption source:** full (Instagram, via yt-dlp. The mirror had cut it off.)
- **Category:** Quant & data (ML education)
- **Verdict:** LEGIT & FREE – accurate beginner explainer, and almost all of the "script" is visible on screen. Small inconsistencies: the "4,386 weights" claim doesn't match the shown 2-32-32-1 network, and the accuracy ranking on a toy two-moons dataset says nothing general about the algorithms.

### Post description
> 9 ML algorithms. One script. One winner.
>
> 01 Linear Regression → the best line (y = 2.56x + 3.53)
> 02 Logistic Regression → a line that outputs probabilities · 81.6%
> 03 KNN → 15 nearest neighbors vote · 90.4%
> 04 Decision Tree → one yes/no question at a time · 85.2%
> 05 Random Forest → 300 trees vote · 88.8%
> 06 Gradient Boosting → each tree fixes the last · 88.8%
> 07 SVM → the widest margin · 89.2%
> 08 K-Means → finds groups with zero labels
> 09 Neural Network → 4,386 weights · 91.6% 🏆
>
> Same data. Same 250 test points. Real Python, real results.
> The simplest one (KNN) came in 2nd. That’s ML for you.
>
> Save this. You’ll need it before your next interview.
> Comment CODE and I’ll send you the full script.
>
> #machinelearning #python #datascience #ai #deeplearning

### Audio
Narration in English with background music. About 230 words, given as close notes with key lines quoted.
- [0.3–6.6] "Nine algorithms. Learn these and you understand most of machine learning. All nine in one video."
- [6.6–15.2] Linear regression "predicts a number. It draws a line and nudges it until the squared errors are as small as possible. Prices, sales, any trend."
- [15.2–26.1] Logistic regression "answers yes or no. It bends a straight line through a sigmoid. So every answer becomes a probability. 81.6% because this data curves."
- [26.1–34.7] KNN "learns nothing up front. A new point asks its 15 closest neighbors and the majority wins. 90.4%."
- [34.7–44.3] Decision tree: "one yes or no question at a time… Four levels deep, 85.2%."
- [44.3–53.0] Random forest: "trains hundreds of trees each on a random sample… Together they vote 88.8%."
- [53.0–60.7] Gradient boosting: "builds trees one after another. Each new tree fixes the mistakes of the ones before. The king of tabular data."
- [60.7–69.7] SVM: "looks for the widest margin between classes. Only the points on the edge decide where it goes. 89.2%."
- [69.7–78.6] K-means: "gets no labels at all. It drops centers, moves each one to the middle of its points and repeats. Customer segments, colors, anomalies."
- [78.6–88.5] Neural network: "stacks layers of tiny neurons. Backprop tunes every weight until the boundary bends around the data. 91.6%, the winner."
- [88.5–94.0] "Same data, one script. The neural network wins. Save this and comment code for the script."

### On-screen content, page by page
Every section has a "NEURON." header, a progress bar, a section label "NN / 09 · …", a large title, a visual panel, a subtitle line, and a `series9.py` code panel showing the code for that section and its printed output.
**Section 0 (0–6.6s) "9 ML ALGORITHMS YOU NEED TO KNOW" – "9 algorithms", "all nine · one script":** A 3×3 grid of thumbnails (01 Linear Regression … 07 Support Vector Machine, 08 K-Means, 09 Neural Network). The code panel shows the imports:
`from sklearn.datasets import make_moons, make_blobs`, `train_test_split`, `LinearRegression, LogisticRegression`, `KNeighborsClassifier`, `DecisionTreeClassifier`, `RandomForestClassifier, GradientBoostingClassifier`, `SVC`, `KMeans`, `MLPClassifier`. These are followed by data generation and a `models = {…}` dictionary loop (too small to read in full).
**01 / 09 "PREDICTS A NUMBER" – Linear Regression (6.6–15.2s):** A fitted line through a scatter, with a "prices · sales · trends" tag and a squared-error readout. Code `lin = LinearRegression().fit(x, t)`, `print(lin.coef_, lin.intercept_)`, output `[2.56] 3.53`.
**02 / 09 "YES OR NO · A PROBABILITY" – Logistic Regression (15.2–26.1s):** A sigmoid inset and a straight boundary through the two-moons data. Badge **81.6%**. Code `LogisticRegression().fit(Xtr, ytr)` / `m.score(Xte, yte)`, output `0.816`.
**03 / 09 "ASK THE NEIGHBORS" – K-Nearest Neighbors (26.1–34.7s):** "15 nearest · 4 orange · 11 white → WHITE". Code `KNeighborsClassifier(15)`. Accuracy **90.4%**.
**04 / 09 "ONE QUESTION AT A TIME" – Decision Tree (34.7–44.3s):** Box partitions grow from depth 1 (2 boxes) to depth 4 (16 boxes max), "acc 85.2%". Code `DecisionTreeClassifier(max_depth=4)`.
**05 / 09 "300 TREES VOTE" – Random Forest (44.3–53.0s):** A grid of tree 1–4 panels. Code `RandomForestClassifier(300)`. Accuracy **88.8%**.
**06 / 09 "EACH TREE FIXES THE LAST" – Gradient Boosting (53.0–60.7s):** The tree counter goes from 1 to 100 as the boundary refines. Code `GradientBoostingClassifier()`, output `0.88`. Accuracy **88.8%** per the leaderboard.
**07 / 09 "THE WIDEST MARGIN" – Support Vector Machine (60.7–69.7s):** A curved boundary, "support vectors: only they decide the boundary". Code `SVC(kernel="rbf")`, output `0.89`. Badge **89.2%**.
**08 / 09 "NO LABELS AT ALL" – K-Means clustering (69.7–78.6s):** Four coloured blob clusters, "step N · points switched group", tag "segments · colors · anomalies". Code `labels = KMeans(4).fit_predict(Xb)` / `print(np.bincount(labels))`, output `[100 96 100 104]`.
**09 / 09 "THE IDEA BEHIND CHATGPT" – Neural Network (78.6–88.5s):** "epoch 120 · loss 0.205 · acc 91.6%". The network diagram is labelled 2 → 32 → 32 → 1. Badge **91.6% test accuracy**. Code `m = MLPClassifier((32, 32), max_iter=120)` / `print(m.fit(Xtr, ytr).score(Xte, yte))`, output `0.91`.
**"SAVE THE SERIES · COMMENT CODE" – "All nine" (88.5–96.1s):** Leaderboard, "same data · 250 test points · all 7 classifiers":
Neural Network 91.6% · KNN 90.4% · SVM 89.2% · Random Forest 88.8% · Gradient Boosting 88.8% · Decision Tree 85.2% · Logistic Regression 81.6%. The code shows the loop `for name, m in models.items(): print(name, m.fit(Xtr, ytr).score(Xte, yte))`.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| scikit-learn (`sklearn`) | library | Code panels | The standard free Python ML library. Every class shown exists with the arguments used. |
| make_moons / make_blobs | datasets | Imports | sklearn's synthetic toy datasets: two interleaved half-moons for classification, Gaussian blobs for k-means. |
| 9 algorithms + accuracies | numbers | Caption, audio, screen | Consistent between caption, screen and audio. Not executed, so unverified. |
| 250 test points | number | Caption, leaderboard | 91.6% = 229/250, 90.4% = 226/250, and so on. All are consistent multiples of 0.4%. |
| "4,386 weights" | number | Caption | **Inconsistent.** The on-screen network is MLPClassifier((32, 32)) on 2 inputs with 1 output, which has 2·32+32 + 32·32+32 + 32+1 = 1,185 parameters. This is reasoned from the code, not executed. |
| "300 trees" | number | Caption, section 05 | Matches `RandomForestClassifier(300)`. |
| "Comment CODE" | comment keyword | Caption, audio, end screen | Auto-DM for "the full script". |

### What's being promoted / the funnel decoded
"Comment CODE" triggers an auto-DM with the full `series9.py`. Nearly all of it is already on screen: each model line, the imports and the loop. Only the data-generation lines are too small to read. The aim is engagement and follower growth for a "save the series" ML-education page. No paid product is visible, though such pages often later push courses or newsletters.

### Verification & insights
- The algorithm descriptions are accurate at beginner level.
- The results are toy-dataset specific. On two-moons data, any non-linear method (KNN, RBF-SVM, MLP) beats linear logistic regression, which is the point the creator makes ("because this data curves"). The 1–3 point gaps between the top models are within noise for 250 test points (about ±2% standard error) and would likely reorder with a different random seed. "One winner" is therefore not meaningful.
- "Gradient boosting: the king of tabular data" is a fair, widely held view, yet it ties with random forest here. That again shows toy data doesn't rank algorithms.
- Minor display inconsistency: the NN code output shows `0.91` while the badge says 91.6%. A raw `print` of 0.916 would show `0.916`, so the display was edited.
- Not verified: the exact accuracies (code not run) and the data-generation parameters.

---

<a id="e-derlbhmofo0"></a>

## DerLBHmOFO0 | @davidarias_cfa | "7 free quant and options trading tools": OpenBB, TradingView MCP, QuantLib, TradingAgents, vectorbt, IBKR paper API, and the creator's own quant-models repo
- **Link:** https://www.instagram.com/p/DerLBHmOFO0/
- **Account:** @davidarias_cfa (David Arias, CFA) · **Posted:** 2026-10-19 · **Type:** reel (18.2s, 11 pages). The mirror only had the cover image; I fetched the video with yt-dlp and processed it myself.
- **Caption source:** full (Instagram, via yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. Every tool is real and free or open source (vectorbt carries a Commons Clause). The "Repo" CTA leads to the creator's own public MIT repo, which holds the integration code.

### Post description
> Free tools for quant and options trading, and how to plug each one into a trading strategy.
>
> OpenBB: options chains, macro and fundamentals data in one open platform.
> TradingView MCP: TradingView data, screeners and alerts inside Claude, Cursor or any MCP client.
> QuantLib: industry standard pricing. One example prices the same option with 21 methods, from Black-Scholes to Monte Carlo.
> TradingAgents: a multi agent LLM framework that reads, debates and rates a stock, and it can run on a local model.
> vectorbt: backtests thousands of strategy settings in seconds.
> Interactive Brokers: a free paper API. A Python engine sends real paper orders to TWS.
>
> All the code is in the repo, with the step by step to connect each tool to a strategy.
>
> Comment "Repo" and the link comes to your inbox.
>
> #quantfinance #optionstrading #algotrading #python #tradingbot

### Audio
Music only. Whisper picked up just a stray "Okay" at 1.5s; there is no narration. The song is not identifiable.

### On-screen content, page by page
- **Page 1 (0–2.0s):** a person at a multi-monitor trading desk in the dark, titled "7 free quant and options trading tools".
- **Page 2 (2.0–4.3s):** **"OPENBB · Open Data Platform · 74,000 stars"**. It shows the OpenBB-finance/OpenBB GitHub page and the OpenBB Platform diagram (data sources such as FRED, BLS and others feeding the platform, a workspace UI and an agent). Caption: "Options, macro and fundamentals data in one free platform for quants."
- **Page 3 (4.3–6.9s):** **"TRADINGVIEW MCP · atilaahmettaner · 5,000 stars"**. It shows the GitHub page for atilaahmettaner/tradingview-mcp and a terminal starting "tradingview-mcp". Caption: "TradingView data, screeners and alerts inside any MCP client."
- **Page 4 (6.9–8.5s):** **"QUANTLIB · pricing library · 7,700 stars"**. It shows source code listing `VanillaOption europeanOption/bermudanOption/americanOption` and a column of `method = "…"` lines: Black-Scholes; Black Vasicek Model; Heston semi-analytic; Bates semi-analytic; Barone-Adesi/Whaley; Bjerksund/Stensland; QD+ fixed-point (fast); QD+ fixed-point (accurate); QD+ fixed-point (high precision); Integral; Finite differences; Binomial Jarrow-Rudd; Binomial Cox-Ross-Rubinstein; Additive equiprobabilities; Binomial Trigeorgis; Binomial Tian; Binomial Leisen-Reimer; Binomial Joshi; MC (crude); QMC (Sobol); MC (Longstaff Schwartz). That is 21 methods. Caption: "One option priced with 21 methods, from Black-Scholes to Monte Carlo."
- **Page 5 (8.5–10.7s):** **"TRADINGAGENTS · Tauric Research · 112,000 stars"**. It shows the TauricResearch/TradingAgents GitHub page and its diagram. Data sources are Market (Yahoo Finance), Social Media (X, Reddit), News (Bloomberg, Reddit, Reuters, FinnHub) and Fundamentals (company profile, financial history, insider transactions). These feed Bullish and Bearish researchers who hold a Discussion, then "Buy Evidence" / "Sell Evidence" to a Researcher Team. Caption: "Multi agent LLM trading framework. Needs an LLM, and it can run locally."
- **Page 6 (10.7–12.0s):** **"VECTORBT · backtesting at scale · 9,400 stars"**. It shows a heatmap of total return (colour scale up to 3500%) for Fast SMA window (x, 0–100) vs Slow SMA window (y, 0–100), with a symbol selector BTC-USD / ETH-USD / XRP-USD. Caption: "Test thousands of strategy settings in seconds, on pandas and NumPy."
- **Pages 7–8 (12.0–14.5s):** **"INTERACTIVE BROKERS · automation · free paper API"**. On the left is a Python engine log; on the right, TWS charts. The log reads:
  - Section 3 "ACCOUNT AND CONTRACT": Paper account [ID partly masked on screen; not reproduced]; net liquidation about $1.03M; instrument MES MESZ6, Micro E-mini S&P 500, expires 18 Dec 2026, $5 a point; MES position now: flat.
  - Section 5 "DECISION 12:10:32 New York": MES at the 09:30 open 7,673.50; MES now 7,703.00 (bar 12:00); Day so far +0.38% up. Reasoning: "long gamma and the day is up, so go against it". Action: SELL 1 MES ("plumbing test size"). Notional $38,515. Exit: market order after 2.5 min.
  - Section 6 "EXECUTION, fills read from the execution log": 12:10:32 SELL 1 MESZ6 market order sent (id 96); 12:10:34 filled 1 @ 7,699.00, commission $0.61; marks 7,703.00 (open P&L −$20.00) at 12:10:34/45/55, then 7,700.00 (−$5.00) at 12:11:06/17. "holding sell 1 MES, exit in 1m 44s".

  Caption: "Python engine on the left, TWS on the right. Real paper orders through the API."
- **Pages 9–10 (14.5–16.2s):** **"QUANT MODELS IN PYTHON · option pricing, Greeks, GEX, vol surfaces"**. It shows the README of github.com/davidalmeida90/quant-models (badges, the "Options for Convertible and Callable Bonds" video thumbnail, and the model table starting Black-Scholes and Option Greeks). Footer: **github.com/davidalmeida90/quant-models**.
- **Page 11 (16.2–18.2s):** desk B-roll, "HOW TO INTEGRATE THEM WITH TRADING STRATEGIES · comment "Repo"".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| OpenBB (OpenBB-finance/OpenBB) | repo | caption, p2 | Real. Apache-2.0. Last commit cbf37e1 on 2026-10-17. About 74.5k stars, so the "74,000" claim is correct. |
| TradingView MCP (atilaahmettaner/tradingview-mcp) | repo | caption, p3 | Real. MIT. Last commit 16ba255 on 2026-10-20. About 5.1k stars (claimed 5,000). The README says it needs no TradingView account, does not log into or scrape a TradingView session, and fetches data from public endpoints. It is not affiliated with TradingView Inc. |
| QuantLib (lballabio/QuantLib) | repo | caption, p4 | Real C++ pricing library with a BSD-style licence. Last commit bf35b19 on 2026-10-20. Its EquityOption example prices one option with many engines; the screen lists 21 method strings, while the creator's README says "20 methods". Stars claimed 7,700, not separately checked. |
| TradingAgents (TauricResearch/TradingAgents) | repo | caption, p5 | Real. Apache-2.0. v0.7.0 merged in commit e8f5503 on 2026-10-16. About 112.4k stars (claim correct). Needs an LLM; the creator's script uses Ollama qwen3:8b locally or a DeepSeek key. |
| vectorbt (polakowo/vectorbt) | repo | caption, p6 | Real. Apache 2.0 **with Commons Clause** (no selling the software itself). Last commit 686c7d4 on 2026-10-18. Stars claimed 9,400, not separately checked. |
| Interactive Brokers paper API / TWS / IB Gateway | broker API | caption, p7–8 | Real. Paper trading is free with an IBKR account. The creator's engine uses the `ib_async` library (ib-api-reloaded/ib_async). |
| MES / MESZ6 (Micro E-mini S&P 500, Dec 2026) | futures ticker | p7–8 | Real CME contract at $5 per index point. Notional 7,703 × $5 = $38,515 is correct, and so is the P&L (short at 7,699, mark 7,703 is 4 points × $5 = −$20). |
| github.com/davidalmeida90/quant-models | repo | p9–10 (the hidden 7th "tool") | Real. MIT. Last commit 1796df7 on 2026-10-19: "quant-options-tools: OpenBB, TradingView MCP, QuantLib, TradingAgents and vectorbt wired into one strategy loop with an IBKR paper engine". The README links X @Davidariasfin, YouTube @DavidAriasCFA222, davidariasfinance.com and its newsletter. |
| `quant-options-tools/` folder | code | repo | Scripts `openbb_data.py`, `tradingview_mcp_client.py`, `quantlib_pricing.py`, `tradingagents_signal.py`, `vectorbt_sweep.py` (4,851 backtests of MA settings on SPY 2010–2019), `ibkr_engine.py` (TWS paper, port 7497) and `loop.py` (dry run by default). |
| "Repo" | CTA keyword | caption, p11 | Comment-to-DM. |

### What's being promoted / the funnel decoded
"Comment 'Repo'" sends the link to github.com/davidalmeida90/quant-models, which is already shown on screen and is free (MIT). The wider funnel is the creator's ecosystem: README badges push GitHub stars, X follows, the YouTube channel @DavidAriasCFA222, and a free weekly newsletter at davidariasfinance.com/newsletter. No paid product was seen in the post or README. The newsletter is the email-capture step. Note that the GitHub username is "davidalmeida90" while the brand is "David Arias, CFA". I did not verify whether these are the same person or whether the CFA charter is real.

### Verification & insights
- I ran `git ls-remote` on all six repos. I shallow-cloned tradingview-mcp and quant-models, made a blobless clone of QuantLib, reused existing clones of OpenBB, TradingAgents and vectorbt, and read the licences and last commits. Star counts were checked on the GitHub pages for OpenBB, TradingAgents and tradingview-mcp. No code was executed.
- **Claims vs reality:**
  - "Free": true for all, though vectorbt's Commons Clause restricts commercial resale, and the full vectorbt PRO is paid.
  - "TradingAgents can run on a local model": true via Ollama.
  - "Backtests thousands of settings in seconds": plausible, since vectorbt is vectorised.
  - The QuantLib "21 methods" count matches the 21 method lines on screen (the repo text says 20; a trivial mismatch).
- **The IBKR demo** is a tiny "plumbing test": a 1-lot MES paper trade with a rule "long gamma and the day is up, so go against it" and a 2.5-minute exit. It demonstrates the connection, not a profitable strategy.
- **Caution:** the vectorbt heatmap (returns up to 3500% on crypto SMA crossovers) is a parameter sweep. Picking the best cell is in-sample overfitting. The creator's own script notes an out-of-sample check, but no results were shown in the reel.
- **Privacy:** the paper-account ID was already partly masked on screen and is omitted here. No keys were visible.

---

<a id="e-ddmmeowmptk"></a>

## DdMMeOwMpTK | @edgarcruz007 | Spanish desk-tour reel: "4 websites" for academic trading research (SSRN, arXiv, IDEAS/RePEc, QuantConnect); he feeds an arXiv options paper to his AI assistant "Polo"; plugs a seminar
- **Link:** https://www.instagram.com/p/DdMMeOwMpTK/
- **Account:** @edgarcruz007 (Edgar Cruz) · **Posted:** 2026-09-12 · **Type:** reel (93.8s, 5 pages)
- **Caption source:** full (Instagram, via yt-dlp; the mirror copy was cut off)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. All four sites are real and free to read (QuantConnect is freemium). The paper shown is a real Oxford-Man paper. The only funnel is a vague "join the seminar tomorrow".

### Post description
> 📚 ¿Quieres encontrar nuevas ideas de trading?
>
> No te limites a TikTok, YouTube o Twitter. Hay investigadores publicando estudios reales sobre mercados, opciones, volatilidad, AI y quantitative trading.
>
> 🔬 SSRN — Finanzas e investigación
> SSRN
>
> 🤖 arXiv — Quant, AI y Machine Learning
> arXiv
>
> 📊 RePEc / IDEAS — Economía y Finanzas
> IDEAS / RePEc
>
> 💻 QuantConnect — Quant Trading & Backtesting
> QuantConnect
>
> 💡 Algunas búsquedas que te recomiendo:
>
> GEX • 0DTE • Options • Volatility • Market Microstructure • VWAP • Order Flow • Machine Learning • Regime Switching
>
> La próxima gran idea puede estar en un paper que casi nadie está leyendo. 🧠📈
>
> La investigación académica no constituye asesoría financiera ni garantiza resultados de trading.

(The repeated site names were Instagram link cards; the URLs are not in the text. English gist: "Want new trading ideas? Don't limit yourself to TikTok/YouTube/Twitter; researchers publish real studies on markets, options, volatility, AI and quant trading… Suggested searches: … The next big idea may be in a paper almost nobody reads. Academic research is not financial advice and doesn't guarantee trading results.")

### Audio
The creator's speech in Spanish (lightly corrected from Whisper), as timestamped English notes with short Spanish quotes:
- [0.0–13.4] While watching F1 qualifying, he shares "cuatro websites" for finding trading ideas and concepts or learning trading academically; the papers come from academics and Wall Street quants.
- [13.4–24.7] It is "un nivel mucho más arriba de lo que puedes encontrar en social media" (a much higher level than social media); the websites will be in the description.
- [24.7–36.3] Names them: **SSRN**, **arXiv**, **IDEAS** [económicas], plus one he is analysing right now.
- [36.3–64.0] His method: once a topic or concept catches his interest, he opens the document, copies it and gives it to **Polo** (his AI assistant), which analyses the whole document; he then chats with Polo about how to apply it and what it thinks of the concept, to raise his understanding of markets.
- [64.0–81.2] This lets him learn things that only someone who went to university would understand, with Polo explaining them more simply and directly. He'll leave the websites.
- [81.2–94] CTA: "Únanse al **seminario mañana**" (join the seminar tomorrow); its goal is to raise the level of Spanish-speaking traders. The last words are garbled in the audio; the name of the seminar or brand could not be made out.

### On-screen content, page by page
A constant overlay on all pages: "**4 websites que elevará tu trading a nivel PRO**". Filmed with a phone across a multi-monitor desk.
**Page 1 (0.0–34.3s):** Dark room. One monitor shows a Formula 1 qualifying broadcast with a timing overlay. Others show trading charts.
**Page 2 (34.3–40.6s):** Monitors with a multi-line performance chart and a chart for ticker **BNDX** (Vanguard Total International Bond ETF; "Día / 10 Años"). The centre monitor shows a PDF in a browser.
**Page 3 (40.6–46.9s):** A web page headed "**Quant Finance Research Hub**" with a "Topics" menu. The article is titled "**Deep Learning for Options Trading: An End-To-End Approach**", with an abstract snippet about data-driven option trading strategies "in contrast to traditional…".
**Page 4 (46.9–86.9s):** The PDF of the same paper: authors **Wee Ling Tan, Stephen Roberts, Stefan Zohren**, followed by the abstract.
**Page 5 (86.9–93.8s):** Upper monitor shows an options chain ("Call ← September 14, 2026 → Put") and a "Superficie 3D" (3D volatility surface) panel. The lower monitor shows a long AI chat answer in Spanish analysing the paper, next to a TradingView chart and a watchlist of mini charts.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| SSRN | site | caption, audio 24.7s | ssrn.com, Elsevier's free preprint repository. Strong in finance and economics. |
| arXiv | site | caption, audio | arxiv.org (Cornell), free preprints. The q-fin and cs.LG sections are relevant here. |
| IDEAS / RePEc | site | caption, audio | ideas.repec.org, a free economics bibliographic database (St. Louis Fed). |
| QuantConnect | site/platform | caption only | quantconnect.com, a cloud algo backtesting platform built on the open-source LEAN engine. Free tier plus paid tiers. |
| "Quant Finance Research Hub" | web page | page 3 | The page hosting the paper. The exact site could not be identified from the footage. |
| "Deep Learning for Options Trading: An End-To-End Approach" (Tan, Roberts, Zohren) | paper | pages 3–4 | Real: arXiv:2407.21791 (Oxford-Man Institute), ICAIF '24. Deep nets trade delta-neutral straddles on S&P 100 options over about 10 years and beat rule-based benchmarks on risk-adjusted terms. Turnover regularisation helps at high transaction costs. |
| "Polo" | AI assistant | audio 47–80s | The creator's name for his AI chat assistant. The underlying model is not stated. |
| Suggested searches: GEX, 0DTE, Options, Volatility, Market Microstructure, VWAP, Order Flow, Machine Learning, Regime Switching | keywords | caption | Search terms. |
| BNDX | ticker | page 2 | Vanguard Total International Bond ETF (background only). |
| "Seminario mañana" | event | audio 81–86s | An unnamed seminar for Spanish-speaking traders. No date, link or price given. |

### What's being promoted / the funnel decoded
A spoken "join the seminar tomorrow" with no name or link in the caption, so it presumably goes through his bio or stories. Web search found no public information on an Edgar Cruz trading seminar or brand (the account had about 17 comments and few likes). Price and format are unknown. The information in the post itself is all free.

### Verification & insights
- All four sites are legitimate and free to search. Google Scholar and NBER working papers would also suit this purpose.
- The paper is real and peer-reviewed (ICAIF '24). Its results are academic backtests on daily data with transaction-cost sensitivity analysis. It is not a ready strategy.
- Using an LLM to summarise papers is reasonable. Hallucinated "applications" are a risk, so check claims against the paper itself.
- Not verified: the seminar (name, price, organiser), the "Quant Finance Research Hub" site, and the model behind "Polo".

---

<a id="e-derolxfoaiu"></a>

## DerOLxFoAIu | @neuron.machinelearning | Animated recreation of Zhang et al. (2017): a 669,706-parameter MLP memorizes shuffled MNIST labels (100% train, 11.5% test)
- **Link:** https://www.instagram.com/p/DerOLxFoAIu/
- **Account:** @neuron.machinelearning (Neuron. Machine Learning) · **Posted:** 2026-10-19 · **Type:** reel (52.1s, ~8 animated scenes; scene detection caught only 3, so the 2-fps frames were reviewed)
- **Caption source:** full (Instagram)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. It is an accurate, well-known result from Zhang et al. (ICLR 2017). The parameter math checks out, and the whole script is on screen.

### Post description
> Neural networks, PhD edition 🧪
>
> Forget neurons. A network is a function f(x; θ), trained to minimize the average loss:
> R̂(θ) = 1/n Σ ℓ(f(xᵢ; θ), yᵢ)
>
> My network: 669,706 parameters. Training set: 2,000 MNIST images. That’s 335 parameters per image.
>
> Real labels → 100% train, 89.2% on unseen images.
> Now I shuffled the labels. Pure noise, nothing to learn.
> → By epoch ~30: 100% train. AGAIN.
> → On unseen images: 11.5%. Basically random guessing (10%).
>
> It didn’t learn. It memorized 2,000 random answers.
>
> Same network, same optimizer. So why does it generalize on real data at all?
> Zhang et al., ICLR 2017: “Understanding deep learning requires rethinking generalization.”
> Candidates: the implicit bias of SGD, structure in real data… still debated.
>
> Kids ✓ → Middle School ✓ → University ✓ → PhD ✓
> Real run. Comment CODE for the file.
>
> #deeplearning #machinelearning #ai #research #phd

### Audio
Voiceover (English):
[0.0] "Neural Network's PhD edition." [2.2] "Forget neurons, here's the question that keeps researchers awake." [6.2] "A network is just a function, f of x with parameters theta, tuned to minimize the average loss." [11.9] "This one has 670,000 parameters for only 2,000 training images." [17.2] "With the real labels, 100% on training, 89% on images it never saw." [23.0] "Now shuffle the labels, every answer becomes random noise." [26.9] "There is nothing left to learn." [28.5] "And yet by epoch 30, it's at 100% again." [32.2] "On new images, 11.5%, pure chance, it memorized 2,000 random answers." [38.6] "Same network, same training." [40.5] "So why does it generalize on real data at all?" [42.9] "Zhang and colleagues 2017, still an open question." [47.0] "Kids to PhD, done." [48.6] "Comment code for the file."

### On-screen content, page by page
The layout throughout: a "NEURON." header, a progress-dot strip, a "🔒 can it learn noise? at the end" chip, and a highlighted-line tag such as "line 7". Underneath is a code window, **phd.py · "19 lines · TensorFlow"**.
**Scene 1 (0–1s):** An empty code window.
**Scene 2 (1–5s):** A ladder: KIDS ✓ → MIDDLE SCHOOL ✓ → UNIVERSITY ✓ → PhD ("you are here"), with the caption "the question that keeps researchers awake". The code appears.
**Scene 3 (6–11s):** "f(x; θ) : x ↦ ŷ — a function with parameters θ"; "R̂(θ) = 1/n Σ ℓ( f(xᵢ; θ), yᵢ ) — average loss on n examples".
**Scene 4 (11–17s):** Counters run up to **669,706 parameters (784 · 512 · 512 · 10)** and **2,000 training images**.
**Scene 5 (17–22s):** A training-curve chart ("epoch 99 · 669,706 params · 2,000 images"): "real labels · train" reaches 100%; "real labels · test 89.2%".
**Scene 6 (23–26s):** A grid of MNIST digits with shuffled labels ("labels shuffled: pure noise"), and a banner reading **"NOW SHUFFLE THE LABELS"**. Line 7 is highlighted: `y_random = np.random.permutation(y)  # same labels, shuffled: pure noise`.
**Scene 7 (26–38s):** The chart again, with "random labels · train" climbing to **"random labels: 100% train"**. A dotted line is labelled "10% = random guessing". A red badge reads **"random labels · test 11.5%"**.
**Scene 8 (38–46s):** **"WHY?"** with "it can memorize noise, yet it generalizes on real data", a citation chip **"Zhang et al., ICLR 2017 · 'rethinking generalization'"**, and chips "implicit bias of SGD", "structure in real data", "flat minima?", "still debated".
**Scene 9 (46–52s):** The ladder again, "kids → PhD · complete ✓", and a button **"Comment CODE"**.
**The code (phd.py, 19 lines), summarized; not executed:** It uses NumPy and Keras. It seeds with `keras.utils.set_random_seed(0)` and loads MNIST. It keeps the first 2,000 train and test images, flattened to 784 values and scaled by /255. It builds `y_random = np.random.permutation(y)`. The model is `Sequential([Input((784,)), Dense(512, relu), Dense(512, relu), Dense(10, softmax)])`, compiled with `"adam"`, `"sparse_categorical_crossentropy"` and accuracy. It loops over `[("true labels", y), ("random labels", y_random)]`, calling `m.fit(x, labels, epochs=100, batch_size=128, verbose=0)` and printing final train accuracy and test accuracy.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Zhang et al., ICLR 2017, "Understanding deep learning requires rethinking generalization" | paper | caption, scene 8, audio 42.9s | A real, famous paper (Zhang, Bengio, Hardt, Recht, Vinyals; ICLR 2017 best-paper award). It showed that networks fit random labels perfectly. |
| 669,706 parameters | number | caption, scene 4 | Checked by arithmetic: 784·512+512 = 401,920; 512·512+512 = 262,656; 512·10+10 = 5,130; total 669,706 ✓. 669,706/2,000 = 334.9, which rounds to 335 ✓. |
| 89.2% test (real labels), 11.5% test (random labels) | numbers | caption, scenes 5–7 | Plausible for a 2-hidden-layer MLP trained on only 2,000 MNIST images. Not executed, so unverified. |
| MNIST, TensorFlow/Keras, Adam | dataset/library/optimizer | code | Standard and public. |
| "Comment CODE" | CTA | caption, scene 9 | Gets the phd.py file by DM. |

### What's being promoted / the funnel decoded
"Comment CODE" gets you the 19-line script by DM. The full script is already readable on screen (summarized above), so the DM adds nothing. The post is part of a "kids → PhD" explainer series; nothing is sold in it. The comment CTA is an engagement and DM-list tactic.

### Verification & insights
- The parameter count and the per-image ratio are arithmetically correct.
- The phenomenon (memorizing random labels to 100% train accuracy with chance-level test accuracy) is the central, widely replicated finding of Zhang et al. The explanations listed (implicit bias of SGD, data structure, flat minima) are fair, and the question really is still debated.
- Small inconsistency: the code trains for `epochs=100`, and the caption says it hit 100% on random labels "by epoch ~30". These are compatible, since 30 < 100.
- The code was read only, never executed, so the exact 89.2% and 11.5% figures are unverified (they are plausible).

---

<a id="e-deuhwjojeq4"></a>

## DeUHWJOjEQ4 | @aryanbuildsai | "5 Distributions every quant uses everyday" carousel: Binomial, Lognormal, Poisson, Student-t, Pareto, each with formula, use case and failure mode
- **Link:** https://www.instagram.com/p/DeUHWJOjEQ4/
- **Account:** @aryanbuildsai (Aryan Chirawdiya) · **Posted:** 2026-10-10 · **Type:** carousel (6 slides)
- **Caption source:** full (Instagram, fetched with yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. Accurate, compact textbook material: the formulas are correct and the 55-of-100 "≈18% by luck" figure checks out (18.4%). Nothing is sold. Two slides contain a leftover AI-writing artefact ("from your projects carousel").

### Post description
> Every risk model on Wall Street quietly picks one of five shapes, and picking the wrong one is how funds get blindsided.
>
> Binomial- a series of up or down moves, and the tree behind option pricing. It also shows why a 55 percent win rate over 100 trades proves almost nothing, since luck alone produces that about 18 percent of the time.

- **Lognormal:** prices cannot go below zero, so normal log returns make the price lognormal; enough binomial steps converge to it, the world of Black Scholes.
- **Poisson:** counts events arriving at a steady average rate (trades, loan defaults, jumps in a pricing model); assumes independence, but real markets cluster, which is where the Hawkes process comes in.
- **Student t:** bell shape with fatter tails, much closer to real daily returns.
- **Pareto:** pure power-law tail; variance can be infinite and one extreme day can outweigh years of ordinary ones.
- Closing claim: "The bell curve calls a crash impossible", and these distributions exist because markets disagree; presented as the map for the fat-tails promise from the creator's CLT post.
- CTA: save it for the next time someone calls a move a six sigma event; asks which one readers met first in a textbook ("Drop it in the comments").
- Hashtags: #quant #finance #math #studygram #trading

*Caption condensed – full text is on the original post.*

### Audio
None (image carousel).

### On-screen content, page by page
**Slide 1 (cover):** "5 Distributions EVERY QUANT USES everyday", over a dark 3D point-cloud "mountain" and terminal-style numbers. Pasted charts: a Z vs t-distribution plot ("Z distribution (standard normal)", "t-distribution (n close to 30)", "t-distribution (n smaller than 30)", μ = 0); a GeeksforGeeks "Poisson Distribution" chart (λ = 1–9, k = 0–20); and a binomial bar chart "(n,p)=(20,0.50) Zero Skewness" with the formulas "Skewness of Binomial Random Variable is E(X³)−3μσ²−μ³ / σ³ = (1−2p)/√(npq)" and "Excess Kurtosis of Binomial Random Variable is E[((X−μ)/σ)⁴] = (1−6p(1−p))/(np(1−p))".
**Slide 2, "Binomial Distribution":** "Binomial counts the successes in n independent trials that each succeed with probability p. It's the engine under the Cox-Ross-Rubinstein tree, where each step is a up or down move, and as the steps multiply that tree converges to the lognormal world of Black-Scholes. It's also how you judge a strategy's hit rate. If a strategy wins 55 of 100 trades with a true 50% chance, that happens by pure luck about 18% of the time, so 55 wins doesn't prove an edge". Formula: P(X = k) = C(n,k) pᵏ(1−p)ⁿ⁻ᵏ. The same binomial chart (n = 20, p = 0.5). "Binomial is also the source of two other distributions. For large n it turns into the normal curve, which is the CLT at work, and when n is large and p is small it turns into Poisson. It breaks when the trials aren't independent or p drifts, and real strategy win rates do both." The background is handwritten quantum-cryptography notes and a textbook page ("Chapter 7: Quantum Cryptography using Untrusted Devices", "Chapter 8: Quantum Cryptography beyond Key Distribution").
**Slide 3, "Lognormal Distribution":** "If log returns are normal, the price itself is lognormal. That's the distribution behind Black-Scholes, and it fixes the obvious problem with a normal price, which is that a stock can't go below zero. It's also right-skewed, so a few large winners pull the mean above the median." Formulas: f(x) = 1/(xσ√(2π)) · exp(−(ln x − μ)²/(2σ²)); mean = e^(μ+σ²/2), median = e^μ. Chart: "Log-Normal Distribution with Theoretical Curve" (a histogram of Value 0–5, density 0–0.75). "The mean is e^(μ+σ²/2) and the median is e^μ, so higher volatility widens the gap between them. That gap is why a high-vol stock can have a good average return and still leave the typical holder behind." The background is a Spanish-language financial terminal photo (Peruvian equities, e.g. "ALICORC1 PE PEN 8.50 +0.05", an analyst-recommendation panel).
**Slide 4, "Poisson Distribution":** "Poisson counts events in a fixed window when they arrive at a steady average rate λ. It's used for trade arrivals, loan defaults and the jumps in Merton's jump-diffusion model, and its mean and variance are both λ." The GeeksforGeeks Poisson chart (λ = 1–9). Formula: P(N = k) = λᵏe^(−λ)/k!. "It assumes events are independent, and in real markets they aren't. Trades and crashes cluster, which is the reason the Hawkes process from your projects carousel exists." The background is a stock-ticker board.
**Slide 5, "Student- t Distribution":** "The Student-t looks like a bell curve with heavier tails, controlled by the degrees of freedom ν. As ν grows it becomes the normal, and for low ν the tails get fat, which matches how real returns behave. Daily equity returns fit best around ν of 3 to 6, but fit it on your own data and don't trust that range." Formula: f(t) = Γ((ν+1)/2) / (√(νπ) Γ(ν/2)) · (1 + t²/ν)^(−(ν+1)/2). The Z vs t chart. "Variance only exists for ν above 2, and kurtosis only for ν above 4. Fit ν too low and the model says risk is infinite, which is a real warning sign that your data has extreme tails."
**Slide 6, "Pareto Distribution":** "Pareto describes a pure power-law tail, where the probability of exceeding x falls as (x_m/x)^α. The tail index α is what the Hill estimator from your projects carousel measures, and a lower α means a more extreme tail. It was first used for wealth, the original 80/20 pattern." A pdf chart for α = ∞, 3, 2, 1 (x_m = 1). Formula: P(X > x) = (x_m/x)^α, x ≥ x_m. "When α is 2 or below the variance is infinite, and when it's 1 or below even the mean is. The Law of Large Numbers converges painfully slowly, so averages from Pareto data can't be trusted until the sample is huge. That's the most dangerous distribution here, and the one that tail-risk models try to price." Background credit: "Quantum Sketches By Amy Karle, 2023".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| 55 wins of 100 at p = 0.5 → "about 18%" by luck | number | caption, slide 2 | **Correct.** P(X ≥ 55) = 0.1841, computed exactly. |
| Cox-Ross-Rubinstein tree → Black-Scholes lognormal | concept | caption, slides 2–3 | Correct: the CRR (1979) binomial tree converges to Black-Scholes as the number of steps grows. |
| Lognormal mean e^(μ+σ²/2), median e^μ | formula | slide 3 | Correct. |
| Poisson mean = variance = λ; Merton jump-diffusion | formula/model | slide 4 | Correct (Merton 1976 uses Poisson jumps). |
| Hawkes process | model | caption, slide 4 | Real self-exciting point process, used for trade clustering. |
| Student-t: variance exists for ν > 2, kurtosis for ν > 4; equity ν ≈ 3–6 | facts | slide 5 | Correct. A ν of roughly 3–6 for daily equity returns is a commonly cited empirical range. |
| Pareto: infinite variance for α ≤ 2, infinite mean for α ≤ 1; Hill estimator; 80/20 | facts | slide 6 | Correct. Pareto originally studied the distribution of land and wealth. |
| GeeksforGeeks Poisson chart; "Quantum Sketches" by Amy Karle (2023) | third-party images | slides 1, 4, 6 | Reused images. The art credit is given on slide 6; the GfG logo is visible. |
| "CLT post", "your projects carousel" | cross-references | caption, slides 4 and 6 | Refer to the creator's other posts. "From your projects carousel" is phrased as if addressed to the author, which looks like unedited AI-generated text. |

### What's being promoted / the funnel decoded
Nothing is sold. The CTAs are "Save this" and "Drop it in the comments". There is no link, comment keyword or product. The handle "aryanbuildsai" suggests an AI-builder brand, but this post has no funnel.

### Verification & insights
- I computed the binomial tail probability (18.4%) and checked every formula against the standard references. All are correct.
- **Small nits:** "first used for wealth": Pareto's 80/20 observation was about land ownership in Italy (wealth broadly), so this is fine. The "Zero Skewness" label on the binomial chart is correct for p = 0.5 only. "Every quant uses everyday" is marketing hyperbole.
- The caption's "the bell curve calls a crash impossible" is rhetorical (a normal model makes a crash extremely improbable, not impossible), but the point about fat tails is valid. It links to the same theme as @quantfinancetogo's Part 18 and 19 (DeUlwIYikQz).
- The slide 3 background shows a broker terminal with analyst names (public sell-side research listings), which is incidental.
- **Not verified:** nothing material.

---

<a id="e-depafqeo-ie"></a>

## DepAfqEo_ie | @datum.ml | "Overfitting & Underfitting, Part 1": train vs validation scores (52/49 underfit, 99/61 overfit, 91/89 good fit). The caption describes a different topic (parameters vs hyperparameters).
- **Link:** https://www.instagram.com/p/DepAfqEo_ie/
- **Account:** @datum.ml (Datum) · **Posted:** 2026-10-18 · **Type:** reel (60.2s, 1 scene page; 5 animated sections, "01/05" to "05/05")
- **Caption source:** full (Instagram, fetched by reviewer)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE: correct, standard ML teaching with no CTA beyond following. The only quirk is that the caption belongs to the previous episode (parameters vs hyperparameters) and announces this video's topic as "tomorrow".

### Post description
> 🧠 Parameters vs Hyperparameters — What's the Difference?
>
> Parameters are learned from data during training, while hyperparameters are the settings we choose before training begins. From neural network weights to learning rates and K-Means' K, every choice matters in building a better model.
>
> 📊 Learn the difference. Understand the model. Build smarter AI.
>
> 🚀 **Tomorrow on Datum.ml:** Overfitting vs Underfitting
>
> #MachineLearning #AI #DataScience #MLBasics #ArtificialIntelligence

### Audio
A synthetic-sounding narrator, with no music of note.
- [0.0–9.1] "A model scores 99% in training, but fails on new data. What went wrong? This is one of the most common problems in machine learning."
- [9.1–22.7] "It comes in two forms, underfitting and overfitting. Underfitting means the model is too simple. It misses the real pattern, so it does badly on the training data and on new data, like a student who barely studied."
- [22.7–36.2] "Overfitting is the opposite. The model is too complex. It memorizes the training data, including the noise, so it does great in training, but poorly on new data, like a student who memorized the answers without understanding them."
- [36.2–42.9] "A good fit learns the real pattern and ignores the noise. It does well on both the training data and new data."
- [42.9–56.3] "How do you spot each one? Compare the training score with the validation score. Both low, underfitting. Training high, validation much lower, overfitting. Both high and close together, a good fit."
- [56.3–60.0] "Tomorrow on datum.ml, how to fix overfitting."

### On-screen content, page by page
Header: "datum.ml · Overfitting & Underfitting · Part 1 · <section>". Each screen has a "KEY IDEA" strip and a highlighted transcript line.
**Section 0, title (0–5s):** "Machine learning, made visible · Part 1"; "Overfitting & Underfitting"; tags "Train · Test · Fit · Noise · Gap"; boxes "training score 99%" and "new data score 61%" (the number counts up from 6% to 61%).
**Section 01/05 "Two Problems" (5–12s):** a scatter of 12 points with the labels "underfitting" and "overfitting"; key idea "too simple · too complex".
**Section 02/05 "Underfitting" (12–18s):** a straight downward line through wavy data, with residuals labelled "big errors everywhere"; "training score 52%", "new data score 49%"; key idea "too simple → misses the pattern".
**Section 03/05 "Overfitting" (18–24s):** a wiggly yellow curve "passes through every point"; "training score 99%", "new data score 61%"; key idea "too complex → memorizes noise".
**Section 04/05 "A Good Fit" (24–30s):** a smooth sine-like curve labelled "learns the pattern, ignores the noise"; "training score 91%", "new data score 89%".
**Section 05/05 "Spot the Gap" (30–57s):** a table with columns model / train / valid. / verdict: "Underfit 52% 49% both low", "Overfit 99% 61% big gap", "Good fit 91% 89%"; key idea "compare train vs validation".
**End card (57–60s):** "datum.ml / Machine learning, made visible. / Next · Part 2 · How to Fix Overfitting".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| datum.ml | brand/handle | caption, header, end card | The account's brand. No website or product was found in the post. |
| Example scores 52/49, 99/61, 91/89 | numbers | screens | Illustrative, not from a real model |
| Parameters vs hyperparameters (weights, learning rate, K-Means' K) | concept | caption | Correct definitions (from the previous episode) |
| Part 2 "How to Fix Overfitting" | series | end card | The next episode |

### What's being promoted / the funnel decoded
- Nothing is sold. The post builds the audience for a daily ML explainer series. There is no link, comment keyword or product.

### Verification & insights
- The content matches standard bias–variance teaching. Underfitting means high bias (both scores low). Overfitting means high variance (a large train–validation gap). A good fit has both high and close together.
- One nuance the video skips: a good model can still show a small gap, and a high validation score needs a properly held-out set (no leakage).
- The mismatch between caption and video suggests the captions are posted one episode behind, or swapped.
- Nothing needed external verification. Could not verify who runs datum.ml.

---

<a id="e-dep8tgkty-h"></a>

## Dep8tGKTY_h | @quant.finance.inside | "LAB/02 Geometric Brownian Motion: from random paths to Black-Scholes": a Python Monte Carlo pricing of a European call (MC $10.44 vs BS $10.45)
- **Link:** https://www.instagram.com/p/Dep8tGKTY_h/
- **Account:** @quant.finance.inside (Quantitative Finance) · **Posted:** 2026-10-19 · **Type:** reel (98.3s, 2 scene pages; 6 tabbed sections MODEL / PATHS / ITO / PAYOFF / MEASURE / PRICE, with an animated code panel)
- **Caption source:** full (Instagram, fetched by reviewer with yt-dlp; the mirror copy was truncated)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE: textbook-correct quant education. I checked every number by hand (BS price 10.45, E[S_T] $108.33, Itô log growth 6%, drift/noise scaling). There is no CTA or product.

### Post description
> Black–Scholes starts with a model of how prices move.
>
> Geometric Brownian motion combines drift and random shocks. Drift scales with time; the noise's standard deviation scales with the square root of time.

- The exponential solution keeps prices positive and brings in the Itô correction: expected log-price growth is μ − σ²/2.
- Pricing a European call on a non-dividend stock: replication and no arbitrage lead to risk-neutral probabilities, so replace μ with r, average the simulated payoffs and discount.
- Hypothetical inputs: S₀ = K = $100, T = 1 year, σ = 20%, r = 5%.
- Results: 100,000 simulations → **$10.44**; Black–Scholes → **$10.45**. "Same model. Same theoretical price. The small difference is sampling error."
- Assumptions that matter: constant volatility, continuous paths and frictionless continuous trading.
- "Save this for your next Python pricing model."
- Hashtags: #QuantFinance #BlackScholes #MonteCarlo #Python #StochasticCalculus

*Caption condensed – full text is on the original post.*

### Audio
A narrator speaks over quiet background music; the speech runs to about 280 words, so these are timestamped notes with key lines quoted. Whisper's "Eto's Lemma" means Itô's lemma.
- [0.0–11.8] "How can we model a stock price when we don't know its next move?" Answer: a drift plus a random fluctuation. Drift depends on mu (μ), the instantaneous expected return; the noise strength depends on sigma (σ), the volatility.
- [11.8–22.7] "Over a short interval, drift scales with time, while noise scales with the square root of time." So at very short horizons the random part typically dominates.
- [22.7–33.0] Python build: generate independent standard normal draws and construct many paths from the same starting price; each differs but all follow the same model.
- [33.8–40.1] Solving the equation gives an exponential: prices stay positive and the future price is log-normally distributed.
- [40.8–55.0] The exponent contains "mu minus half of sigma squared", a correction from Itô's lemma: expected log-price growth is lower than μ, even though the expected price grows at the continuously compounded rate μ.
- [55.9–66.2] A European call pays the greater of final price minus strike, or zero, at expiration; the payoff is computed for every simulated price.
- [66.8–84.5] Pricing needs more than averaging real-world payoffs. Under Black-Scholes assumptions, replication and no arbitrage allow risk-neutral probabilities: for a non-dividend stock, replace μ with the risk-free rate, simulate, average the payoffs and discount to today.
- [85.1–95.9] "As we add simulations, the Monte Carlo estimate converges to the Black-Scholes price." Both calculate the same value within this model; "It all starts with an assumption about how prices move."

### On-screen content, page by page
Fixed frame: "QUANT FINANCE INSIDE · LAB / 02 · Geometric Brownian Motion · from random paths to Black-Scholes". The tabs are MODEL / PATHS / ITO / PAYOFF / MEASURE / PRICE. Footer: "hypothetical inputs · simulated data · T = 1 year", "QFI / GEOMETRIC BROWNIAN MOTION", and a seconds counter "NN / 98".
**MODEL (0–12s):** "One model. Many possible futures. S0 = $100" → "dS / S = μ dt + σ dW" (labels DRIFT, RANDOM FLUCTUATION). Chart "PRICE / USD · ILLUSTRATIVE SIMULATED PATHS", axes $50–$150 by 0.00–1.00 years. Caption "drift + random fluctuation"; footer "SIMULATED · 32 paths · annual inputs". Code file "gbm_paths.py" begins: `import numpy as np`, `rng = np.random.default_rng(7)`, `S0, mu, sigma = 100., .08, .20`.
**PATHS (12–33s):** "Drift scales with Δt / Noise SD scales with √Δt". Bar comparisons, which I verified:
- Δt = 0.2500 years: drift 2.000%, noise SD 10.000%, "Typical noise / drift = 5.0×".
- Δt = 0.1364: drift 1.091%, noise SD 7.387%, 6.8×.
- Δt = 0.0040: drift 0.032%, noise SD 1.260%, 39.7×.

Code "time_scaling.py" (`drift = mu * dt`, `noise_sd = sigma * np.sqrt(dt)`, `ratio = noise_sd / abs(drift)`). Then "simulate exact log-price increments": gbm_paths.py with T, steps = 1., 252; 32 standard-normal paths; log increments (mu − .5·sigma²)·dt + sigma·√dt·Z; cumulative exp. Footer "EXACT LOG STEPS · positive prices".
**ITO (33–55s):** "S_T = S0 exp[(μ − ½σ²)t + σW_t] · Normal log returns → lognormal prices". A histogram "DENSITY" of "PRICE AT T = 1 YEAR" ($40–$200), right-skewed. Code "terminal_prices.py" draws 100_000 normals ("log(ST/S0) is normal; ST is lognormal"). Then "The Itô correction μ − ½σ²: 8% − ½ × (20%)² = 6%"; "EXPECTED LOG RETURN 6.0% E[log(S_T / S0)]"; "EXPECTED PRICE $108.33 = 100 × exp(0.08 × 1)"; "Different quantities. Same price model."; "LOG GROWTH: 8% − 2% = 6% per year"; "E[log(ST/S0)] = 6% | E[ST] = $108.33".
**PAYOFF (55–66s):** "EUROPEAN CALL · STRIKE $100 · payoff = max(S_T − K, 0)", with a hockey-stick chart. Examples: "S_T $60 → payoff $0", "S_T $107 → payoff $7", "S_T $120 → payoff $20". Code "call_payoff.py" includes the comments `# payoff is NOT profit` and `# pricing also needs the right measure`.
**MEASURE (66–80s):** "REAL WORLD → RISK NEUTRAL: μ = 8% → r = 5%. Volatility stays at 20%" ("SAME SHOCKS · DIFFERENT DRIFT"). Code "risk_neutral.py": r, K, T = .05, 100., 1.; `# under Q, no dividends: mu -> r`; the same z is reused. Footer "Q: pricing probabilities · NOT a forecast".
**PRICE (80–98s):** "C = exp(−rT) E_Q[max(S_T − K, 0)]". Convergence chart over N on a log scale (100 to 100k), shaded "APPROX. POINTWISE 95% INTERVAL":
- 100 simulations: MC $11.37 ± $3.48 (95% CI) vs BS $10.45.
- 14,784: MC $10.37 ± $0.24.
- 100,000: MC $10.44 ± $0.09.

Code "monte_carlo_call.py" computes the discounted payoff mean and standard error, then the closed-form d1, d2 and BS price with scipy.stats.norm. Final card: "ONE MODEL · TWO METHODS: Monte Carlo $10.44 / Black–Scholes $10.45. Sampling error explains the difference. Same assumptions. Same theoretical price." Key idea: "A PRICE MODEL. A PRICING MEASURE. Constant volatility · continuous paths · Replication · no arbitrage · no dividends".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| GBM dS/S = μdt + σdW | model | MODEL tab | The standard Black-Scholes price model |
| Inputs S0 = K = 100, μ = 8%, σ = 20%, r = 5%, T = 1, 252 steps, seed 7 | parameters | code, caption | Hypothetical inputs |
| Itô correction μ − σ²/2 = 6% | number | ITO tab | Correct: 0.08 − 0.5×0.04 = 0.06 |
| E[S_T] = 100·e^0.08 = $108.33 | number | ITO tab | Correct (108.329) |
| Black-Scholes call = $10.45 | number | caption, PRICE tab | Correct: the textbook value for S = K = 100, r = 5%, σ = 20%, T = 1 is 10.4506 |
| MC 100k = $10.44 ± 0.09 | number | caption, PRICE tab | Consistent with BS within the CI. Not executed, so the exact figure is unverified, but plausible. |
| Python/NumPy/SciPy | tools | code panels | numpy default_rng, scipy.stats.norm. These are short educational snippets; I summarised them rather than copying them in full. |

### What's being promoted / the funnel decoded
- No funnel: no link, no comment keyword, no product. "Save this" is engagement bait only. "LAB / 02" implies a numbered series.

### Verification & insights
- Hand-checked: drift/noise ratios (5.0×, 6.8×, 39.7×), the Itô correction, E[S_T], and the BS price of 10.45. All are correct.
- The MC standard errors scale as expected: ±3.48 at n = 100 → ±0.09 at n = 100,000, roughly 1/√n (3.48/√1000 ≈ 0.11).
- The point about risk-neutral pricing ("Q: pricing probabilities · NOT a forecast") is correct and often misunderstood. It is the same point the @otsullu.insta delta post (DeqDC8pBTp-) makes about N(d₂).
- Caveats, which the reel itself states: constant volatility, continuous paths, frictionless trading and no dividends. Real markets have volatility smiles and jumps.
- Code not executed. The numbers are verified analytically.

---

<a id="e-deqk1wtbq-n"></a>

## DeqK1wtBq_n | @drcsdataclinic | "Hypothesis testing: 15 concepts every researcher needs": 15 animated formula cards (z, SE, α, p, Type I/II, power, t-tests, χ², ANOVA, CI duality, FWER/Bonferroni), with a "comment TEST" PDF lead magnet
- **Link:** https://www.instagram.com/p/DeqK1wtBq_n/
- **Account:** @drcsdataclinic (Dr. C's Data Clinic) · **Posted:** 2026-10-19 · **Type:** reel (37.5s, 15 pages of ~2.5s each, numbered "01 / 15" to "15 / 15")
- **Caption source:** full (Instagram, fetched by reviewer)
- **Material note:** only the cover image (m01.jpg) was supplied. I downloaded the video with yt-dlp and processed it (scene frames, 2-fps frames, transcript) in work3/DeqK1wtBq_n/.
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE: all 15 formulas are correct, and the example numbers check out (z = 2.30, t₀.₉₇₅,₂₉ = 2.045, χ² cutoff 11.07, F cutoff 3.22, FWER 95% at m = 60). The only "sale" is a free PDF in exchange for a follow and a comment.

### Post description
> A small p-value is only part of the story. 📊
>
> Explore 15 hypothesis-testing concepts every researcher should know:
>
> Null and alternative hypotheses • z test statistic • Standard error • Significance level and rejection region • p-value • Type I error • Type II error • Power • One-sample t-test • Welch two-sample t-test • Paired t-test • Chi-square test • ANOVA F-test • Confidence interval duality • Multiple testing correction.
>
> Useful across public health, medicine, psychology, business, education, and data science.
>
> 📌 Save this reel for your next analysis.
> 📘 Want the full PDF with definitions, equations, worked examples, and R and Python code? Follow and comment TEST.
>
> #Statistics #hypothesistesting #biostatistics #bioinformatics #DataScience

### Audio
Music only: a recording of Michael Jackson's "Billie Jean", identified from the audio and possibly a cover or remix. There is no speech, and the lyrics are not transcribed.

### On-screen content, page by page
Each card has a progress bar, "• Dr. C's Data Clinic" with "NN / 15", a category label, a title, a formula box, an animated chart, a one-line takeaway, and a button "Follow and comment TEST / for complete PDF with R and Python codes". Values marked "→" animate, and the final values are listed.
**Cover (m01.jpg):** "HYPOTHESIS TESTING / 15 CONCEPTS EVERY RESEARCHER NEEDS / p-values · Errors · Power / Dr. C's Data Clinic @drcsdataclinic / STATISTICS · RESEARCH · DATA SCIENCE".
**Page 1 (0–2.5s), THE SETUP, "Null & Alternative Hypotheses":** H₀: μ = μ₀ vs H₁: μ ≠ μ₀; curves H₀ and H₁, with δ = μ₁ − μ₀. "H₀ is the default claim. H₁ is what the data must support."
**Page 2 (2.5–5s), TEST STATISTIC, "The z Test Statistic":** z = (x̄ − μ₀)/(σ/√n); z → 2.30 with x̄ = 52.3, μ₀ = 50, σ = 10, n = 100; SE = σ/√n = 1.0. "How many standard errors is x̄ from μ₀?"
**Page 3 (5–7.5s), SAMPLING, "Standard Error of the Mean":** SE(x̄) = σ/√n; n → 256, SE → 0.062 (σ = 1 known); band "± SE". "Quadruple the sample size, halve the standard error."
**Page 4 (7.5–10s), DECISION RULE, "Significance Level & Rejection Region":** Reject H₀ if |z| > z_α/2; α → 0.050, z_α/2 = ±1.960; regions "reject H₀ | fail to reject | reject H₀"; "tail area is split: α/2 on each side". "Choose α first. It sets where rejection begins."
**Page 5 (10–12.5s), EVIDENCE, "The p-Value":** p = 2[1 − Φ(|z|)]; p → 0.0357; "p < α = 0.05 ⇒ reject H₀"; z_obs ≈ 2.09–2.10; "shaded: area at least this extreme". "How surprising is this data if H₀ is true?"
**Page 6 (12.5–15s), ERROR TYPE I, "Type I Error (False Positive)":** α = P(reject H₀ | H₀ true); "false alarms = 15/300 — 5.0% ≈ α = 5%"; "every dot is a test run when H₀ is true". "A true H₀ gets rejected in about α of all tests."
**Page 7 (15–17.5s), ERROR TYPE II, "Type II Error (False Negative)":** β = P(fail to reject H₀ | H₁ true); β → 0.295, 1 − β → 0.705. "More overlap between the curves means a higher β."
**Page 8 (17.5–20s), SENSITIVITY, "Statistical Power":** 1 − β = Φ(λ − z_α/2) + Φ(−λ − z_α/2), with λ = δ√n/σ; a power curve from 0.05 at λ = 0 through "0.80 at λ ≈ 2.8" to 1.00. "Larger n or a bigger effect raises power. Aim for 0.80."
**Page 9 (20–22.5s), MEANS, "One-Sample t-Test":** t = (x̄ − μ₀)/(s/√n), df = n − 1 = 29; t₀.₉₇₅,df = 2.045 vs z₀.₉₇₅ = 1.960 "normal (dashed)". "Small samples have heavier tails and wider cutoffs."
**Page 10 (22.5–25s), MEANS, "Welch Two-Sample t-Test":** t = (x̄₁ − x̄₂)/√(s₁²/n₁ + s₂²/n₂); t = 1.09/0.36 = 3.02; dot plots for group 1 and group 2. "Unequal variances? Welch is the safe default."
**Page 11 (25–27.5s), MEANS, "Paired t-Test":** t = d̄/(s_d/√n), df = n − 1; paired t = 7.07; d̄ = 3.28, s_d = 1.47, df = 9; before→after lines and bars dᵢ = after − before. "Pairing removes between-subject noise."
**Page 12 (27.5–30s), COUNTS, "Chi-Square Test":** χ² = Σ(Oᵢ − Eᵢ)²/Eᵢ; χ² → 15.2, p → 0.0095; six category bars with E = 20; cutoff 11.07 on χ²₅ under H₀. "A large χ² means the counts drift from expected."
**Page 13 (30–32.5s), GROUPS, "ANOVA F-Test":** F = MSB/MSW = [SSB/(k−1)]/[SSW/(N−k)]; F = 9.67, df = (2, 42); groups A, B, C; cutoff 3.22. "Between-group variance versus within-group variance."
**Page 14 (32.5–35s), INTERVALS, "Confidence Interval Duality":** x̄ ± t_α/2,n−1 · s/√n; 20 intervals around μ₀ = 0, of which "reject H₀: 14/20"; "CI excludes μ₀: reject / CI covers μ₀: keep". "A CI that excludes μ₀ ⇔ reject H₀ at α."
**Page 15 (35–37.5s), CORRECTION, "Multiple Testing Correction":** FWER = 1 − (1 − α)^m, α_adj = α/m; curves 1 − (1 − α)^m and 1 − (1 − α/m)^m for m = 1…60; at m = 60: 95% vs 4.9%. "Many tests inflate false positives. Correct the threshold."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| 15 test concepts (list above) | content | caption, pages 1–15 | Standard intro-statistics material. All formulas are correct. |
| Example values (z = 2.30; SE 0.062 at n = 256; ±1.960; p = 0.0357; β = 0.295; λ ≈ 2.8 for 80% power; t = 2.045 at df 29; χ² 15.2 p = 0.0095, cutoff 11.07 at df 5; F = 9.67, cutoff 3.22 at df (2, 42); FWER 95%/4.9%) | numbers | pages | Hand-checked and correct (see below) |
| "Follow and comment TEST" | CTA | caption, every page | An auto-DM with a "complete PDF with R and Python codes" |
| Dr. C's Data Clinic | brand | cover, header | A statistics, research and data-science education account. Its owner's identity was not verified. |
| "Billie Jean" (Michael Jackson) | music | audio | Background track |

### What's being promoted / the funnel decoded
- **Comment "TEST" (and follow)** gets the free PDF "with definitions, equations, worked examples, and R and Python code". This is follower and engagement growth plus DM-list building. No price or paid product was seen in the post, and none was found.

### Verification & insights
- Hand checks:
  - (52.3 − 50)/(10/√100) = 2.30.
  - 1/√256 = 0.0625.
  - z₀.₉₇₅ = 1.960.
  - 2[1 − Φ(2.10)] ≈ 0.036.
  - Power 0.80 needs λ ≈ 1.96 + 0.84 = 2.80.
  - t₀.₉₇₅,₂₉ = 2.045.
  - Paired: 3.28/(1.47/√10) = 7.06 ≈ 7.07.
  - Welch: 1.09/0.36 = 3.03 (shown as 3.02, a rounding difference).
  - χ²₀.₉₅,₅ = 11.07, and P(χ²₅ > 15.2) ≈ 0.0095.
  - F₀.₉₅(2, 42) ≈ 3.22.
  - 1 − 0.95⁶⁰ = 0.954.
  - 1 − (1 − 0.05/60)⁶⁰ ≈ 0.049.
- One small presentational point: page 14's "14/20 reject" is a simulated case where H₀ is false. It is not a coverage claim.
- Uses a commercial song as background. That is common on Instagram, but rights are handled by the platform's licensing.
- The PDF itself was not obtained (doing so would require engaging with the funnel).

---

<a id="e-deex52fdcg3"></a>

## DeeX52FDCg3 | @aryanbuildsai | "4 Advanced Quant Projects to build in college": Marchenko-Pastur matrix cleaning, Avellaneda-Stoikov market making, Kalman-filter hedge ratio, Almgren-Chriss optimal execution (with formulas)
- **Link:** https://www.instagram.com/p/DeeX52FDCg3/
- **Account:** @aryanbuildsai (display name not in data) · **Posted:** 2026-10-14 (decoded from the post ID) · **Type:** carousel (5 slides)
- **Caption source:** possibly truncated (mirror). The yt-dlp full-caption fetch returned HTTP 429.
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. All four projects are standard, well-known quant models. Every formula shown is correct, and the project descriptions are accurate and appropriately cautious (out-of-sample comparisons, "check that your simulation agrees"). No product is visible. Any CTA would be in the truncated part of the caption.

### Post description
> Most of your correlation matrix is noise, and there is a theorem that tells you exactly which part.
>
> Four quant projects that go past moving averages and teach the math real desks use:
>
> Marchenko-Pastur - run it on a real stock correlation matrix and...

(cut off by the mirror; the full caption could not be retrieved because Instagram returned 429)

### Audio
Not applicable (image carousel).

### On-screen content, page by page
**Slide 1 (cover):** "4 Advanced **QUANT PROJECTS** to build in college". It is a collage over a dark 3-D point-cloud image, showing:
- the Avellaneda-Stoikov spread formula δᵃ + δᵇ = γσ²(T − t) + (2/γ) ln(1 + γ/k);
- a "Bayesian Update in 1D Kalman Filter (Gaussian)" plot;
- the Kalman gain and update formulas K_t = P_{t|t−1} x_t / (x_t² P_{t|t−1} + R), β̂_t = β̂_{t|t−1} + K_t (y_t − x_t β̂_{t|t−1});
- two density plots (dψ(x)/dx curves for λ = 0.3, 0.6, 1, 1.3, 1.6);
- a market-making price chart (reserved price, mid price, bid, ask, optimal_bid, optimal_ask, around 0.02190–0.02220).

**Slide 2: "Run Marchenko-Pastur on a real stock correlation matrix"**
> "Pull daily returns for a few hundred stocks, build the correlation matrix, and plot its eigenvalues against the Marchenko-Pastur density. That density describes what a matrix of pure noise would look like for the same number of assets N and observations T. Eigenvalues inside the band between λ₋ and λ₊ can't be told apart from noise, so only the few above λ₊ carry real structure, and the largest is the market factor."

Formulas: λ± = σ²(1 ± √q)², q = N/T; ρ(λ) = (1 / 2πqσ²) · √((λ₊ − λ)(λ − λ₋)) / λ.
Images: a "Correlation Matrix Heatmap" for AAPL, MSFT, GOOG, ADBE, CRM, XOM, CVX, COP, PSX, OXY (tech names correlate about 0.6–0.8 with each other, energy names about 0.7–0.9 with each other, cross-sector about 0.2–0.4); a histogram "Marchenko-Pastur Theorem (1000, 5000)" with the theoretical curve, λ from about 0.25 to 2.1.
> "Clean the matrix by flattening the noise eigenvalues and keeping the signal ones, then build a minimum variance portfolio from both the raw and the cleaned matrix and compare them out of sample. The gap between the two is what trusting noise costs you, and measuring it is the whole point."
The background is a blurred trading-platform screen.

**Slide 3: "Simultate [sic] Avellaneda-Stoikov market making and watch inventory risk"**
> "A market maker earns the spread, but every fill changes inventory, and inventory is risk. Avellaneda and Stoikov solve this by quoting around a reservation price instead of the mid price. If you're long, both quotes shift down so you sell more easily, and if you're short they shift up. The quoted spread widens with volatility and with the time left in the session."

Formulas: r(s,t) = s − qγσ²(T − t); δᵃ + δᵇ = γσ²(T − t) + (2/γ) ln(1 + γ/k).
Chart: reserved price / mid price / bid / ask / optimal_bid / optimal_ask (y-axis 0.02190–0.02220).
> "Simulate a Brownian mid price with Poisson order arrivals whose intensity falls as you quote further from the mid, then run the strategy against a naive symmetric quote and compare profit and inventory. The paper reports that inventory-aware quoting reduces the spread of outcomes at a small cost in average profit. Check that your simulation agrees before you believe it."
The background is a trading floor with a market-data board.

**Slide 4: "Replace a fixed hedge ratio with a Kalman Filter"**
> "A static OLS hedge ratio assumes the relationship between two stocks never changes, but it drifts. Treat the hedge ratio β as a hidden state that follows a random walk, and the Kalman filter updates it every day. It's a Bayesian update that weighs the new price against the previous estimate, with the weight (the Kalman gain) set by how noisy you think each one is."

Formulas: y_t = β_t x_t + ε_t, β_t = β_{t−1} + w_t; K_t = P_{t|t−1} x_t / (x_t² P_{t|t−1} + R); β̂_t = β̂_{t|t−1} + K_t (y_t − x_t β̂_{t|t−1}).
Chart: "Bayesian Update in 1D Kalman Filter (Gaussian)", with Prior P(x) (green), Likelihood P(z|x) (red) and Posterior P(x|z) (blue), x from −4 to 6.
> "The spread you trade is the filter's prediction error, and dividing it by its own standard deviation gives a live z score for entries and exits. The process noise Q is the knob that matters: too high and β chases noise, too low and you've rebuilt OLS. Backtest it against a rolling OLS hedge on the same pair, out of sample"

**Slide 5: "Solve Almgren-Chriss and find the cheapest way to sell a large position"**
> "Selling a large position in one go moves the price against you, but selling slowly leaves you exposed to price moves while you wait. Almgren-Chriss turns that trade-off into one objective: minimise expected cost plus λ times the variance of cost, where λ is your risk aversion. With linear temporary impact the optimal schedule has a closed form, so a patient trader sells almost evenly and a nervous one sells early."

Formulas: min over x of E[C] + λ Var[C]; x(t) = X · sinh(κ(T − t)) / sinh(κT), κ = √(λσ²/η).
Chart: "Optimal Trajectories (Figure 2 in AC paper)", share holdings (×1e6) vs time period j = 0–5, for lambda near zero = 1e-8, very low = 0.25e-6, low = 0.5e-6, med = 1e-6, high = 2e-6, very high = 4e-6.
> "Plot trajectories for several values of λ, plus the efficient frontier of expected cost against variance. Then swap in square root impact, which is closer to what real data show, and see how the schedule changes. The model's linear impact is a simplification, and finding where it breaks is the useful part"
The background is a notebook with handwritten finance notes (convertible-bond "conversion value" formulas) and a stopwatch showing "5:06:25.20". These are decorative.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Marchenko-Pastur law | theorem | caption; slides 1–2 | Random-matrix result (Marchenko & Pastur, 1967) for the eigenvalue density of noise covariance matrices. It is applied to finance by Laloux, Cizeau, Bouchaud & Potters (1999) and Plerou et al. (1999), and to "eigenvalue clipping" by López de Prado (*Machine Learning for Asset Managers*, 2020). The formulas shown are correct. |
| Avellaneda-Stoikov | model/paper | slides 1, 3 | M. Avellaneda & S. Stoikov, "High-frequency trading in a limit order book", *Quantitative Finance* 8(3), 2008. The reservation price r = s − qγσ²(T − t) and optimal total spread γσ²(T − t) + (2/γ)ln(1 + γ/k) match the paper. The paper did find a lower P&L standard deviation for the inventory strategy at a slightly lower mean profit than the symmetric strategy. |
| Kalman filter hedge ratio | method | slides 1, 4 | Standard dynamic-beta pairs-trading method (e.g. E. Chan, *Algorithmic Trading*, 2013). The scalar gain and update equations are correct. |
| Almgren-Chriss | model/paper | slide 5 | R. Almgren & N. Chriss, "Optimal execution of portfolio transactions", *Journal of Risk* 3, 2000/2001. The sinh trajectory with κ = √(λσ²/η) is the continuous-time solution, and "Figure 2" refers to the paper's trajectory figure. |
| Square-root impact | concept | slide 5 | Empirical market-impact law (impact ∝ √(volume/ADV)), widely documented (e.g. Bouchaud et al.; Tóth et al. 2011). |
| Minimum-variance portfolio, out-of-sample test | method | slide 2 | Standard portfolio-construction test. |
| AAPL, MSFT, GOOG, ADBE, CRM, XOM, CVX, COP, PSX, OXY | tickers | slide 2 heatmap | Real US tickers (five tech/software, five energy) in an example correlation heatmap. |
| @aryanbuildsai | handle | account | The creator. Web search found no linked site or product. |

### What's being promoted / the funnel decoded
- No call to action is visible on the slides. The caption is truncated after the first project, so a CTA (e.g. "comment X for code") may follow but could not be read. No product, course or link was identified.

### Verification & insights
- Every formula was checked against the original papers and textbooks: Marchenko-Pastur bounds and density, Avellaneda-Stoikov reservation price and spread, scalar Kalman gain and update, Almgren-Chriss trajectory and κ. All are correct.
- The descriptions are accurate and include sensible caveats: compare raw vs cleaned matrices out of sample; test whether a simulation reproduces the paper; compare the Q trade-off against rolling OLS; note where linear impact fails.
- Practical notes: Marchenko-Pastur assumes i.i.d. returns, and real returns have fat tails and time-varying volatility, so the "noise band" is approximate. Avellaneda-Stoikov needs calibrated k (order-arrival decay) and γ, and naive implementations ignore adverse selection. Kalman pairs trading still faces regime breaks and costs.
- The slide images (heatmap, MP histogram, AS chart, AC "Figure 2" replication, Kalman Bayesian plot) look reused from public notebooks and blogs. They are illustrative, not the creator's own results.
- Not verified: the full caption and any CTA (Instagram returned 429).

---

<a id="e-depjrwctzao"></a>

## DepjRwcTZAo | @thetaquant | Animated explainer: Fourier analysis (ocean waves) applied to option pricing via the Fourier-cosine (COS) method, converging to $9.93
- **Link:** https://www.instagram.com/p/DepjRwcTZAo/
- **Account:** @thetaquant (Theta) · **Posted:** 2026-10-18 · **Type:** reel (51s, 1 scene-change page; ~11 distinct animated screens reviewed from 2-fps frames)
- **Caption source:** full (Instagram, fetched with yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – accurate pop-science explainer of Fourier option pricing; the history in the caption checks out; no product or CTA

### Post description
> In 1807, French mathematician Joseph Fourier introduced a radical idea: even the most complicated patterns of heat could be understood through combinations of simple oscillations.
>
> His work on heat conduction, later published in The Analytical Theory of Heat in 1822, laid the foundations of Fourier analysis.
>
> Nearly two centuries later, the same mathematical machinery found an unexpected application on Wall Street.
>
> In 1993, Heston introduced a stochastic volatility model whose characteristic function could be used for option pricing. In 1999, Peter Carr and Dilip Madan showed how Fourier transforms could efficiently compute option prices.

(No hashtags. The mirror copy was cut off after "The Analytical Theory..."; the full text above came from Instagram.)

### Audio
A narrated voice-over (calm narrator) over a soft background bed. No song is identifiable and no lyrics are present.
- [0.0–4.5] "Can the same mathematical patterns found in ocean waves also appear in finance?"
- [4.5–9.7] "An ocean may look chaotic, but its surface can be represented as a combination of simpler waves."
- [9.7–13.3] "Each wave has its own frequency, amplitude and phase."
- [13.3–18.0] "Using Fourier analysis, we can separate these frequencies and reveal the hidden structure."
- [18.0–20.7] "And something similar happens in quantitative finance."
- [20.7–24.6] "This allows us to work with frequencies rather than individual outcomes."
- [24.6–26.6] "And here is where it gets interesting."
- [26.6–31.0] "Each frequency contributes to the mathematical calculation of an option price."
- [31.0–34.2] "Some contributions are positive, while others are negative."
- [34.2–37.9] "As we combine more terms, the approximation begins to converge"
- [37.9–43.4] "until the entire calculation produces a single number, $9.93."

### On-screen content, page by page
The scene detector caught only the first frame because the animation fades slowly. Screens below come from the 2-fps frames; times are approximate.

**Page 1 (0–~3s):** Jane Street logo (blue rings, "Jane Street") fading in on a dark background.
**Page 2 (~3–6s):** Jane Street logo + "CAN THE SAME PATTERNS IN OCEAN WAVES SHOW UP IN FINANCE?" over a photo of a breaking ocean wave.
**Page 3 (~6–12s):** "AN OCEAN HIDES MANY FREQUENCIES". An animated 3D wire-mesh wave surface.
**Page 4 (~12–20s):** "COMPLEX ROTATIONS BUILD THE WAVE". A rotating phasor (vector in a circle) traces out a wavy line, i.e. a sum of sinusoids.
**Page 5 (~21–25s):** "THE WAVE BECOMES A SPECTRUM". A wiggly time-series line above a bar chart with 4 frequency bars of decreasing height (teal, purple, green, yellow).
**Page 6 (~25–32s):** "UNCERTAINTY HAS A SPECTRUM TOO". A complex plane with axes labelled "Im" and "Re", and a spiral winding inward to the origin. This depicts a characteristic function.
**Page 7 (~33–37s):** "EACH FREQUENCY ADDS TO THE OPTION PRICE". Formula C_N = e^(−rT) Σ′_{k=0}^{N−1} A_k V_k. Bar chart over k = 0–5: a large positive bar at k=0, tiny at 1, a large negative (red) bar at 2, tiny at 3, a small positive bar at 4, ~0 at 5.
**Page 8 (~37–45s):** "WAVES CANCEL / THE PRICE CONVERGES". A counter of Fourier modes with the running price and "REFERENCE $9.9251" at the bottom:
- "1 FOURIER MODE": $44.842
- then a few intermediate mode counts (digits blurred mid-transition, about 2 and 4 modes); one frame reads $11.476
- "16 FOURIER MODES": $9.925
- "64 FOURIER MODES": $9.925, with a bar strip of 64 small terms

**Page 9 (~46–51s):** "ONE EUROPEAN CALL OPTION", "$9.93", "64 MODES / FOURIER-COSINE PRICING".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Jane Street (logo) | company | Pages 1–2 | Real quant trading firm. The post gives no evidence that @thetaquant is affiliated; the logo is used as a hook |
| Joseph Fourier, 1807 | person/date | caption | Correct: Fourier's 1807 memoir on heat propagation |
| *The Analytical Theory of Heat*, 1822 | book | caption | Correct: *Théorie analytique de la chaleur*, 1822 |
| Heston (1993) stochastic volatility model | paper | caption | Correct: Steven Heston, *Review of Financial Studies* 1993, closed-form solution via the characteristic function |
| Peter Carr & Dilip Madan (1999) | paper | caption | Correct: "Option valuation using the fast Fourier transform", *Journal of Computational Finance*, 1999 |
| Fourier-cosine pricing (COS) | method | Page 9; formula on page 7 | The COS method of Fang & Oosterlee (2008). The formula shown has the COS structure (discounted primed sum of A_k·V_k) |
| $44.842 / $11.476 / $9.925 / $9.93 | numbers | Pages 8–9; audio 43s | Successive approximations at 1, a few, 16 and 64 modes |
| REFERENCE $9.9251 | number | Page 8 | Parameters are not shown. By hand calculation (not run as code), Black–Scholes with S=K=100, T=1, r=4%, σ=20% gives ≈ $9.925, so it fits a standard test case |

### What's being promoted / the funnel decoded
Nothing is sold and there is no call to action. This is an educational/brand-building quant-animation account.

### Verification & insights
- All four historical facts in the caption are accurate (Fourier 1807/1822, Heston 1993, Carr–Madan 1999).
- The math shown is a sound simplification. Option pricing via the characteristic function, the COS series with alternating-sign coefficients, and fast convergence (16 terms already at $9.925) are all real properties of the COS method.
- Ocean waves are an analogy only. The post makes no claim that markets are wave-like or predictable with cycles, and it should not be read as a "Fourier cycles predict price" trading idea.
- The Jane Street branding implies a connection that could not be verified. Web search found no information on the @thetaquant account.
- Could not verify: the exact model parameters behind $9.9251 (only inferred), and who runs @thetaquant.

---

<a id="e-ded3ruocxgg"></a>

## DeD3ruoCXGg | @quantfinancetogo | Quant Finance from Scratch Part 13: the Markowitz efficient frontier, built from 5,000 random mixes of three simulated assets in 16 lines of NumPy (825 mixes on the edge)
- **Link:** https://www.instagram.com/p/DeD3ruoCXGg/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-04 · **Type:** reel (101.8s, 1 scene page; one continuous animation, reviewed from the 2-fps frames)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; the mirror copy was cut off at "…11 ...")
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct, self-contained teaching video. I re-ran the code shown on screen and it reproduces every number exactly. There is no funnel.

### Post description
> ➡️ Quant Finance from scratch Part 13: the efficient frontier
>
> Step 1, three simulated assets with assumed numbers, not forecasts: A, like bonds, earns 4 % a year at 6 % risk (volatility), B, like stocks, 7 % at 18 %, and C, like a riskier stock, 11 % at 25 %.

- **Step 1 (cont.):** A moves on its own; B and C have a correlation of 0.5. For real assets these inputs would have to be estimated from data.
- **Step 2, every mix is a dot:** the program mixes the three assets in 5,000 random ways (weights 0–100 %, summing to 100 %) and plots each on a map with risk across and expected return up. A mix's risk depends on how its assets move together, which is why mixing can lower it (Parts 10 and 11).
- **Step 3, the upper edge:** at every risk level the mixes on the cloud's upper edge earn the most. The program sorts mixes by risk and keeps one only if it earns more than every lower-risk mix; **825 of the 5,000 pass**.
- **Lowest-risk mix:** swings **5.7 %** (return **4.4 %**), a little less than A alone.
- **Asset B vs the edge:** at the same 18 % risk the edge earns **9.1 %** instead of **7.0 %**, so its Sharpe ratio (Part 8, safe rate 3 %) is **0.34** instead of **0.22**. Along the edge more return always costs more risk; the right point depends on how much risk someone wants.
- More mixes bring the edge closer to the exact frontier, which the caption says Markowitz showed in **1956** can be computed directly by quadratic programming.
- **History:** Harry Markowitz, "Portfolio Selection" (Journal of Finance, **1952**). He shared the **1990** Nobel prize in economics with Merton Miller and William Sharpe, for having developed the theory of portfolio choice, whose core picture is this curve.
- Everything is simulated with a fixed seed, nothing was downloaded, and every number comes from a real run of the code. "This video is for education only, and nothing in it is financial advice."
- **Hashtags:** #quantfinance #portfoliotheory #efficientfrontier #markowitz #python

*Caption condensed – full text is on the original post.*

### Audio
English voice-over (the creator's narration) over soft background music. No identifiable song. Condensed to timestamped notes:
- [0.0–9.4] Hook: "Harry Markowitz won a Nobel Prize for this curve." It shows the best portfolios you can build; the video shows how to find it. "Quantitative Finance from Scratch, Part 13."
- [10.3–27.3] Three simulated assets with assumed numbers (real ones would have to be estimated): A, like bonds, 4 % a year at 6 % risk; B, like stocks, 7 % at 18 %; C, a riskier stock, 11 % at 25 %.
- [27.3–49.7] On a risk-across / return-up map each asset is a dot. The program mixes them in 5,000 random ways; each mix is a dot and together they fill a cloud. At every risk level the mixes on the upper edge earn the most and all below earn less for the same risk: "This upper edge is the efficient frontier."
- [49.7–69.6] To find it, the program sorts mixes by risk and keeps a mix only if it earns more than every lower-risk mix; 825 pass. The first one kept is the lowest-risk mix, at 5.7 %, slightly below asset A alone, because mixing lowers risk (Part 11).
- [69.6–86.2] Even asset B sits below the edge: at the same 18 % risk the edge earns 9.1 % instead of 7 %, which means a higher Sharpe ratio (Part 8). Along the edge more return always costs more risk, so the right point depends on how much risk someone wants to take.
- [86.2–100.2] Recap: mix the assets in every way, put each mix on the risk/return map, and at every risk level keep the mix that earns the most. CTA: "Follow to really learn quantitative finance."

### On-screen content, page by page
Fixed layout throughout. Header "QUANT FINANCE FROM SCRATCH ▌ · PART 13". Episode tabs 13 (highlighted), 14, 15, 16, 17, 18, 19, 20, 21. A chart panel with a caption bar, a code editor `frontier.py` ("python · running"/"done") and the footer "simulated assets, assumed numbers · education only · not financial advice".
**Segment 1 (0–4s), title "The Nobel Prize Curve", subtitle "5,000 simulated portfolios on one map":** The animated cloud of portfolios with a glowing upper edge. Caption bar: "5,000 portfolios, one map · risk across, return up". A pop-up reads "KEY IDEA — Efficient Frontier".
**Segment 2 (4–8s):** The complete 16-line code is shown at once. Excerpt (lines 3–12, the core logic):
```
3  m = np.array([0.04, 0.07, 0.11])        # return
4  s = np.array([0.06, 0.18, 0.25])        # risk
5  corr = [[1, 0, 0], [0, 1, .5], [0, .5, 1]]
6  C = np.array(corr) * np.outer(s, s)     # together
7  w = rng.dirichlet([1, 1, 1], 5000)      # mixes
8  r = w @ m                               # mix return
9  v = np.sqrt((w @ C * w).sum(1))         # mix risk
10 o = np.argsort(v)                       # low to high
11 top = np.maximum.accumulate(r[o])       # best so far
12 edge = o[r[o] >= top]                   # the frontier
```
The rest: line 1 imports NumPy and line 2 creates the random generator with `np.random.default_rng(13)` (seed 13). Line 13 prints how many of the 5,000 mixes are on the edge ("825 of 5000 mixes on the edge"). Line 14 picks the lowest-risk edge mix `t = edge[0]` and the last edge mix with risk ≤ B's 18 % (`edge[v[edge] <= s[1]][-1]`). Lines 15–16 print "lowest risk 5.7%, return 4.4%" and "edge at B's risk 9.1%, B 7.0%" (formatted to one decimal as percentages).
**Segment 3 (8–10s):** Title card "QUANTITATIVE FINANCE FROM SCRATCH ▌" with a small animated curve.
**Segment 4 (10–28s), title "The Efficient Frontier", subtitle "the most return for every level of risk":** Axes expected return 4–12%, risk 0–25%. Caption bar "three simulated assets · assumed numbers". The code types lines 3–5. Labels appear: "A, like bonds — 4 % return · 6 % risk" ("A: 4 % at 6 % risk"), "B, like stocks — 7 % return · 18 % risk" ("B: 7 % at 18 % risk"), "C, like a riskier stock" ("C: 11 % at 25 % risk"). A tag reads "SIMULATED ASSETS · ASSUMED NUMBERS — how they move together: A alone, B and C 0.5".
**Segment 5 (28–40s):** "every mix is a dot · risk across, return up", then "random weights, 5,000 mixes". Lines 6–9 are typed. Dots fill the cloud with the counter "mixes 4,620" running up to 5,000.
**Segment 6 (40–50s):** "at every level of risk · same risk, less return below". Vertical slices through the cloud highlight the top dot in each slice. Then "the efficient frontier" with a KEY IDEA pop-up, "Efficient Frontier".
**Segment 7 (50–59s):** "from low to high risk · sort by risk". Lines 10–13 are typed. A sweep line runs right, with the counter "kept 825". Output tag: "> 825 of 5000 mixes on the edge" ("825 of 5000 on the edge").
**Segment 8 (59–69s):** "the lowest risk · 5.7 %". Zoom on the tip of the frontier: "LOWEST RISK IN THIS SIMULATION", "> lowest risk 5.7%, return 4.4%", vertical markers "5.7 %" vs "6.0 %" (A). Caption "5.7 % against A's 6.0 %". A tag reads "a mix of A, B and C — part 11".
**Segment 9 (69–79s):** "B alone · same risk, 18 %", then "edge 9.1 % against B 7.0 %". Labels "9.1 %" (edge) and "7.0 %" (B). Tag "> edge at B's risk 9.1%, B 7.0%". Then "Sharpe 0.34 against 0.22": two lines from "safe 3 %" on the y-axis, one to the edge point ("Sharpe 0.34") and one to B ("Sharpe 0.22"), with a dot-colour legend "dot colour = Sharpe ratio".
**Segment 10 (79–86s):** "along the edge · more return, more risk". A marker slides along the frontier with live labels, for example "return 8.0 % / risk 14.5 %", "return 8.2 % / risk 15.1 %" and "return 10.1 % / risk 21.7 %". Annotations: "less risk, less return" and "more return, more risk".
**Segment 11 (86–101.8s), title "The Nobel Prize Curve", subtitle "at every level of risk, keep the top mix":** Box "HOW DO YOU FIND THE CURVE?" with "1 Mix the assets in every way." / "2 Put each mix on the risk and return map." / "3 At every level of risk, keep the top mix." Caption bar "the answer · keep the top mix". End text: "follow to really learn quant finance".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Harry Markowitz, "Portfolio Selection", Journal of Finance, 1952 | paper | caption, audio 0.0s | Real: J. Finance 7(1):77–91, 1952. The founding paper of modern portfolio theory. |
| Markowitz 1956, quadratic programming | paper | caption | Real: "The Optimization of a Quadratic Function Subject to Linear Constraints", Naval Research Logistics Quarterly, 1956 (the critical-line algorithm). |
| 1990 Nobel (economics), shared with Merton Miller and William Sharpe | fact | caption, audio | Correct. The Nobel citation credits Markowitz for "having developed the theory of portfolio choice". |
| Efficient frontier | concept | title, caption | Standard mean-variance concept. Correctly explained. |
| Sharpe ratio, safe rate 3% (Part 8) | concept/number | caption, segment 9 | (9.1 − 3)/18 ≈ 0.34 and (7 − 3)/18 ≈ 0.22. Correct. |
| Inputs A 4%/6%, B 7%/18%, C 11%/25%, corr(B,C) = 0.5, seed 13, 5,000 Dirichlet(1,1,1) mixes | parameters | caption, code | Assumed numbers, as the post says. |
| 825 of 5,000; lowest risk 5.7% (return 4.4%); edge at 18% risk 9.1% vs B 7.0% | results | caption, audio, screen | **Reproduced exactly** by re-typing the 16 on-screen lines and running them locally (my own transcription; no downloaded code). |
| Parts 8, 10, 11 (and 14–21 tabs) | series references | caption, tab bar | Earlier and later episodes of the same series (Part 14 "market beta" is also in this collection: DeFCbkaiVMa). |

### What's being promoted / the funnel decoded
Nothing is sold. The only CTA is "Follow to really learn quantitative finance". There is no comment keyword, link, product or affiliate.

### Verification & insights
- **Code check:** I ran the exact script with NumPy and got `825 of 5000`, `lowest risk 5.7%, return 4.4%`, `edge at B's risk 9.1%, B 7.0%` (the edge point's risk is 17.99%), and Sharpe 0.336 vs 0.222.
- **Small nuance:** line 12 uses `>=`, so a mix is kept when it earns *at least* as much as every less-risky mix. The caption says "more than". With continuous random weights there are no ties, so this makes no practical difference.
- **Accuracy:** the explanation is textbook-correct. The random-sampling "upper edge" is only an approximation of the true frontier, which the caption itself notes (exact solution by quadratic programming). The caption also states the big real-world caveat: the inputs (expected returns, volatilities, correlations) must be estimated, and mean-variance optimisation is notoriously sensitive to errors in expected returns.
- **Historical facts:** all correct (1952 paper, 1956 QP, 1990 Nobel co-laureates).
- **Not verified:** nothing material. Both the account's identity and the series are anonymous-brand educational content.

---

<a id="e-deo-8t-k5cj"></a>

## Deo_8t_k5cJ | @arwazaz_ | 8-slide "ML trading strategies for free" roadmap: Python/pandas/scikit-learn/Backtesting.py workflow, with example (illustrative) model and backtest metrics and a "comment ROADMAP" DM funnel
- **Link:** https://www.instagram.com/p/Deo_8t_k5cJ/
- **Account:** @arwazaz_ (display name not in data; slides are branded "ARWAZ AZ · ALGO TRADING | AI | SYSTEMS") · **Posted:** 2026-10-18 (decoded from the post ID; no upload_date in the data) · **Type:** carousel (8 slides)
- **Caption source:** possibly truncated (mirror). The caption is cut off at "Scik...". A yt-dlp re-fetch hit HTTP 429 from Instagram (one attempt, not retried).
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE (educational). Every tool named is real and free (Python, pandas, scikit-learn, Backtesting.py, TradingView free plan, Yahoo Finance/Alpha Vantage/Polygon free tiers). The pipeline and the validation advice are standard and sound. All the metrics shown are labelled "example" and are illustrative, not results. The CTA is a comment-for-DM lead magnet.

### Post description
> Comment ROADMAP and I'll share the tools and resources to start building your own machine-learning trading strategy for free.
>
> You don't need an expensive AI subscription to begin exploring ML in algorithmic trading.
>
> You can use Python, Pandas, Scik...

(Cut off by the mirror. The rest of the caption, including any hashtags, was not retrievable.)

### Audio
None. This is an image carousel.

### On-screen content, page by page
Every slide has the header "ARWAZ AZ / ALGO TRADING | AI | SYSTEMS" and a page counter "0N/08". Slide 1 also says "REAL INVESTMENT WISDOM INTO ALGORITHMS". The art is a glossy, AI-generated-looking infographic style; slide 3's scikit-learn logo is misspelled "ccikit".

**Slide 1 (01/08):** "WINNING STRATEGIES WITH MACHINE LEARNING **FOR FREE.**" Subtitle: "A practical roadmap to build, test and validate your own ML trading strategy." Handwritten note: "Same Data. Better Insights. Smarter Strategies." Graphic: Python logo → DATA / ML MODEL / BACKTEST. A laptop shows code, quoted here as a short excerpt: `from sklearn.ensemble import RandomForestClassifier`, `model = RandomForestClassifier(n_estimators=200, random_state=42)`, `model.fit(X_train, y_train)`, `pred = model.predict(X_test)`, `proba = model.predict_proba(X_test)`. Footer: "REAL MARKET DATA · OPEN SOURCE TOOLS · TEST & VALIDATE · IMPROVE REPEAT · SWIPE NEXT".

**Slide 2 (02/08):** "FROM IDEA TO A TESTED STRATEGY." "A step-by-step workflow to build, test and validate machine learning trading strategies (using free tools)." Note: "Clear Process. Real Tools. Practical Results." Seven steps:
1. GET DATA: "Download historical market data." Yahoo Finance, Alpha Vantage, Polygon (free tier).
2. CREATE FEATURES: "Convert raw data into useful inputs." Returns, Moving Averages, Volatility, Volume, Trend Indicators, …
3. TRAIN ML MODEL: "Use machine learning to find patterns." Logistic Regression, Random Forest, XGBoost, Other Models.
4. GENERATE SIGNALS: "Model predicts probabilities." "Buy Signal (Probability ↑)". Model Output: Probability (Up) 0.72, Probability (Down) 0.28.
5. BACKTEST STRATEGY: "Turn signals into trading rules and test on historical data." ✔ Entry & Exit Rules ✔ Position Sizing ✔ Transaction Costs ✔ Slippage.
6. VALIDATE RESULTS: "Check if strategy is robust and not overfitted." Chart split Train / Test / Out-of-Sample. ✔ Out-of-sample testing ✔ Walk-forward validation ✔ Multiple market conditions ✔ Compare with baseline.
7. REFINE & REPEAT: "Improve features, test new ideas and iterate." Cycle: New Ideas → Improve Features → Test Again → Analyze Results.
Footer: "A COMPLETE RESEARCH PIPELINE: From data to a validated strategy using free tools and machine learning."

**Slide 3 (03/08):** "FREE TOOLS TO BUILD ML TRADING STRATEGIES." "You don't need expensive software. These free and open-source tools are enough to build, test and validate machine learning strategies."
1. PYTHON: "The programming language for trading and machine learning." ✔ Flexible and powerful ✔ Huge community ✔ Free and open source.
2. PANDAS: "Prepare and analyze market data." ✔ Load and clean data ✔ Time series analysis ✔ Create features.
3. SCIKIT-LEARN: "Machine learning models for prediction and classification." ✔ Simple and easy to use ✔ Multiple ML models ✔ Well documented.
4. BACKTESTING.PY: "Backtest your strategy with realistic trading rules." ✔ Event-driven backtesting ✔ Strategy customization ✔ Supports real market data.
Diagram: Market Data (Yahoo Finance, Alpha Vantage, Polygon (free tier)), Python ("Build models and strategies") and Pandas ("Prepare and analyze data") feed a laptop. Outputs: Scikit-learn ("Train machine learning models"), Backtesting.py ("Test strategies on historical data"), Visualize ("Analyze results and iterate"). Laptop code excerpt: `data = pd.read_csv('data.csv')`, `data['return'] = data['Close'].pct_change()`, `data['ma_20'] = data['Close'].rolling(20).mean()`, `model = RandomForestClassifier()`, `model.fit(X_train, y_train)`, `signals = model.predict(X_test)`. TOOL FLOW: Get Data → Prepare Data (Pandas) → Train Model (Scikit-learn) → Backtest (Backtesting.py) → Analyze Results → Improve and Repeat.

**Slide 4 (04/08):** "TURN MARKET DATA INTO USEFUL FEATURES." "Machine learning models learn from data. Good features help the model find meaningful patterns in the market."
1. HISTORICAL DATA: "Price and volume data (OHLCV)." Example bar: Open 2410.2, High 2415.6, Low 2408.1, Close 2413.4, Volume 125,430.
2. FEATURE ENGINEERING: Returns (Short and medium term), Moving Averages (Trend and distance), Volatility (Market dynamics), Volume (Liquidity and strength), Technical Indicators (RSI, MACD, etc.), Custom Features (Create your own ideas).
3. FEATURE MATRIX, with columns Return_1 | MA_20 | Volatility | RSI | Volume | Target:
   - 0.0012 | 0.23 | 0.015 | 56.3 | 1.24 | 1
   - −0.0008 | −0.11 | 0.018 | 42.1 | 0.93 | 0
   - 0.0021 | 0.35 | 0.012 | 61.7 | 1.56 | 1
   - 0.0004 | 0.12 | 0.014 | 48.5 | 1.02 | 0
   - −0.0015 | −0.28 | 0.020 | 38.9 | 1.11 | 0
   - 0.0018 | 0.31 | 0.013 | 59.4 | 1.43 | 1
EXAMPLE FEATURES: Price Returns ("1, 5, 10, 20 period returns"), Moving Average Features ("Distance, crossover, slope"), Volatility Features ("Rolling standard deviation"), Volume Features ("Relative volume, volume change"), Technical Indicators ("RSI, MACD, Bollinger Bands"), Custom Features ("Create and test your own ideas"). Stacked charts: Price, Returns, Moving Average, Volatility, Volume, RSI, MACD.
4. MODEL INPUT: "These features are used to train the machine learning model." Features → ML Model.

**Slide 5 (05/08):** "TRAIN THE MODEL TO FIND TRADING PATTERNS." "Use machine learning algorithms to learn from your data and identify patterns that can lead to profitable signals."
1. PREPARE DATA: "Split data into training and testing sets." Train 70% / Test 30%.
2. CHOOSE ALGORITHM: "Start with simple models and compare performance." Logistic Regression, Random Forest (highlighted), XGBoost, Support Vector Machine.
3. TRAIN THE MODEL: `RandomForestClassifier(n_estimators=200, max_depth=10, random_state=42)`, `model.fit(X_train, y_train)`.
4. GET PREDICTIONS: Probability (Up) 0.78, Probability (Down) 0.22, "Buy Signal (p = 0.78)".
MODEL PERFORMANCE (EXAMPLE), Accuracy / Precision / Recall / F1:
   - Logistic Regression: 0.56 / 0.52 / 0.50 / 0.51
   - Random Forest: 0.62 / 0.60 / 0.58 / 0.59 (highlighted)
   - XGBoost: 0.61 / 0.58 / 0.57 / 0.57
   - SVM: 0.55 / 0.50 / 0.48 / 0.49
FEATURE IMPORTANCE (RANDOM FOREST), descending bars: Returns (1D), Moving Average Dist., RSI, Volatility, Volume Change, MACD, High − Low Range, Custom Feature 1.
Footer: "TEST MULTIPLE MODELS: Compare different algorithms, tune parameters and choose the one that performs best on unseen data."

**Slide 6 (06/08):** "TURN PREDICTIONS INTO A TRADING STRATEGY." "Convert model outputs into clear entry, exit and risk rules, then test them on historical data."
1. MODEL OUTPUT: P(Up) = 0.72. Probability (Up) 0.72, (Down) 0.28.
2. TRADING RULES: `if prob_up > 0.7: enter_long()` / `elif prob_up < 0.3: enter_short()` / `else: no_trade()`. "Add risk rules: Position size, Stop loss, Take profit, Max positions."
3. EXECUTION LOGIC: ✔ Use next bar execution ✔ Include transaction costs ✔ Add slippage ✔ Test multiple markets.
4. BACKTEST RESULTS: Total Trades 368, Win Rate 54%, Profit Factor 1.68, Max Drawdown 12.4%, Sharpe Ratio 1.21.
EXAMPLE: SIMPLE LONG STRATEGY: Model Prediction P(Up) = 0.72 → Entry Rule "P(Up) > 0.7 and trend up" → Position Size "1% risk per trade" → Exit Rule "Take profit: 2R, Stop loss: 1R". Chart marks BUY, Take Profit (2R) and Stop Loss (1R).
BACKTEST EQUITY CURVE (EXAMPLE): y-axis −50 to 150, equity line rising with a drawdown band.
KEY METRICS TO CHECK: Win Rate > 50%; Profit Factor > 1.5; Max Drawdown Acceptable; Sharpe Ratio Higher is better; Number of Trades Sufficient; Stability Across markets.

**Slide 7 (07/08):** "VALIDATE THE STRATEGY BEFORE YOU TRADE IT." "A strategy may look great in backtests but can fail in real markets. Use proper validation to make sure it's robust and not overfitted."
1. SPLIT THE DATA: "Test on data the model has never seen." Train / Validation / Test. ✔ Use chronological split ✔ Keep test data untouched ✔ Avoid using future data.
2. WALK-FORWARD TESTING: "Test the strategy across multiple time periods." Period 1–4. ✔ Train on past data ✔ Test on next period ✔ Repeat over time ✔ Check consistency.
3. INCLUDE REALISTIC COSTS: Brokerage / Commission, Slippage, Spread, Execution Delay, Position Size Limits.
4. CHECK ROBUSTNESS: Trending Markets, Sideways Markets, Volatile Markets, Downtrends.
EXAMPLE: WALK-FORWARD EQUITY CURVE: Train 1/Test 1 … Train 5/Test 5, y-axis 0–250. COMPARE WITH A SIMPLE BASELINE: ML Strategy (rising to about 250) vs Buy & Hold (Baseline) (flat at about 50–75).
COMMON MISTAKES TO AVOID: Look-ahead bias ("Using future information by mistake."); Overfitting ("Too many parameters and curve fitting."); Data leakage ("Features using future data (even indirectly)."); Only testing on one period ("May not work in different market conditions.").
A ROBUST STRATEGY SHOULD: Perform reasonably well on unseen data; Be stable across different market conditions; Work after realistic trading costs; Not rely on over-optimized parameters.

**Slide 8 (08/08):** "YOU DON'T NEED EXPENSIVE AI TO START. FOR FREE". COMPLETE WORKFLOW: 1 GET DATA ("Download historical market data.") → 2 CREATE FEATURES ("Convert raw data into informative inputs.") → 3 TRAIN MODEL ("Use machine learning algorithms to learn patterns.") → 4 GENERATE SIGNALS ("Convert predictions into clear trading rules.") → 5 BACKTEST ("Test on historical data with realistic costs.") → 6 VALIDATE ("Check robustness with out-of-sample tests and different conditions."). FREE TOOLS YOU CAN USE: Python (Programming language), pandas (Data preparation and analysis), Scikit-learn (Machine learning models), Backtesting.py (Strategy testing), TradingView (Free plan) (Charts and visualization), Public Data Sources (e.g. Yahoo Finance, Alpha Vantage, others). CTA: "COMMENT ROADMAP and I'll share the complete step-by-step roadmap, code examples and resources to build your own ML trading strategy for free."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Python | language | caption, slides 1, 3, 8 | Free, open source |
| pandas | library | caption, slides 3, 8 | Free (BSD-3) data library |
| scikit-learn | library | caption (truncated "Scik…"), slides 1–5, 8 | Free (BSD-3) ML library; provides RandomForestClassifier, LogisticRegression, SVM |
| XGBoost | library | slides 2, 5 | Free (Apache-2.0) gradient boosting library; not part of scikit-learn |
| Backtesting.py | library | slides 3, 8 | Real open-source Python backtester (kernc/backtesting.py), AGPL-3.0. "Event-driven" is loosely true: it is a bar-by-bar simulator. |
| TradingView (Free plan) | app | slide 8 | Real charting platform with a free tier (ads, limited indicators) |
| Yahoo Finance | data source | slides 2, 3, 8 | Free data, but there is no official API. Python users rely on the unofficial `yfinance` scraper, which can break or be rate-limited. |
| Alpha Vantage | data API | slides 2, 3, 8 | Real; the free key is heavily rate-limited (a small daily request cap) |
| Polygon (free tier) | data API | slides 2, 3 | Real; Polygon.io rebranded as Massive (massive.com) around late 2025. The free "Basic" plan allows about 5 calls/min, end-of-day/delayed data and about 2 years of history. |
| RandomForestClassifier(n_estimators=200, max_depth=10, random_state=42) | parameters | slides 1, 5 | Valid scikit-learn syntax (not executed) |
| prob_up > 0.7 long / < 0.3 short; 1% risk; TP 2R / SL 1R | strategy rules | slides 6, 8 | Example rule set, no performance evidence |
| 368 trades, 54% win, PF 1.68, MaxDD 12.4%, Sharpe 1.21 | numbers | slide 6 | Illustrative "example" values, not tied to any instrument or period |
| Accuracy 0.55–0.62 table | numbers | slide 5 | Labelled "EXAMPLE"; not from a real run |
| ROADMAP | comment keyword | caption, slide 8 | DM lead magnet |

### What's being promoted / the funnel decoded
Commenting "ROADMAP" triggers a DM (normally ManyChat-style automation) with a "complete step-by-step roadmap, code examples and resources". Nothing priced is shown in the post. A web search found a me.sh profile for an "Arwaz Az", described as a stock trader and financial planner and founder of "Pro Tradingz" (swing-trading services). The link to @arwazaz_ is not confirmed. Expect the DM to lead to a newsletter, a community or paid trading services later; nothing in the post proves that. All the tools named are free, so you don't need the DM to get started.

### Verification & insights
- The tools were checked against general knowledge and web searches. All are real and free or open source. Backtesting.py is AGPL-3.0, which matters only if you redistribute it or run it as a network service. The Polygon → Massive rebrand was confirmed by web search, though sources disagree on the exact date.
- The code snippets are syntactically plausible scikit-learn (they were read, not executed). The data has a minor inconsistency: 'data.csv' with a capitalised 'Close' column is assumed and never defined.
- **Claims vs reality:**
  - "Winning strategies … for free": the tools are free, but nothing in the post shows a winning strategy. Every number is labelled "example".
  - An accuracy of 0.62 for direction classification would be extraordinary on real out-of-sample data. Typical honest results are close to 0.50–0.53. A 0.62 figure usually signals leakage or a look-ahead bug, which slide 7 itself warns about.
  - The walk-forward and baseline charts (ML strategy ≈5× vs flat buy-and-hold) are illustrative drawings, not results.
  - The validation advice on slide 7 is sound and matches standard practice: chronological splits, walk-forward testing, costs and slippage, avoiding look-ahead and leakage, comparing to a baseline.
- **Better-known free sources of the same material:** the scikit-learn docs; the Backtesting.py docs and examples; Marcos López de Prado, *Advances in Financial Machine Learning* (purged CV and leakage); Stefan Jansen's "Machine Learning for Algorithmic Trading" GitHub notebooks.
- **Could not verify:** the rest of the caption; what the DM actually sends; the account's identity and display name.

---

<a id="e-dergbr-ous-"></a>

## DeRgBR-ous_ | @mar_antaya | "Quant finance projects I wish I did sooner": price options (Monte Carlo, Black-Scholes, QuantLib), build a rule-based strategy and paper trade it (Alpaca, Massive), then backtest
- **Link:** https://www.instagram.com/p/DeRgBR-ous_/
- **Account:** @mar_antaya (Mariana Antaya) · **Posted:** 2026-10-09 · **Type:** reel (83.6s, 14 pages)
- **Caption source:** full (Instagram, fetched with yt-dlp; the caption is one line)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. Sensible beginner project ideas pointing to real, mostly free resources (QuantLib, an OIC webinar, pytrade.org, r/algotrading, Alpaca paper trading). One quibble: she lists backtesting *after* paper trading, while the usual order is backtest first. Nothing is sold.

### Post description
> Financial engineering time 📈👩🏼‍💻💹

### Audio
The creator talks to camera. Word-by-word subtitles are burned in. Condensed to timestamped notes:
- [0.0–3.4] Hook: "These are the coding projects I regret not doing sooner."
- [3.4–12.1] #1, learn to price options. There are several methods, including the Monte Carlo method and Black-Scholes; she points to a video she found really helpful when learning.
- [12.1–26.3] QuantLib: an open-source library for pricing options that lets you "double check your math on a tool that all of the firms actually use."
- [26.3–41.1] #2, create your own trading strategy. Starting out she read many books, watched YouTube videos (fewer existed then) and read Reddit to see how people built their own strategies.
- [41.1–57.0] She took a few stocks she was interested and invested in (some shown on screen), looked at their patterns and how she traded them, and turned those patterns into very simple rules. From there you can paper trade the algorithm to see how it does in the market…
- [57.0–74.5] …which she recommends, so you play with fake money rather than real money "off the rip". The last one: backtesting the algorithm on historical data to see how it would have performed.
- [74.5–83.6] Close: hopes these inspire your next project; "follow along to learn about more financial engineering."

### On-screen content, page by page
**Page 1 (0.0–3.4s):** Text "Quant Finance" (hair-flip intro).
**Page 2 (3.4–4.7s):** "Quant Finance Projects I wish I did sooner" with 💸 and 👩🏼‍💻 emoji.
**Page 3 (4.7–12.2s):** Screenshots from a brokerage app that looks like Robinhood (orange and green styling). An options chain with expiries Oct 9, Oct 16, Oct 23, Oct 30, Nov 6, Nov 13, Nov 20, Nov 27 and call strikes with prices, breakeven and "To breakeven", e.g. $222.5 → $2.18 (breakeven $224.65, +3.04%, −86.29% today); $225 (Nov 6) → $15.75 (breakeven $240.28, +10.21%, −41.79% today); $220 → $18.00; "Share price: $218.02". Then an "Options Strategy Builder" screen ("NBIS is at $218.02", i.e. Nebius) with bullish, bearish, volatility and neutral icons and "Single Leg — The fundamental options strategies. Buy or sell calls and puts."
**Pages 4–6 (12.2–16.1s):** A YouTube search result: "Option Pricing Models Explained [With Formulas]", YouTube · The Options Industry Council (OIC), May 15, 2019, 1:03:04, "10 key moments in this video".
**Pages 7–9 (16.1–29.1s):** "QuantLib — QuantLib: a free/open-source library for quantitative finance" (the website header). Then text "Create your own strategy".
**Pages 10–11 (29.1–40.4s):** The book cover "O'REILLY — Python for Algorithmic Trading — From Idea to Cloud Deployment — Yves Hilpisch". A GitHub card "PFund-Software-Ltd / pytrade.org — Educational Hub for Python Trading — pytrade.org/doc — CC-BY-4.0 license" (around 230 stars and 29 forks visible). Text: "Also Reddit! Don't take everything for granted face value, there are a lot of beginners but get ideas! r/algotrading".
**Page 12 (40.4–75.9s):** "Great APIs for historical data": Alpaca ("API for Stock, Options, Crypto Trading & more — Trade with algorithms, connect with apps, and build financial apps with our easy to use APIs.") and Massive docs ("REST Quickstart — Get started with the Massive REST API"). Caption "Alpaca is good for paper trading too". Floating tickers "NVDA", "TSLA", "TQQQ", "SQQQ" with the note "I started w UGAZ and DGAZ but those have been delisted". The Alpaca card again: "great to start paper trading! Really easy in my experience". Then "Backtesting your strategy".
**Pages 13–14 (75.9–83.6s):** The talking head, ending with "engineering" on black.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Monte Carlo, Black-Scholes | methods | audio 7s | Standard option-pricing methods. |
| "Option Pricing Models Explained [With Formulas]", OIC, 2019, 1:03:04 | video | pages 4–6 | A free webinar by The Options Industry Council (an industry education body funded by the options exchanges and OCC). |
| QuantLib (quantlib.org) | library | audio 12s, page 7 | Real, free open-source C++ library (with Python bindings via SWIG). Modified BSD licence. Widely used in industry. "All of the firms actually use" overstates it: many firms use in-house libraries, though QuantLib is common. |
| "Python for Algorithmic Trading" (Yves Hilpisch, O'Reilly, 2020) | book | page 10 | A real paid book. |
| pytrade.org (github.com/PFund-Software-Ltd/pytrade.org) | repo/site | page 10 | Verified with `git ls-remote` and a shallow clone. CC-BY-4.0, last commit 2026-09-11. A curated "Educational Hub for Python Trading" (TradeLabs, tutorials, guides and a curated library list) with a single editor. Free. |
| r/algotrading | community | page 11 | A real Reddit community. She herself warns that many posters are beginners. |
| Alpaca | broker/API | page 12 | A real US API-first broker with free paper trading and market-data APIs (free and paid data tiers). |
| Massive (formerly Polygon.io) | data API | page 12 | A real market-data API (Polygon.io rebranded as Massive). Paid tiers plus a limited free tier. Also covered in the same creator's Detron4IyAF. |
| NVDA, TSLA, TQQQ, SQQQ | tickers | page 12 | The stocks and 3× leveraged Nasdaq ETFs she traded. |
| UGAZ, DGAZ | tickers | page 12 | VelocityShares 3× long/short natural-gas ETNs, delisted in 2020. Correct. |
| NBIS (Nebius) at $218.02; options chain | screenshot | page 3 | Her own brokerage screenshot (Robinhood-style UI). Illustration only. |

### What's being promoted / the funnel decoded
Nothing is sold, and there is no link, code or comment keyword. The CTA is "follow along to learn about more financial engineering". No "Paid partnership" label was seen. Alpaca and Massive also appeared in her earlier API review (Detron4IyAF) without a disclosed sponsorship.

### Verification & insights
- The resources are real and appropriate for beginners. The QuantLib, OIC, pytrade.org and Alpaca paper trading tiers are free, and the O'Reilly book is paid.
- **Order of steps:** she presents "paper trade, then backtest". The standard workflow is backtest on historical data first, then paper trade forward, then trade live with small size. Both steps are useful; just do them in that order.
- **"Turn patterns you see in stocks you like into simple rules":** this is a natural starting point but highly prone to hindsight and selection bias, especially with 3× leveraged ETFs (TQQQ/SQQQ decay through daily rebalancing). Backtests should include costs and out-of-sample checks.
- **Not verified:** the exact star count on the pytrade.org card (the GitHub API was unavailable), and whether the brokerage app is Robinhood (the UI suggests it).

---

<a id="e-deyjoajnwd4"></a>

## DeYjoajNWd4 | @quantfinance.ai | "The Quant Research Iceberg" infographic: beginner tools above the waterline (ChatGPT, Claude, Copilot, Jupyter, Python/Pandas) vs five layers of real quant work below it
- **Link:** https://www.instagram.com/p/DeYjoajNWd4/
- **Account:** @quantfinance.ai · **Posted:** 2026-10-12 (decoded from the post ID) · **Type:** image (1 slide)
- **Caption source:** full (Instagram embed page; yt-dlp cannot read image posts)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A sound, generic checklist of what separates a pretty backtest from a deployable strategy. There are no specific claims to falsify and nothing is sold. The image appears AI-generated.

### Post description
> 🧊 **The Quant Research Iceberg: What Beginners See vs. What Professionals Actually Do.**
>
> Everyone wants to build an algorithmic trading strategy.
>
> A few prompts to ChatGPT.
> Some Python code.
> A beautiful equity curve.
> A Sharpe ratio above 2.
>
> And suddenly, you've discovered alpha. 📈

- "But here's what the backtest doesn't tell you": six bullet questions on point-in-time data accuracy, look-ahead and survivorship bias, out-of-sample testing, slippage/fees/market impact, regime shifts and liquidity shocks, and surviving live execution.
- The real challenge is not generating signals but separating statistical noise from genuine alpha, understanding why an edge exists, and whether it survives real market conditions.
- Key lines (bold in the caption): "AI can accelerate research. It cannot replace statistical rigour, market intuition, or risk management." and "Anyone can generate a strategy. Very few can prove it survives reality."
- Closing: the deeper you go, the more you realise "The model is only a small part of the problem" (italic).
- CTA: 💬 "What's the most underestimated part of quant research?"
- Tags: #QuantFinance #QuantResearch #AlgorithmicTrading #SystematicTrading #QuantTrading, then plain words without "#": Backtesting AlphaResearch RiskManagement PythonForFinance MachineLearning HedgeFunds QuantitativeFinance.

*Caption condensed – full text is on the original post.* (The original is about 190 words, from the Instagram embed. The `**`/`*` marks are literal characters in the caption.)

### Audio
None (image post).

### On-screen content, page by page
**Slide 1:** Title "The Quant Research Iceberg — What Beginners See vs. What Professionals Actually Do".
- **Above water**, labelled "What Beginners See — Tools & Easy Wins" ("Most people stop here…", with a man in a rowing boat): **ChatGPT** "for quick explanations & ideas"; **Claude** "for summarising research papers"; **Copilot** "for code snippets (Python, R, SQL)"; **Jupyter** "for experimenting with data"; **Python / Pandas** "for data analysis & prototyping"; "Nice looking backtests & charts".
- **Below water**, five layers. Each has a left label, a left list, a centre tag and a right list:
  1. **Data — The Real Foundation**: Point-in-time data · Survivorship bias · Corporate actions · Data cleaning & validation | **Data Engineering & Integrity** | Alternative data (news, satellite, web, options) · Feature engineering · Scalable pipelines · Data versioning & reproducibility.
  2. **Research — Building Robust Ideas**: Statistical models (time series, cross-sectional) · Feature selection · Causality & hypothesis testing | **Modelling & Validation** | Machine learning (but only when it adds value) · Avoiding overfitting · Walk-forward & cross-validation · Robustness checks.
  3. **Market Realities — From Paper to Practice**: Transaction costs · Market impact · Slippage modelling · Order execution logic | **Strategy Design & Execution** | Portfolio construction · Position sizing & risk targeting · Capacity & liquidity constraints · Realistic assumptions.
  4. **Risk Management — Survival Over Everything**: Drawdown control · Stress testing · Scenario analysis · Tail risk (fat tails, regime shifts) | **Risk & Monitoring** | Real-time monitoring · Model decay detection · Kill switches & risk limits · Explainability & governance.
  5. **Production — Where Alpha Lives (or Dies)**: Robust, low-latency infrastructure · Backtest → paper trade → live · Monitoring & alerting · Continuous improvement | **Live Deployment & Iteration** | Analyse failures · Iterate with new data · Adapt to changing regimes · Keep it simple & robust.
- Footer banner: "Anyone can generate a strategy. Very few can prove it survives reality." Arrow note: "This is where real quant work begins."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| ChatGPT, Claude, Copilot | AI tools | slide | Real general-purpose AI assistants (OpenAI, Anthropic, Microsoft/GitHub), each paired with a plausible use. |
| Jupyter, Python/Pandas | dev tools | slide | Real, free, open-source tools. |
| Point-in-time data, survivorship bias, look-ahead bias, walk-forward validation, slippage, market impact, capacity, kill switches, model decay | concepts | caption, slide | Standard, correctly used quant-research concepts. |
| "Sharpe ratio above 2" | number | caption | Used rhetorically as a too-good-to-be-true backtest (rightly so: in-sample Sharpe ratios above 2 are a common overfitting red flag). |

### What's being promoted / the funnel decoded
Nothing is sold. The only CTA is the engagement question "What's the most underestimated part of quant research?" There is no comment keyword, link or product. This matches the same account's earlier infographic DeCVMMwtDqg ("15 Must-Know Quant Concepts"), which also had no funnel.

### Verification & insights
- The content is generic but correct. It reads as the counterweight to the many "AI built me a trading bot" posts in this collection (for example DeZZNwVAP0F's "AI allows anyone… to become a quant trader").
- The image has hallmarks of an AI image generator (uniform hand-lettered style, stock iceberg composition). The caption's `**bold**` markdown pasted as literal asterisks suggests AI-drafted text. No factual errors.
- Good, free deeper sources on the same pitfalls: Marcos López de Prado's work on backtest overfitting (e.g. "The Probability of Backtest Overfitting", Bailey et al. 2014) and the Deflated Sharpe Ratio.
- **Not verified:** who runs @quantfinance.ai (no bio or funnel was found).

---

<a id="e-debex7eizzu"></a>

## Debex7eiZZu | @quantfinancetogo | Quant Finance from Scratch Part 22: hypothesis testing for a strategy (t-statistic, p-value, confidence interval, t ≈ Sharpe×√years, multiple testing), with a 16-line NumPy simulation (t 1.50, p 13.3%, 7 of 100 lucky passes)
- **Link:** https://www.instagram.com/p/Debex7eiZZu/
- **Account:** @quantfinancetogo (QuantFinanceToGo) · **Posted:** 2026-10-13 · **Type:** reel (157.2s, 2 scene pages; one continuous animation, reviewed from 2-fps frames)
- **Caption source:** full (Instagram, fetched with yt-dlp; the mirror metadata had failed with HTTP 502, so the handle and caption came from yt-dlp)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct, well-caveated lesson on testing whether backtest profits are luck. Every number reproduces exactly from the on-screen code. Nothing is sold.

### Post description
> ➡️ Quantitative Finance From Scratch, Part 22: Hypothesis Testing.
>
> You start with the null hypothesis: the strategy's true average return is zero, so there is no edge. Then you ask how often pure luck would produce a result at least as extreme as yours if that were true.

- Definitions: the t statistic is the average return divided by its standard error (the typical size of the random error in an average); the p value is the probability of a t statistic at least this far from zero when there is really no edge. At 95% confidence a result is significant when p is below 5%, matching a 95% confidence interval that excludes zero.
- Simulation: a strategy with a small real edge (true Sharpe ratio 1, daily swings 1%) over five years reaches t = 1.50 and a two-sided p of 13.3%. The 95% interval for the average daily return is −0.013% to +0.096%, which includes zero, so it is not significant at 5% even though the edge is real. By chance the run showed a Sharpe of only 0.67, and five years were not enough this time.
- Rule of thumb: t ≈ yearly Sharpe × √years; with Sharpe 1 you need about four years to reach t = 2.
- Biggest trap, testing many rules: of 100 no-edge strategies about 5 pass at 5% by luck; in this run, 7 did.
- Caveats: "A p value is not the probability that your strategy works." The test assumes independent returns and an unchanging market, and a real edge can still be too small to survive trading costs.
- All numbers come from one simulated run with assumed numbers (seed 22); no real market data, no strategy recommendation. Education only, not financial advice.
- Hashtags: #quantitativefinance #quant #hypothesistesting #trading #statistics

*Caption condensed – full text is on the original post.*

### Audio
English voice-over by the creator over quiet background music (no identifiable song). Condensed into timestamped notes:
- [0.0–12.5] Hook: "How can you statistically determine whether a trading strategy's profits are just luck or a real edge?" Promises the "scientifically correct way". Series title: Quantitative Finance from Scratch, Part 22.
- [12.5–32.5] Hypothesis testing checks whether a result is real or could easily come from chance. Start with the null hypothesis (for a strategy: true average return zero, no edge), then ask how often pure luck would give a result at least as far from zero as yours.
- [32.5–56.8] Divide the average return by its standard error (typical size of the random error in an average): the t-statistic. The p-value is the probability of a result at least that far from zero if the null is true (no edge, pure luck). A low p-value means such a result would be rare without an edge.
- [56.8–78.8] Simulation: a strategy with a small real edge trades five years and reaches t = 1.5, p = 13.3%. The threshold depends on the chosen confidence level (common: 90, 95, 99%); at 95%, significant means p below 5%.
- [78.8–96.3] A confidence interval is the range of true average returns that fit the data; here the 95% interval runs from about −0.01 to +0.1% a day, includes zero, so not significant at 5% despite the built-in real edge.
- [96.3–117.6] Rule: t ≈ yearly Sharpe × √years; with Sharpe 1 you need about four years for t = 2. The run's true Sharpe was 1 but by chance it showed 0.67 over five years, hence t = 1.5.
- [117.6–133.2] "The biggest trap is testing many rules": of 100 no-edge strategies about five pass at 5% by luck. Quants use these tests to check backtests, whether a factor earns a premium, and whether a beta differs from zero.
- [133.2–155.6] "A p-value is not the probability that your strategy works." It assumes independent past returns and an unchanging market, and a real edge can be too small to survive trading costs. Summary: testing asks how often luck alone would beat your result; if rarely, you may have a real edge. CTA: "Follow for more if you want to properly learn quantitative finance."

### On-screen content, page by page
The layout is fixed: header "QUANT FINANCE FROM SCRATCH ▌ · PART 22", title "Hypothesis Testing", subtitle "luck or a real edge?", and episode tabs 13–22 with 22 highlighted. Below are a chart panel, a caption bar and the editor `hypothesis.py`. The footer reads "simulated returns, assumed numbers · education only · not financial advice". The scene detector caught only 2 pages, so the segments come from the 2-fps frames.
**0–12s:** Counters "t = 0.00 → 1.50" ("your strategy · 5 simulated years") and "p = 0.0 % → 13.3 %" ("luck alone gets this far"). A histogram of the t statistic for "10,000 simulated strategies with no edge · 5 years each", with ±1.96 lines, the tail shaded, and "P ABOVE 5 %: LUCK CAN EXPLAIN IT" / "YOUR STRATEGY". Pop-up: "KEY IDEA — HYPOTHESIS TESTING — luck or a real edge?"
**12–30s:** "real or chance? · one edge, one coin flip" (two empty 5-year panels). "null hypothesis · true average = 0": a histogram of the "daily return of the strategy, 1,260 days" with tags "NULL: TRUE AVERAGE = 0" and "OUR AVERAGE +0.041 % A DAY".
**30–41s:** "how often would luck do it? · 100 strategies, no edge": a fan of 100 random equity paths, "YOURS" highlighted, "AS FAR FROM ZERO AS YOURS: 18 OF 100".
**41–47s:** "t statistic · average / standard error": "t = average / standard error", "TYPICAL SIZE OF THE RANDOM ERROR IN AN AVERAGE", "average +0.041 %", "standard error 0.028 %".
**47–66s:** "p value · if there is no edge": a bell curve with "T = 1.50", "IF THE NULL IS TRUE", "PURE LUCK", "p = 13.3 %", "example t = 3: p = 0.3 %", "LOW P: RARE WITHOUT AN EDGE".
**66–72s:** "our run · simulated, seed 22": terminal "$ python hypothesis.py → t 1.50, p 13.3%, 95% CI -0.013% to +0.096% a day", with "REAL EDGE BUILT IN: SHARPE 1" and "5 YEARS = 1,260 DAYS".
**72–79s:** "confidence level · 90 · 95 · 99 %": "99 % confidence — OUTSIDE THE LINES: 1 %" (lines at ±2.58), then "95 % confidence — OUTSIDE THE LINES: 5 %" (±1.96), "SIGNIFICANT WHEN P IS BELOW 5 %".
**79–96s:** "confidence interval · 95 %, our run": "range of true averages that fit the data (95 %)", a bar from "−0.013 %" to "+0.096 %" spanning 0 on the axis "true average daily return" (−0.04 % to +0.12 %).
**96–118s:** "t ≈ Sharpe × √years · rule of thumb": a curve of the t statistic against years of data (0–8), "4 YEARS: T = 2", "TRUE SHARPE 1", output "t = Sharpe 0.67 x sqrt(5 years)", and a dashed blue curve for the run's realised Sharpe.
**118–126s:** "testing many rules · 100 strategies, no edge": a dot plot of the "t statistic of each strategy", −3 to +3.
**126–133s:** "what quants test · schematic": panels "BACKTESTS (real or luck?)", "FACTOR PREMIUM (factor vs market — premium real?)", "BETA VS ZERO (β = 0 ?)".
**133–144s:** "the limits · what a p value cannot tell": "1 p ≠ chance that your strategy works — how rare luck is: p 13.3 % / edge real? not measured"; "2 assumes independent returns, a market that stays the same".
**144–157s:** "hypothesis testing · part 22": "NULL: NO EDGE", "LUCK GETS THIS FAR: P = 13.3 %", "RARELY? THEN MAYBE A REAL EDGE", "OURS: T = 1.50".

**Final code (`hypothesis.py`, 16 lines, read from the last frames), excerpt:**
```
rng = np.random.default_rng(22)
days, edge = 252 * 5, .01 / sqrt(252)  # Sharpe 1
rets = rng.normal(edge, .01, days)  # daily
se = rets.std(ddof=1) / sqrt(days)  # std error
t = rets.mean() / se  # the t statistic
p = erfc(abs(t) / sqrt(2))  # two-sided p value
ci = rets.mean() + np.array([-1.96, 1.96]) * se
luck = rng.normal(0, .01, (100, days))  # no edge
ts = luck.mean(1) / luck.std(1, ddof=1) * days**.5
print(f"luck: {sum(abs(ts) > 1.96)} of 100 pass")
```
The omitted lines import numpy and `erfc, sqrt` from `math`, print t, p and the 95% CI as signed percentages a day, and compute and print the realised annualised Sharpe (`mean / std × √252`) in the form "t = Sharpe … x sqrt(5 years)". Inputs: seed 22, 1,260 days, daily edge 0.01/√252 (Sharpe 1), daily swing 1%, 100 no-edge strategies tested at |t| > 1.96. Printed results: "t 1.50, p 13.3%, 95% CI -0.013% to +0.096% a day", "t = Sharpe 0.67 x sqrt(5 years)", "luck: 7 of 100 pass".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| t 1.50, p 13.3%, 95% CI −0.013% to +0.096% a day; realised Sharpe 0.67; 7 of 100 no-edge strategies pass | results | caption, audio, screen | **Reproduced exactly** by re-typing the 16 on-screen lines and running them locally (my own transcription, no downloaded code). |
| Daily edge .01/√252 (true Sharpe 1), 1% daily volatility, 1,260 days, seed 22 | parameters | caption, code | As stated. |
| t ≈ Sharpe × √years; Sharpe 1 needs ~4 years for t = 2 | rule of thumb | caption, audio 97s | Correct (t = SR_annual × √T, so √4 = 2). Matches the run: 0.67 × √5 = 1.50. |
| ~5 of 100 no-edge strategies pass at 5% | multiple testing | caption, audio 120s | Correct expectation (binomial mean 5). The run gave 7. |
| "Average +0.041 %, standard error 0.028 %", "18 of 100 as far from zero" | screen numbers | segments | Consistent with t = 1.50 and p = 13.3% (roughly 13 to 18 of 100 expected by luck). |
| Normal approximation (erfc, ±1.96) | method | code | For 1,260 observations the normal approximation to the t-distribution is effectively exact. |

### What's being promoted / the funnel decoded
Nothing is sold. The only CTA is "Follow for more if you want to properly learn quantitative finance." There is no comment keyword, link or product. Same series as DeUlwIYikQz (Part 19), DeD3ruoCXGg (13), DeFCbkaiVMa (14) and DeG3qGCirGO (15).

### Verification & insights
- **Code check:** the output was `t 1.50, p 13.3%, 95% CI -0.013% to +0.096% a day`, `t = Sharpe 0.67 x sqrt(5 years)` and `luck: 7 of 100 pass`. That is identical to the caption and the screen.
- **Accuracy:** the definitions are correct, including the often-missed point that a p-value is not the probability the strategy works. The caveats (independence, stationarity, costs) are the right ones.
- **Directly relevant to other posts in this collection:** it is the statistical counterweight to "strategy that works" claims (for example DePoq9qovVj's intraday-momentum pitch and the many tier-list and bot posts). A strategy needs years of out-of-sample data, or a multiple-testing correction (Bonferroni, or Harvey-Liu-Zhu's suggested t > 3), before its edge is believable.
- The critical values drawn (±1.96 for 95%, ±2.58 for 99%) are correct.
- **Not verified:** nothing material.

---

<a id="e-deovtfbzxwp"></a>

## DeovTfBzXWP | @rick.automates | "$30,000 Bloomberg Terminal for $0 with 5 tools": yfinance, SEC EDGAR, FRED, FinBERT, Yahoo Finance news on one dashboard (animated 3D explainer); "comment TERMINAL" for links
- **Link:** https://www.instagram.com/p/DeovTfBzXWP/
- **Account:** @rick.automates (rick) · **Posted:** 2026-10-18 · **Type:** reel (32.9s, 25 pages)
- **Caption source:** full (Instagram, via yt-dlp on the second attempt)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE – all five data sources are real and free, but "your own Bloomberg Terminal" is a big overstatement (delayed/unofficial data, no real-time feeds, no execution, no chat, no analytics depth)

### Post description
> Comment „TERMINAL" and I'll send you the links
>
> Here's how you can make a $30,000 Bloomberg Terminal yourself.
> Completely free, with just five tools.
>
> Step one: market data. Python's yfinance pulls live prices for any ticker.
> Step two: SEC EDGAR. Every company filing, straight from the source.
> Step three: FRED. Interest rates, inflation, jobs, all the macro data.
> Step four: FinBERT reads every headline and scores it, bullish or bearish.
> Step five: Yahoo Finance feeds you the news in real time.
>
> Put it all on one dashboard, and you've got your own stock market terminal for zero dollars.
>
> #bloombergterminal #python #stockmarket #trading #fintech

### Audio
A voice-over narrator (English) over upbeat background music; no identifiable song.
- [0.0–5.2] "Here's how you can make a $30,000 Bloomberg terminal yourself, completely free with just five tools."
- [5.2–9.6] "Step 1. Market data. Python's yfinance pulls live prices for any ticker."
- [9.6–13.6] "Step 2. SEC EDGAR. Every company filing, straight from the source."
- [13.6–17.8] "Step 3. FRED. Interest rates, inflation, jobs, all the macro data." (Whisper heard "Bread"; the on-screen label is FRED.)
- [17.8–21.9] "Step 4. FinBERT reads every headline and scores it. Bullish or bearish."
- [21.9–24.9] "Step 5. Yahoo Finance feeds you the news in real time."
- [24.9–28.4] "Put it all on one dashboard and you've got your own terminal for $0."
- [28.4–31.4] "Want the links? Comment terminal and I'll send them to you."

### On-screen content, page by page
A blocky 3D cartoon world (toy-like characters). Each page has a taped paper banner title at the top and word-by-word subtitle tags at the bottom.

1. (0–1.5s) "THE $30,000 TERMINAL". A glowing terminal on a velvet-rope pedestal with "TERMINAL <GO>", "INDU" and green/red % rows (+1.92%, −2.52%, −2.31%, −1.87%, +0.22%, +1.12%), plus a red "$30,000" price tag.
2. (1.5–2.9s) "MAKE IT YOURSELF". A monocled, top-hatted block character; screen rows +1.26%, +0.72%, +1.91%, +0.07%, −1.06%, +0.29%; tag "$30,000".
3. (2.9–3.5s) "FREE, WITH 5 TOOLS"; "Terminal yourself".
4–5. (3.5–4.9s) "FREE, WITH 5 TOOLS". The screen switches to green "FREE"; "Completely free".
6. (4.9–7.6s) "STEP 1: MARKET DATA". A green candlestick forest; "five tools".
7. (7.6–9.3s) "PYTHON + yfinance". A blue/yellow Python snake; "Python's yfinance".
8. (9.3–11.2s) "STEP 2: SEC EDGAR". A white columned "SEC · EDGAR" building and filing cabinet; "for any ticker".
9. (11.2–13.3s) "EVERY FILING, AT THE SOURCE". An eagle on a filing cabinet; "SEC EDGAR".
10. (13.3–16.6s) "STEP 3: FRED". Gauges and a bank-vault door; "the source".
11–13. (16.6–17.6s) "ALL THE MACRO DATA". The vault opens to a glowing bar chart; "jobs", "all the".
14. (17.6–19.9s) "STEP 4: FINBERT". Block robots at a desk; "macro data".
15–17. (19.9–21.7s) "BULLISH OR BEARISH?". A robot screen shows "+0.92"; "bullish".
18–19. (21.7–23.8s) "STEP 5: YAHOO FINANCE". A ticker tape "…DS RATES STEADY ▲ TECH +2.…", "GRID 47.… RYZE 512.48"; flying newspapers; "bullish or bearish".
20. (23.8–25.0s) "NEWS IN REAL TIME". Ticker "▲ TECH +2.1%" and a blue label "YAHOO FINANCE: HEADLINES IN REAL TIME".
21. (25.0–27.5s) "ALL ON ONE DASHBOARD"; "real time".
22. (27.5–28.2s) "YOUR OWN TERMINAL: $0". Screen "$30K"; "your own".
23–24. (28.2–28.9s) "YOUR OWN TERMINAL: $0". Screen "$0"; "for zero".
25. (28.9–32.9s) "COMMENT TERMINAL FOR THE LINKS". Characters celebrate with fireworks; "for zero dollars".

(The ticker symbols and percentages are decorative props, not real quotes.)

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Bloomberg Terminal, "$30,000" | product / price | caption, audio, pages 1–3, 22 | Bloomberg Professional service. ~$30k per seat per year is the commonly reported list price, so the number is roughly right as an annual cost |
| yfinance (Python) | repo | caption, audio 7.2s, page 7 | github.com/ranaroussi/yfinance: `git ls-remote` OK; last commit 2081dca 2026-10-18 ("Merge pull request #2992…"); Apache-2.0. README: "the Yahoo! finance API is intended for personal use only"; not affiliated with Yahoo |
| SEC EDGAR | site / API | caption, audio 10.6s, pages 8–9 | sec.gov/edgar, the official free filings database with free JSON APIs (requires a declared User-Agent and rate limits) |
| FRED | site / API | audio 14.6s, page 10 | Federal Reserve Bank of St. Louis economic data, free with an API key |
| FinBERT | repo / model | audio 18.8s, page 14 | github.com/ProsusAI/finBERT: `git ls-remote` OK; last commit 3b4bfed 2026-10-12 ("license-remediation-2026-10-09"). Apache-2.0 covers code only. The model weights (Hugging Face ProsusAI/finbert) and training data (Financial PhraseBank) carry their own terms; "not an official Prosus product". Outputs positive/negative/neutral sentiment |
| Yahoo Finance news | site | audio 22.9s, pages 18–20 | finance.yahoo.com; headlines are also accessible via yfinance |
| "+0.92" | number | pages 16–17 | Illustrative sentiment score |

### What's being promoted / the funnel decoded
Commenting "TERMINAL" triggers an auto-DM with links, presumably the five tool pages and possibly the creator's own dashboard code or template. The handle "rick.automates" suggests an automation/AI-content account that grows its audience with comment-gated freebies. No product or price is shown. Nothing about the account was found by web search. There is no need to engage: all five tools are listed above with official locations.

### Verification & insights
- All five sources are real and free. Both repos exist and are actively maintained (cloned locally; code not executed).
- How it differs from a Bloomberg Terminal:
  - yfinance is an unofficial scraper of Yahoo endpoints. Quotes are often delayed (exchange-dependent), it breaks when Yahoo changes, and its data is for personal use per its README.
  - EDGAR and FRED are excellent but end-of-period data.
  - FinBERT gives generic 3-class sentiment and needs Python/ML setup.
  - "Put it all on one dashboard" hides the actual build work (e.g. Streamlit/Dash coding).
  - Bloomberg's value is real-time multi-asset data, fixed income, analytics, news exclusives, chat (IB) and execution, none of which this replicates.
- Useful context: similar open-source "terminal" projects exist (e.g. OpenBB) that already bundle these sources.
- Could not verify: what the DM actually sends.

---

<a id="e-decvmmwtdqg"></a>

## DeCVMMwtDqg | @quantfinance.ai | "15 Must-Know Quant Concepts" one-image infographic (Black-Scholes to Market Making), each with a one-line definition and a sketch chart
- **Link:** https://www.instagram.com/p/DeCVMMwtDqg/
- **Account:** @quantfinance.ai (Hrishikesh Matre | QuantFinance.ai) · **Posted:** 2026-10-03 · **Type:** image (1 slide)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; the mirror copy was cut off at "13. C...")
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. A correct-in-spirit glossary poster that looks AI-generated. A few panels are simplified or slightly muddled (CAPM/β axis, Sharpe without the risk-free rate). No funnel.

### Post description
> 15 Must-Know Quant Concepts 📊
>
> 1. Black-Scholes
> 2. Brownian Motion
> 3. Monte Carlo
> 4. Greeks
> 5. Mean Reversion
> 6. Sharpe Ratio
> 7. Efficient Frontier
> 8. CAPM & Beta
> 9. Value at Risk
> 10. Kelly Criterion
> 11. Central Limit Theorem
> 12. Bayes' Theorem
> 13. Cointegration
> 14. GARCH
> 15. Market Making
>
> How many of these can you explain without Googling? 👇
>
> Save this post for your next quant interview prep 📌
> Tag a friend who's learning quant finance.
>
> #quant #quantfinance #quanttrading #quantitativefinance #hedgefund blackscholes montecarlo statistics probability finance trading datascience mathematics interviewprep wallstreet

### Audio
None (image post).

### On-screen content, slide 1
Title: "**15 Must-Know Quant Concepts**". A 5×3 grid of dark-blue tiles, each with a mini-chart and a one-line caption:
1. **Black-Scholes:** Option Price vs Stock Price curve, legend "Model Price" / "– – Closed-form". "Prices options with a closed-form formula".
2. **Brownian Motion:** Price vs Time, "Random Walk" / "Possible Paths". "Models prices as continuous random moves".
3. **Monte Carlo:** Price vs Time fan, "Simulated Paths" / "Expected Path". "Estimates outcomes via random simulation".
4. **Greeks:** Option Price vs Underlying Price with a tangent, "Δ = slope". "Sensitivity of option price to inputs".
5. **Mean Reversion:** Price oscillating around a dashed "mean". "Prices tend to pull back to their average".
6. **Sharpe Ratio:** "μ (Return) ÷ σ (Risk) = **1.8** Sharpe Ratio". "Return earned per unit of risk taken".
7. **Efficient Frontier:** Expected Return vs Risk (Standard Deviation), curve labelled "Efficient Frontier" above scattered dots. "Best return for each level of risk".
8. **CAPM & Beta:** "Stocks" scatter with an orange "Security Market Line", "β = slope". Axes Expected Return vs "Market Return (β)". "How much a stock moves with the market".
9. **Value at Risk:** Probability vs Loss bell curve with the left tail shaded and marked "VaR". "Worst expected loss at a set confidence".
10. **Kelly Criterion:** Expected Growth vs Bet Size (Fraction of Capital), peak marked "f*". "Optimal bet size to maximize growth".
11. **Central Limit Theorem:** Frequency vs Sample Mean histogram with a normal curve. "Averages of samples look normal".
12. **Bayes' Theorem:** Venn diagram A ∩ B, "P(A|B) = P(B|A)P(A) / P(B)". "Updates beliefs as new evidence arrives".
13. **Cointegration:** Price vs Time, "Asset 1" / "Asset 2" with the gap marked "spread". "Trades the spread of two linked assets".
14. **GARCH:** Volatility vs Time with a burst between dashed lines. "Volatility comes in clusters".
15. **Market Making:** Order-book ladder, "Ask" (red) above "Bid" (green), bracket "Spread". "Quotes both sides to earn the spread".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| The 15 concepts (Black-Scholes … Market Making) | concepts | caption, image | All standard quant-finance and interview topics. The definitions are broadly correct (see the caveats below). |
| Sharpe Ratio = 1.8 | example number | tile 6 | Illustrative. The real definition is (return − risk-free rate) ÷ volatility. |
| QuantFinance.ai / Hrishikesh Matre | account | profile name | No web footprint found for the domain or person. |

### What's being promoted / the funnel decoded
Nothing is sold. The only CTAs are engagement prompts ("How many can you explain…", "Save…", "Tag a friend"). There is no comment keyword, link or product.

### Verification & insights
- **Accuracy caveats:**
  - **Sharpe:** the tile omits the risk-free rate (μ − r_f)/σ.
  - **CAPM & Beta:** the tile mixes two charts. β is the slope of a stock's returns regressed on market returns (the characteristic line), while the Security Market Line plots expected return against β. Labelling the x-axis "Market Return (β)" conflates them.
  - **Black-Scholes:** "Model Price" vs "Closed-form" lines are the same thing in Black-Scholes. The second line is decorative.
  - **VaR:** "worst expected loss at a set confidence" is the common shorthand. More precisely, it is a loss quantile that is exceeded with probability 1 − confidence (CVaR/expected shortfall is the average beyond it).
  - **Monte Carlo:** "Expected Path" is the mean of the simulated paths.
  - **Kelly:** correct (growth-optimal fraction f*). In practice traders bet fractional Kelly.
  - **Cointegration:** correct (stationary spread between non-stationary series).
  - **GARCH:** correct (volatility clustering).
- **Use:** a reasonable checklist for interview prep. Learn each from primary sources (e.g. Hull for options and Greeks, Markowitz 1952 for the frontier, Engle 1982 / Bollerslev 1986 for ARCH/GARCH, Engle-Granger 1987 for cointegration, Kelly 1956).
- **Related:** the efficient-frontier and beta concepts are worked through with code in @quantfinancetogo's series (DeD3ruoCXGg, DeFCbkaiVMa).
- **Not verified:** who runs the account and whether it sells anything elsewhere (no web footprint).

---

<a id="e-dd6s9vmtb1i"></a>

## Dd6s9VMtb1i | @quantchics | "Quant Research Starterpack": SSRN, arXiv, Alpha Architect, 3 books (López de Prado, Chan ×2), Yahoo Finance, Kaggle, Databento, NautilusTrader, QuantConnect, vectorbt, OpenBB, KDB-X, Jupyter
- **Link:** https://www.instagram.com/p/Dd6s9VMtb1i/
- **Account:** @quantchics (Quantgirl) · **Posted:** 2026-09-30 · **Type:** reel (11.7s, 7 pages)
- **Caption source:** full (Instagram, via yt-dlp on 2026-10-21. The mirror copy was truncated.)
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. All 14 items are real, well-known resources. Most are free or open source. Databento, QuantConnect's paid tiers and some KDB-X use cost money, and vectorbt carries a Commons Clause. The "comment QUANT" call to action only gets you the same public links.

### Post description
> If you're getting into quant research, don't just collect resources… know what to use them for.
>
> Here's a starter pack covering:
>
> → Finding research ideas
> → Building your foundation
> → Getting market data
> → Building & backtesting
> → Research tools
> → Reading real quant research
>
> Pick one question, one dataset, one hypothesis and start testing.
>
> Comment "QUANT" and I'll send you the full list of links.
>
> Save this for your next research rabbit hole.

### Audio
Music only. No speech (Whisper detected none). The song is not identified on screen or in the caption.

### On-screen content, page by page
Background on every page: the same mirror-selfie video (a woman in a black blazer and jeans, with her phone covering her face). Text and logos are overlaid.
**Page 1 (0.0–1.5s):** "Quant Research Starterpack"
**Page 2 (1.5–3.0s):** "**Find ideas**"
- **SSRN**: "Academic finance papers, working papers & empirical research"
- **arXiv**: "Preprints in ML, statistics & quantitative finance"
- **alpha architect**: "Factor research, asset pricing & systematic strategies"

**Page 3 (3.0–5.0s):** "**UNDERSTAND THE THEORY**"
- *Advances in Financial Machine Learning* (Marcos López de Prado, Wiley): "ML concepts applied to financial markets"
- *Quantitative Trading: How to Build Your Own Algorithmic Trading Business* (Ernest P. Chan, 2nd ed., Wiley): "Strategy development, testing & implementation"
- *Algorithmic Trading* (Ernest P. Chan, Wiley Trading Series): "Practical frameworks for developing trading strategies"

**Page 4 (5.0–6.5s):** "**GET DATA**"
- **yahoo!finance**: "Historical market data for quick research & prototypes"
- **kaggle**: "Datasets, competitions & real-world modelling problems"
- **databento**: "High-quality market data for deeper quantitative research"

**Page 5 (6.5–8.0s):** "**BUILD + BACKTEST**"
- **NautilusTrader**: "Event-driven research, backtesting & live trading infrastructure"
- **QUANTCONNECT**: "Research, strategy development & historical backtesting"
- **"V" logo (vectorbt)**: "Fast Python-based strategy research & backtesting"

**Page 6 (8.0–9.5s):** "**RESEARCH TOOLS**"
- **OPENBB**: "Explore financial data, markets & company fundamentals"
- **KDB-X** ("The next-gen kdb+ is here"): "High-performance time-series data analysis"
- **jupyter**: "Interactive notebooks for research, experimentation & analysis"

**Page 7 (9.5–11.7s):** "Pick one question, one dataset, one hypothesis and start testing." / "Comment "QUANT" and I'll send you the links."

(The caption's sixth heading, "Reading real quant research", has no page of its own in the video.)

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| SSRN (ssrn.com) | site | page 2 | Elsevier-owned preprint and working-paper repository. Free to read most papers. |
| arXiv (arxiv.org), incl. q-fin | site | page 2 | Cornell's free preprint server, with a q-fin section |
| Alpha Architect (alphaarchitect.com) | site | page 2 | Free research blog on factor investing, from an asset manager (Wes Gray) |
| *Advances in Financial Machine Learning*, M. López de Prado | book | page 3 | Wiley 2018. The standard financial-ML text. |
| *Quantitative Trading* (2nd ed.), E. P. Chan | book | page 3 | Wiley, 2nd ed. 2021. Subtitle "How to Build Your Own Algorithmic Trading Business". |
| *Algorithmic Trading*, E. P. Chan | book | page 3 | Wiley 2013, "Winning Strategies and Their Rationale" |
| Yahoo Finance | data site | page 4 | Free historical prices (commonly used via the unofficial `yfinance` library). Fine for prototypes; known for data errors and survivorship issues. |
| Kaggle | site | page 4 | Google-owned datasets and competitions platform. Free. |
| Databento (databento.com) | data vendor | page 4 | Paid, pay-as-you-go institutional-grade tick and order-book data (CME, US equities, etc.), with free starter credit |
| NautilusTrader | repo | page 5 | `github.com/nautechsystems/nautilus_trader`. LGPL-3.0. Rust/Python event-driven backtest and live engine. Last commit 2026-10-18 ("Seed Interactive Brokers exec provider from cache (#5349)"). Active. |
| QuantConnect / LEAN | platform + repo | page 5 | Cloud platform with free and paid tiers. The engine is open source at `github.com/QuantConnect/Lean`, Apache-2.0, last commit 2026-10-16. |
| vectorbt ("V" logo) | repo | page 5 | `github.com/polakowo/vectorbt`. Apache-2.0 **with Commons Clause** (you may not sell a product or service built substantially on it). Last commit 2026-10-18. A paid "vectorbt PRO" also exists. Logo identification is by visual match. |
| OpenBB | repo/platform | page 6 | `github.com/OpenBB-finance/OpenBB`. Apache-2.0. Last commit 2026-10-17. Open-source investment research platform. |
| KDB-X (KX) | database | page 6 | KX's next-generation kdb+ time-series database. Free Community Edition launched 19 Nov 2025 (public preview with usage limits, per KX), with commercial availability planned for early 2026. |
| Jupyter | tool | page 6 | Open-source notebooks (BSD). Free. |
| "QUANT" | comment keyword | caption, page 7 | Triggers a DM with the links |

### What's being promoted / the funnel decoded
- "Comment 'QUANT' and I'll send you the full list of links": an engagement-bait DM automation. Everything it would send is already named above, so there is no need to comment. No product, course or paid community is mentioned in the post. The account is a lifestyle-style quant-education creator building an audience.

### Verification & insights
- All repos were confirmed live with `git ls-remote` (HEAD hashes returned) and by the existing local clones in `scratchpad/repos/` (nautilus_trader, OpenBB, Lean, vectorbt): license and last commit as listed above. No code was run.
- The descriptions on the slides are accurate one-liners.
- Things the post doesn't mention:
  - Yahoo data is unofficial and can break, and its data has survivorship gaps.
  - Databento and QuantConnect's live and pro features cost money.
  - vectorbt's Commons Clause restricts commercial resale.
- The caption's sixth category ("Reading real quant research") is not shown in the video.
- Could not verify: who is behind @quantchics.

---

<a id="e-deec0avpu2f"></a>

## Deec0AVPu2F | @fidetolabs.math | Animated chart explaining triple-barrier labeling (±3 % barriers, 20-session time limit, 60 simulated trades) and the "stopped-out trade scored as a winner" mistake
- **Link:** https://www.instagram.com/p/Deec0AVPu2F/
- **Account:** @fidetolabs.math (display name not in data) · **Posted:** 2026-10-14 (decoded from the post ID) · **Type:** reel (7.1s, 1 scene page; a single animated chart)
- **Caption source:** possibly truncated (mirror). The yt-dlp full-caption fetch returned HTTP 429.
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE. This is a correct, concise illustration of the triple-barrier method (from López de Prado's *Advances in Financial Machine Learning*) and of a common backtest-labeling error. The data is simulated, and there is no product or funnel.

### Post description
> In trading, the triple barrier method tracks a trade using three boundaries: a profit level, a loss limit, and a time limit. Whichever boundary the price hits first decides if the trade was a win, a loss, or a draw. Standard tests often cheat by call...

(cut off by the mirror, presumably continuing "…calling a stopped-out trade a winner…". The full caption could not be retrieved because Instagram returned 429.)

### Audio
No speech (Whisper detected 0 speech segments). There is an audio track, probably background music; no title is identifiable from the post.

### On-screen content, page by page
**Single animated page (0.0–7.1s):** Header "@fidetolabs.math", title **"Triple barrier"**, subtitle "WHAT THE LABEL ACTUALLY IS", formula line "label = whichever barrier it touches **first**". The legend reads "TAGGED THE TOP" (green), "TAGGED THE BOTTOM" (red), "RAN OUT OF TIME" (white). The chart heading is "60 TRADES, ONE SIGNAL, THREE WAYS TO END".

The chart's y-axis runs from −8 % to +8 %, and the x-axis is "BARS SINCE THE SIGNAL", 0–20 ("60 EVENTS, THE SAME RULE"). There are horizontal lines "TAKE PROFIT +3%" and "STOP −3%", and a vertical time barrier "20 SESSIONS".

The animation sequence:
1. A big counter "±3%" with "BARRIERS, 20 SESSIONS".
2. 60 random paths fan out from 0. Hits are marked with green dots on +3 % and red dots on −3 %, with the counter "31 TRADES STILL OPEN" at "BAR 6".
3. "11 TRADES STILL OPEN" at "BAR 15".
4. At "BAR 20" the remaining paths end at the time barrier with white circles.
5. Final frame: one highlighted path drops below the −3 % stop around bar 7 (to about −4.7 %), then recovers to **+5.2 %** at bar 20. It is labelled "+5.2% STOPPED OUT, CALLED A WINNER" against "−3.0%" at the stop line.

Bottom text: "in trading: label a trade by what it touched first, then stop scoring a stopped-out trade as a winner."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Triple-barrier method | concept | caption; page title | A labeling method from Marcos López de Prado, *Advances in Financial Machine Learning* (Wiley, 2018), ch. 3. It has an upper (profit-take) barrier, a lower (stop-loss) barrier and a vertical (time) barrier. The label is set by the first barrier touched (+1 / −1 / 0 or sign of return at expiry). |
| ±3 % barriers, 20 sessions, 60 trades | parameters | page | Illustrative parameters on simulated paths. |
| "31 / 11 trades still open" at bars 6 / 15 | numbers | page | Animation counters on the simulated set. They can't be independently checked, and it doesn't matter. |
| +5.2 % vs −3.0 % | numbers | final frame | The illustrated mislabel: the trade's end-of-window return is +5.2 %, but the stop at −3 % was hit first, so the correct label is a loss of −3 %. |
| @fidetolabs.math | handle | header | The creator. No website or product found by web search. |

### What's being promoted / the funnel decoded
- Nothing visible: no CTA on screen, and none in the visible part of the caption. The truncated caption may contain one, but it could not be read.

### Verification & insights
- The concept is correct. Scoring trades by their return at a fixed horizon, ignoring that the stop would have triggered earlier, inflates backtests (a form of look-ahead or path-ignorance bias). The triple-barrier method fixes the labeling, and López de Prado also pairs it with "meta-labeling" and sample-uniqueness weights.
- Practical notes not in the post: barriers are usually scaled to volatility (e.g. a multiple of daily σ), not fixed ±3 %. With bar data, you can't always tell whether the stop or the target was touched first within the same bar (intrabar ambiguity), so conservative backtests assume the stop.
- Open-source implementations of the method exist (e.g. the `mlfinlab` library, now commercial; various free GitHub notebooks).
- Not verified: the full caption (429) and the background audio identity.

---

<a id="e-dequuypo8pr"></a>

## DeQuUyPo8pR | @neuron.machinelearning | "Let's build a neural network from scratch": a 16-line NumPy MLP (64→32 ReLU→10 softmax) trained on sklearn's 8×8 digits, from 9.8% to 98.4% train accuracy, with an animated network and a "comment CODE" funnel to the free NEURON learning app
- **Link:** https://www.instagram.com/p/DeQuUyPo8pR/
- **Account:** @neuron.machinelearning (Neuron. Machine Learning) · **Posted:** 2026-10-09 · **Type:** reel (45.1s; 1 detected scene because it is a smooth animation, so it was read from all 90 2-fps frames)
- **Caption source:** full (Instagram, via yt-dlp; the mirror copy was cut at "Backprop sends th...")
- **Category:** Quant & data
- **Verdict:** LEGIT & FREE: a correct, complete and honest from-scratch neural network. The full code is on screen (transcribed below), so there is no need to comment "CODE". The caption correctly says "train accuracy". Minor caveat: the 98.4% is measured on the training data with no test split.

### Post description
> Let's build a neural network from scratch. 🧠
> No PyTorch. No TensorFlow. Just NumPy.
>
> 1,797 handwritten digits, 8×8 pixels each.
>
> ■ 64 pixels in → 32 hidden neurons (ReLU) → 10 outputs (softmax)
> ■ Untrained: it guesses → 9.8% right
> ■ Backprop sends the error backwards, every weight takes a small step
> ■ 300 steps later: 98.4% train accuracy
>
> 16 lines. Zero frameworks.
>
> Want the code? Comment "CODE" 👇
> Learn it interactively on NEURON → link in bio
>
> #machinelearning #neuralnetworks #python #deeplearning #learnai

### Audio
English voice-over (calm narration, possibly synthetic) with burned-in captions; no identifiable song.
- [0.0–4.8] "Let's build a neural network from scratch. No PyTorch. Just NumPy."
- [6.8–10.4] "Eighteen hundred handwritten digits. Each one just 8 by 8 pixels."
- [12.3–17.0] "64 pixels go in. 32 hidden neurons. 10 outputs, one per digit."
- [18.4–22.2] "The forward pass: ReLU in the middle. Softmax at the end."
- [24.0–26.4] "Untrained, it just guesses. Ten percent right."
- [27.4–31.4] "Backprop sends the error backwards and every weight takes a small step."
- [33.4–37.4] "Three hundred steps later it reads handwriting. Ninety-eight percent right."
- [39.4–43.4] "Sixteen lines. Zero frameworks. That's a neural network."

### On-screen content, page by page
Constant header: "NEURON." logo, a "FROM SCRATCH" pill, "ML IN PYTHON · DEEP LEARNING", title "Neural *Network*". The top panel animates the network; the bottom panel is a code editor "neural_network.py" that types the code line by line, synced to the narration.
**0–2s (cover frame):** Completed network ("digit #4 · label 5", "loss 0.226", "epoch 85/300", output 5 at 92%) with the overlay "It reads handwriting." Subtitle "Let's build a neural network from scratch."
**2–7s:** Empty editor ("Just NumPy."), then lines 1–3 start typing; a faint digit "0".
**7–12s:** "digit #1 · label 0" 8×8 grid, "8 × 8 = 64 pixels". Subtitles "Eighteen hundred handwritten digits", "each one just eight by eight pixels." Highlight on `X = X / 16`.
**12–18s:** Input column of 64 nodes, "ARCHITECTURE 64 → 32 → 10", then hidden and output nodes 0–9. Subtitles "Sixty-four pixels go in.", "Ten outputs, one per digit." Code lines 5–7 (seed, lr, W1/b1, W2/b2).
**18–24s:** "The forward pass:" with lines 8–11. Formula box "2 · OUTPUT p = softmax(hW₂ + b₂)". Output bars about 11%, 10%, 11%, 13%… (uniform guessing).
**24–27s:** "**9.8%** train accuracy", "loss 2.287", "epoch 0/300", and a row of 22 sample digits all boxed red. Subtitle "Ten percent right."
**27–33s:** "Backprop sends the error backwards", formula box "EVERY WEIGHT W ← W − η∇_W L", "loss 2.285". Lines 12–15 typed.
**33–37s:** "**86.0%**", "loss 0.933", "epoch 23/300" (digit #3, label 2, 68% on output 2), sample row turning green. Subtitle "Three hundred steps later,".
**37–45s:** "**98.4%** train accuracy", "**loss 0.082**", "**epoch 300/300**", outputs at about 100% on the correct digit, all samples green. Line 16 `print(...)` runs: "$ python neural_network.py" → "**0.9838619922092376**". Subtitles "ninety-eight percent right.", "Sixteen lines. Zero frameworks.", "That's a neural network."

**The code shown on screen (16 lines, transcribed from the final frame). Excerpt, the training loop (lines 8–15):**
```python
for epoch in range(300):
    h = np.maximum(0, X @ W1 + b1)                  # 1 ReLU layer
    e = np.exp(h @ W2 + b2)
    p = e / e.sum(1, keepdims=True)                 # 2 softmax
    d2 = (p - Y) / len(X)                           # 3 backprop
    d1 = (d2 @ W2.T) * (h > 0)
    W2 -= lr * h.T @ d2; b2 -= lr * d2.sum(0)
    W1 -= lr * X.T @ d1; b1 -= lr * d1.sum(0)
```
The rest: lines 1–2 import NumPy and scikit-learn's `load_digits`; line 3 loads the digits (`return_X_y=True`) and scales pixels with `X = X / 16`; line 4 one-hot encodes the labels with `np.eye(10)[y]`; line 5 sets `np.random.seed(0)` and learning rate `lr = 0.5`; lines 6–7 initialise `W1` (64×32) and `W2` (32×10) as `np.random.randn(...) * 0.1` with zero biases `b1` (32) and `b2` (10). Line 16 prints the training accuracy `(p.argmax(1) == y).mean()`, which outputs 0.9838619922092376.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| NumPy | library | caption, audio 0.0s, code | Standard Python numerics library (BSD) |
| sklearn `load_digits` | dataset | code line 2 | scikit-learn's UCI handwritten digits: **1,797** images of 8×8 pixels, values 0–16 (hence `X / 16`). The caption's 1,797 is exact; the audio rounds to "eighteen hundred". |
| PyTorch, TensorFlow | frameworks (not used) | caption, audio | Named only as "not needed" |
| Architecture 64 → 32 (ReLU) → 10 (softmax) | model | caption, audio 12.3s, screen | As coded |
| lr = 0.5, seed 0, 300 epochs, init N(0, 0.1²) | parameters | code | Full-batch gradient descent |
| 9.8% → 86.0% (epoch 23) → 98.4% (epoch 300); loss 2.287 → 0.933 → 0.082 | numbers | screen, caption | 9.8% is chance level for 10 classes. The final printout is 0.9838619922092376. |
| NEURON (kw1fpt-ahmet-duyar.shinyapps.io/Neuron/) | site | caption ("link in bio"); bio | The bio link "NEURON · learn Machine Learning live", hosted on shinyapps.io (an R Shiny app by "ahmet-duyar"). Page title: "NEURON. Machine learning, made visible." No pricing was visible. |
| Comment "CODE" | CTA | caption | DM with the code, which is already fully visible above |

### What's being promoted / the funnel decoded
- "Comment CODE" gets the 16 lines in a DM (an engagement and follower driver). They are reproduced above.
- "Learn it interactively on NEURON → link in bio" points to a Shiny web app. Instagram bio (fetched 2026-10-21): "I take you from 0 to 100 in Machine Learning. / Real math. Real code. Visual explanations. / 👇Practice Machine Learning for free". About 20k followers; personal (non-business) account. The app presents as free; no paid tier was found.

### Verification & insights
- **Code review (read, not executed; scikit-learn is not installed in the sandbox, so the run was not reproduced):** the math is correct. It is a softmax plus cross-entropy gradient (`p − Y`, averaged), a ReLU derivative mask `(h > 0)`, and full-batch gradient descent. The printed accuracy uses `p` from the last forward pass, so it is the training-set accuracy just before the final update. 98.4% train accuracy on sklearn digits with this setup is entirely plausible (well-known baselines reach about 97–99%).
- **Honest caveats the reel glosses over:**
  1. There is no train/test split, so 98.4% is memorisation-inclusive. Test accuracy would typically be a little lower.
  2. `np.exp` without subtracting the row max can overflow on larger logits. It is fine here because of the small init.
  3. "300 steps" means 300 full-batch epochs over all 1,797 samples.
  4. sklearn is still a dependency (only for loading data), so "zero frameworks" means zero deep-learning frameworks.
- **Could not verify:** whether the NEURON app has paid features (the fetched page exposed only its title).

---

<a id="e-dejenwmbcla"></a>

## DejEnwmBclA | @italian_founder | "151 Trading Strategies" series, strategy 2/151: monthly Time-Series Momentum backtested on 6 markets (worked on gold and indices, lost on EUR and GBP)
- **Link:** https://www.instagram.com/p/DejEnwmBclA/
- **Account:** @italian_founder (Giacomo Ghinelli) · **Posted:** 2026-10-16 · **Type:** reel (18.6s, 8 pages). The batch folder only held the cover frame; I downloaded the full video during review.
- **Caption source:** full (Instagram; fetched with yt-dlp during review; the mirror copy was truncated)
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE – the source paper is real, the rules are fully disclosed, and losing markets are shown honestly. But it's the creator's own unaudited backtest with per-market tuned look-backs, a short out-of-sample window (indices only ~2 years), and a "comment MOMENTUM" lead-capture CTA.

### Post description
> Same idea, six markets. Gold loved it. The euro didn't.
>
> Comment MOMENTUM for the full spec.
>
> — Backtest. From "151 Trading Strategies" (Kakushadze & Serur). Look-back tuned per market on old data, then one run on unseen data: Apr 2022 – Sep 2026 (gold, forex), Jan/May 2024 – Sep 2026 (indices). Tick data, commission and swap included. Past performance doesn't guarantee future results.

### Audio
Creator's own speech (English; Whisper auto-detect failed, so I re-transcribed with English forced; matches the burned-in captions):
- [0.0–6.8] "This research paper describes 151 trading strategies and has more than 200,000 downloads."
- [6.8–9.8] "I'm testing them one by one and sharing the results."
- [9.8–15.8] "Being a trend-following strategy, it worked well on gold and indices but failed on currencies."
- [15.8–18.4] "Same idea, different market, opposite the result."

### On-screen content, page by page
**Page 1 (0.0s):** Creator to camera (trading desk; "fim"-style logo on the PC case). Caption "this research paper describes 151 trading strategies".
**Page 2 (0.5–3.7s):** Title page of "151 Trading Strategies", Zura Kakushadze and Juan Andrés Serur (Quantigic Solutions LLC, Stamford CT; Free University of Tbilisi; Universidad del CEMA, Buenos Aires), August 17, 2018. Abstract (summary: over 550 formulas for 150+ strategies across stocks, options, fixed income, futures, ETFs, indices, commodities, FX, convertibles, structured assets, volatility, real estate, distressed assets, cash, crypto, miscellany, global macro, infrastructure, tax arbitrage; some ML-based; source code for backtesting; ~2,000 references; 900+ glossary entries). "Copyright © 2018 Zura Kakushadze and Juan Andrés Serur. All Rights Reserved." Footnote "Electronic copy available at: https://ssrn.com/abstract=3247865".
**Pages 3–4 (3.7–6.7s):** SSRN listing: "151 Trading Strategies — Z. Kakushadze and J.A. Serur. 151 Trading Strategies. Cham, Switzerland: Palgrave Macmillan, an imprint of Springer Nature, 1st Edition (2018)…", "361 Pages · Posted: 13 Sep 2018 · Last revised: 13 Sep 2019", "Date Written: August 17, 2018". Paper statistics: **Downloads 247,728**, **Abstract views 377,730**, 781 References (red circle around the statistics).
**Page 5 (6.8s):** Card "Testing them", "Time-Series Momentum" (empty). Caption "and has more than 200,000 downloads".
**Page 6 (6.9s):** Tag "STRATEGY 2 / 151"; "Testing them one by one."
**Page 7 (9.7s):** Tags "STRATEGY 2 / 151 · TREND FOLLOWING"; "A trend-following…"; card **"Time-Series Momentum"** (Trend following):
- 01 "Once a month, close any open position."
- 02 "Compare last month's close with the close 3, 6 or 12 months before (chosen per market on old data)."
- 03 "Higher: buy and hold for the month. Lower: stay out (forex: sell)."
- 04 "No stop, no target: next month's check decides."
- 05 "Size so one average daily range risks the same amount."
**Page 8 (15.7s, final state from 2-fps frames):** Tags "STRATEGY 2 / 151 · TREND FOLLOWING · 6 MARKETS", "Worked on gold and indices." / "Same idea." Results grid with equity curves:
- **Gold — WORKED — Profit factor 2.00**
- **NASDAQ — WORKED — Profit factor 2.10**
- **Japan 225 — WORKED — Profit factor 2.41**
- **Euro — LOST — Profit factor 0.92**
- **Pound — LOST — Profit factor 0.73**
- **S&P 500 — WORKED — Profit factor 1.84**

Summary chips: "Gold & indices PF 1.84 – 2.41" | "Currencies PF 0.73 – 0.92". Footer: "Unseen data only · gold & forex Apr 2022 – Sep 2026, indices 2024 – Sep 2026 · tick data · costs included". Captions "but failed on currencies", "same idea, different market, opposite the result". (The cover image shows the grid mid-animation, with Euro and Pound still "Profit factor —".)

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "151 Trading Strategies", Z. Kakushadze & J.A. Serur (SSRN 3247865; Palgrave Macmillan 2018, ISBN 978-3-030-02791-9) | paper / book | caption; audio 0s; p.2–4 | Real and widely downloaded: SSRN listing 361 pages, posted 13 Sep 2018, revised 13 Sep 2019. The screen shows 247,728 downloads, so "more than 200,000" is accurate. A Spanish edition is on SSRN 3402665. It's a descriptive catalogue of formulas, not tested profitable systems. |
| Time-Series Momentum (strategy 2/151) | strategy | p.6–8 | A classic trend rule (cf. Moskowitz, Ooi & Pedersen 2012). The rule set shown (monthly rebalance, 3/6/12-month look-back, long/flat with short for FX, volatility-scaled sizing by average daily range) is a faithful, simple implementation. |
| Markets: Gold, NASDAQ, Japan 225, Euro (EUR/USD), Pound (GBP/USD), S&P 500 | instruments | p.8 | Results as listed above (PF 2.00 / 2.10 / 2.41 / 0.92 / 0.73 / 1.84). |
| Test windows: gold & forex Apr 2022–Sep 2026; indices Jan/May 2024–Sep 2026; tick data; commission and swap included | test settings | caption; p.8 | As stated by the creator. Not independently reproducible from the post. |
| Comment "MOMENTUM" | CTA | caption | DM "full spec". |

### What's being promoted / the funnel decoded
"Comment MOMENTUM for the full spec" sends an automated DM with the strategy spec. The rules are already fully shown on page 7, so the DM mainly builds the account's audience and lead list for a running "151 strategies" series. The handle "italian_founder" and the desk branding suggest the creator is building a trading or backtesting product, but none is named in the post, and web search found nothing on the creator. No price is shown.

### Verification & insights
- Web search confirmed the paper (SSRN abstract 3247865 and the Palgrave book), the authors and the posting dates. The on-screen download count (247,728) supports "200,000+".
- Credit where due: the post shows losing markets (EUR, GBP) and says costs are included, which is more honest than most.
- Caveats: (1) "Look-back tuned per market on old data" is a mild form of selection. (2) The out-of-sample window is short: about 4.5 years for gold and FX and only about 2–2.7 years for indices, during a strong bull run in gold, the Nasdaq, the Nikkei and the S&P. Long-only trend-following naturally looks good there. (3) A monthly rule over 2–4 years produces very few trades (roughly 24–54 decisions per market), so profit factors of 1.8–2.4 are statistically weak. (4) No drawdown, return or trade count is shown.
- Academic evidence for time-series momentum is long-standing across asset classes, but it has had long flat or losing stretches (e.g. 2012–2019 for many CTAs).
- Could not verify: the backtest itself (platform, data source, exact contracts); what the DM "full spec" contains.

---

<a id="e-derwxsizyex"></a>

## DerwxsIzyeX | @markus_ai_quant | Tier list of 6 strategy-building tools (ChatGPT F, Excel D, MetaTrader C, TradingView B, QuantConnect A, "Qube" S) – an ad by a co-builder of Qube (TQX / PandaAI)
- **Link:** https://www.instagram.com/p/DerwxsIzyeX/
- **Account:** @markus_ai_quant (display name not in data) · **Posted:** 2026-10-19 (decoded from shortcode; not in fetched data) · **Type:** reel (84s, 26 scene pages)
- **Caption source:** possibly truncated (mirror) – looks complete
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE – the descriptions of ChatGPT/Excel/MetaTrader/TradingView/QuantConnect are broadly fair, but the ranking is self-promotion: the creator says "I am biased because we built one" and puts his own product (Qube by TQX) in S tier

### Post description
> ranking the best quant tools so you don't have to #quant #trading #algotrading #aitrading #tqx

### Audio
Creator speaking to camera (English), lav mic in hand:
- [0.0–6.0] "I ranked 6 tools for building a trading strategy from S to F so you don't have to."
- [6.0–10.4] Quant trading = trading with rules and data instead of your gut.
- [10.4–13.1] "And yes, I am biased, because we built one."
- [13.1–19.7] **ChatGPT, F tier:** asking it what to buy just gives "an opinion that nobody has actually tested."
- [19.7–33.2] **Excel, D tier:** you can backtest in a spreadsheet, but one wrong cell can make the test use tomorrow's price for today's trade (look-ahead): results "look amazing, but they're fake." (Whisper: "one wrong sell")
- [33.2–44.8] **MetaTrader, C tier:** popular for forex (trading currencies such as the dollar and euro), but building a bot means learning its own coding language.
- [44.8–53.5] **TradingView, B tier:** very good charts and can backtest, but you must learn its language, Pine Script.
- [53.5–60.7] **QuantConnect, A tier:** powerful for testing, but you write real code in Python or C#.
- [60.7–64.7] "Everything from C to A wants you to be a programmer."
- [64.7–74.3] **Qube, S tier:** describe the idea in plain English; it turns it into exact rules, backtests them and runs it. "No code required." (Whisper: "Cube")
- [74.3–78.8] "The hard part of trading should be the idea, not learning how to code."
- [78.8–83.6] CTA: drop your own tier list in the comments, "Or comment Qube and I'll send you the full breakdown."

### On-screen content, page by page
Talking head in a hotel-lobby setting throughout, with burned-in uppercase word-by-word subtitles (mirroring the audio). Graphic overlays on the upper half:
**Pages 1–3 (0–13s):** Talking head only; subtitles "6 TOOLS FOR BUILDING A TRADING STRATEGY FROM S TO F SO YOU DON'T HAVE TO", "QUANT TRADING JUST MEANS TRADING WITH RULES AND DATA INSTEAD OF YOUR GUT", "AND YES I AM BIASED BECAUSE WE BUILT ONE" (small overlay text "I'm biased", "we built one").
**Pages 4–5 (13–19s):** Empty tier board S / A / B / C / D / F; overlay "Asking ChatGPT what to buy".
**Page 6 (19–23s):** Board: **F = ChatGPT** (logo), **D = Excel** (logo).
**Pages 7–9 (23–33s):** Dark spreadsheet titled "Premium" with columns Date / Open / High / Low / Close / Strategy Result (index-level prices ~14,000–28,000, rows dated 2023–2024); on page 8 one cell is highlighted red ("one wrong cell" → look-ahead). Overlay "Your" (results look amazing…).
**Page 10 (33–36s):** Board adds **C = MetaTrader**.
**Pages 11–12 (36–45s):** Big "$ DOLLAR" and "€ EURO" icons.
**Page 13 (45–47s):** Board adds **B = TradingView**.
**Pages 14–15 (47–53s):** TradingView chart screenshots (red/green candles, toolbar).
**Pages 16–17 (53–56s):** Board B–F filled; subtitle "PINE SCRIPT QUANT CONNECT"; an A-tier slot animating in.
**Page 18 (56–61s):** Code editor screenshot (Visual Studio-style IDE with C#/Python code, a chart pane) – "you have to write real code".
**Page 19 (64–66s):** Full board: **S = Qube** (cube logo), **A = QuantConnect**, **B = TradingView**, **C = MetaTrader**, **D = Excel**, **F = ChatGPT**.
**Pages 20–22 (66–70s):** Chat input box typing "Create a 5/20 MA crossover strategy on Tencent", model selector **"GPT-5.5"**.
**Pages 22–24 (69–73s):** Qube app UI (read from a full-res crop at 71s):
  - Left (chat): "Create a 5/20 MA crossover strategy on Tencent" → "Processed 1s – I will handle this in two steps: create the strategy, then run a backtest." – "Main agent · Completed Delegate Strategy agent" – "I'll create an HK stock strategy for Tencent (0700.HK): use daily close prices, buy when the 5-day moving average crosses above the 20-day moving average, exit when the 5-day moving average crosses below the 20-day moving average, and allocate available cash to Tencent on entry. Then I'll run a backtest with the default daily backtest settings unless you specified otherwise." – "Strategy agent · Completed Save HK strategy" – card "Created HK strategy · Tencent 5/20 MA · 0700.HK d0xba – 5/20 MA crossover on Tencent [View]".
  - Right (tabs Versions / **Params / Code** / Run history / Optimization): "V1 Initial 5/20 MA crossover", buttons Discard draft / Save / **Run backtest**. Backtest params: **Period 2025/09/03 → 2026/09/03**, **Initial capital 10000000**, **Commission mult. 1**, **Slippage 0**, **Frequency Daily 1d**. Strategy code: `from panda_backtest.api.api import *`, `from panda_backtest.api.stock_hk_api import *`, `import tqx_data`, `import pandas as pd`, `def initialize(context):`, `context.account = "15032863"`, `context.stock = "0700.HK"`…
**Pages 25–26 (73–84s):** Talking head; overlay "no code required"; subtitles "THE HARD PART OF TRADING SHOULD BE THE IDEA…", CTA.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| ChatGPT | app | audio 13s, page 6 (F tier) | OpenAI chatbot |
| Excel | app | audio 19.7s, page 6 (D tier) | Microsoft spreadsheet; look-ahead bias warning is a real, common backtest error |
| MetaTrader | platform | audio 33s, page 10 (C tier) | MetaQuotes MT4/MT5; bots ("Expert Advisors") written in MQL4/MQL5 – true |
| TradingView / Pine Script | platform / language | audio 44.8s, pages 13–15 (B tier) | Charting platform; strategy backtests need Pine Script – true |
| QuantConnect | platform | audio 53.5s, page 19 (A tier) | Cloud backtesting/live platform (LEAN engine), algorithms in Python or C# – true |
| Qube | product | audio 64.7s, pages 19–24 (S tier) | AI research/backtesting app of **TQX** (tqx.ai), "All-in-One AI Research" – natural language → strategy → backtest, HK and US equities |
| #tqx / TQX | brand | caption hashtag | tqx.ai – "Global AI Quantitative Trading Competition Platform"; footer entity **PandaAI Quantum Holdings Limited**; also runs an AI-only trading championship; docs at docs.tqx.ai |
| panda_backtest, tqx_data | code libraries | page 22–24 code | PandaAI/TQX's own backtest framework and data module (not public PyPI packages found) |
| GPT-5.5 | model | pages 20–22 | Model selector inside Qube (suggests it calls OpenAI models under the hood) |
| Tencent 0700.HK, 5/20 MA crossover | ticker / strategy | pages 20–24 | Demo strategy: buy when 5-day SMA crosses above 20-day, exit on cross below, all cash |
| Backtest params 2025/09/03–2026/09/03, capital 10,000,000, commission mult 1, slippage 0, daily | settings | page 22–24 | Defaults shown; slippage set to 0 |
| "Comment Qube" | CTA | audio 81s | DM funnel to the product |

### What's being promoted / the funnel decoded
The whole reel is an advertisement for **Qube**, the AI strategy builder of TQX (tqx.ai, PandaAI Quantum Holdings Limited); the creator discloses "we built one". "Comment Qube and I'll send you the full breakdown" → an automated DM with, in all likelihood, a sign-up/referral link to tqx.ai/Qube. The site has a payment page (/en/payment) but no prices could be retrieved (JS-only page), so pricing and any free tier are unconfirmed. TQX also promotes an AI trading competition run on its platform.

### Verification & insights
- tqx.ai homepage fetched: product Qube; markets HKEX securities and US (NASDAQ stocks/ETFs); entity PandaAI Quantum Holdings Limited; links to Discord, LinkedIn, Telegram, docs.tqx.ai, oss.pandaaiquant.com. Third-party listings describe TQX as an AI quant platform with a visual workflow editor and an LLM agent ("TQ1"), and a "Global AI Trading Championship".
- Claims vs reality:
  - Excel look-ahead point: valid, but look-ahead/overfitting risk exists in **every** backtester, including AI-generated ones – an LLM writing the code does not remove it; you then have to trust code you can't read.
  - "No code required": the demo still produces Python code; the user just doesn't write it.
  - The demo backtest uses **slippage 0** and a single-stock MA crossover; no results are shown, so there is no evidence the tool produces profitable strategies.
  - The ranking criteria (needs coding = worse) are chosen to put the creator's product on top; QuantConnect and TradingView are mature, widely used platforms; LuxAlgo, StrategyQuant X and others also offer plain-English → backtest features, so "S tier" uniqueness is overstated.
- Not verified: Qube pricing, the creator's role at TQX, account identity (no web results for @markus_ai_quant).

---

<a id="e-dbyl8lioyjk"></a>

## DbYL8liOyJk | @imelcapitanx | "The Math Behind the Markets" ep. 2 (model 2 of 9): logistic regression for trading bots – direction bot (>50% long) vs conviction bot (≥70% threshold, size up)
- **Link:** https://www.instagram.com/p/DbYL8liOyJk/
- **Account:** @imelcapitanx (display name not in data) · **Posted:** unknown (not in fetched data) · **Type:** reel (80s, ~35 animated screens; only 2 scene frames captured, all 160 2-fps frames reviewed via contact sheets)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE – correct, simplified explanation of logistic regression and probability-threshold sizing; the "single honest probability" framing glosses over calibration, overfitting and the fact that next-candle direction is close to a coin flip; no product shown

### Post description
> Ep. 2 of The Math behind the Markets. - Logistic Regression.
> Tell you the probability the market will go up or down #tradingbot #cryptotradingbot

### Audio
Voiceover (English), dark animated motion graphics:
- [0.0–12.9] Linear regression predicts how much price moves; the next model predicts which way and the odds. "It's called logistic regression and it's how quants turn a chart into a straight yes or no."
- [12.9–36.4] Linear gives a number; logistic gives a probability: the percent chance the next candle closes green. You feed it current data (recent moves, momentum, volume) and it returns one number from 0 to 100%. Over 50 = leaning up, under 50 = leaning down; "a single honest probability".
- [36.4–49.5] Two bots from that probability. Bot 1, a direction bot, just takes the call: over 50% goes long, under 50% goes short; "a straight up prediction machine".
- [49.5–67.3] Bot 2, "the smarter one", a conviction bot: you don't treat a 51% edge like a 90%, so it only fires when the model is confident, 70% or higher, and sizes up the surer it gets. "The probability becomes your risk control."
- [67.3–79.9] Limitation: logistic regression can only draw one straight line between up and down, and markets are messier. Next model: decision trees, "a bot that makes calls the way a trader actually does, one question at a time."

### On-screen content, page by page
Bold italic subtitles at the bottom follow the voiceover throughout.
**Page 1 (0–4s):** Rising candlestick chart; then a fitted line and a box "HOW MUCH? 5,845.98".
**Page 2 (6–12s):** "UP or DOWN?" + "the odds"; label "LOGISTIC REGRESSION"; small tag "The Math Behind the Markets".
**Page 3 (14–17s):** Card "LINEAR = a number 24,750" over a chart with a trend line.
**Page 4 (18–23s):** Card "LOGISTIC = a probability 72%" with an arrow to the next (green) candle.
**Page 5 (24–27s):** Input chips "RECENT MOVES", "MOMENTUM", "VOLUME" flowing into a box "MODEL – LOGISTIC".
**Page 6 (28–33s):** Gauge 0%–50%–100% moving from 50% to "72% LEANING UP", then "68% LEANING UP" ("over 50 leaning up / under 50 leaning down").
**Page 7 (34–36s):** "P ( NEXT CANDLE CLOSES GREEN )" – big "72%"; then "68%".
**Page 8 (38–41s):** "68%" branching into "BOT #1" and "BOT #2" – "TWO DIFFERENT BOTS".
**Page 9 (41–49s):** "BOT #1 — DIRECTION": gauge 69% → 68% → "LONG ▲"; 35% → "SHORT ▼".
**Page 10 (50–67s):** "BOT #2 — CONVICTION": gauge with a dashed "70% CONFIDENCE" line; 47%, 52%, 51% → "51% — too weak, skip"; 70% → "FIRES — threshold crossed", "POSITION SIZE · 0.8x"; 88% → "high conviction — size up", "POSITION SIZE · 2.0x", labels "stand aside" / "big, confident bet", "probability = risk control".
**Page 11 (68–73s):** Scatter of green and red dots split by one straight cyan line; caption "…[a str]aight line isn't enough." with misclassified dots circled.
**Page 12 (73–78s):** Decision-tree teaser: "Volatility > average?" → YES "Trend up?" / NO "Volume spike?" → leaves UP / DOWN / UP / DOWN; "decision trees — one question at a time."
**Page 13 (78–80s):** End card: "THE MATH BEHIND THE MARKETS · ✓ LOGISTIC REGRESSION · MODEL 2 OF 9 · NEXT → Decision Trees".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "The Math Behind the Markets", Ep. 2, "Model 2 of 9" | series | caption, pages 2, 13 | Creator's 9-part series (ep. 1 linear regression, ep. 3 decision trees) |
| Logistic regression | method | caption, audio, all pages | Standard binary classifier outputting P(class) via the sigmoid; explanation is correct |
| Linear regression "= a number" | method | audio 0–19s, page 3 | Predicts a continuous value; correct contrast |
| Features: recent moves, momentum, volume | inputs | audio 23–26s, page 5 | Example inputs; no exact definitions or lookbacks |
| Direction bot: >50% long, <50% short | rule | audio 39–49s, page 9 | Always in the market; no cost filter |
| Conviction bot: trade only if ≥70%, size up with probability (0.8x at 70%, 2.0x at 88%) | rule | audio 49–67s, page 10 | Threshold + probability-scaled sizing (Kelly-like idea). Only meaningful if the model's probabilities are **calibrated** |
| Example numbers 5,845.98; 24,750; 72%; 68%; 69%; 35%; 47%; 51%; 52%; 88% | numbers | pages 1–10 | Illustrative values only, not real model output |
| Decision trees ("Volatility > average?", "Trend up?", "Volume spike?") | next episode | pages 12–13 | Teaser for ep. 3 |
| #tradingbot #cryptotradingbot | hashtags | caption | Suggests a crypto-bot audience |

### What's being promoted / the funnel decoded
No CTA, link or product in this post. It's a free educational series; the hashtags suggest the account sells or promotes a crypto trading bot elsewhere, but nothing in this post shows one. Other @imelcapitanx posts exist in this batch set (DbUGaVAtQDU, DboqABjuY-v; not reviewed here). Web search found nothing indexed for the account.

### Verification & insights
- Concepts are textbook-correct: logistic regression gives a linear decision boundary and outputs probabilities; thresholding plus confidence-scaled sizing is a real technique.
- Missing caveats: (1) for "next candle green", out-of-sample accuracy for simple features is usually barely above 50%, so a model rarely outputs 70–88% honestly; when it does, that's often overfitting. (2) Raw logistic outputs need calibration checks (reliability plots, Brier score) before they can be used as "risk control". (3) Costs, slippage and walk-forward validation aren't mentioned. (4) Always-in "direction bot" trading every candle is usually eaten by fees.
- Not verified: any bot the account may sell; the account's identity.

---

<a id="e-det2rqpher4"></a>

## Det2rqpheR4 | @fidetolabs | "How To Build A Self-Improving AI Trading Agent #8": a stock-picking agent tries 4 of 24 factor/list-size combos per run, and without a written record repeats 27 checks in 12 runs, so "write a note for every try"
- **Link:** https://www.instagram.com/p/Det2rqpheR4/
- **Account:** @fidetolabs (FidetoLabs) · **Posted:** 2026-10-20 (decoded from the post ID; not in metadata) · **Type:** reel (35.8s, 1 animated page in 4 sections)
- **Caption source:** possibly truncated (mirror). Cut off at 253 characters ("…find a good..."). Full fetch failed (HTTP 429).
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE. The memory/trial-log point is correct and useful. But the toy example (picking whichever of 24 factor combos was "right in 6 of 7 years" on 77 stocks) is a textbook multiple-testing/overfitting setup the reel never warns about. The creator's own repo removed its trial ledger and significance bar, citing this exact problem.

### Post description
> An AI agent forgets everything when a run ends. The next run starts from zero. So it can't get better on its own. It gets better only if the last run wrote something down, and the new run reads that first.
>
> For example, say you want it to find a good...

(truncated by the mirror; the rest could not be fetched)

### Audio
Creator voice-over (also typed out as a subtitle box):
- [0.0–3.0] "Say you want an agent that finds a good way of picking stocks."
- [3.0–8.0] "A way of picking is two things: what you rank the companies on, and how many of the top ones you keep."
- [8.0–12.0] "Six things to rank on, four sizes of list, so there are 24 ways to try."
- [12.0–17.0] "It tries four of them, checks each one against seven past years, and keeps whatever was right in nearly all of them."
- [17.0–21.0] "Tomorrow it starts from nothing and tries four again out of the same 24."
- [21.0–24.0] "Do that 12 times and more than half of its tries are ones that already checked."
- [24.0–26.0] "You'd remember doing that. It can't."
- [26.0–32.0] "So give it a second tool: a file it writes every try into, with what it tried, which years it checked and how that went."
- [32.0–35.0] "Now it reads the file first and never checks the same thing twice."

### On-screen content, page by page
Dark terminal-style animation. Tag "@fidetolabs". Title "**How To Build A Self-Improving AI Trading Agent #8**". A diagram of boxes: "**the agent** – tries things, and reads back" connected to "**the data platform** – prices and filings, as they stood" and a third slot.
**Section 00 (0–~12s): "THE LOOP, AND ITS TWO TOOLS"**. Subtitle "77 companies in one industry · it checks 7 past years, one at a time". Third box: "**no second tool** – every run starts from nothing". Grid "RANK ON" × "KEEP 10 / KEEP 20 / KEEP 30 / KEEP 40". Rows: how much it rose (LAST 12 MONTHS) · price against its assets (PRICE TO BOOK) · price against its profit (PRICE TO EARNINGS) · how much cash it holds (NET CASH TO VALUE) · how fast it is growing (REVENUE GROWTH) · how small it is (SMALLEST FIRST). Text: "rank them on one number, keep the top few" / "**6 things to rank on × 4 sizes of list = 24 ways it could try**" / "good enough, for you, means right in 6 of the 7 years" / footer "in: a way to try › step: one tool, no memory › out: 24 to choose from".
**Section 01 (~12–18s): "ONE RUN, FOUR TRIES"**. "it was right in a year if the few it kept beat the rest of them". Table "WHAT IT TRIED – RIGHT IN – OF 7": how much it rose, keep 30 → **4** not good enough · price against its assets, keep 10 → **7** good enough · price against its profit, keep 30 → **4** not good enough · how much cash it holds, keep 30 → **2** not good enough. Footer "in: 4 of the 24 › step: checked on 7 years › out: 1 good enough".
**Section 02 (~18–26s): "TWELVE RUNS, NO RECORD"**. "the same agent, run again and again, with nothing kept in between". The grid fills, with repeats outlined red. Stats: "**48** tries spent · **21 of 24** ways actually tried · **27** checked before · **3** never tried at all" / "14 of those had already come back not good enough" / footer "in: 12 runs, nothing kept › step: try, check, forget › out: 27 done twice".
**Section 03 (~26–35.8s): "THE SAME AGENT, WITH A RECORD"**. "one note per try, and the next run reads them before it tries anything". Third box becomes "**the record** – what it tried · the years · how it went". The grid fills green, each cell once. "24 tries, all 24 ways covered, nothing checked twice" / "**WRITE A NOTE FOR EVERY TRY**" / "what it tried, which years it checked, how it went, and what you call good enough and read them first, before it tries anything" / "next session: it starts from the record, not from a blank screen".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| @fidetolabs / FidetoLabs | handle/company | tag, title | fidetolabs.com: a solo quant builder with waitlisted Data and Agents products, a newsletter and a free Discord (from a prior review of this account, DeUE0tQPmgX) |
| "the data platform – prices and filings, as they stood" | product concept | diagram | Matches FidetoLabs' open-source **Qanat** (github.com/fidetolabs/qanat, MIT): a point-in-time data platform served to agents as an MCP server. Remote HEAD 5cf5d14 (2026-10-20). |
| "the record" (trial log) | concept | section 03 | A persistent experiment ledger/memory file. Qanat's docs/agents.md says `record_trial` / `list_trials` / `read_bar` / `set_bar` were **removed in 0.4.0**. |
| Factors: 12-month return, P/B, P/E, net cash to value, revenue growth, size | factors | grid rows | Standard momentum, value, quality, growth and size factors |
| 77 companies, 7 years, 6-of-7 threshold, keep 10/20/30/40 | parameters | section 00 | Toy setup. Universe and tickers are not named. |
| 24 / 48 / 21 of 24 / 27 / 3 / 14 | numbers | sections 00–02 | Internally consistent: 12 runs × 4 = 48; 48 − 21 unique = 27 repeats; 24 − 21 = 3 untried. Audio "more than half of its tries already checked" → 27/48 = 56%. |
| Results 4/7, 7/7, 4/7, 2/7 | numbers | section 01 | Illustrative. No real data or dates are shown. |

### What's being promoted / the funnel decoded
No call to action is visible in the clip or the visible caption. It is part #8 of an educational series that builds an audience for FidetoLabs (waitlisted paid data/agent products, newsletter, Discord). No pricing was found.

### Verification & insights
- `git ls-remote` and fetch of fidetolabs/qanat: MIT license, active (last commit 2026-10-20, "Fix a docstring that still named purge and embargo"). Code not executed.
- **The important caveat the reel skips:** an agent that tries all 24 combos and keeps the one "right in 6 of 7 years" is doing a specification search. With 24 tries on 77 stocks over 7 years, some combo will pass by chance. The record prevents *wasted* repeats but makes the search more complete, which raises overfitting risk unless the record also tracks the number of trials and applies a stricter bar (deflated Sharpe, out-of-sample years). FidetoLabs' own docs make this point. They removed the trial ledger and significance bar because "at fourteen annual rebalances the significance bar lands at an IC of 0.069 and a real indicator is 0.02 to 0.06, so the test fails on a true effect".
- The "agent memory" advice (persist what was tried and read it first) is a sound, standard agent-engineering pattern (scratchpads, experiment logs, CLAUDE.md-style notes).
- Not verified: the full caption, and whether the numbers came from a real run (no tickers or dates are shown).

---

<a id="e-derq3lkinis"></a>

## DerQ3LKinis | @quantifiedstrategies | 6-slide summary of the Barahhou & Abitbol ETF-flow paper: long 12M flow minus 3M flow, long top 50 / short bottom 50
- **Link:** https://www.instagram.com/p/DerQ3LKinis/
- **Account:** @quantifiedstrategies (Quantified Strategies) · **Posted:** 2026-10-19 · **Type:** reel (12.1s, 6 pages, 2s each, a slideshow)
- **Caption source:** full (Instagram)
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE. The paper is real (Barahhou & Abitbol, covered by Kepler Cheuvreux), but the headline stats (17.6% / 0.98 Sharpe) could not be checked against the paper. The post itself says the strategy can't realistically be replicated by retail traders. The funnel is a paid Skool community.

### Post description
Over 150 words, so the opening is quoted verbatim, followed by every remaining fact.
> ETF flows may help predict stock returns — but timing matters.
>
> A recent study found that long-term and short-term ETF flows can tell very different stories about future stock performance.
>
> 📌 THE RESEARCH IN A NUTSHELL
>
> Persistent ETF inflows may signal strong institutional demand. Stocks experiencing sustained buying pressure may deliver stronger future returns.
>
> However, very recent inflows may indicate temporary crowding or short-lived enthusiasm that could later reverse.
>
> The trading idea:
> ✅ Favor stocks with strong long-term ETF demand
> ✅ Avoid stocks with excessive short-term crowding
>
> THE RULES
>
> The strategy:
> 1️⃣ Measures ETF buying pressure over 12 months
> 2️⃣ Measures ETF buying pressure over 3 months
> 3️⃣ Standardizes both signals
> 4️⃣ Combines them into a ranking score
> 5️⃣ Buys the strongest stocks
> 6️⃣ Shorts the weakest stocks
>
> The goal is to capture persistent demand while avoiding temporary flow-driven distortions.
>
> 📊 HISTORICAL RESULTS
>
> ✅ 17.6% annualized return
> ✅ 0.98 Sharpe ratio
> ✅ Approximately 16% maximum drawdown
> ✅ 0.06 market beta
>
> The effect appeared stronger in the U.S. than in Europe.

The rest of the caption:
- "WHY DOES THIS MATTER?": ETF activity "may reveal information beyond price movements, showing where capital is consistently accumulating and where short-term buying may have become crowded."
- "One major limitation: Replicating this strategy requires detailed ETF holdings and fund-flow data."
- Key lesson: persistent flows and short-term crowding give different signals.
- CTA: "Want more evidence-based trading strategies, backtests, and systematic market research? Join our Skool community — link in bio."
- "ABOUT QUANTIFIED STRATEGIES": run by former proprietary traders **Håkan Samuelsson and Oddmund Groette**; publishing since **2012**; "millions of readers"; newsletter **25,000+ subscribers**; trading books **30,000+ copies** sold.
- Hashtags: #ETFFlows #TradingResearch

### Audio
No speech. Whisper output only a spurious "You" at 0.8s. Background music, not identified.

### On-screen content, page by page
Every slide has the footer "QUANTIFIEDSTRATEGIES.COM" and a page counter.
**Page 1 (0–2s, 1/6):** "CAN ETF FLOWS **PREDICT** STOCK RETURNS?" / "RESEARCH TRADING EDGE" / "LONG-TERM FLOWS + SHORT-TERM REVERSAL" / ✓ PAPER BREAKDOWN ✓ RULES ✓ RESULTS. Photo of a bald man in a blazer (likely an AI-styled image of a founder).
**Page 2 (2–4s, 2/6):** "THE RESEARCH IN A NUTSHELL": ✓ "ETF flows may contain useful information about future stock returns." ✓ "When money flows into ETFs, the funds often buy the underlying stocks." ✓ "Short-term ETF-driven pressure tends to reverse." ✓ "Longer-term sector and thematic ETF flows can support continued strength." The graphic shows ETF INFLOWS → ETF → AAPL, MSFT, NVDA, AMZN. Box: "Paper: ETF Flows and Stock Market Dynamics — Barahhou & Abitbol".
**Page 3 (4–6s, 3/6):** "THE RULES — PLAIN ENGLISH": (1) "MEASURE ETF BUYING PRESSURE OVER THE LAST 12 MONTHS." (2) "MEASURE ETF BUYING PRESSURE OVER THE LAST 3 MONTHS." (3) "STANDARDIZE BOTH MEASUREMENTS AND SUBTRACT SHORT-TERM FROM LONG-TERM." (4) "RANK ALL STOCKS, BUY THE TOP 50, SHORT THE BOTTOM 50, REBALANCE MONTHLY." Formula: **Score = 12M Flow Signal − 3M Flow Signal**. Icons: BUY TOP 50 | SHORT BOTTOM 50 | REBALANCE MONTHLY. Banner: "THE STRATEGY TRIES TO CAPTURE PERSISTENT DEMAND WHILE FADING SHORT-TERM CROWDING."
**Page 4 (6–8s, 4/6):** "THE LOGIC BEHIND THE EDGE": (1) "Long-term ETF inflows may signal persistent institutional demand." (2) "Very recent ETF buying can create short-term price pressure that later reverses." (3) "Stocks with strong long-term flows but less extreme recent pressure may be more attractive." An "EXAMPLE STOCKS" bar chart (scale −2 to 2) shows 12M Flow (green), 3M Flow (red) and Combined Score (12M minus 3M, standardized) for Stock A (Attractive: about +1.6 / +0.35 / +1.3), Stock B (Overheated: about +1.0 / +1.4 / −0.5) and Stock C (Weak Flows: about +0.3 / +0.45 / −0.8). Banner: "Best candidates: strong 12M flows, less overheated 3M flows."
**Page 5 (8–10s, 5/6):** "THE RESULTS AND LIMITATION": **17.6% ANNUALIZED RETURN · 0.98 SHARPE RATIO · ~16% MAX DRAWDOWN · 0.06 MARKET BETA**. "The effect appeared stronger in the U.S. than in Europe." "HARD TO REPRODUCE WITH ORDINARY PRICE DATA. YOU NEED ETF HOLDINGS AND FUND-FLOW DATA." "INTERESTING RESEARCH, BUT NOT AN EASY RETAIL STRATEGY TO REPLICATE."
**Page 6 (10–12s, 6/6):** "WANT MORE RULE-BASED STRATEGIES?" "Explore more trading research, backtests, and strategy ideas at Quantified Strategies." ✓ Backtests and research ✓ Trading ideas and education ✓ Rules-based strategies ✓ Practical market insights. A laptop graphic reads "BETTER STRATEGIES HIGHER RETURNS". Button: **skool.com/rulebasedtrading →**

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "ETF Flows and Stock Market Dynamics", Barahhou & Abitbol | paper | page 2 | Real. The full title is "ETF Flows and Stock Market Dynamics: Patterns, Signals and Portfolio Construction Insights" by Inès Barahhou (CFA) and Sacha Abitbol, covered by Kepler Cheuvreux (allnews.ch summary). It uses Trackinsight global ETF data and finds short-term ETF-driven buying followed by corrections. The full PDF was not found. |
| 17.6% / 0.98 / ~16% / 0.06 beta | numbers | page 5, caption | Attributed to the paper. Could not be checked against the paper. |
| AAPL, MSFT, NVDA, AMZN | tickers | page 2 graphic | Decorative examples only. |
| quantifiedstrategies.com | site | every page | Quantified Strategies, a long-running backtest blog by Oddmund Groette and Håkan Samuelsson. Its site was behind bot protection when fetched. |
| skool.com/rulebasedtrading | community | page 6, caption ("link in bio") | Verified: the "Rule-Based Trading" Skool group, owned by Oddmund Groette, **paid, $99/year**, 365 members. Offers daily backtested strategies, code for 6 platforms, courses and AI prompt templates. |
| Trackinsight | data vendor | (found in verification) | The ETF-flow data source behind the paper. |

### What's being promoted / the funnel decoded
"Join our Skool community — link in bio" leads to skool.com/rulebasedtrading, the **Rule-Based Trading** community run by Oddmund Groette at **$99/year**. The research summary is free content that funnels into it.

### Verification & insights
- The paper exists and its direction matches the slides: short-term ETF pressure reverses, and longer-term flows persist. The exact top-50/bottom-50 monthly long-short construction and the performance numbers come only from this post.
- Realism: these are pre-cost academic long-short results. Shorting 50 names monthly carries borrow fees, plus turnover and slippage. A 0.98 Sharpe before costs can shrink substantially after them. The post itself flags that ETF holdings and flow data are required (Trackinsight and similar vendors are paid).
- The 0.06 beta means it is market-neutral, so returns don't depend on the market's direction.
- Not verified: the 17.6% / 0.98 / 16% figures, the sample period, and whether the image of the man is AI-generated.

---

<a id="e-dd4ub-8sd-c"></a>

## Dd4uB-8Sd_C | @julias.algos | Explainer: order-book Level 1 (BBO), Level 2 (market by price), Level 3 (market by order), and CME pro-rata matching
- **Link:** https://www.instagram.com/p/Dd4uB-8Sd_C/
- **Account:** @julias.algos (julia) · **Posted:** 2026-09-29 · **Type:** reel (78.1s, 35 scene pages)
- **Caption source:** full (Instagram, via yt-dlp; the mirror copy was cut off)
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE. The L1/L2/L3 explanation is accurate. Two overstatements: L3 does not normally show "who placed" an order (MBO feeds are anonymous), and "HFT firms pay millions" for it is exaggerated, since MBO data is commercially available relatively cheaply. The pro-rata point is real for some CME interest-rate products.

### Post description
> An order book is a real-time list of all the buy and sell orders waiting to be filled for a stock, crypto, or other traded asset.
>
> Level 1 data shows the highest bid and lowest ask, along with their sizes.
>
> Level 2 data goes deeper, showing multiple price levels of bids and asks and how much is available at each price, giving you a better picture of market depth.
>
> Level 3 data is even more detailed, showing the individual orders that make up those price levels, often including information such as order size, position in the queue, and order updates.
>
> Together, these levels provide increasingly detailed views of supply, demand, liquidity, and how orders are positioned in the market.
>
> #finance #quantfinance #quant #optionstrading #stock

### Audio
The creator's own speech (English), timestamped:
- [0.0–5.8] Hook: "Most traders look at charts, but quants look at something called the order book." It has three distinct levels.
- [5.8–20.0] Level 1 (top of book): the best bid (highest price a buyer will pay) and best ask (lowest price a seller will accept); the gap is the bid-ask spread. This is what retail traders see, "just the tip of the iceberg".
- [20.0–41.4] Level 2 (depth of book): total quantity at every price level, not just the best. Example: if Apple's best ask is $200, L2 shows how many shares sit at $200.01, $200.02 and so on. This is market depth; firms use it to see where liquidity stacks up before trading.
- [41.4–55.8] Level 3: instead of aggregated totals, every single order in the queue, "who placed it, how much, and when". Claim: "This is the data that high-frequency trading firms pay millions for", because it shows exactly where you are in line and whether someone is about to jump in front of you.
- [55.8–69.4] Pro-rata matching: most assume first in, first out (FIFO), but on exchanges like the CME for interest-rate futures it's pro rata, so the biggest order gets the biggest fill regardless of arrival time.
- [69.4–75.2] HFT firms exploit this by flooding the book with large orders to secure a bigger allocation.
- [75.2–78.0] CTA: like and follow for more.

### On-screen content, page by page
Talking head with word-by-word subtitles that match the audio. Inserted graphics:
- **Pages 2–3 (0.7–2.9s):** Grid of candlestick-pattern diagrams (small "vt" logo).
- **Page 4 (2.9–3.7s):** Exchange order book with a depth chart. Order | Volume | Buy || Sell | Volume | Order rows: 2 1452 2,842 | 2,850 647 2 · 4 2635 2,840 | 2,852 1179 1 · 2 2756 2,838 | 2,854 2656 4 · 3 3621 2,836 | 2,856 3009 2 · 2 979 2,834 | 2,858 829 3 · 3 8566 2,832 | 2,860 5000 1 · 4 6382 2,830 | 2,862 13587 3 · 2 958 2,828 | 2,864 804 2 · 2 3596 2,826 | 2,866 5000 1 · 5 22030 2,824 | 2,868 2714 2. Totals: 29 orders, 52,975 bid volume vs 35,425 ask volume, 21 orders.
- **Page 6 (5.8–8.4s):** Purple label "**Level 1 : BBO (Best Bid and Offer)**".
- **Pages 8–11 (8.9–14.8s):** Order-book diagram (Volume | Price). Supply (ASK): 300@1.27, 650@1.26, 1200@1.25, 750@1.24, 400@1.23, 200@1.22. Spread 1.21. Demand (BID): 240@1.20, 400@1.19, 800@1.18, 650@1.17, … Speech bubbles: "I'm willing to sell EUR750 at $1.24", "I'm willing to sell EUR200 at $1.22", "I'm willing to buy EUR240 at $1.20".
- **Page 12 (14.8–17.0s):** Bid-ask spread bar chart (red asks above, green bids below; "best bid", "best ask", spread marked).
- **Page 13 (17.0–18.6s):** Code-style box: "Best Bid: 28,500 USDT / Best Ask: 28,505 USDT / Last Trade: 28,502 USDT / Bid Volume: 0.75 BTC / Ask Volume: 0.60 BTC".
- **Page 15 (20.0–22.4s):** Purple label "**Level 2 : MBP (Market by Price)**".
- **Page 16 (22.4–26.8s):** Table "makefile / timestamp | price | size | side": 2024-12-10T14:32:01Z | 41250.50 | 0.584 | bid · …| 41250.00 | 1.122 | bid · …| 41251.00 | 0.340 | ask · …| 41251.50 | 0.945 | ask.
- **Page 17 (26.8–29.3s):** Apple store logo (for the "$200 ask" example).
- **Page 21 (41.3–44.2s):** Purple label "**Level 3 : MBO (Market by Order)**".
- **Pages 22–23 (44.2–48.0s):** Table "timestamp | order_id | price | size | side | event". The first row reads 2024-12-10T14:32:01Z | 8432089231 | 41250.50 | 0.40 | bid | new. Further rows show the events "modify" and "cancel".
- **Pages 24, 26 (48.0–55.7s):** Dense raw L3 message-log tables (order IDs, prices, sizes, timestamps; too small to read in full).
- **Page 28 (55.7–57.5s):** Purple label "**Pro-Rata Allocation**".
- **Page 31 (61.8–64.8s):** Photo of a CME Group building.
- **Pages 32–33 (64.8–69.5s):** Diagram of an incoming order split among boxes labelled "TOP $", "☆ 30%", "Pro rata", "…", "FIFO".
- **Pages 34–35 (69.5–78.1s):** Talking head, then the outro.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Level 1 / BBO | concept | audio, page 6, caption | Correct: best bid and offer with sizes. |
| Level 2 / MBP | concept | audio, page 15, caption | Correct: aggregated size per price level. |
| Level 3 / MBO | concept | audio, page 21, caption | Correct in that it shows individual orders with IDs, queue position and add/modify/cancel events (e.g. CME MDP 3.0 MBO, Nasdaq TotalView-ITCH). **Not** "who placed it": orders are anonymous apart from optional MPID attribution on some US equity venues. |
| "HFT firms pay millions" | claim | audio 48s | Overstated. Firms do spend millions on co-location and direct feeds for speed, but historical and real-time MBO data is sold by vendors such as Databento at prices far below that. |
| CME pro-rata matching | fact | audio 55.8–69.4s, pages 31–33 | Real. CME Globex uses pro-rata or split FIFO/pro-rata algorithms (e.g. "A" and "K" algorithms with TOP-order priority) for products such as SOFR futures, some options and Treasury calendar spreads. Treasury outrights and equity index futures use FIFO. So "interest rate futures = pro rata" is partly true. |
| HFT over-sizing orders under pro-rata | claim | audio 69–75s | A documented practice (well known from Eurodollar futures): over-sizing orders to gain allocation, then managing overfills. |
| Apple $200 / $200.01 / $200.02 | example | audio 26.8–36s | Illustrative only. |
| BTC prices 28,500 / 41,250 | example data | pages 13, 16, 22 | Illustrative; they do not match actual BTC prices on 2024-12-10 (about $97k). |

### What's being promoted / the funnel decoded
Only "like and follow". A third-party creator-marketplace profile (Motion) lists @julias.algos as an education creator (about 133k Instagram followers) who has done brand partnerships (OpenAI, Vibe.us and others). No sponsor is shown in this reel.

### Verification & insights
- Overall a good, accurate primer. The caption is more careful than the audio: it says "position in the queue, order updates" and does not claim "who placed it".
- Saying retail sees "just the tip of the iceberg" is dated. Many retail brokers and platforms now offer L2, and L3/MBO futures data is purchasable.
- Free sources to go deeper: CME Group "Matching Algorithm Overview" documentation, Databento's MBO/MBP schema docs, and Nasdaq TotalView-ITCH specs.
- Not verified: the creator's identity beyond the first name "julia", and the sources of the inset images.

---

<a id="e-deqdc8pbtp-"></a>

## DeqDC8pBTp- | @otsullu.insta | "Why option delta is lying to you": a 50-delta call is not a 50% ITM probability (Delta = N(d1) vs ITM probability = N(d2))
- **Link:** https://www.instagram.com/p/DeqDC8pBTp-/
- **Account:** @otsullu.insta (OTS Ullu) · **Posted:** 2026-10-19 · **Type:** reel (81.0s, 4 scene pages; ~40 distinct subtitle and animation states). The video is low resolution (356×634), and the yt-dlp download has the same resolution.
- **Caption source:** full (Instagram, fetched by reviewer). The caption itself stops mid-word ("🦉 Stop treating Del"), probably at Instagram's 2,200-character limit because the bold Unicode letters count double.
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE: the core maths is correct (call Delta = N(d1) > N(d2) = risk-neutral ITM probability, and the gap grows with σ√T). Two problems: the narration equates "expiring in the money" with "the option actually turns a profit", which is wrong because premium is ignored, and the video cuts off mid-sentence. The opening "options chain" and "formula board" images are AI-generated with nonsense numbers and equations.

### Post description
Opening quoted verbatim (bold Unicode rendered as plain text). The whole caption is informational.
> 🚨 Why Option Delta Is Lying to You! The ITM Probability Myth 📈💡
>
> 🎯 Does a 50-delta call really have a 50% probability of expiring in-the-money (ITM)?
>
> Not exactly. And the mathematics explains why. 🛑

- Many traders treat Delta as a direct measure of ITM probability; it can be a useful approximation, but confusing the two misses a fundamental distinction in options pricing.
- "💡 The Math Behind the Myth" section:
  - **Delta is not probability:** it measures sensitivity to the underlying's price, not simply the likelihood of expiring ITM.
  - **Digital options:** a cash-or-nothing digital pays a fixed amount if ITM at expiry, however far past the strike; its normalized price reflects risk-neutral ITM probability, not its Delta.
  - **Vanilla calls:** under Black-Scholes, call Delta N(d₁) exceeds risk-neutral ITM probability N(d₂), because Delta includes the effect of increasingly valuable ITM outcomes.
  - **Vanilla puts:** the relationship reverses; |put Delta| is lower than the corresponding risk-neutral ITM probability.
  - **Volatility effect:** higher volatility and longer time to expiry widen the gap between d₁ and d₂, making the shortcut potentially more misleading.
- "⚠️ The Key Takeaway": "Delta measures price sensitivity. ITM probability measures the likelihood of a terminal outcome. They are related, but they are not interchangeable."
- Even the model-implied ITM probability is risk-neutral, not necessarily the actual probability of the outcome.
- The caption ends mid-word: "🦉 Stop treating Del".

*Caption condensed – full text is on the original post.*

### Audio
A synthetic-sounding narrator, with no music of note. Burned-in handwritten-style subtitles follow the speech word by word.
- [0.0–7.5] "Option Delta is a common mental shortcut. Traders assume a 50 Delta means exactly a 50% chance of winning."
- [7.5–16.0] Treating it as the exact probability of expiring in the money, which the narrator equates with "the option actually turns a profit", "is a mathematical trap."
- [16.0–23.0] Example: a one-year call at exactly 50 Delta on "a wildly unpredictable tech stock."
- [23.0–33.0] If the trade paid a flat, fixed cash reward once it crossed the target price, 50 Delta would match a 50% chance of cashing out.
- [33.0–46.0] "But standard options don't have capped rewards." The stock could in theory rise without limit, and the payout grows the further it goes past the strike.
- [46.0–59.0] As a measure of risk exposure, Delta must account for those rare huge payouts, which "pulls the Delta higher than the raw probability of simply crossing the target line."
- [59.0–71.0] When the market expects big swings (high implied volatility) and months remain to expiry, the gap is at its widest.
- [71.0–81.0] Back to the example: the "supposedly safe 50 Delta option might actually only give you a 40% chance of ever seeing" (the video ends here, mid-sentence)

### On-screen content, page by page
A yellow "OTS Ullu" header appears throughout.
**Page 1 (0.0–7.7s):** An AI-generated illustration of an "OPTIONS CHAIN" on a whiteboard. Columns: Call Last, Call Bid, Call Ask, Call Vol | DELTA (highlighted in red) | Put Vol, Put Ask, Put Bid, Put Last. Strikes and deltas: 140 → 0.78, 145 → 0.65, 150 → 0.54, 155 → 0.41, plus a fifth row partly hidden. The bid/ask/last cells hold incoherent numbers and percentages, such as call row 140 "2.30 / 1.32 / 1.74" with "29.5% 22.7% 10.6%". They are decorative, not real quotes.
**Page 2 (7.7–16.5s):** An AI-generated "math trap" image: a bear trap around the Black-Scholes PDE "∂V/∂t + ½σ²S²∂²V/∂S² + rS∂V/∂S − rV = 0", surrounded by garbled pseudo-equations.
**Page 3 (16.5–~23s):** A phone mockup showing a jagged multi-colour price chart. Subtitles: "option sitting at", "on a wildly unpredictable", "tech stock."
**Page 4 (~23–81s):** An animated chart. Y-axis "Payout / Prob", x-axis "Stock Price", a dashed line at "Strike (K)", and a bell-shaped probability curve with the area right of the strike shaded.
- ~24–33s: a red step payoff (a digital/fixed payout). Labels: "Probability ITM: 50%" and "Option Delta: 50" (in red).
- ~35–52s: the payoff becomes a ramp to "Infinity" (a vanilla call), and red arrows grow larger to the right (larger payouts). The labels stay at 50% / 50, and then "Probability = N(d₂)" and "Delta = N(d₁)" appear.
- ~54–72s: "Option Delta: 60" while "Probability ITM: 50%". The formula "d₁ = d₂ + σ√T" appears, and a double arrow between N(d₂) and N(d₁).
- ~74–81s: the distribution shifts left and flattens. Labels: "Probability ITM: 40%" and "Option Delta: 50".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Delta = N(d₁) | formula | caption, page 4 | Correct Black-Scholes call delta (no dividends) |
| Risk-neutral P(ITM) = N(d₂) | formula | caption, page 4 | Correct for a call under the risk-neutral measure |
| d₁ = d₂ + σ√T | formula | page 4 | Correct by definition |
| Cash-or-nothing digital option | product type | caption, audio 23s | Real. Its price is e^(−rT)·N(d₂), so the normalised price equals the risk-neutral ITM probability. |
| Black-Scholes PDE | formula | page 2 | Shown correctly in the centre of an otherwise AI-garbled image |
| Example: 1-year 50-delta call, "40%" ITM | number | audio 16–81s, page 4 | A plausible illustration, not computed (see below) |
| OTS Ullu | brand | header | The account's own brand. No product or link is in the post. |

### What's being promoted / the funnel decoded
- No CTA, link or product appears in the post. It is educational content that builds the account's audience. The caption's cut-off final line ("Stop treating Del…") is probably a sign-off.

### Verification & insights
- **N(d₁) > N(d₂) for calls:** true, since d₁ − d₂ = σ√T > 0.
- **The put relation reverses (|put Δ| = N(−d₁) < N(−d₂) = put ITM probability):** true.
- **The gap grows with volatility and time:** true.
- **"50-delta... might only give you a 40% chance":** for Δ = 0.50, d₁ ≈ 0 (ignoring r), so P(ITM) = N(−σ√T). That gives 40% at σ√T ≈ 0.25, for example σ = 25% over 1 year. For a "wildly unpredictable tech stock" with σ around 50–60% over 1 year, the risk-neutral P(ITM) would be roughly 27–31%, so the video's 40% is conservative. (Hand calculation, not executed code.)
- **Error in the narration:** "expiring in the money, meaning the option actually turns a profit" is wrong. ITM at expiry means S_T > K. Profit needs S_T > K + premium paid, so the probability of profit is lower still.
- The caption correctly adds that N(d₂) is a risk-neutral, not real-world, probability. The video omits this.
- The page 1 options chain and the page 2 equations are AI-generated decoration with meaningless values. Do not read them as data.
- Could not verify: who is behind OTS Ullu. The video ends mid-sentence, possibly cut short in editing.

---

<a id="e-dboqabjuy-v"></a>

## DboqABjuY-v | @imelcapitanx | "Math Behind the Markets" Ep. 4: Random Forest explained as two trading bots (majority-vote "consensus bot" and vote-count "confidence bot"), branded "Atomik Trading presents"
- **Link:** https://www.instagram.com/p/DboqABjuY-v/
- **Account:** @imelcapitanx · **Posted:** unknown (not in mirror data) · **Type:** reel (79.5s, 5 scene pages; continuous animation, verified on 2-fps frames)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE. The explanation of random forests (bagging, random feature subsets, majority vote) is correct. "Models quants use to make millions" is hype. Raw tree-vote share is not a calibrated probability, so sizing positions on it needs calibration and out-of-sample testing. The video is marketing for Atomik Trading, a paid futures-automation service.

### Post description
> Machine learning models quants use to make millions Ep. 4 Random Forrest #algotrading #tradingbot #aitrading

### Audio
Voice-over narration (English) over music:
- [0.0–10.7] Intro: "Welcome to Math Behind the Markets. These are the machine learning models quants use to make millions", buildable into your own trading bot. Today: "one of the most powerful ones, the Random Forest."
- [10.7–23.3] A Random Forest is a bunch of decision trees (simple yes/no flow charts). Each tree trains on a different random slice of your history and looks at different signals, so each makes different mistakes.
- [23.3–39.4] On every new setup all 100 trees vote buy, sell or sit out, and the majority wins. If one tree overfits to a pattern that isn't real, the other 99 outvote it. "The randomness is the whole point."
- [39.4–50.4] Bot 1, a consensus bot: takes the majority vote, "one steady call out of 100 opinions", so no single bad tree can wreck it.
- [50.4–67.9] Bot 2, a confidence bot: uses the vote count, not just the vote. 90 of 100 agreeing = conviction, size up; a 55–45 split = unsure, stay small or sit out. "You trade how much the crowd agrees, not just which way it leaned."
- [67.9–79.3] Teaser for the next episode: drop rules entirely; a bot that finds the one moment in history most like right now and trades what happened next: K nearest neighbors.

### On-screen content, page by page
Dark animated motion graphics in teal and green with word-by-word captions at the bottom.
**Page 1 (0.0–10.6s):** "ATOMIK TRADING PRESENTS / THE MATH BEHIND THE MARKETS" over a rising candlestick chart. Icons for a chart, a network and a node graph. A "YOUR BOT" card.
**Page 2 (10.6–39.3s):** "TODAY'S MODEL: RANDOM FOREST". A single tree with BUY / NO leaves, labelled "a decision tree — simple yes / no rules". A counter "33 decision trees" grows to a full grid. "YOUR TRADE HISTORY" strip with a highlighted window: "each tree learns a **different random slice**". "◆ NEW SETUP". A vote bar with green/red trees and "MAJORITY: BUY". Red, overfit trees outvoted. Quote card: *"the crowd beats the genius"*.
**Page 3 (39.3–50.3s):** "From that forest, **two bots**." "BOT 1 · CONSENSUS BOT", "NEW SETUP", "100 TREES", "MAJORITY VOTE": counter goes from 0 BUY / 0 SELL to **72 BUY / 28 SELL**, then a "▲ BUY" button.
**Page 4 (50.3–67.8s):** "BOT 2 · CONFIDENCE BOT": tree icons with a tally "31 BUY / 3", then "**90 BUY / 10**" with a tall "POSITION SIZE" bar labelled "LOAD UP". Next, "**55 BUY / 45** · CONFIDENCE · 55 / 100 TREES" with a small bar, "STAY SMALL / SIT OUT". Side-by-side panels: "90 / 10 BUY VOTES → LOAD UP" vs "55 / 45 BUY VOTES → SIT OUT", and the caption "VOTE MARGIN → POSITION SIZE".
**Page 5 (67.8–79.5s):** "THE FOREST VOTES": small trees voting +BUY / +SELL, "MAJORITY CALL BUY 4–1". "NOW — THROW OUT THE RULES". "FIND THE CLOSEST MATCH": a "NOW" candle pattern matched against history, "CLOSEST MATCH". Ends with "THAT'S K NEAREST [neighbors]".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Atomik Trading | product/brand | page 1 ("ATOMIK TRADING PRESENTS") | A futures trading-automation SaaS. It routes TradingView alerts and webhooks to Tradovate and Interactive Brokers (TopstepX in beta), with an AI strategy builder, backtesting, copy trading, a strategy marketplace and a $100k paper simulator. The AlternativeTo listing says plans start at **$89/month** with a 7-day money-back guarantee (unconfirmed on the official site). |
| "Math Behind the Markets" | series title | audio 0.0s, page 1 | The creator's episodic series (this is Ep. 4; KNN is teased next) |
| Random Forest | ML model | caption, audio, page 2 | Real ensemble method (Breiman, 2001): bagged decision trees with random feature subsets, combined by majority vote |
| Consensus bot / Confidence bot | concepts | pages 3–4 | Majority-vote classification vs using the vote fraction (`predict_proba`) for position sizing |
| 100 trees; 72/28; 90/10; 55/45; 31/3 | numbers | audio, pages 3–4 | Illustrative vote counts, not results |
| K-nearest neighbors | ML model | audio 77.7s, page 5 | Real method, teased for the next episode |

### What's being promoted / the funnel decoded
- There is no explicit call to action in the visible caption. The series is branded "ATOMIK TRADING PRESENTS", and the narration pitches "you can build them straight into your own trading bot". So the account is content marketing for Atomik Trading, a paid automation platform (about $89/month and up per the third-party listing) whose pitch is turning strategies into live futures bots.

### Verification & insights
- The technical content is accurate. Each tree trains on a bootstrap sample ("random slice of history") and a random subset of features ("different signals"). Errors decorrelate, and averaging the votes lowers variance.
- Caveats the video omits:
  - With financial time series, bootstrap sampling leaks information unless you use purged or embargoed walk-forward validation (López de Prado). That leakage is the usual source of fake backtest edges with random forests.
  - The vote fraction from a forest is often poorly calibrated. Mapping 90/10 to "size up" needs calibration on out-of-sample data.
  - A random forest cannot fix a lack of signal. If the features carry no edge, 100 trees vote noise.
- "Models quants use to make millions" is unsupported marketing language. Random forests are a common baseline, not a secret.
- Could not verify: the identity of @imelcapitanx and its exact relationship to Atomik (likely the creator or an affiliate), the official Atomik site, and current pricing.

---

<a id="e-dec0l3vte3f"></a>

## Dec0l3vtE3f | @josholdmixon | Founder demo of PentPort's "OpenWater" quick backtest and "DeepDive" validation engine (in-sample/out-of-sample, cost stress, walk-forward) feeding a strategy marketplace (beta)
- **Link:** https://www.instagram.com/p/Dec0l3vtE3f/
- **Account:** @josholdmixon (display name not in data) · **Posted:** 2026-10-13 (decoded from the post ID) · **Type:** reel (140.7s, 28 scene pages; talking head plus screen recording)
- **Caption source:** The mirror flagged it as possibly truncated, but the caption is short and complete-looking (93 characters, ends with a CTA). Instagram returned 429 on re-fetch.
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE. The validation ideas shown are sound practice: out-of-sample holdout, cost and latency stress, walk-forward windows, regime splits, a "many similar tests" flag. But this is the creator's own platform (PentPort), and the post is a product demo funnelling to a strategy marketplace that will sell algos. The "25,000 % in a year" hook is not what the on-screen chart shows. The AI "analysis" is generic boilerplate.

### Post description
> OpenWater and DeepDive strategy validation engines! #quant
>
> Comment "valid" and I'll send you the link!

### Audio
The creator speaks to camera (English). Condensed into timestamped notes; Whisper's "Quad" is most likely "Quant" (Lab).
- [0.0–13.1] Hook: "Did you know this strategy returned 25,000% in a year? Well, according to this back test, it did." He can keep changing a strategy until the backtest shows anything, so to tell whether it works "I built this free tool to validate any strategy."
- [13.1–17.7] The tool has two parts, OpenWater and DeepDive; DeepDive is much more thorough.
- [17.7–35.2] OpenWater walkthrough: in the Quant[?] Lab, create a new project and name it, select "strategy", pick the run frequency and define a universe (here NVIDIA and Apple). A fresh sandbox opens for any strategy; he uses a basic moving-average one for the demo.
- [35.2–53.4] "Run strategy" starts the OpenWater engine. Results show in-sample and out-of-sample performance, drawdowns, return distribution, trading costs, volume per symbol and every trade. You can ask Quant[?] to analyse the results and say what to change; here it flags trade timing and position sizing as the main issues.
- [53.4–66.9] OpenWater is built to be fast and give a decent overview; DeepDive takes longer. Clicking "validate" runs DeepDive; this strategy did well in the quick OpenWater test but failed DeepDive.
- [66.9–82.6] DeepDive first lists the main failure reasons (here: higher trading costs), then a more thorough in-sample vs out-of-sample view, per-asset performance and a return comparison: in-sample far better than out-of-sample, and severe stress made it much worse.
- [82.6–95.6] "The most interesting part": a validated strategy moves to your library, from which you can automate it with live trading or share and sell it on the marketplace.
- [95.6–105.7] Motivation: "I'm so tired of people selling algos and strategies that simply don't work"; sellers show an overfit backtest and fancy graphs "and then they steal your money." He sees this as a possible solution.
- [105.7–124.0] Any marketplace strategy must pass DeepDive; its results are public to all marketplace users, and every algo is forward-tested with paper trading for the first 30 days, so buyers can watch live performance before buying instead of trusting "scammers' overfit back tests".
- [124.0–141.2] Anything on the marketplace has passed the "strict validation engine". The marketplace is in beta to work out problems before selling starts, so "for now, everything in the marketplace is completely free." CTA: link in bio; he posts quant[?] trading videos daily, "so follow for more."

### On-screen content, page by page
A persistent top title reads **"Quant shows free tool for validating any strategy"** (pink, pages 1–9), with burned-in word-by-word subtitles throughout. "PentPort.com" branding is on the creator's hoodie and microphone.
**Pages 1–9 (0.0–13.1s):** The creator at a whiteboard with handwritten pairs-trading and Kalman formulas: K_t = P_t⁻ H_tᵀ(H_t P_t⁻ H_tᵀ + R)⁻¹; θ̂_t = θ̂_t⁻ + K_t(y_t − H_t θ̂_t⁻); S_t = log(P_A,t) − α_t − β_t log(P_B,t); z_t = (S_t − μ_t)/σ_t; q_t = −sgn(z_t)·1(|z_t| > …). Pages 5–6 inset a chart **"Performance of SPY"**: Balance from about 10,000 to about 50,000, Apr 2023 – Jan 2025, legend "Strat (SL=1.5, TP=3.5)".
**Page 10 (13.1–18.9s):** "There's OpenWater". A PentPort screen (nav: Markets · Compete · Learn · Community; search "people, politicians, markets, or pages") with project **"Demo algo v0.1.3"**, Python 3.10.12, Auto-save On, Run. The code: `from pentport import Strategy` / `class SandboxStrategy(Strategy):` / `on_start: self.status = 'closed'` / `on_data: symbol_1 = data.universe.stocks[0] # NVDA; symbol_2 = data.universe.stocks[1] # MSFT; last_price = data.price(symbol_1); moving_average = data.sma(symbol_1, period=20); # rsi = data.rsi(symbol_1, period=14); if last_price >= moving_average and status == 'closed': orders.buy(symbol_1, percent=10); orders.short(symbol_2, percent=5); status='open'; elif last_price < moving_average and status == 'open': close both positions`. In other words: long NVDA / short MSFT when NVDA is above its 20-bar SMA.
**Pages 11–14 (18.9–34.8s):** The project list (Build · Library · Live Algos · Marketplace BETA; projects "Demo algo", "nvdamsft", "NVDAtest2", each with Validate / Move to Library). The "Build Project" form: name "Test Demo", version 0.1.0, project type Research / **Strategy** / Indicator / Option model, file type Python file / Jupyter Notebook, strategy frequency "Every hour", coverage Stocks, "Specific symbol(s)". Then a fresh "Test Demo v0.1.0" sandbox (blank scaffold with commented API examples: data.current, data.history, data.price, data.sma, data.rsi, portfolio.has_position, portfolio.cash, portfolio.equity), universe NVDA, AAPL.
**Page 16 (37.4–50.7s), OpenWater "Strategy performance – NVDA, AAPL · 1h", Complete:**
- OOS return **1.02 %** (+$1,023.20)
- OOS final equity **$101,023.20** (complete period 1.54 %)
- OOS Sharpe **4.07** (Sortino 9.22)
- OOS max drawdown **−0.28 %** (68 bars underwater)
- OOS volatility 2.06 %
- OOS exposure 50.00 % (2 open positions)
- OOS trades 30 (2.27× capital turnover)
- OOS trading costs $75.35 (0.08 % of starting capital)
- Results summary: "No issues found in this run."

"Development versus evaluation (Chronological 60/40)":

| Sample | Return | Sharpe | Sortino | Max DD | Trades | Costs |
|---|---|---|---|---|---|---|
| In sample | 0.51 % | 0.94 | 1.64 | −1.20 % | 58 | $146 |
| Out-of-sample evaluation | 1.02 % | 4.07 | 9.22 | −0.28 % | 30 | $75 |
| Cost + latency stress | 0.97 % | 3.70 | 8.46 | −0.46 % | 28 | $162 |
| Complete period | 1.54 % | 1.88 | 3.45 | −1.20 % | 82(?) | $208(?) |

The header shows "Active portfolio: Trade War I".
**Page 17 (50.7–53.3s), AI chat:** The prompt "analyze these results, how can i make it better" produces a generic bullet list: trade timing and condition logic; enhance position sizing and partial fills; add exit logic triggers (stop-loss, take-profit); improve state tracking; include portfolio-wide analytics; add logging and debugging; consider multi-asset and cross-asset signals; use a state machine or rule engine.
**Pages 18–19 (53.3–65.7s):** Clicking Validate shows "validating…". A "Test Demo · DeepDive validation results" pop-up says "Validation failed".
**Pages 20–22 (65.7–82.5s), "sdfnwsejfoiwejf · DeepDive validation results"** (note: a different project from the Test Demo):
- "Validation failed – This exact project version did not pass validation for Library use, paper execution, or Marketplace publishing."
- Why it failed: "Fails With Higher Trading Costs".
- Automated flags: "Fails With Higher Trading Costs", "Strategy Settings Could Not Be Tested", "Many Similar Tests".
- Resolved strategy profile: Stocks · Symbol List · NVDA, MSFT · Return Seeking · Long Short · Regular session · Detected parameters: None · Benchmark beta 0.045 · Benchmark correlation 0.597 · (Excess return) −28.21 %.
- Evidence quality: Historical validation gate: Blocked · Statistical confidence: Low · Raw OOS Sharpe 0.18 · Selection-adjusted Sharpe −1.87 · Related project versions 13 · Related saved versions 1 · Economically similar prior results 0 · Future-leakage price test: Pass. Note: "Repeated visible evaluations reduce confidence; they do not automatically reject a strategy."
- Equity curves: in-sample (+5.0x % return, 158 trades) vs out-of-sample (−1.77 % return, 189 trades).
- Return comparison: In sample 6.27 % · Holdout 0.62 % · Cost stress −0.11 % · Severe stress −2.91 % · Walk 1 −0.01 % · Walk 2 −1.11 % · Walk 3 0.72 % · Walk 4 0.06 % · Bear −0.88 % · Bull 3.82 % · High volatility 0.33 %.
- Core validation (return / drawdown / Sharpe / trades / costs / exposure): In sample 6.27 % / 2.88 % / 1.19 / 386 / 1467.35 / 50.70 %; Chronological holdout 0.62 % / 2.66 % / 0.18 / 386 / 566.29 / 51.70 %; Cost and latency stress −0.11 % / 2.41 % / −0.02 / 384 / 2206.49 / 53.05 %; Severe cost and latency stress −2.91 % / 5.08 % / −0.96 / 352 / 4024.20 / 58.05 %.
- Walk-forward windows: Window 1 −0.01 % / −1.56 % / 0.01 / 110 / 273.00 / 51.00 %; Window 2 −1.11 % / −1.83 % / −1.67 / 128 / 518.08 / 51.60 %. (Some values were small and blurry; best reading.)
**Pages 23–25 (82.5–90s):** "DeepDive validation successful – This version passed the PentPort DeepDive Engine. Do you want to move it to your Library? [Not now] [Move to Library]". Then "Moved to Library."
**Pages 26–28 (90–140.7s):** The Library and Marketplace (BETA). Items: "dfgdfg" (Options volatility model, with Trade Live / Publish buttons), "Merton Jump-Diffusion" ("This extends Black-Scholes by allowing the stock to jump suddenly"), "Black-Scholes-Merton" ("Constant volatility and lognormal stock returns"), "Cox-Ross-Rubinstein Binomial Tree" (formula cards). These are options-pricing models, not validated trading strategies. The video ends on the talking head.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| PentPort / PentPort.com | site / platform | hoodie, mic, UI, code (`from pentport import Strategy`) | pentport.com describes itself as building a brokerage that "shares order flow revenue with traders". It has live paper-trading competitions and leagues, a brokerage cost calculator, an API / Python package and a mobile app, and claims 7,268 joined. The fetched homepage does not mention OpenWater, DeepDive or the marketplace. The creator appears to be the builder ("I built this free tool"). |
| OpenWater | feature | caption; audio 13s; page 10 | PentPort's quick backtest engine. Seen only in this demo. |
| DeepDive | feature | caption; audio 13s; pages 18–25 | PentPort's validation engine (holdout, cost stress, walk-forward, regime splits, multiple-testing flag). Seen only in this demo. |
| Quant Lab ("Quad Lab" in Whisper) | feature | audio 18.9s | The PentPort project workspace. |
| Marketplace (BETA) | feature | audio 95s, 105–135s; pages 26–28 | Strategy marketplace. Validated algos are listed with results and a 30-day paper forward test. "Completely free" during beta, with selling planned later. |
| "25,000 % in a year" | claim | audio 0s | Hook. The chart shown ("Performance of SPY", Strat SL=1.5 / TP=3.5) goes from about 10k to about 50k over about 21 months (≈400 %), not 25,000 %. It is presented as an example of an overfit backtest. |
| NVDA, AAPL, MSFT | tickers | audio 27s; pages 10–22 | Demo universe. |
| "Trade War I" | portfolio name | page 16 | Likely a PentPort paper-trading competition portfolio. |
| Merton Jump-Diffusion, Black-Scholes-Merton, Cox-Ross-Rubinstein | models | pages 26–28 | Standard option-pricing models listed in the library and marketplace. |

### What's being promoted / the funnel decoded
- "Comment 'valid' and I'll send you the link" plus "the link is in my bio". This leads to the creator's own platform, **PentPort (pentport.com)**: a free sign-up for paper trading, Quant Lab, validation and a marketplace beta. The business model, from the site, is a brokerage sharing order-flow revenue, plus a planned strategy marketplace where people will sell algos (any commission is not disclosed). There is no price now: "everything in the marketplace is completely free" during beta. The product is self-promoted, not an affiliate link.

### Verification & insights
- Web: pentport.com exists and matches the branding. Its public homepage confirms paper trading, an API / Python package and the order-flow-sharing brokerage pitch. The OpenWater, DeepDive and marketplace features could not be confirmed beyond this video. No independent coverage, and nothing on the founder, was found. No regulatory registration (broker-dealer status) was checked or found; a "brokerage" claim would require FINRA/SEC registration.
- The validation concepts are legitimate best practice: chronological holdout, cost and latency stress, walk-forward, bull/bear/high-volatility regime splits, a "selection-adjusted Sharpe" and "related versions" penalty (a multiple-testing correction similar to the deflated Sharpe ratio), and a look-ahead / future-leakage test.
- Weak points in the demo:
  - The OpenWater results (Sharpe 4.07 on a 1.02 % return over a short OOS window, 30 trades) are statistically meaningless. The engine said "No issues found", yet a very similar strategy then failed DeepDive.
  - The DeepDive failure shown is for a different project ("sdfnwsejfoiwejf", NVDA/MSFT) than the Test Demo being validated (NVDA/AAPL).
  - The "validation successful" screen is shown without saying which strategy passed.
  - The AI "analysis" is a generic checklist (it even garbles the condition as "ND ≥ SMA").
- Marketplace caution: passing a backtest-validation gate plus 30 days of paper trading does not make a strategy profitable going forward. 30 days is far too short to tell skill from luck. Paid algo marketplaces carry the same risks the creator criticises.
- Not verified: the full feature set, pricing after beta, marketplace commissions, PentPort's regulatory status, the creator's identity and credentials. Nothing was executed.

---

<a id="e-dbugavatqdu"></a>

## DbUGaVAtQDU | @imelcapitanx | "Math Behind the Markets" episode 1 of 9: an animated explainer of linear regression on price (slope = trend bot, distance from line = mean-reversion bot)
- **Link:** https://www.instagram.com/p/DbUGaVAtQDU/
- **Account:** @imelcapitanx (display name not retrieved) · **Posted:** unknown (Instagram refetch got HTTP 429) · **Type:** reel (69s; only 2 scene-detected pages because the animation changes gradually, so all 138 2-fps frames were reviewed)
- **Caption source:** full (Instagram). The later full-caption fetch confirmed the mirror text was already complete.
- **Category:** Quant & data
- **Verdict:** PARTLY TRUE – the regression mechanics are explained correctly and the tool is free. But "the models quants used to make millions" and "the actual math the funds use" oversell a textbook linear-regression channel; no evidence of edge, costs or a backtest is given.

### Post description
> Math concepts used by quants to make millions #tradingbot #algotrading #aitrading

### Audio
English voice-over (synthetic-sounding narrator), no music lyrics:
- [0.0–8.6] Hook: "Welcome to Math Behind the Markets. These are the machine learning models quants used to make millions" that you can build into your own trading bot.
- [8.6–27.6] Starts with the simplest, linear regression: it takes time and price and draws the single best-fitting line through recent candles. Like a flat average through the middle of price, except the line tilts to follow where price is going: "One line capturing the trend as a number."
- [27.6–50.1] From that line come two bots. Bot 1, a trend bot: the slope is basically momentum (direction and strength). Steep slope = strong trend, ride it; flat slope = no real trend, stay out. You can also extend the line forward to trade toward where price is headed.
- [50.1–58.4] Bot 2, a mean-reversion bot: reads the distance from the line; when price stretches too far it bets on the snapback as price returns to the average.
- [58.4–68.8] Closing claim: "people pay thousands for secret indicators that do less than this. This is the actual math the funds use and it costs you nothing." Next in the series: logistic regression.

### On-screen content, page by page
Dark animated chart (axes "PRICE" and "TIME →"), pill label "The Math Behind the Markets", and big word-by-word captions (e.g. "WELCOME TO MATH", "MAKE MILLIONS", "LINEAR REGRESSION").
**0–8.6s:** Title pill "The Math Behind the Markets"; green/red candlesticks build up in a rising trend.
**8.6–27.6s:** Candles turn into close-price dots; a flat average line appears ("AVERAGE", "OF PRICE"), then tilts into a cyan fitted line ("BUT THE LINE… GOING"). Label "line of best fit".
**27.6–50.1s:** Tag "BOT #1 — TREND". Slope-angle arc labelled "steep = strong momentum" and a flat reference line labelled "no trend" ("BASICALLY MOMENTUM", "WHICH WAY PRICE", "RIDE IT", "FLAT", "NO REAL TREND"). The line is extended dashed into the future with the label "where price is headed →" ("EXTEND THE LINE", "WHERE THE PRICE").
**50.1–58.4s:** Tag "BOT #2 — MEAN REVERSION". A point far above the line, bracketed "too far", with a curved arrow back to the line ("DISTANCE FROM THE", "WHEN PRICE STRETCHES", "THE SNAPBACK", "AS PRICE RETURNS").
**58.4–65.4s:** "ONE LINE." splitting into two cards "BOT #1 – TREND BOT" and "BOT #2 – MEAN-REVERSION BOT" ("FOR SECRET INDICATORS", "THAN THIS").
**65.4–69.0s:** "LINEAR REGRESSION ✓", progress bar "Model 1 of 9", and card "NEXT → Logistic Regression" ("NEXT UP IN").

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| "Math Behind the Markets" | series name | audio 0–2s, all frames | The account's own 9-part series ("Model 1 of 9"). |
| Linear regression (price on time) | model | audio 8.6–27.6s | Standard OLS fit over a rolling window. In trading platforms: TradingView "Linear Regression Channel", the LSMA/linreg indicator, and the "Linear Regression Slope" indicator (all free). |
| Trend bot: slope = momentum; trade the extended line | rule | audio 27.6–50.1s | The slope is a valid trend/momentum measure. "Extend the line forward to trade toward where the price is headed" is naive extrapolation; regression lines on prices are unstable and lag. |
| Mean-reversion bot: trade the distance from the line | rule | audio 50.1–58.4s | The standard regression-channel/z-score idea (residual ÷ std dev). It conflicts with the trend bot in strong trends, so a regime filter is needed. |
| Logistic regression | next model | final card | Announced as episode 2. |
| "Machine learning models quants used to make millions" | claim | audio 0–8.6s, caption | Hype. Regression is foundational in quant work (factor models, signal blending), but a single price-vs-time regression line is a retail chart indicator, not a fund strategy. |
| "People pay thousands for secret indicators that do less than this" | claim | audio 58–62s | A fair warning about paid "secret" indicators. |

### What's being promoted / the funnel decoded
No CTA, link or product in the video or caption; only the series hook ("Next up… logistic regression") and hashtags #tradingbot #algotrading #aitrading. No public info on @imelcapitanx was found. The trading-bot hashtags suggest the account may later sell a bot or course, but nothing in this post shows it.

### Verification & insights
- The method was checked against standard definitions; the visuals match the narration exactly.
- Missing for realism: lookback-window choice, parameter overfitting, transaction costs and slippage, and the fact that in-sample fitted lines look great in hindsight (the demo chart is a clean synthetic uptrend). Regressing price on time also violates OLS assumptions (trending, autocorrelated data), so "confidence" from the fit is misleading.
- Free equivalents: the linreg functions in TradingView Pine (`ta.linreg`), pandas/NumPy `polyfit`, statsmodels.
- Not verified: upload date, full caption (429), the account's identity and the other 8 episodes.

---

<a id="e-ddrl-yrr-1h"></a>

## DdRl-yRR_1h | @tradingstraty | Spanish talking-head: OpenAI's claimed Navier–Stokes proof framed as something that "could revolutionise trading", via econophysics and markets-as-fluids
- **Link:** https://www.instagram.com/p/DdRl-yRR_1h/
- **Account:** @tradingstraty (𝐓𝐫𝐚𝐝𝐢𝐧𝐠 𝐒𝐭𝐫𝐚𝐭𝐲) · **Posted:** 2026-09-14 · **Type:** reel (63.6s, 27 scene pages)
- **Caption source:** full (Instagram, via yt-dlp; it matches the mirror)
- **Category:** Quant & data
- **Verdict:** MISLEADING. The news is real: OpenAI announced on 2026-09-08 a claimed, Lean-checked finite-time blow-up proof for 3D Navier–Stokes. It is not peer-reviewed, not accepted by Clay, and contested. Calling it "ChatGPT" is wrong, and there is no link at all to trading beyond generic econophysics analogies.

### Post description
> ChatGPT resolvió un problema matemático que podría revolucionar el trading #fyp #trading #daytrading #daytrader #finance

(English: "ChatGPT solved a mathematical problem that could revolutionise trading.")

### Audio
The creator's own speech in Spanish, as timestamped English notes with short Spanish quotes:
- [0.0–6.4] Hook: what if an equation describing how a fluid moves could help us understand how chaotic financial markets are?
- [6.4–16.3] Claim: OpenAI "acaba de proponer una solución" (has just proposed a solution) to one of the Millennium mathematical problems, which could turn quantitative finance upside down: the Navier–Stokes equations.
- [16.3–26.7] Navier–Stokes describes how a fluid's behaviour emerges from millions of microscopic interactions (colliding particles, force, pressure, velocity). He asks how this relates to the financial market.
- [26.7–38.9] Every day traders, banks, market makers and institutions each make individual decisions at the same time; each is unpredictable, but millions together produce "algo fascinante" (something fascinating).
- [38.9–49.7] That collective behaviour is where econophysics comes in: in some ways the market behaves like a fluid, with flows, turbulence, shocks, pressure build-up and extreme events.
- [49.7–63.4] The key is not predicting the exact next price but which statistical patterns emerge when millions of agents interact; perhaps "the most interesting connection" between physics, AI and quantitative finance.

### On-screen content, page by page
Talking head at a trading desk throughout. Background monitors show a TradingView chart of a CME contract around 7,600–7,640 (likely ES/MES, the S&P 500 e-mini) and **gexbot.com/state** ("SPX – state – gamma"; tabs classic / state / orderflow / research). Two framed "CERTIFICATE" plaques on the wall, one reading "JUAN ALBERTO L" (apparently trading/prop-firm certificates).
**Pages 1–2 (0.0–2.9s):** Overlay of the vector Navier–Stokes momentum equation: ρ(∂u/∂t + u·∇u) = −∇p + μ∇²u + ρg.
**Pages 3–4 (2.9–7.4s):** Talking head.
**Page 5 (7.4–11.0s):** Screenshot of an X post by **@OpenAI** (verified): "We're sharing a solution to the Navier-Stokes Millennium Prize Problem, one of the deepest problems at the frontier of mathematics. / The proof was produced by a group of agents, using an OpenAI next-generation model significantly more capable than GPT-6 Astra. / The problem concerns whether the description of smooth three-dimensional fluid motion modeled by the Navier-Stokes equations can break down. It has remained unresolved for roughly 90 years." Image: a vortex-line visualisation labelled "inward spiral" and "axial stretching".
**Pages 6–7 (11.0–14.1s):** Talking head.
**Page 8 (14.1–16.3s):** NASA Glenn Research Center sheet "Navier-Stokes Equations, 3-dimensional – unsteady" (Coordinates (x,y,z), Time t, Pressure p, Heat Flux q, Velocity components (u,v,w), Density ρ, Stress τ, Reynolds Number Re, Total Energy Et, Prandtl Number Pr; Continuity, X/Y/Z-Momentum and Energy equations).
**Pages 9–12 (16.3–22.8s):** Talking head.
**Pages 13–16 (22.8–26.8s):** GIF of colliding particles (watermark "BBANGIF.com") and a two-body force diagram (m₁, m₂, F₁₂, F₂₁, v₁, v₂).
**Pages 17–18 (26.8–32.0s):** Archival footage of a crowded trading floor.
**Pages 19–27 (32–63.6s):** Talking head to the end. No text overlays and no call to action.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| OpenAI Navier–Stokes announcement | news | audio 6–14s, page 5 | Real. OpenAI announced on **2026-09-08** (openai.com/index/navier-stokes-solution/) a claimed proof of **finite-time blow-up** for 3D Navier–Stokes, with a Lean formalisation and about a 166-page paper. Coverage cites about 10,000 coordinating agents on an unreleased internal model over about 88 hours. |
| "ChatGPT resolvió…" | claim | caption | Inaccurate. It was an internal multi-agent system on an unreleased model, not ChatGPT. |
| "GPT-6 Astra" | product | page 5 (tweet) | Named in the tweet as the comparison model. News search did not independently confirm which model produced the proof. |
| Navier–Stokes Millennium Prize | math problem | audio, page 5 | One of the Clay Institute's seven $1M problems. Clay still lists it as **unsolved**. Payment needs publication, peer review and 2 years of acceptance. Reports say the proof covers the **forced** case. There is a public priority dispute with NYU's Tristan Buckmaster (whose related work with Levent Alpöge was announced the day before). |
| Econophysics | field | audio 38.9s | A real research field (Mantegna & Stanley; Bouchaud). Fluid and turbulence analogies for markets date back to the 1990s (e.g. Ghashghaie et al., *Nature* 1996, "Turbulent cascades in foreign exchange markets"). |
| gexbot.com | site | background monitor | GEXbot, a paid gamma-exposure data service. Shown only in the background and not mentioned. |

### What's being promoted / the funnel decoded
No call to action in the reel or caption. It is a news-hook engagement post on a Spanish-language trading account. The background (GEXbot, prop-style certificates) suggests the account's broader trading-education brand, but nothing is sold here.

### Verification & insights
- The news hook is real and current, but the framing overstates it. The result is a claimed proof, not peer-reviewed, not accepted by Clay, covering the forced equations, and disputed over credit (sources: Smithsonian, NYU Shanghai RITS, implicator.ai and aiweekly coverage, 9–10 September 2026).
- A blow-up (singularity) result for 3D fluid equations has **no direct application to trading**. The creator himself switches to the general econophysics idea, which predates this news by decades and does not depend on it.
- "Could revolutionise quantitative finance" has no support. No model, strategy or data is presented.
- Not verified: the identity behind @tradingstraty (the certificate reads "Juan Alberto L"), and what the certificates are.

---

<a id="e-decxbp-typg"></a>

## DeCXBP_tyPg | @quantchics | "5 quant projects to do this weekend" reel that names only 4 project titles over academic-paper backgrounds, then gates "6 more + the papers" behind comment "QUANT"
- **Link:** https://www.instagram.com/p/DeCXBP_tyPg/
- **Account:** @quantchics (Quantgirl) · **Posted:** 2026-10-03 · **Type:** reel (9.3s, 12 scene frames; 4 project cards)
- **Caption source:** full (Instagram, via yt-dlp)
- **Category:** Quant & data
- **Verdict:** NO SUBSTANCE – the project ideas are sound standard quant topics, but the reel shows titles only (four, despite "5"), with no data, methods or links. The real content is gated behind a comment funnel.

### Post description
> 5 quant projects you can actually build and put on GitHub.
>
> I picked these because they're small enough to finish, but each gives you a real research question to investigate.
>
> Think less "build another trading bot" and more:
>
> → form a hypothesis
> → find the data
> → test it
> → analyse what happened
> → document your findings
>
> If you're building a quant portfolio, start with one and go deep.
>
> Save this for your next project.

### Audio
Music only (no speech detected by Whisper; the song is not identified on screen or in the caption).

### On-screen content, page by page
Material note: the mirror had only a cover still. The video was downloaded with yt-dlp, and pages and 2/5/10-fps frames were extracted into scratchpad/work3/DeCXBP_tyPg/.
**Page 1 (0–1.6s):** "5 QUANT projects to do this weekend" over a blurred Bloomberg-terminal-style market monitor (world indices, a pie chart "Global Market Intraday Return by region").
**Page 2 (1.6–2.9s):** "Volatility Clustering Detector" over a paper page whose visible text is the "Volatility clustering: as noted by Mandelbrot… 'large changes tend to be followed by large changes…'" stylized-facts passage (R. Cont, "Empirical properties of asset returns: stylized facts and statistical issues", *Quantitative Finance* 2001).
**Page 3 (2.9–4.2s):** "Intraday Seasonality Map" over the abstract/introduction of a 1997 Elsevier paper. The visible keywords "Volatility; Intraday periodicity; Temporal aggregation; ARCH", JEL C14 C22 G14 G15, and a University of Virginia / NBER address match Andersen & Bollerslev (1997), "Intraday periodicity and volatility persistence in financial markets", *Journal of Empirical Finance*.
**Page 4 (4.2–5.6s):** "Factor Neutrality Check" over the first page of Fama & French (1993), "Common risk factors in the returns on stocks and bonds", *Journal of Financial Economics* ("Correspondence to: Eugene F. Fama, Graduate School of Business, University of Chicago…"; size, E/P, leverage, book-to-market).
**Page 5 (5.6–7.0s):** "Regime-Dependent Momentum" over a recent Elsevier article page (Article info/Abstract layout, received about 2021). Title not legible, not identified.
**Pages 6–12 (7.0–9.3s):** "I've got 6 more + the papers I'd start with." / "Comment “QUANT” and I'll send them." over a mirror selfie of a woman in a black suit (face covered by phone).

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| Volatility Clustering Detector | project idea | page 2 | Standard exercise: test autocorrelation of absolute/squared returns, fit GARCH(1,1). Backed by Cont (2001) and Mandelbrot (1963). |
| Intraday Seasonality Map | project idea | page 3 | Map the U-shaped intraday volatility/volume pattern. Backed by Andersen & Bollerslev (1997). |
| Factor Neutrality Check | project idea | page 4 | Regress a strategy's returns on Fama-French factors to see whether "alpha" is just factor exposure. Backed by Fama & French (1993). |
| Regime-Dependent Momentum | project idea | page 5 | Momentum performance conditional on market state/volatility (literature e.g. Cooper-Gutierrez-Hameed 2004 "Market States and Momentum", Daniel & Moskowitz 2016 "Momentum crashes"). The paper shown is not identified. |
| 5th project | missing | title card says "5" | Only 4 titles appear in the video; no 5th was found in the 10-fps frames. |
| "QUANT" | comment keyword | page 6+ | DM trigger for "6 more + the papers". |

### What's being promoted / the funnel decoded
Comment "QUANT" → DM with 6 more project ideas and paper references. No price or product is visible in the post. The account looks like a faceless/aesthetic "quant girl" lifestyle-education page, and a web search found no public info on @quantchics, so whether the DM leads to a paid product, newsletter or link-in-bio offer is unknown. The papers it hints at are freely findable: Cont 2001, Andersen & Bollerslev 1997, Fama & French 1993.

### Verification & insights
- The paper identifications above come from the visible text in the frames (keywords, addresses, quoted passages). All three identified papers are real, canonical references.
- The caption's workflow (hypothesis → data → test → analyse → document) is good practice, but the reel itself contains no instructions.
- Free data for these projects: daily/intraday prices (yfinance, Alpaca free IEX feed) and Fama-French factor files (Kenneth French Data Library, free).
- Not verified: the 5th project, the "6 more", the music track and the account owner.

---

<a id="e-deg0msre2oc"></a>

## DeG0mSRE2oc | @quant_grad | 6-slide "Self-Study Roadmap for a Non-Finance Undergrad Wanting to Go Quant" (Math → Python → Finance → Projects → Internships) with illustrative charts; "comment Quant" funnel
- **Link:** https://www.instagram.com/p/DeG0mSRE2oc/
- **Account:** @quant_grad (Quant Grad) · **Posted:** 2026-10-05 · **Type:** carousel (6 slides)
- **Caption source:** full (Instagram, re-fetched with yt-dlp; identical to the mirror text)
- **Category:** Quant & data
- **Verdict:** NO SUBSTANCE – generic but reasonable career advice; the chart numbers are decorative or illustrative (several look AI-generated); the actual "full roadmap" is gated behind a comment

### Post description
> Comment "Quant" for full roadmap..

### Audio
Not applicable (image carousel).

### On-screen content, page by page
Every slide carries the header "QUANT GRAD", a slide number at bottom left, and a "→" arrow.
**Slide 1:** Title "Self-Study Roadmap for a Non-Finance Undergrad Wanting to Go Quant". Six dark chart panels:
- "Skill Progression (Illustrative)": proficiency 0–1 over 0–24 months for Math (highest, about 0.9), Programming (about 0.7), Finance (about 0.47), Projects (about 0.33).
- "Impact of Key Skills on Quant Roles" (relative importance): Math & Statistics 0.85; Programming 0.80; Finance Knowledge 0.60; Projects / Research 0.65; Domain Knowledge 0.50; Communication 0.30.
- "Compounding Effect of Skills": Structured Learning (reaching about 1.8 at 24 months) vs Unstructured Learning (about 0.7).
- "Correlation Between Core Skills": a heat map of Math / Programming / Finance / Projects.
- "Distribution of Quant Job Requirements": histograms of requirement level for Math, Programming, Finance, Statistics.
- "Path to a Quant Career (Illustrative)": Learn Fundamentals → Build Projects → Gain Experience → Quant Role over 0–24 months.

Footer text: "You don't need a finance degree. You need the right technical foundation."
**Slide 2, "01 — BUILD YOUR MATH FOUNDATION" / "Build Your Math Foundation":** Panels "Normal Distribution (Probability)" (68% / 95% / 99.7% bands), "Matrix Operations (Linear Algebra)" (5×5 matrix A heat map), "Function Optimization" (Gradient Descent path to Optimum on contours of θ₁, θ₂), "Calculus: Function and Derivative" (f(x) = sin(x), f′(x) = cos(x)), "Statistics: Sampling Distribution" (Sample Mean histogram with Normal Approx.), "Multivariate Distribution" (3D bell surface f(x,y)). Text: "Start with Calculus, Linear Algebra and Probability. / Then move into Statistics and Optimization. / Focus on understanding concepts—not just memorizing formulas."
**Slide 3, "02 — GET COMFORTABLE WITH PYTHON" / "Get Comfortable With Python":** The panel "Python: Data Analysis Workflow" shows a 16-line pandas script. Excerpt:
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
# Load and inspect data
df = pd.read_csv('market_data.csv')
df.head()
# Calculate daily returns
df['return'] = df['Close'].pct_change()
# Rolling statistics
df['volatility'] = df['return'].rolling(30).std()
```
The rest ("# Visualize") makes a `plt.figure(figsize=(10,4))`, plots `df['Close']` labelled 'Price' and `df['volatility']*50` labelled 'Volatility (30D)', then calls `plt.legend()` and `plt.show()`. No printed output is shown.
Other panels: "Stock Price and Rolling Volatility (Using pandas & matplotlib)" (2018–2024, price 50–250, volatility spike in 2020); "Correlation Matrix (Using pandas)" (AAPL, MSFT, GOOG, AMZN, META); "Distribution of Daily Returns" (Empirical vs Normal Fit, −0.10 to 0.10); "Strategy Backtest (Example)" (Strategy vs Buy & Hold, 2018–2024). Text: "Learn NumPy, pandas, matplotlib and basic SQL. / Then build projects using real market or financial datasets. / Your goal: turn data into insights."
**Slide 4, "03 — LEARN THE FINANCE BASICS" / "Learn The Finance Basics":** Panels:
- "Asset Class Total Returns (2010–2024)": U.S. Stocks (SPY), Global Stocks (ACWI), U.S. Bonds (AGG), Commodities (DJP), normalised to 0–500.
- "Volatility Smile (Options)": strike 70%–130%, IV about 0.08–0.41.
- "Bond Yield Curve (U.S. Treasuries)": Current / 1Y Ago / 3Y Ago, maturities 0.25–30 years.
- "Black-Scholes Option Prices": 3D surface of stock price S against time to maturity T.
- "Efficient Frontier (Portfolio Theory)": Portfolios, Efficient Frontier, Max Sharpe Portfolio.
- "Factor Model Exposures (Example)": AAPL, MSFT, GOOG, AMZN, META against MKT, SMB, HML, MOM, QLT.

Text: "Understand markets, stocks, bonds, derivatives and portfolio theory. / Then learn concepts like volatility, risk, pricing and factor models. / You don't need an MBA-level finance curriculum."
**Slide 5, "04 — TURN KNOWLEDGE INTO PROJECTS" / "Turn Knowledge Into Projects":** Panels "Strategy Backtest (Example)" (2018–2024), "Forecast vs Actual (Example)" (2023-01 to 2024-07), "Risk Analysis (Value at Risk)" (daily P&L histogram with VaR (95%) at about −2%), "Factor Model Exposures (Example)", "Portfolio Optimization (Example)" (frontier coloured by Sharpe Ratio 0–1.5), and the table "Performance Metrics (Example)":

| Metric | Strategy | Buy & Hold |
|---|---|---|
| Annual Return | 18.4% | 9.7% |
| Volatility | 12.1% | 15.3% |
| Sharpe Ratio | 1.52 | 0.63 |
| Max Drawdown | -8.6% | -22.4% |
| Sortino Ratio | 2.14 | 0.87 |
| Win Rate | 58% | 51% |

Text: "Build 2–4 serious projects around backtesting, forecasting or risk. / Document your assumptions, methodology, results and limitations. / A strong project can prove what your degree doesn't."
**Slide 6, "05 — CREATE A QUANT-READY PROFILE" / "Create a Quant-Ready Profile":** Panels:
- "Competitions (Example Performance)": My Strategy vs Benchmark vs Competition Median, Jan–Jun 2024.
- "GitHub Contributions (Example)": "Contributions in the last 6 months: 312".
- "Quant Problem Solving Progress": problems solved rising to about 165 by Month 5, accuracy to about 90%.
- "Sample Quant Project Structure": `mean_reversion_project/` containing data/ (prices.csv, features.csv), src/ (backtest.py, strategy.py), notebooks/ (analysis.ipynb), results/ (equity_curve.png, metrics.csv).
- "Backtest Results (Example)": Annual Return 18.7%, Max Drawdown -12.3%, Sharpe Ratio 1.42, Win Rate 56%; 2020–2024.
- "From Learning to Landing (Illustrative)": Math → Python → Finance → Projects → Internships.

Text: "Join competitions, contribute to GitHub and solve quantitative problems. / Target internships and roles where math + coding matter. / Math → Python → Finance → Projects → Internships / That's your roadmap."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| NumPy, pandas, matplotlib, SQL | tools | slide 3 | Standard free Python data stack. |
| SPY, ACWI, AGG, DJP | tickers | slide 4 | Real ETF/ETN tickers (S&P 500, MSCI ACWI, US Aggregate Bond, Bloomberg Commodity). The curves are illustrative and not verified against real data. |
| AAPL, MSFT, GOOG, AMZN, META | tickers | slides 3–5 | Example stocks in heat maps with made-up values. |
| MKT, SMB, HML, MOM, QLT | factors | slides 4–5 | Market, size, value, momentum and quality factors (Fama-French / Carhart style). |
| Black-Scholes, efficient frontier, volatility smile, VaR | concepts | slides 4–5 | Standard quant-finance topics. |
| "Performance Metrics (Example)" 18.4% / Sharpe 1.52 etc.; "Backtest Results" 18.7% / 1.42 | numbers | slides 5–6 | Labelled "Example" and fictional. Not a real strategy. |
| "Impact of Key Skills" 0.85 / 0.80 / 0.60 / 0.65 / 0.50 / 0.30 | numbers | slide 1 | No source. Illustrative opinion presented as data. |
| "Comment 'Quant'" | funnel | caption | See below. |
| @quant_grad / "QUANT GRAD" | brand | all slides | Possibly linked to QuantGrad (quantgrad.com), an admissions consultancy for Master's in Quantitative Finance / Financial Engineering. Not confirmed. |

### What's being promoted / the funnel decoded
Commenting "Quant" triggers an auto-DM with the "full roadmap", most likely a link to a PDF or lead-magnet page that collects your email. If the account belongs to the QuantGrad MFE/MQF admissions consultancy (unconfirmed), the lead would feed paid admissions consulting. No price is shown.

### Verification & insights
- The advice is mainstream and sound but generic: math (calculus, linear algebra, probability, statistics, optimisation), then Python, then finance basics, then 2–4 documented projects, then GitHub, competitions and puzzle practice, then internships. Free, better-known versions of the same roadmap exist: QuantNet's guides, the "Heard on the Street" and "Green Book" interview-prep books, and QuantStart articles.
- All the charts are decorative. Several are explicitly "(Illustrative)" or "(Example)". The others ("Impact of Key Skills", "Distribution of Quant Job Requirements", "Correlation Between Core Skills") have no data source and appear AI-generated. Do not treat them as data.
- The example backtest metrics (Sharpe 1.52, max drawdown −8.6%) would be exceptional for a student project, so don't use them as a benchmark.
- Not verified: who runs @quant_grad and what the "full roadmap" DM contains (it was not engaged with, per instructions).

---

<a id="e-deo8xihndig"></a>

## Deo8xIhNdIg | @quantfinance.ai | Infographic: "20 Quant Skills That Set You Apart", a list of 20 skills each with a two-line slogan
- **Link:** https://www.instagram.com/p/Deo8xIhNdIg/
- **Account:** @quantfinance.ai · **Posted:** unknown (the mirror gave no date) · **Type:** image (1 slide)
- **Caption source:** possibly truncated (mirror). I made one yt-dlp attempt and it failed ("There is no video in this post"; yt-dlp cannot read image-only posts), so I did not retry.
- **Category:** Quant & data
- **Verdict:** NO SUBSTANCE – a generic motivational skills checklist with no resources, methods or data. Harmless, and nothing is sold in the post.

### Post description
> 🧠 20 Quant Skills That Set You Apart
>
> Anyone can learn Python. Anyone can build a backtest.
>
> But becoming a strong quant requires much more than writing code.
>
> 📊 Statistical thinking
> 📉 Risk management
> 🔬 Research & validation
> ⚙️ System design
> 🎯 Discip...

(Cut off by the mirror. The rest, including any hashtags or CTA, is not retrievable.)

### Audio
None. This is an image post.

### On-screen content, page by page
**Slide 1:** The header reads "20 QUANT SKILLS THAT SET YOU APART", with the logo "quantfinance.ai · Quant Research" and the script slogan "Learn · Build · Compound". The subtitle reads "Technical skills get you in. Quant skills keep you ahead." Below is a 5×4 grid of blue icons with the following text:
1. Statistical Thinking – "See patterns, not noise."
2. Probability & Distributions – "Model uncertainty, not just outcomes."
3. Programming (Python/R) – "Automate, backtest, scale."
4. Data Wrangling & Analysis – "Clean data. Better insights."
5. Machine Learning – "Find patterns beyond the obvious."
6. Domain Knowledge – "Markets, economics, sectors, instruments."
7. Risk Management – "Protect capital. Stay in the game."
8. Backtesting & Validation – "Test, verify, repeat."
9. System Design & Automation – "Build once. Scale forever."
10. Cloud & Infrastructure – "Compute, store, execute."
11. Time Series Analysis – "Understand trends, cycles, regimes."
12. Trading & Execution – "Minimise costs. Maximise edge."
13. Research & Critical Thinking – "Question, analyse, connect dots."
14. Communication – "Turn complex ideas into clear decisions."
15. Teamwork & Collaboration – "Better minds. Bigger ideas."
16. Discipline & Emotional Control – "Follow the plan. Ignore the noise."
17. Creativity & Problem Solving – "New ideas. Better solutions."
18. Continuous Learning – "The market evolves. So should you."
19. Global Perspective – "Markets are connected. Think wider."
20. Adaptability – "New tools. New markets. Same mindset."

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| quantfinance.ai | site / brand | Logo on the image, handle | The domain exists (it responded through the proxy), but the site returned HTTP 503 when fetched, so I could not see what it offers. A web search found no listing for this specific brand. |
| Python / R | languages | Item 3 | Standard quant languages. |
| 20 skills | list | Image | Generic. No courses, books or tools are named. |

### What's being promoted / the funnel decoded
There is no visible CTA in the image, and the caption is cut off before any CTA it may have. The brand domain quantfinance.ai suggests a product or newsletter site, but its contents could not be checked (HTTP 503). Nothing is being collected in the post as seen.

### Verification & insights
- Nothing to fact-check: it is a list of broad skill headings with slogans, and the skills listed are reasonable.
- Better-known, more concrete sources on the same topic: the CQF Institute's quant skills research (which reports that 88% of quant professionals see a skills gap and 76% say it is widening), QuantNet reading lists, and the "Quant Finance From Scratch" series from @quantfinancetogo in this same batch (DemrBpwCemC, Deo-i-zCdMb), which actually teaches methods.
- Not verified: the full caption, the posting date, and what quantfinance.ai sells.

---

# Category: Crypto (2 posts)

<a id="e-der78ymm0he"></a>

## Der78ymM0he | @tradingwithkayyy | "3 websites": Poe (AI chatbots), Dulo (pirate streaming) and the Fomo memecoin app's leaderboard, pitched as copy-trading, with a "comment Trade" CTA
- **Link:** https://www.instagram.com/p/Der78ymM0he/
- **Account:** @tradingwithkayyy (Kayla Nguyen) · **Posted:** 2026-10-19 · **Type:** reel (51s, 32 pages)
- **Caption source:** full (Instagram)
- **Category:** Crypto
- **Verdict:** MISLEADING – Poe isn't "free premium AI", Dulo is a piracy site, and "copy the top crypto millionaires" is manual memecoin trading shown with one cherry-picked, unresolved trade. The CTA is an engagement and referral funnel.

### Post description
> HUHHHH??
> #crypto #trading #memecoin #sidehustle #daytrading

### Audio
Creator's own voice-over (English). Burned-in captions repeat it word by word.
- [0.0–4.4] Hook: "three websites even Spider-Man doesn't want you knowing about".
- [4.4–8.6] On the first site "you have access to premium versions of AI for free like Claude and ChatGPT 5."
- [8.6–12.0] She calls the next one "the first website": **Dulo**, where "you can access all the streaming platforms for free", including movies like Spider-Man and Odyssey.
- [12.0–15.5] On the third you can "find the top crypto millionaires and follow them so you can copy their trades exactly."
- [15.5–28.1] Testing "the last one": on the top-trader leaderboard she picks someone "up eight hundred thousand dollars in the last 24 hours" and follows him.
- [28.1–37.9] A notification says he put 30,000 into one coin; she copies the same move at the same time.
- [37.9–45.8] She put in only "a couple hundred dollars" and will wait for him to sell, checking back in a few hours. "Not gonna lie, I think it actually works."
- [45.8–55.8] CTA: for "access to the software and a list of traders to copy, comment 'trade'", or use the link in her bio.

Note: the voice-over announces three websites but only shows two (Poe, then Dulo) before switching to the trading app, which she calls "the last one".

### On-screen content, page by page
The first ~12s are a reused clip of another creator (a young man in glasses holding a red jelly object, in a purple-lit room) with her face cut out and overlaid in a corner. A title banner sits over the clip.
**Page 1 (0.0s):** Banner "3 websites SPIDERMAN GATEKEPT from u 😭". Man holding a red jelly heart, her face overlaid.
**Page 2 (1.0s):** Same banner; caption "Watch this".
**Page 3 (3.5s):** Laptop screen of a streaming site: a "1 / 2" top list with "Avatar Aang: The Last Airb…" and "Accidental Pa…". "Popular Movies": "Spider-Man: Brand New … 2026" and "The Odyssey 2026". "Popular Shows", plus a "HEADS UP" pop-up warning about ads. Caption "if you go".
**Page 3a (2-fps frames, 3.5–4.0s):** Browser tab "Poe", address bar **poe.com**. Bookmarks bar: "ChatGPT", "LLC SDR SCRI…", "NEW LLC SCRIPT…", "Brez Report". Poe left-hand sidebar visible. Captions "if you go" / "to this website".
**Page 4 (4.5s):** Poe bot grid, first row: Claude-Opus-5, Claude-Fable-5, Grok-4.6, Kimi-K3. Second row: GPT-4o-mini, GPT-5.4-Nano, Gemini-3-Fl(ash). Third row: Gemini-2.5-Pro, Perplexity-Adv-Deep-Research, Perplexity-Pro-Search, GPT-4o-Search. Caption "to this website".
**Page 5 (6.6s):** More Poe bots: "…Assistant", GPT-5.6-Sol, Claude-Opus-5, Claude-Fable-5. Section "…et-friendly bots": GPT-5-mini, Grok-4.1-Fast-Non-Reasoning, GPT-4o-mini. Section "…ch bots". Tabs at the top: "…Untitled – Miro", "Closing Script – Mi…". Caption "free".
**Page 6 (8.0s):** Back to the jelly clip with the banner; caption "about".
**Page 7 (8.1s):** Browser tab "dulo.gd — Stream Movies & T…", address bar **dulo.cx**. "Top 10 TV Shows" #1 "Teach You a Lesson". Caption "the first website".
**Page 8 (9.5s):** Dulo "Toy Story 5" and "Spider-Man: Brand New Day" banners. "Channels & Apps" tiles: Netflix, prime video, Disney+. "Top 10 TV Shows". Caption "where you can".
**Page 9 (11.3s):** Dulo "Popular Movies" again (Spider-Man: Brand New Day 2026, The Odyssey 2026); caption "free".
**Pages 10–11 (13.4s):** Desktop crypto leaderboard on a laptop. Top cards: "+$3.6M", "chubbic… +$3.2M", "Reach +$2.4M", "Collect…", "Top…", "#1 Trade". Time tabs "…H / 7D / 30D / ALL"; "Your rank", "PnL". Rows: 5. The… +$5,396,942.71; 6. Vee @thevee… +$4,718,381.36; 7. Nate @Natan… +$4,177,298.02; 8. frank @frankd… +$3,998,110.07; 9. AJC @AvgJo… +$3,973,944.16; 10. Burgz @burgz… +$3,919,279.29. Right panel "$1,58…" / "-$83,867.11", "Total ca(sh) $50,6…", "Positions 39". Footer tickers: $82,862.86 +2.15%, $2,647.92 +2.52%, $118.33 +4.72% (probably BTC, ETH, SOL). "Split bottom / Split right" layout buttons. Caption "You can find".
**Page 12 (15.1s):** A trader profile page: banner image of pagodas, name "Ethermon…" @ether_monk, 4 Mutuals, 79 Following, 329.5K Followers, Share and Follow buttons. Chart; "…5,015.01". Positions list (FONE, STONKEX, ETH, CPU, UBIK, ETH, CATALYST, SPIKE). Caption "and follow them."
**Pages 13–15 (16.3–16.8s):** Close-ups of a positions list, "Total cash $934.78". Approximate readings (blurry): 牛事 8.2M $945,675.20 +7.41%; UBIK 10.1M $424,718.60 +58.78%; STANDARD 1.4M $356,742.45 +1.09%; UMIA 500K $335,076.68 +8.77%; fone 22.6M $176,057.58 +33.30%; Max 21.5M $118,257.27 60.40%; JUGGERNAUT 14.5M $110,279.37 3.09%; STONKEX 12.5M $103,410.09 +80.47%; microduck 25.6M $96,571.63 +78.73%; MINI 21.6M $92,203.73 +306.18%; CPU 8.3M $26,079.17 +86.42%; SPIKE 20.7M $13,356.88; PCC 2.8M $8,2xx; 招财 3.4M $6,784.65 +74.83%; SIRIUS $5,764.11. Side token list: ETH, CATALYST, SPIKE, WTCOIN, BOT, SHIT, PENGU, GOONER, SPYB, SPCXB, NVDA, ZEC, MAX. Caption "trades. Exactly."
**Pages 16–17 (17.2s):** The creator speaking to camera with a pen; caption "Okay, let's see".
**Page 18 (19.3s):** Phone app "Leaderboard" (behind her): 1 whatever @whatever_fomo +$1,509,662.58; 2 HUMANbeingET @humanbeingET +$386,244.51; 3 dalegend(?) +$293,899.82; 4 +$222,925.22; then +$198,896.96, …185,601.82. Caption "I found the".
**Page 19 (19.3s):** Tabs "Friends (149) | Leaderboard". 1 ExactTallTakin @ExactTallTakin +$785,800.05; 2 pricedin @pricedin +$511,296.23; 3 big babba johnson +$448,298.58; 4 +$447,914.42; 5 +$444,013.88; 6 +$438,388.41; 9 @000000 +$382,699.33; 10 Hifive @Hifive_07 +$375,928.79. Caption "WE'RE GONNA HEAD".
**Pages 20–21 (22.2–26.2s):** Profile "rasmr @rasmr", bio "5k to 500k challenge ✅", 175 Following, 52.6K Followers, "38 mutuals following", "4d 18h avg. hold", "657…". Value **$1,689,655**, **+$830,364.24 24h**; Total cash $105,64…; Positions (34) [Open/Closed; All/Tokens/Perps]: MarsCoin 3.5M MarsCoin $702,376.83 +845.64%; A Meme Coin 9.5M MEME $528,823.08 +989.62%. "Follow" button. Captions "TO COPY." / "SO I'M ACTUALLY".
**Pages 22–23 (29.4s):** The creator by a window; caption "A TRADE."
**Page 24 (31.7s):** Phone notifications from the app: "BORDR at $4.06m MC — @rasmr bought $15,000.00 (now)"; "BORDR at $3.71m MC — @rasmr bought $15,000.00 (now)"; "S…MER thesis by @kikaka10000 (1m ago)"; partly hidden "…ht $1,251.87" (1m ago), "…1,257.37" (2m ago), "…1,309.36" (3m ago). Caption "HE MADE A TRADE."
**Pages 25–26 (39.9s):** Creator; captions "HUNDRED DOLLARS," / "SO NOW I'M".
**Page 27 (43.9s):** Her own app profile: "Kay Invests @Kayinvestss", bio "I need to pay my loans", 27 Following, 1 Followers, "1 day 6 hrs avg. hold", "7 tr(ades)", value **$3,933.22**, **+$3,823.97**, Total cash $3,933.22, "Rewards" button; header photo of a Porsche 911 GT3.
**Pages 28–31 (45.8–48.6s):** Creator to camera; captions "actually works." / "to the software" / "traders to copy". Banner "Comment "Trade" 📲".
**Page 32 (51.3s):** Black end card: "Comment "Trade" 📲".

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| poe.com (Poe) | site | p.3a–5; audio 4.4s | Quora's multi-model chatbot hub. Free tier has limited daily compute points; top models need a paid subscription. Not "premium AI for free". |
| Claude-Opus-5, Claude-Fable-5, GPT-5.6-Sol, GPT-5.4-Nano, GPT-5-mini, GPT-4o-mini, GPT-4o-Search, Grok-4.6, Grok-4.1-Fast-Non-Reasoning, Kimi-K3, Gemini-3-Flash, Gemini-2.5-Pro, Perplexity-Adv-Deep-Research, Perplexity-Pro-Search | bots on Poe | p.4–5 | Third-party models served through Poe and metered by points. |
| dulo.cx → dulo.gd ("Dulo") | site | p.7–9; audio 8.6s | An unlicensed piracy streaming site that rotates domains (dulo.sx/.site/.mov/.tv…). Scanners flag it for ads and pop-ups and rate it risky. |
| Spider-Man: Brand New Day, The Odyssey, Toy Story 5, Avatar Aang, Teach You a Lesson | titles | p.3, 8, 9 | Copyrighted titles shown streaming on the piracy site. |
| Fomo app (fomo.family) | app | p.18–24, 27 ("@whatever_fomo", Friends/Leaderboard, Rewards, buy notifications) | A Solana memecoin social-trading app with leaderboards (24h/7d/30d/all) and notifications when people you follow buy or sell. By its own help page, copying is manual, not automatic. Self-custodial, with fees per trade and a referral program. |
| Desktop leaderboard/terminal ("Reach", "Collect", "#1 Trade", "Split bottom/right") | web app | p.10–15 | A desktop crypto PnL leaderboard and positions screen. Most likely Fomo's web view; not confirmed. |
| @rasmr ("5k to 500k challenge") | trader handle | p.20–24 | The trader she "copies": $1,689,655 portfolio, +$830,364.24 in 24h, bought BORDR twice at $15,000 each (= the "$30,000" in the audio). |
| BORDR, MarsCoin, A Meme Coin (MEME) | memecoin tickers | p.20–24 | Micro-cap memecoins ($3.7–4.1M market cap). |
| @Kayinvestss ("Kay Invests") | her app profile | p.27 | Shows $3,933.22, +$3,823.97, 1 follower. |
| Other handles: @whatever_fomo, @humanbeingET, @ExactTallTakin, @pricedin, @Hifive_07, @000000, @ether_monk, @kikaka10000 | handles | p.12, 18–19, 24 | Leaderboard users inside the app. |
| "Comment Trade" / link in bio | CTA | audio 45.8s; p.31–32 | See funnel. |

### What's being promoted / the funnel decoded
"Comment Trade" gets you a DM with "access to the software and a list of traders to copy". The software on screen is the **Fomo** memecoin app. Fomo runs a referral and rewards program (the "Rewards" button is visible on her profile), so the DM is almost certainly a Fomo referral or invite link plus some leaderboard handles, which pays her a share of your trading fees. The comment section is all "Trade" replies, which also boosts the reel's reach. No paid course or price is shown. The bio link could not be read from the material.

The Poe and Dulo segments are hooks (the "3 websites" format reuses another creator's clip). Only the trading app is the funnel.

### Verification & insights
- Web: Fomo's own help pages say copy trading isn't automatic; you decide each trade after a notification. Leaderboards cover 24h/7d/30d/all-time. Independent reviews note it's self-custodial, has fees, and that people report trouble selling in volatile markets. Dulo domains are documented piracy mirrors. Poe is legit but metered and paid for heavy use.
- "Copy their trades exactly": you get a notification after the trader buys, then you buy at a later price. In micro-cap memecoins, the trader's own $15k buys move the price (here BORDR went from $3.71M to $4.06M market cap between his two buys). Followers are structurally exit liquidity.
- "I think it actually works": she never shows the result. She says she'll "check back in a few hours" and the video ends. Her profile's +$3,823.97 doesn't match "a couple hundred dollars" on one trade, and nothing ties it to this trade.
- Leaderboard PnL is survivorship-biased: it ranks today's winners, and a 24h top performer in memecoins says nothing about the next trade.
- Watching movies on Dulo is copyright infringement, and it's an ad and malware-risk site.
- Could not verify: her bio link, what the DM actually contains, or whether the desktop screen is Fomo's web app.

---

<a id="e-desv9nqron5"></a>

## DesV9NQRON5 | @anon.callz | "Elon accidentally exposed" a Trump plan to tokenize seized Venezuelan/Iranian oil as "IOF" (Institutional Oil Fund): a masked-narrator memecoin shill pushing the Candles app
- **Link:** https://www.instagram.com/p/DesV9NQRON5/
- **Account:** @anon.callz (Anon Callz) · **Posted:** 2026-10-19 · **Type:** reel (117s, 63 pages). The batch folder only held the cover frame; I downloaded the full video during review.
- **Caption source:** full (Instagram; checked with yt-dlp during review)
- **Category:** Crypto
- **Verdict:** SCAM-RISK – a classic memecoin pump script: a doctored or fabricated Elon Musk clip, an anonymous "4chan leak", a fake "BlackRock holds it" proof, a "$10 = millionaires" calculation, and a "comment IOF / download Candles" funnel into a ~$5.6M-market-cap token.

### Post description
> This will change everything…
>
> #investing #trump #wealth #oil

### Audio
The masked narrator's speech, plus a short opening clip presented as Joe Rogan and Elon Musk:
- [0.0–3.1] (voice presented as Joe Rogan) "What do you think would be the best investment right now?"
- [3.1–10.6] (voice presented as Elon Musk) "My Tesla stock, thanks to my new flying roadster coming out, the SpaceX for obvious reasons, then I would say IOF. And it's because…" (the IOF line is almost certainly dubbed or AI-cloned; see verification)
- [11.5–22.0] "Elon Musk just pointed out something that the elites don't want you knowing about." Viewers are told to save the video and "watch to the end before it gets taken down."
- [22.0–34.4] Claims: Trump and Elon are no longer friends; Trump has been doing "really shady stuff" with notable elites; there are "literal wars" between Iran and America; Trump is "very money hungry".
- [34.4–51.9] Claims: oil is Iran's largest income source and the US "ranks bottom" in oil reserves; Trump already "captured Venezuelan President Nicolas Maduro" and forced a deal to take over Venezuelan oil, and seems to be doing the same in Iran.
- [51.9–64.4] Claims the two countries' oil is "worth over 51 trillion dollars", more than the US national debt, and that Elon is now "blabbing" about Trump's and his friends' shady business.
- [64.4–82.7] The pitch: to pay the national debt, Trump's "real plan is to tokenize the seized oil from Venezuela and Iran into a singular blockchain asset, IOF". BlackRock is supposedly in on it, "already holding it in their public on-chain holdings."
- [82.7–92.8] Says Larry Fink "owns BlackRock" and is a long-time Trump friend. He downloaded the **Candles** app, searched IOF and found it "already verified."
- [92.8–110.4] He says he "personally invested a good amount of money" because a 4chan user posted that Trump is planning IOF and leaked the date, "the 27th". At "just a penny", once IOF hits $10, "millionaires will be made".
- [110.4–116.6] CTA: "Comment IOF, and I'll send you the link, or download the Candles app. Search for it and buy it there."

### On-screen content, page by page
A narrator in a silver spiked mask and a black hoodie holds up images; word-by-word captions throughout.
**Pages 1–3 (0–7.9s):** Red banner "🚨Elon Accidentally EXPOSED plan to retire 9-5 workers just 6 days from now🚨". Inset: a podcast clip of Elon Musk; one shot of Joe Rogan with "JOE ROGAN EXPERIENCE" signage. Captions "What / do you / now?".
**Page 4 (7.9s):** Musk clip; caption "there's SpaceX".
**Pages 5–11 (11.5–19.5s):** Captions "because / Elon Musk / that the / and it's / good reason. / now, / and watch". Images: a collage of Musk, Trump, Bezos and Zuckerberg; a "TOP SECRET" folder; a yellow bookmark (save) icon; a fake Instagram warning "Your content can't be recommended at the moment".
**Page 12 (22s):** BBC headline card "Why is President Trump and billionaire Elon Musk no longer friends?"
**Pages 13–20 (24.4–33.1s):** Trump photos and cartoon, an Oval Office signing photo ("some notable elites"), US vs Iran flags, Trump in money.
**Pages 21–24 (34.5–38.1s):** Oil barrels, Iran flag, chart "COUNTRIES WITH THE LARGEST OIL RESERVES — Oil Reserves in 2025 (Billion Barrels)": Venezuela 303, Iran 209, Canada 163, Iraq 145, UAE 113, Kuwait 102, Russia 80, United States 74 (US circled, "bottom in").
**Pages 25–32 (40.2–49.3s):** Trump photos; a headline card "Trump Announces U.S. Military's Capture of Maduro" (Jan. 3, 2026, "By Matthew Olay, Pentagon News"); a photo of a detained, blindfolded man; "TOP SECRET" folder; oil; Venezuela flag.
**Pages 33–36 (50.5–58.4s):** Iran flag; the oil-reserves chart with Venezuela 303 and Iran 209 circled ("These"); "DEBT" weight on a US map ("that's more"); Musk and Trump ("And Elon").
**Pages 37–46 (60.6–73s):** Musk clip, Trump cartoon, Oval Office photo, Trump in money, the DEBT image, Trump at a podium, an icon of an oil barrel → crypto token ("is to tokenize"), Venezuela and Iran flags.
**Page 47 (73.5s):** Token card: "IOF Institutional Oil Fund ✓ IOF — **$0.005595** ↑ $0.00187 (50.34%) Past day".
**Page 48 (76.8s):** BlackRock building.
**Page 49 (78.8s):** Arkham Intelligence entity page "BlackRock" ($76,915,460,824.69 shown), holdings rows: BTC, ETH ($2,687.52 +0.46%), **IOF $0.0008 +2.47%** (highlighted), SBET $0.00019, USDT.
**Pages 50–51 (82.8–84.4s):** Larry Fink with a BlackRock logo; Trump with Fink.
**Page 52 (86.7s):** App Store card "Candles – Trade Everything — Web3: DeFi, Wallet, Memecoins [Open]", "88 RATINGS".
**Page 53 (88.6s):** Candles search for "iof": "Institutional Oil Fund ✓ $5.59M MC — $0.00559 +50.34%".
**Pages 54–55 (95.4–97s):** 4chan-style post: "Anonymous (ID: LmLuu0HEI) 10/04/26(Sun)03:06:60 No.4829433" with an IOF logo (Capitol dome): "$IOF launch slated for October 4th. Officials have been plotting for years. Announcement on October 27th." "99 Replies / 33 Images". (The timestamp "03:06:60" is not a valid time.)
**Page 56 (102.3s):** Calculator "1,000×1,673.27 = 1,673,270".
**Page 57 (103.4s):** IOF price card $0.005595 again.
**Page 58 (104.3s):** Chatbot screenshot. Question: "If I put $1,000 into IOF at $0.0055 price point, how much will that $1,000 be worth if IOF reaches $10?" Answer: "At $0.0055 per IOF, $1,000 buys about 181,818.18 IOF. If IOF reached $10.00, that position would be worth $1,818,181.82. That's roughly a 1,673.27x return, before any fees, taxes, or slippage."
**Pages 59–60 (107.9–109.1s):** Elites collage; "TOP SECRET".
**Pages 61–63 (110.5–115s):** "Comment IOF", the Candles App Store card, and the Candles search result for IOF.

### Everything named or linked
| Item | Type | Where it appeared | What it really is (verified) |
|---|---|---|---|
| IOF "Institutional Oil Fund" | crypto token | audio 7.0s, 73s; p.47, 53, 57, 61–63 | A micro-cap memecoin (~$5.59M market cap at $0.00559, so roughly 1B supply). Web search found **several different Solana tokens** named "Institutional Oil Fund (IOF)" with pump.fun-style addresses (…pump), one with about $4.2M market cap and another worth about $2K with nearly all supply in one wallet. There's no official project, issuer or link to any government. |
| Candles – Trade Everything (App Store) | app | audio 86.6s; p.52, 62 | A "Web3: DeFi, Wallet, Memecoins" trading app (88 ratings). No independent coverage found. Being "verified" inside it means nothing about legitimacy. The account is very likely paid by or affiliated with the app, the token, or both. |
| Arkham "BlackRock" entity holdings showing IOF | "proof" | audio 76.7s; p.49 | Anyone can send tokens to a known BlackRock wallet; unsolicited "dust" tokens then appear in that wallet's holdings on Arkham. It's a known memecoin promotion trick, not evidence BlackRock bought anything. The price shown there ($0.0008) doesn't even match the $0.0056 used elsewhere. |
| Elon Musk on the Joe Rogan Experience ("…then I would say IOF") | clip | audio 0–10.6s; p.1–4 | Real JRE footage of Musk, with the IOF line dubbed or AI-cloned. Musk has never endorsed a token called IOF. |
| 4chan "Anonymous (ID: LmLuu0HEI)" post, "launch Oct 4, announcement Oct 27" | "leak" | audio 95.4s; p.54–55 | Unverifiable and trivially fakeable; the invalid timestamp ("03:06:60") suggests it was fabricated. |
| "6 days from now" / "the 27th" | date | title; audio 99.6s | An urgency device. Posted Oct 19 → "6 days" lands around Oct 25–27. |
| Oil reserves chart (Venezuela 303, Iran 209, Canada 163, Iraq 145, UAE 113, Kuwait 102, Russia 80, US 74 bn bbl) | data | p.23–24, 34 | Roughly consistent with commonly cited reserve figures, but the chart is a top-8 list. The US being "bottom" of it doesn't mean the US ranks last overall. |
| "$51 trillion" (Venezuela + Iran oil) | number | audio 51.9s | ≈512 bn bbl × ~$100/bbl. Reserves in the ground aren't liquid value, and nothing links them to a token. |
| "$10 → millionaires"; 1,673.27x; $1,818,181.82 | math | audio 102.2s; p.56–58 | At ~1B supply, $10 per token implies a ~$10B market cap from $5.6M. The screenshot's own numbers are inconsistent (181,818 × $10 = 1,818x, not 1,673x). |
| BBC headline; "Trump Announces U.S. Military's Capture of Maduro" (Jan 3, 2026, Pentagon News) | news cards | p.12, 27 | Real-world news context used as a credibility prop. It has no connection to any token. |
| Larry Fink, BlackRock | names | audio 82.7s; p.48–51 | Used for credibility. Note that Fink is CEO and chairman, not the "owner". |

### What's being promoted / the funnel decoded
"Comment IOF" leads to a DM with the buy link. The alternative is "download Candles and search IOF". This is a paid or affiliated memecoin promotion: the narrator says he "personally invested a good amount", which is classic exit-liquidity framing. Viewers' buys push up the price for insiders who hold the supply. The Candles app is the on-ramp, likely paying referrals. The comments are mostly "IOF"/"Iof" bot-like replies plus one sceptic: "If this was real you would have to download an app to buy it!!"

### Verification & insights
- Web search: multiple same-named "Institutional Oil Fund (IOF)" Solana tokens exist on pump.fun-style addresses. Scam-tracking reports describe exactly this playbook (pay influencers, fake volume, dump at a target market cap, send tokens to famous wallets for "proof").
- There is no government "tokenized oil fund". Seized sovereign oil can't be issued as a pump.fun memecoin.
- Red flags, all present: a celebrity deepfake, "before it gets taken down", a secret elite plan, an anonymous 4chan leak, a fixed date for urgency, "$10 = millionaires" math, and an obscure app to buy through.
- Could not verify: which IOF contract the Candles listing uses; whether the Joe Rogan question audio was altered as well; who operates Candles.

---

# Category: Markets & macro (8 posts)
