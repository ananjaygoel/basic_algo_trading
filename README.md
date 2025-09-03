# Unsupervised Learning Trading Strategy

This repository contains a Jupyter Notebook (`strategy.ipynb`) that implements an unsupervised learning-based trading strategy for S&P 500 stocks. The strategy involves using K-Means clustering to group similar assets based on various features and then constructing a portfolio from a selected cluster using Efficient Frontier optimization.

## Project Description

The project aims to explore the application of unsupervised learning, specifically K-Means clustering, to identify groups of stocks with similar characteristics. Based on these clusters, a trading strategy is developed to select assets and construct a portfolio with the goal of outperforming a benchmark (S&P 500).

## Data

The strategy utilizes the following data:

*   **S&P 500 Stock Prices:** Historical daily price data for S&P 500 constituents is downloaded using the `yfinance` library.
*   **Fama-French 5 Factors:** Monthly Fama-French 5 Factors data is downloaded using `pandas_datareader`.
*   `sentiment_data.csv`
*   `simulated_5min_data.csv`
*   `simulated_daily_data.csv`
## Features and Indicators

The notebook calculates various features and technical indicators for each stock:

*   Garman-Klass Volatility
*   Relative Strength Index (RSI)
*   Bollinger Bands (Low, Mid, High)
*   Average True Range (ATR)
*   Moving Average Convergence Divergence (MACD)
*   Dollar Volume
*   Monthly Returns for different time horizons (1, 2, 3, 6, 9, 12 months)
*   Rolling Fama-French Factor Betas

## Methodology

The trading strategy follows these steps:

1.  **Data Loading and Preparation:** Download and prepare historical stock price data and Fama-French factor data.
2.  **Feature Engineering:** Calculate various technical indicators and historical returns as features.
3.  **Data Aggregation and Filtering:** Aggregate data to a monthly frequency and filter for the top 150 most liquid stocks based on rolling dollar volume.
4.  **Fama-French Factor Betas:** Calculate rolling betas to the Fama-French factors.
5.  **K-Means Clustering:** Apply K-Means clustering to group stocks based on their features each month. Pre-defined centroids based on RSI values are used for initialization.
6.  **Portfolio Selection and Optimization:** Select stocks from a specific cluster (based on a hypothesis, e.g., stocks with high RSI) and use the Efficient Frontier to optimize portfolio weights to maximize the Sharpe Ratio. A weight bound constraint is applied for diversification.
7.  **Strategy Simulation:** Simulate the trading strategy based on the monthly portfolio rebalancing.
8.  **Performance Evaluation:** Compare the strategy's cumulative returns to a buy-and-hold S&P 500 benchmark.

## Visualization

The notebook includes visualizations to show:

*   The distribution of stocks across different clusters based on selected features (e.g., ATR vs. RSI) for each month.
*   The cumulative returns of the unsupervised learning trading strategy compared to the S&P 500 benchmark over time.
