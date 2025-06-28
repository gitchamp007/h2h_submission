# 📊 RSI + DMA Crossover Backtest Strategy

This repository contains a Python implementation of a **backtesting framework** for a simple yet powerful **technical trading strategy** based on:
- **Relative Strength Index (RSI)**
- **Moving Average (20DMA and 50DMA) crossover**

It also includes a suite of **performance metrics** (e.g., Sharpe ratio, drawdown, annualized return) to evaluate the strategy across multiple stock time series.

---

## 📌 Strategy Logic

The strategy enters a **long position** (buys) when the following two conditions are met:

1. **RSI Condition**:  
   - The Relative Strength Index (RSI) is **below 30**, indicating the stock is oversold.

2. **DMA Crossover Condition**:  
   - The **20-day Moving Average (20DMA)** crosses **above** the **50-day Moving Average (50DMA)**.  
   - This is a classic signal indicating a potential **trend reversal to the upside**.

Once these two conditions are satisfied, the strategy enters a long position **on the next trading day** and holds until a new signal is generated.

---

## ⚙️ How It Works

### 1. `calculate_rsi(series, period=14)`
- Calculates the RSI of the given price series using the standard formula.
- Period default: 14 days.

### 2. `backtest_strategy(df)`
- Takes a stock price dataframe with columns: `['Date', 'Open', 'High', 'Low', 'Close', 'Volume']`.
- Computes:
  - RSI
  - 20-day and 50-day simple moving averages
  - Buy signals
  - Position holding logic
  - Daily strategy returns

### 3. `calculate_metrics(df, risk_free_rate=0.06)`
- Computes key performance metrics:
  - **Total Return**
  - **Maximum Drawdown**
  - **Annualized Return**
  - **Annualized Volatility**
  - **Sharpe Ratio** (uses excess return over the risk-free rate)
  - **Number of Trades Executed**

> 📌 The Sharpe ratio is calculated using the annualized return and volatility. Ensure `risk_free_rate` is also annualized (e.g., 0.06 for 6%).

---

## 📈 Performance Metrics Explained

| Metric | Description |
|--------|-------------|
| **Total Return** | Overall cumulative return of the strategy. |
| **Max Drawdown** | Largest observed loss from peak to trough. |
| **Annualized Return** | Compounded yearly return. |
| **Annualized Volatility** | Risk measure using daily std. dev. scaled to yearly. |
| **Sharpe Ratio** | Risk-adjusted return over risk-free rate. |
| **Trades** | Number of buy signals triggered by the strategy. |

---
