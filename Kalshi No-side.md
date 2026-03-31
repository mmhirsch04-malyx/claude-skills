# Kalshi NO-Side Parlay Strategy Skill

## Purpose
Identify and size bets on the NO side of multi-leg Kalshi parlay markets
where the true probability of all legs hitting is low enough to generate
positive expected value.

## Core Strategy Logic
- Scan open Kalshi markets for multi-leg parlays with 9 or more legs
- Only enter when NO cost is below $0.99 (meaning the market has active trading)
- Calculate true YES probability by fetching each leg's individual market price
  and multiplying them together
- Calculate edge as: (trueNoProb * 1.0 - trueYesProb * noCost) / noCost
- Only bet when edge exceeds 0.5%

## Backtest Findings (2000 settled markets, March 2026)
- 4-8 leg parlays: negative expected value, do not bet
- 9 leg parlays: 100% win rate, +4.19% avg return per bet
- 10 leg parlays: 100% win rate, +4.44% avg return per bet
- 11-20 leg parlays: 100% win rate, +1-3% avg return per bet
- Minimum viable threshold: 9 legs
- Sample size caveat: only 39 observations at 9+ legs, directional signal strong
  but needs more data t
