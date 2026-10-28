# Evaluation test set

Fill this in after every refresh, before you publish. The agent is the system under test.
You are the grader. Nothing here is automated on purpose: the point is to decide, with a
source you trust, whether the agent told you the truth.

**Ground truth sources.** Pick one and use the same one every time, so your scores are
comparable week to week:

- Prices: Google Finance (google.com/finance), Yahoo Finance, or your brokerage app.
- News: the article itself. Open the link. Check the date on the page.
- Calendar: the company's investor relations page (search "TICKER investor relations
  events"), or the Fed's own meeting calendar for FOMC dates.

Refresh date: 2026-10-28    Grader: number-checker

## A. Prices (one row per ticker)

Pass if the dashboard's last price is within $0.10 (close) or $1.00 (intraday) of the
ground truth for the same day and the same price type (close vs intraday). If the agent recorded an intraday price,
compare against the intraday price at about the same time; do not compare it to a close.

### Run 2 (2026-10-28, current rules, six closes per ticker)

Rules for this run: closes pass within $0.10, intraday prices pass within $1.00 (same price type only).

Google Finance returned "not supported on this device" to the fetch tool (https://www.google.com/finance/quote/NVDA:NASDAQ), so every row uses Yahoo Finance history (named below). Intraday rows (2026-10-28) cannot be reproduced at the agent's exact minute; the Yahoo Oct 28 row is mid-session, not a close, and is compared as intraday with the $1.00 tolerance. The new Oct 20 closes (each with its own Yahoo source URL in BRIEF) were checked against the same Yahoo history pages.

| Ticker | Date shown | Price type shown | Dashboard price | Ground truth price | Source you used | Pass / Fail |
|---|---|---|---|---|---|---|
| NVDA | 2026-10-20 | close | 216.47 | 216.47 | Yahoo Finance history | Pass |
| NVDA | 2026-10-21 | close | 221.97 | 221.97 | Yahoo Finance history | Pass |
| NVDA | 2026-10-22 | close | 212.21 | 212.21 | Yahoo Finance history | Pass |
| NVDA | 2026-10-23 | close | 210.96 | 210.96 | Yahoo Finance history | Pass |
| NVDA | 2026-10-26 | close | 216.00 | 216.00 | Yahoo Finance history | Pass |
| NVDA | 2026-10-27 | close | 217.94 | 217.94 | Yahoo Finance history | Pass |
| NVDA | 2026-10-28 | intraday 12:51 PM | 217.18 | 217.63 (Yahoo row, mid-session) | Yahoo Finance history | Pass (off by 0.45, within $1.00 intraday) |
| JPM | 2026-10-20 | close | 335.26 | 335.26 | Yahoo Finance history | Pass |
| JPM | 2026-10-21 | close | 335.19 | 335.19 | Yahoo Finance history | Pass |
| JPM | 2026-10-22 | close | 336.54 | 336.54 | Yahoo Finance history | Pass |
| JPM | 2026-10-23 | close | 331.58 | 331.58 | Yahoo Finance history | Pass |
| JPM | 2026-10-26 | close | 334.04 | 334.04 | Yahoo Finance history | Pass |
| JPM | 2026-10-27 | close | 335.79 | 335.79 | Yahoo Finance history | Pass |
| JPM | 2026-10-28 | intraday 12:51 PM | 340.25 | 340.21 (Yahoo row, mid-session) | Yahoo Finance history | Pass (off by 0.04, within $1.00 intraday) |
| ACN | 2026-10-20 | close | 239.12 | 239.12 | Yahoo Finance history | Pass |
| ACN | 2026-10-21 | close | 240.26 | 240.26 | Yahoo Finance history | Pass |
| ACN | 2026-10-22 | close | 258.74 | 258.74 | Yahoo Finance history | Pass |
| ACN | 2026-10-23 | close | 249.37 | 249.37 | Yahoo Finance history | Pass |
| ACN | 2026-10-26 | close | 247.23 | 247.23 | Yahoo Finance history | Pass |
| ACN | 2026-10-27 | close | 235.16 | 235.16 | Yahoo Finance history | Pass |
| ACN | 2026-10-28 | intraday 12:51 PM | 244.71 | 244.87 (Yahoo row, 1:02 PM) | Yahoo Finance history | Pass (off by 0.16, within $1.00 intraday) |
| HLI | 2026-10-20 | close | 130.33 | 130.33 | Yahoo Finance history | Pass |
| HLI | 2026-10-21 | close | 128.39 | 128.39 | Yahoo Finance history | Pass |
| HLI | 2026-10-22 | close | 133.24 | 133.24 | Yahoo Finance history | Pass |
| HLI | 2026-10-23 | close | 131.31 | 131.31 | Yahoo Finance history | Pass |
| HLI | 2026-10-26 | close | 131.21 | 131.21 | Yahoo Finance history | Pass |
| HLI | 2026-10-27 | close | 132.35 | 132.35 | Yahoo Finance history | Pass |
| HLI | 2026-10-28 | intraday 12:48 PM | 135.45 | 135.02 (Yahoo row, mid-session) | Yahoo Finance history | Pass (off by 0.43, within $1.00 intraday) |
| LLY | 2026-10-20 | close | 1283.66 | 1283.66 | Yahoo Finance history | Pass |
| LLY | 2026-10-21 | close | 1270.75 | 1270.75 | Yahoo Finance history | Pass |
| LLY | 2026-10-22 | close | 1306.69 | 1306.69 | Yahoo Finance history | Pass |
| LLY | 2026-10-23 | close | 1273.46 | 1273.46 | Yahoo Finance history | Pass |
| LLY | 2026-10-26 | close | 1279.14 | 1279.14 | Yahoo Finance history | Pass |
| LLY | 2026-10-27 | close | 1281.91 | 1281.91 | Yahoo Finance history | Pass |
| LLY | 2026-10-28 | intraday 12:51 PM | 1287.24 | 1286.68 (1:03 PM) | Yahoo Finance history | Pass (off by 0.56, within $1.00 intraday) |

Sources: https://finance.yahoo.com/quote/NVDA/history/ , https://finance.yahoo.com/quote/JPM/history/ , https://finance.yahoo.com/quote/ACN/history/ , https://finance.yahoo.com/quote/HLI/history/ , https://finance.yahoo.com/quote/LLY/history/

### Run 1 (superseded rules, restored from the earlier report)

These Fails were recorded under the old rule that an intraday price had to be within $0.10. The rule was changed afterwards to $1.00 for intraday, so Run 2 passes the same rows. They are kept as the record of what Run 1 found. Do not delete.

| Ticker | Date shown | Price type shown | Dashboard price | Ground truth price | Source you used | Pass / Fail |
|---|---|---|---|---|---|---|
| NVDA | 2026-10-28 | intraday | 217.18 | 217.63 | https://finance.yahoo.com/quote/NVDA/history/ | Fail (gap 0.45; rule was changed afterwards) |
| ACN | 2026-10-28 | intraday | 244.71 | 245.02 | https://finance.yahoo.com/quote/ACN/history/ | Fail (gap 0.31; rule was changed afterwards) |
| LLY | 2026-10-28 | intraday | 1287.24 | 1286.68 | https://finance.yahoo.com/quote/LLY/history/ | Fail (gap 0.56; rule was changed afterwards) |

## B. Weekly change (one row per ticker)

### Run 2 (2026-10-28, current page formula)

Graded by what the page now computes: weekChange() = (last close minus base close) / base close, ignoring the intraday price, where base is the sixth close from the end when six exist. BRIEF now has six closes per ticker, so the base is the Oct 20 close and the last close is Oct 27 (five trading days). "Dashboard" is what the page computes from BRIEF; "Your calculation" uses the Yahoo closes verified in A. Pass if within 0.3 points.

| Ticker | Dashboard weekly change (page formula) | Your calculation (verified closes) | Pass / Fail |
|---|---|---|---|
| NVDA | (217.94-216.47)/216.47 = +0.7% | 1.47/216.47 = +0.7% | Pass (0.0 apart) |
| JPM | (335.79-335.26)/335.26 = +0.2% | 0.53/335.26 = +0.2% | Pass (0.0 apart) |
| ACN | (235.16-239.12)/239.12 = -1.7% | -3.96/239.12 = -1.7% | Pass (0.0 apart) |
| HLI | (132.35-130.33)/130.33 = +1.5% | 2.02/130.33 = +1.5% | Pass (0.0 apart) |
| LLY | (1281.91-1283.66)/1283.66 = -0.1% | -1.75/1283.66 = -0.1% | Pass (0.0 apart) |

Sources: the Yahoo Finance history pages listed under A (Oct 20 to Oct 27 rows).

### Run 1 (superseded rules, restored from the earlier report)

Under the old page formula (Oct 21 close to Oct 28 intraday), the page figure was compared with the checker figure (Oct 20 close to Oct 27 close). The formula was changed afterwards, so Run 2 passes. Kept as the record of what Run 1 found. Do not delete.

| Ticker | Page figure (old formula) | Checker figure (Oct 20 to Oct 27 close) | Pass / Fail |
|---|---|---|---|
| NVDA | -2.2% | +0.7% | Fail (formula was changed afterwards) |
| JPM | +1.5% | +0.2% | Fail (formula was changed afterwards) |
| ACN | +1.9% | -1.7% | Fail (formula was changed afterwards) |
| HLI | +5.5% | +1.5% | Fail (formula was changed afterwards) |
| LLY | +1.3% | -0.1% | Fail (formula was changed afterwards) |

## C. News grounding (one row per news item, three per ticker)

Open every link. Pass only if all four are true: the link opens, the headline matches the
article, the article date is within the last seven days, and the "why it matters" line is
supported by the article (not just plausible).

Window: 2026-10-21 to 2026-10-28 inclusive. All four articles re-opened in Run 2 (dates and quoted sentences re-confirmed); JPM Fortune on-page H1 is "Jamie Dimon spent years warning about America's reliance on China. A year in, JPMorgan has put $230 billion behind fixing it" (matches; the browser title is a shorter variant). Article published Oct 21, 2026, 9:27 AM ET. ACN and HLI have no news items (empty lists), so there are no rows to grade for them; see Section E.

| Ticker | Headline (first few words) | Link opens | Headline matches | Dated within 7 days | "Why" is supported | Pass / Fail |
|---|---|---|---|---|---|---|
| NVDA | NVIDIA and Oracle Expand NVIDIA Vera Rubin... | Yes | Yes | Yes (Oct 27) | Yes: "growing customer demand" and scaling OCI Superclusters to multi-gigawatt levels | Pass |
| NVDA | NVIDIA and Meta to Expand Collaboration on Muse... | Yes | Yes | Yes (Oct 26) | Yes: "Meta intends to expand the deployment of NVIDIA infrastructure" and "NVIDIA will invest $3 billion in Meta's equity offering." | Pass |
| JPM | Jamie Dimon spent years warning... | Yes | Yes | Yes (Oct 21, boundary, inclusive) | Yes: "it has financed or facilitated $230 billion into sectors it considers essential for economic and national security" incl. critical minerals, defense, frontier tech | Pass |
| LLY | Lilly's retatrutide delivered greater A1C reduction... | Yes | Yes | Yes (Oct 28) | Yes: both retatrutide doses cut A1C 2.2% vs 1.8% for Ozempic 2 mg; release says retatrutide is investigational and not approved | Pass |

Sources: https://nvidianews.nvidia.com/news/nvidia-and-oracle-expand-nvidia-vera-rubin-to-multi-gigawatt-scale-and-bring-nvidia-vera-cpu-to-oracle-cloud-infrastructure (NVDA row 1); https://nvidianews.nvidia.com/news/nvidia-and-meta-to-expand-collaboration-on-muse-and-muse-family-of-models-amid-robust-growth (NVDA row 2); https://fortune.com/2026/10/21/jamie-dimon-jpmorgan-china-critical-minerals-defense/ (JPM); https://www.biospace.com/press-releases/lillys-retatrutide-delivered-greater-a1c-reduction-and-more-than-double-the-weight-loss-of-ozempics-highest-approved-dose-in-head-to-head-trial (LLY)

(Add rows as needed. Fifteen items is normal for five tickers.)

## D. Calendar (one row per event)

Pass if the event and its date appear on the source linked, and the date is in the future
relative to the refresh date.

The HLI and LLY investor relations pages did not load (empty page and HTTP 403). The sources below are the companies' own Business Wire releases as copied on Finviz; the HLI one is dated Oct 7 and the LLY one Oct 15. Not the IR page itself, noted as a limitation.

| Ticker | Event | Date shown | Confirmed on source | Pass / Fail |
|---|---|---|---|---|
| JPM | FOMC meeting concludes (Oct 27-28) | 2026-10-28 | Yes: Fed calendar lists "October 27-28" with no asterisk or tentative note for 2026. Not before asOf (equal). | Pass |
| HLI | Q2 FY2027 results, call 5:00 PM ET | 2026-10-28 | Yes: "Wednesday, October 28, 2026, after the close of trading on the New York Stock Exchange"; call "5:00 p.m. (ET) that same day." Confirmed, not expected. | Pass |
| LLY | Q3 2026 results, call 10:00 AM ET | 2026-10-29 | Yes: "October 29, 2026"; "The conference call will begin at 10 a.m. Eastern time." | Pass |

Sources: https://www.federalreserve.gov/monetarypolicy/fomccalendars.htm (JPM); https://finviz.com/news/400062/houlihan-lokey-announces-release-date-for-second-quarter-results-for-fiscal-year-2027 (HLI); https://finviz.com/news/403165/lilly-confirms-date-and-conference-call-for-third-quarter-2026-financial-results-announcement (LLY)

## E. Omissions

Did the agent miss something a human analyst would have included? List anything you found
in the ground-truth sources that the brief does not mention (a big headline, an earnings
date inside the window). Each one counts as a Fail in the score below.

- 
- 

## F. Your own test cases

Write two tests of your own that none of the sections above cover. Examples students have
used: "the as-of date on the page matches the changelog date", "no ticker shows a flat
sparkline when the real stock moved", "the page still renders if I delete one ticker's
news list in the data". Write the test, run it, record the result.

| Test | How you checked | Pass / Fail |
|---|---|---|
| | | |
| | | |

## Score

| Section | Passes | Total | Rate |
|---|---|---|---|
| A. Prices | | | |
| B. Weekly change | | | |
| C. News | | | |
| D. Calendar | | | |
| E. Omissions (fails only) | 0 | | |
| F. Your own | | | |
| **Overall** | | | |

Publish only if A and B are 100% and C is at least 80% after fixes. If a row failed, tell
Claude exactly which row and what the correct value is, let it fix only that, rerun the
`qa-reviewer` agent, and regrade that row. Keep the original Fail in this file: a record of
what the agent got wrong is more useful than a clean sheet.
