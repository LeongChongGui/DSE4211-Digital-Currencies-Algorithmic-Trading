**README.md**

# Dynamic Multi-Asset Trading Strategy: Prophet-MVOP Ensemble

## Overview
This project develops and backtests a dynamic, predictive trading strategy that performs hourly portfolio allocation across traditional stocks (AAPL, GLD, GOOGL) and cryptocurrencies (BTC, ETH). The core innovation is an ensemble model that integrates **Facebook's Prophet** for multivariate price forecasting with **Minimum-Variance Optimization (MVOP)** for risk-adjusted weight allocation, enabling forward-looking, adaptive portfolio management.

## Key Features
- **Hybrid Methodology**: Combines machine learning (Prophet) for prediction with quantitative finance (MVOP) for optimization.
- **Multi-Asset Focus**: Simultaneously allocates across equities and digital assets for diversification.
- **Dynamic & High-Frequency**: Recalculates and adjusts portfolio weights hourly based on latest forecasts.
- **Risk-Managed**: Employs MVOP to minimize portfolio variance while targeting returns, supplemented by stop-loss mechanisms.
- **Backtested Performance**: Evaluated on out-of-sample data (Mar–Apr 2025) against a buy-and-hold benchmark.

## Methodology
1.  **Data**: Hourly price data (Jan 2024 – Apr 2025) from Yahoo Finance (stocks) and CryptoDataDownload (crypto).
2.  **Forecasting**: A Prophet model is trained for each asset, using prices of other assets as external regressors to capture cross-asset dependencies.
3.  **Signal Generation**: The forecasted price trend is compared against historical averages to generate a directional signal.
4.  **Portfolio Optimization**: The signal dynamically adjusts the asset weight constraints within an MVOP framework, which is solved hourly to determine the final allocation.
5.  **Backtesting**: The strategy is executed on the test set with transaction costs and real-world constraints (e.g., market hours alignment).

## Results
On the test period, the Prophet-MVOP ensemble strategy achieved:
- **Final Portfolio Value**: $1,042,153 (from $1M initial)
- **Annualized Return**: 65.54%
- **Sharpe Ratio**: 2.30
- **Maximum Drawdown**: -5.47%
- **Win Rate**: 52.08%

The strategy consistently outperformed a simple buy-and-hold benchmark, demonstrating superior risk-adjusted returns and adaptability.

## Project Structure
```
├── data/                   # Scripts for data fetching & preprocessing
├── forecasting/            # Prophet model training and prediction
├── optimization/           # MVOP portfolio construction and weight calculation
├── backtesting/           # Portfolio simulation and performance analysis
├── utils/                 # Helper functions (metrics, plotting)
└── config.py              # Parameters and asset definitions
```

## Requirements
Key Python libraries: `prophet`, `numpy`, `pandas`, `cvxpy` (or `scipy` for optimization), `yfinance`, `plotly`/`matplotlib`.

## Usage
1.  Run data collection scripts in `data/` to fetch and clean hourly price data.
2.  Train Prophet models and generate forecasts using scripts in `forecasting/`.
3.  Run the main ensemble strategy (`main.py`) to generate hourly allocations via MVOP.
4.  Execute the backtest to evaluate performance and generate metrics and equity curves.

## Uniqueness & Contributions
- Bridges time-series forecasting and modern portfolio theory in a high-frequency, multi-asset context.
- Proposes a novel weight-adjustment mechanism that uses Prophet's predictions to inform MVOP constraints.
- Demonstrates the practical efficacy of combining traditional and digital assets in a single, dynamically managed portfolio.

## Future Work
- Implement dynamic model selection from a broader pool of forecasting algorithms.
- Incorporate additional risk factors and constraints (e.g., leverage, sector limits).
- Explore reinforcement learning for adaptive parameter tuning.

## Team
Project by a cross-disciplinary team in data science and quantitative finance.
