---
title: "Three Books, One Spreadsheet: Comparing the Alpaca, Fintech, and Aggressive Challenger Portfolios"
date: 2026-08-22
layout: single
categories:
  - Projects
  - Finance
  - Data Visualization
tags:
  - algorithmic-trading
  - paper-trading
  - alpaca-api
  - portfolio-tracking
  - risk-management
  - python
permalink: /posts/2026/8/three-portfolios-compared/
header:
  teaser: joint-portfolio-dashboard-banner.png
excerpt_separator: <!--more-->
---

Now that the [Joint Portfolio Platform](/posts/2026/8/joint-portfolio-dashboard/) has been live long enough to accumulate real numbers, it's worth pulling those three books apart and asking what they're actually doing differently — and whether any of it should change.

<!--more-->

# 📊 Three Books, One Spreadsheet

<p align = "center">
  <img src = "https://datadoctor100.github.io/images/joint-portfolio-dashboard-banner.png" alt = "Joint Portfolio Platform Banner" width = "90%">
</p>

Each of the three books started with $1,000,000 in Alpaca paper capital and its own strategy logic. As of this writing (2026-08-22), combined equity across all three sits at **$3,038,576.13**, up **$38,576.13** (+1.29%) on $3,000,000 deployed. That headline number is close to useless on its own, though — the three books weren't funded on the same day, so it blends three different clocks into one figure. Alpaca Trader has been running since July 31, Fintech Trader since August 7, and Aggressive Challenger only since August 14. Everything below compares them on their own terms rather than pretending they're on equal footing.

---

## 🥊 The Three Books, Side by Side

| | Alpaca Trader | Fintech Trader | Aggressive Challenger |
|---|---|---|---|
| Inception | 2026-07-31 | 2026-08-07 | 2026-08-14 |
| Current equity | $1,038,721.86 | $1,006,535.06 | $993,319.21 |
| Total P&L | **+$38,721.86** (+3.87%) | +$6,535.06 (+0.65%) | **−$6,680.79** (−0.67%) |
| Max drawdown | −6.45% (8/19) | −0.94% (8/19) | −1.15% (8/19) |
| Open positions | 13 | 496 | 6 |
| Filled orders to date | 146 | 1,495 | 18 |
| Avg. trade size | $79,210 | $2,128 | $38,887 |
| Cash sitting idle | $44.76 (0.0%) | $81,191.54 (8.1%) | $603,812.77 (60.8%) |
| Top holding as % of book | 32.7% (SGOV) | 0.4% (SILJ) | 29.4% (NVDA) |

The best return, the worst drawdown, and the highest concentration are all sitting in the same book. That's not a coincidence — it's the same trade-off showing up three times in the same table.

---

## 🎯 Alpaca Trader: winning on the back of one position

Alpaca Trader is up $38,721.86, and $32,414.33 of that — **83.7% of the entire gain** — is sitting in a single position, BMNR, which is up 27.8% since entry. Take that one line out and the book has made about $6,300 on everything else combined, roughly in line with Fintech Trader's return over a comparable stretch.

The concentration behind that number is real: SGOV, SNDK, and BMNR together make up 67.9% of invested capital, and the book is essentially fully deployed (0.0% cash). That's what produced the −6.45% drawdown on 8/19 — when a book has two-thirds of its money in three names, a bad day in any one of them shows up immediately in the equity curve. The strategy is working, but the return is closer to "one good stock pick plus a Treasury-bill parking position" than a diversified systematic edge. A single-position cap — say, no name above 15–20% of the book — would have meant giving up some of that BMNR upside, but it also would have meant the August 19 drawdown was smaller, and the book's return wouldn't be one trade away from looking very different.

---

## 🌐 Fintech Trader: diversified almost to the point of invisibility

Fintech Trader holds 496 positions and has filled 1,495 orders since August 7 — an average trade size of $2,128. No single position is worth more than 0.4% of the book, and the top three combined are 1.3%. The result is exactly what you'd expect from that structure: the smoothest curve of the three (max drawdown −0.94%), the smallest single-name winners and losers (best: SILJ +$258.86; worst: XSD −$141.85), and a return, +$6,535.06, that looks more like a broad-market index fund than an active strategy.

That's not necessarily a problem — smooth and market-like is a legitimate mandate — but the trading pattern raises a real cost question. 1,495 fills to move a $1,006,535 book is a lot of turnover for a book this diversified, and several of the sector buckets clearly overlap: "US Equity - Style/Factor" (22.6%) and "US Equity - Broad Market" (13.5%) are very likely holding factor-tilted and cap-weighted versions of much of the same underlying market. Paper trading doesn't charge commissions or show slippage, so none of that turnover costs anything here — but it would in a live account. Consolidating overlapping ETF sleeves into fewer, larger positions would cut both the position count and the order volume without meaningfully changing the book's actual exposure. Four tickers (BALT, RECS, UCON, XHLF) also remain unclassified in the sector taxonomy — worth mapping before drawing conclusions from the sector breakdown, since 0.81% of the book is currently unaccounted for in that view.

---

## 😴 Aggressive Challenger: the least aggressive book of the three

This is the most interesting finding in the data. The book branded for "higher-variance strategy testing more aggressive entries and sizing" is the one holding **60.8% cash** — $603,812.77 of its $993,319.21 sitting uninvested — and it has filled only 18 orders since inception on August 14. Its realized volatility over that short window is actually the lowest of the three books (annualized ~6.7% vs. ~35% for Alpaca Trader), though with only 6 return observations that number is too noisy to lean on heavily.

What's not noisy is the cash figure. A book that's supposed to be testing aggressive sizing is currently running at 39% deployment. Its six positions — NVDA, TSLA, NFLX, AAPL, SONY, and META — are concentrated (top holding NVDA at 29.4% of invested capital) but the concentration is happening inside a shrunken sleeve of the total account, which caps how much the strategy's actual thesis can move the book's bottom line either way. The −$6,680.79 loss to date is coming almost entirely from NVDA (−$5,370.52) and META (−$3,671.25), partially offset by TSLA (+$3,758.92). There isn't a design problem visible in the trade selection — the problem is that the book isn't living up to its name. Either the sizing logic needs to deploy the idle capital to match the stated mandate, or the book should be relabeled to reflect what it's actually doing: a small, concentrated satellite position wrapped in a mostly-cash shell.

---

## 🧩 What Synthesizing These Three Would Actually Look Like

Looking at all three side by side, the shape of a better combined approach is sitting right there in the data:

Fintech Trader is doing the diversification job well — smooth, broad, low single-name risk — but doing it with more trades and more overlapping exposure than it needs. Alpaca Trader is doing the concentrated-bet job, but doing it by accident, with no explicit position-size discipline, which means its strong return is fragile rather than structural. Aggressive Challenger has the mandate for the concentrated-bet job but isn't funding it — 61% of that book is doing nothing.

A synthesized version of these three strategies would look less like three unrelated $1M accounts and more like a core-satellite structure: Fintech Trader's diversified sleeve as the core, trimmed down to consolidate overlapping ETF categories and cut order volume; a genuinely capped satellite sleeve — sized like Alpaca Trader's concentrated bets but with an explicit ceiling per name — funded by the cash currently idling in Aggressive Challenger instead of a separate account. That doesn't require new capital or a new strategy; it requires taking the $603,812.77 sitting uninvested in one book and either deploying it under real sizing rules or moving it to where capital is actually being put to work. Right now, roughly 20% of the combined $3,038,576.13 book value ($603,812.77 of $3,038,576.13) isn't participating in any strategy at all.

---

## ⚠️ What This Is and Isn't

All three books are paper money against Alpaca's simulated fills — no real capital at risk, and the differences in inception date mean the return comparisons here are about behavior and structure, not a fair race. A book with a 3-week head start and full deployment should be expected to show a bigger dollar swing, in either direction, than a book seven days old and 61% in cash. None of this is investment advice, and a concentration or cash-allocation call that reads as a clear improvement in three weeks of paper data can read very differently after three months of real drawdowns.

**[See the live numbers for yourself →](https://datadoctor100.github.io/trading/)**
