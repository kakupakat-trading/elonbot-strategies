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
- **🛡️ Why a Universal Strategy?** We apply identical parameters across all assets to prevent overfitting. A strategy that performs consistently across diverse markets captures true market dynamics rather than just memorizing historical noise, ensuring greater robustness and reliability in live trading.
- Historical candles are downloaded via CCXT for each pair and timeframe.
- Results are evaluated with standard performance and risk metrics (ROI, PF, Max DD, Winrate, etc.).
- All data shown is unleveraged (1x).
- Each report indicates whether SL and TP were calculated by Percentage or by ATR 14,3.
- We use **5 TPs**:
  - TP1-TP4: Secure profits incrementally (20% each).
  - **TP5 is our 'Moonbag':** Designed to catch outlier moves and parabolic trends. By keeping this final portion active, the strategy remains exposed to potential "home runs" without risking the secured gains from earlier TPs.

## 🏆 Score Metric
A single value that reflects the overall strategy performance on your selected timeframe.

The higher the Score — the more stable and reliable the strategy is on this timeframe.
Perfect for quickly comparing timeframes and finding the best setups.

**FORMULA:**

Score = ((Profit + 100) / 100) × Winrate² × log(1 + Trades)

Where:
- **Profit** — total profit across all TPs
- **Winrate²** — accuracy squared (because consistency wins)
- **log(1 + Trades)** — logarithm of total trades (no luck on 2 trades allowed)

The result:
High Profit + Stable Winrate + Active Trading = **MAX SCORE 🏆**

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

## Atlas AI Framework
Atlas AI is not just a simple indicator bot; it is a hybrid quantitative decision engine that combines advanced technical modeling with Artificial Intelligence validation. It operates in four critical stages:

1. **Market Scanning (The Scanner)**: The system monitors Binance Futures in real-time, applying dynamic filters to isolate high-liquidity assets and discard dead or susceptible markets.
2. **The Mathematical Engine**: This is where the proprietary logic resides. The algorithm utilizes multi-factor statistical modeling and momentum coherence analysis to detect high-probability market anomalies, distinguishing genuine structural moves from market noise and "fake-outs."
3. **AI Validation (The Brain)**: This is the game-changer. Once the quantitative model detects a potential signal, it is sent to an LLM (Large Language Model) Validation module. The AI analyzes the full market context to approve or reject the trade, acting as a senior risk manager that filters out false positives.
4. **Execution & Transparency**: If the AI approves the trade, Atlas calculates dynamic risk parameters based on real-time volatility (adaptive sizing) and broadcasts the trade to our channels, ensuring total transparency.

Free trial: https://t.me/VIP_Agent_bot?start=m_hEkkwYo
Official channel: https://t.me/kakupakat_trading_oficial

#tradingview #indicator #algo #tradingview-strategy #strategy #code #pinescript #crypto #bitcoin #download #telegram #predictum #ggshot
