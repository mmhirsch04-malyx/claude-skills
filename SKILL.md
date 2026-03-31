# Kalshi Strategy Builder Skill

## Purpose
Help build, test, and refine prediction market trading strategies on Kalshi, with a current focus on MLB moneyline markets.

## Core System Context
- Probability model: Log5 for head-to-head matchup win probabilities
- Position sizing: Kelly Criterion from a $10,000 bankroll
- Data: Real 2023-2024 MLB game results
- Stack: Python backtesting engine, Claude API reasoning layer, React dashboard

## When This Skill Is Active
- Building or debugging the backtesting engine
- Extending the strategy to new markets or sports
- Evaluating edge, expected value, and Kelly fractions
- Improving the Claude API reasoning layer prompts
- Adding features to the React dashboard

## Code Standards
- Python for all backtesting and data logic
- Functional, modular code with clear variable names
- Always show Kelly fraction, edge percentage, and expected value alongside any bet recommendation
- Never recommend a bet without a stated probability estimate and implied odds comparison

## Output Defaults
- Lead with the math before the code
- Flag any assumptions explicitly
- When backtesting, always report win rate, ROI, max drawdown, and Sharpe ratio
