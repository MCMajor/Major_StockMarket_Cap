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
- **Data Source:** Yahoo finance by way of yfinance
- **Time period:** January 2015 through July 2026
- **Observations:** 2,891 trading days
- **Original fields:** Open, High, Low, Close, and Volume
- **Frequency:** Daily
- **Current case-study ticker:** NVDA

The first notebook downloads the data, engineers the features, and prepares a flattened dataset. The second notebook reads the prepared CSV and performs backtesting and statistical analysis.

---
