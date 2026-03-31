# Bitcoin Arbitrage Strategy Skill

## Purpose
Build, test, and run a cross-platform arbitrage system that detects
price discrepancies between Kalshi and Polymarket on Bitcoin markets
and places paired orders to lock in risk-free profit.

## Core Strategy Logic
- Monitor the same Bitcoin event on both platforms simultaneously
- Calculate the combined cost of opposite legs:
  - UP leg: Kalshi UP ask + Polymarket DOWN ask
  - DOWN leg: Kalshi DOWN ask + Polymarket UP ask
- If either sum is below $1.00 (minus fees), an arbitrage exists
- Only enter when net profit after fees exceeds minimum threshold

## Bankroll and Sizing
- Total bankroll: $1,000 (conservative end of $500-$2k range)
- Max single trade exposure: 5% of bankroll ($50)
- Never size into a trade where fees eliminate the edge
- Track cumulative P&L and pause if drawdown exceeds 10% of bankroll

## Fee Assumptions
- Kalshi: ~2% per side
- Polymarket: ~2% per side
- Total round-trip fee load: ~4%
- Minimum arb threshold: sum must be below $0.94 to be worth entering

## Markets in Scope
- Kalshi: KXBTC15M (Bitcoin 15-minute up/down)
- Polymarket: btc-updown-15m matching slug
- Expandable to daily/weekly BTC price target markets later

## Code Standards
- TypeScript preferred (matches the Kalshi SDK and Polymarket CLOB client)
- Always run in dry-run mode first before live execution
- Log every opportunity detected, whether taken or not
- Store logs locally with timestamp, leg prices, sum, and action taken

## Output Defaults
- Always show: UP leg sum, DOWN leg sum, fee-adjusted edge, and
  position size before any trade recommendation
- Flag when no edge exists clearly rather than forcing a trade
- When backtesting, report: number of opportunities, win rate,
  average edge per trade, total P&L, and max drawdown

## Risk Rules
- Never place a live order without dry-run validation first
- Never trade both legs unless both orders can be placed near-simultaneously
- If one leg fills and the other fails, log it as a broken arb and
  do not chase the second leg
- Pause all trading if daily loss exceeds $50
