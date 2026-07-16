# Major_StockMarket_Capstone

# Stock Market Signal Analysis

## Feature Engineering, Backtesting, and Statistical Inference

**Author:** Micheal Major  
**Program:** Nashville Software School — Data Science  
**Project Type:** Capstone Project

---

## Project Overview
For my capstone, I will analyze stock market data to better understand what conditions tend to lead to profitable trade setups. The goal is to look at price action, indicators, and candlestick patterns to determine the conditions around trades that could support better decision-making and lead to profitable trades.
Technical indicators are often used to describe momentum, trend, volatility, and possible entry points in the stock market. However, a signal that looks convincing on a chart does not automatically produce a profitable or statistically meaningful result.

This project examines whether several commonly used technical features can help explain future stock returns or support repeatable trading strategies. The project combines:

- feature engineering from daily price data;
- exploratory data analysis;
- rule-based backtesting;
- linear regression;
- logistic regression; and
- visual storytelling.

A single stock was used as the initial case study so the feature-engineering and testing process could be developed in detail. The current notebooks use **NVDA**, but the broader purpose of the project is to create a framework that can later be applied to other stocks.

---

## Main Research Question

> Can technical features derived from daily stock prices help explain future returns and produce useful trading signals?

### Supporting Questions

1. What features and targets will we to determine profit?
2. Did trend, RSI, EMAs positioning, or candlestick patterns change the average future return?
3. Which trading rule produced the strongest total return?
4. Which strategy produced the highest win rate or lowest drawdown?
5. Were the observed relationships statistically significant?
6. How did the active strategies compare with a buy-and-hold benchmark?

---

## Data

Daily historical stock data was downloaded with `yfinance`.
- **Time period:** January 2015 through July 2026
- **Observations:** 2,891 trading days
- **Original fields:** Open, High, Low, Close, and Volume
- **Frequency:** Daily
- **Current case-study ticker:** NVDA

The first notebook downloads the data, engineers the features, and prepares a flattened dataset. The second notebook reads the prepared CSV and performs backtesting and statistical analysis.

---

## Technologies Used

- Python
- Jupyter Notebook
- pandas
- NumPy
- yfinance
- TA-Lib
- matplotlib
- mplfinance
- SciPy
- statsmodels
- vectorbt
- numba

  
## Project Workflow

### 1. Gather and Inspect the Data

The market-data notebook downloads daily price data and checks the number of observations, column structure, and data types.

### 2. Engineer Technical Features

The project creates measurable features instead of relying only on visual chart interpretation.

#### Candlestick Features

- Candle body size
- Full candle range
- Bullish, bearish, or doji classification
- Candle body percentage
- Upper wick size and percentage
- Lower wick size and percentage
- Wick-to-body ratio
- Price-gap size and percentage

#### Moving-Average Features

- 5-day EMA
- 10-day EMA
- 20-day EMA
- 50-day EMA
- 200-day EMA
- Bullish, bearish, or divergent EMA alignment
- Whether price touched an EMA
- Number of days since an EMA touch
- Candle location above, below, or touching an EMA
- Distance between price and an EMA

#### Momentum and Pattern Features

- Relative Strength Index (`RSI`)
- Bullish and bearish Harami patterns
- Bullish and bearish Harami Cross patterns

#### Trend Structure

The project uses closing-price peaks and valleys to identify market structure. Recent swing points are compared with previous swing points and grouped into an uptrend, downtrend, or neutral condition.

> Important limitation: confirming a peak or valley requires the following trading session. The trend signal should therefore be shifted before any production or live-trading use to prevent look-ahead bias.

### 3. Create Future-Return Targets

Forward percentage returns were created for:

- 5 trading days
- 10 trading days
- 15 trading days
- 22 trading days
- approximately 6 months
- approximately 1 year
- approximately 5 years

The project also creates binary targets, such as whether the 22-day return was positive.

### 4. Backtest the Strategies

The second notebook uses `vectorbt` to simulate rule-based entries and exits. Each strategy begins with **$3,000** and includes:

- 0.1% fees;
- 0.1% slippage; and
- a fixed holding period based on the strategy.

Strategies tested:

- Bullish Harami
- RSI below 35
- Bullish Harami during an uptrend
- Price setup above the 10EMA
- Uptrend
- Downtrend

### 5. Use Statistical Models

The project uses `statsmodels` for inference rather than building a machine-learning prediction system.

#### Linear Regression

Ordinary least squares regression was used to estimate how a signal changed the average future return.

#### Logistic Regression

Logistic regression was used to estimate the probability of a positive future return after a signal occurred.


## Main Findings

1. **Buy-and-hold was the strongest overall approach for the selected stock and time period.**
2. **Downtrend was the strongest active strategy by total return.**
3. **RSI below 35 offered the best win-rate and drawdown profile.**
4. **The 10EMA setup was another strong active signal, although it traded more frequently.**
5. **Bullish Harami showed weak standalone regression evidence.**
6. **A strategy can backtest well even when its regression relationship is weak or statistically insignificant.**
7. **Technical features were more useful for creating testable rules and describing market behavior than for explaining a large share of future-return variation.**

---

## Limitations

- The analysis currently uses one stock as a case study.
- Results may not generalize to stocks with different volatility, liquidity, or market behavior.
- The backtests use fixed holding periods rather than dynamic exits or stop losses.
- The analysis does not include taxes or bid-ask spreads.
- Slippage and fees are simplified assumptions.
- The peak-and-valley trend feature requires future confirmation and must be shifted to avoid look-ahead bias.
- The models use simple specifications and do not control for market regime, earnings, macroeconomic events, or broader market returns.
- Statistical significance was weak for several individual features.
- This project is educational and is not financial advice.

---

## Future Work

The framework can be expanded by:

- applying the same process to other stocks;
- comparing results across industries;
- testing weekly and monthly timeframes;
- adding market-index and volatility controls;
- creating dynamic stop-loss and profit-target rules;
- separating training and out-of-sample evaluation periods;
- testing walk-forward validation;
- improving the trend feature to remove look-ahead bias;
- combining features more carefully;
- building a reusable Python feature-engineering module; and
- creating a Streamlit application for interactive exploration.

I still plan to create the Streamlit application and expand the analysis beyond the current case study.
