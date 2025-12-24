# Backtesting and reports

This repository provides an informational overview of the backtesting and reporting flow.

## Introduction (how we run backtesting)
- We run backtests per pair and timeframe with a minimum of 40,000 candles.
- We explore millions of internal indicator combinations to find viable configurations.
- We filter and select only coins that meet performance and risk objectives (profit factor and ROI).
- Only results that qualify as tier1 grade are considered.

## Objective
- Validate strategies with a minimum of 40,000 candles per pair and timeframe.
- Produce comparable results across coins and timeframes to build and refine the strategy.

## Methodology (high level)
- Historical candles are downloaded via CCXT for each pair and timeframe.
- Results are evaluated with standard performance and risk metrics (ROI, PF, Max DD, Winrate, etc.).
- All data shown is unleveraged (1x).
- Each report indicates whether SL and TP were calculated by Percentage or by ATR 14,3.
- We use 4 TPs: you can close everything at TP1 or, if you prefer, use all four TPs with partial exits of 50%, 25%, 15%, and 10%.

## Workflow
- The backtesting engine consumes the internally prepared strategy list, runs historical simulations, and outputs the CSV at `backtesting/resultado_backtest.csv`.
- The report generator reads the CSV, removes internal technical columns, and builds an HTML report in `report_html/` with:
  - `index.html` with the general table and charts.
  - `images/` with charts (ROI and accuracy trend).
  - `details/` with per-coin detail pages.

## Folder structure
- Each timeframe folder follows the format `TF_<timeframe>` (example: `TF_5m`).
- HTML reports live in `report_html/` and CSVs in `backtesting/`.

## Available strategies
- TF_5m
- TF_15m
- TF_30m

## Strategy pages
Live HTML reports by timeframe:

### TF_5m
- Folder: `TF_5m/`
- Report: https://kakupakat-trading.github.io/elonbot-strategies/TF_5m/
- Notes: _Add summary or key takeaways here._

### TF_15m
- Folder: `TF_15m/`
- Report: https://kakupakat-trading.github.io/elonbot-strategies/TF_15m/
- Notes: _Add summary or key takeaways here._

### TF_30m
- Folder: `TF_30m/`
- Report: https://kakupakat-trading.github.io/elonbot-strategies/TF_30m/
- Notes: _Add summary or key takeaways here._

## Estimated time
- Although we can scan the whole market, each coin takes ~3 hours to reach a solid result for building the strategy.
- Sometimes it can take up to 6 hours due to the number of combinations evaluated.

Free trial: https://t.me/VIP_Agent_bot?start=m_hEkkwYo
Official channel: https://t.me/kakupakat_trading_oficial

#tradingview #indicator #algo #tradingview-strategy #strategy #code #pinescript #crypto #bitcoin #download #telegram #predictum #ggshot
