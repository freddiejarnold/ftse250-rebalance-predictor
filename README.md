# FTSE 250 Index Rebalance Predictor

## The Thesis
Passive funds tracking the FTSE 250 are forced to buy/sell when the index 
reconstitutes. This creates predictable price pressure. This model identifies 
which stocks are approaching market cap thresholds for inclusion or exclusion — 
and quantifies how many days of average daily volume (ADV) passive funds will 
need to absorb the resulting flows.

## The Data
- **Prices & volume**: Yahoo Finance API (`yfinance`) — 90 days of daily OHLCV
- **Shares outstanding**: Yahoo Finance company info endpoint
- **Index thresholds**: FTSE Russell methodology (~£0.5bn deletion, ~£8bn promotion)

## The Logic
1. Calculate real-time market cap for each constituent
2. Measure proximity to deletion/promotion thresholds
3. Model passive fund flow pressure: `shares × 25% ownership ÷ 30d ADV`
4. Flag stocks with >5 days ADV needed as high-impact rebalance candidates

## The Result
Stocks flagged as HIGH IMPACT provide a tradeable signal — going long 
(additions) or short (deletions) 10–15 trading days before reconstitution, 
with an exit at the close of rebalance day, captures systematic price pressure 
from forced passive fund flows.

## Tech
`Python` · `Pandas` · `NumPy` · `yfinance` · `Matplotlib` · `Jupyter`
