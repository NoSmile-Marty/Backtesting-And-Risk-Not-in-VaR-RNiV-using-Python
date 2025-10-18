# 📊 Backtesting & Risk Not in VaR (RNiV) Analysis 
This project demonstrates how to calculate and backtest **Value at Risk (VaR)** and **Conditional Value at Risk (CVaR)** for a diversified portfolio of stocks using **Python**. I have used daily stock data from Yahoo Finance (`yfinance`) over a 3-year period and analyzed tail risk through quantitative and visual techniques.

---

## 🧠 Project Overview

**Objective:**  
Estimate portfolio and individual asset risk using Value at Risk (VaR) and Conditional VaR (CVaR), and perform **backtesting** to verify model accuracy.

**Techniques Used:**
- VaR and CVaR calculation (historical method)
- Backtesting (Kupiec Test)
- Outlier and breach analysis
- Risk visualization (exception timelines)

---

## 📁 Project Structure

1. ⚙️ Data Collection
- Downloaded 3 years of daily price data for a diversified portfolio

2. 📈 Calculated Daily Returns

3. 📉 Compute VaR
- Calculate 99% daily VaR (1% left tail quantile)

4. 🚨 Identify VaR Breaches (Exceptions)
- Days where the actual return < VaR threshold

5. 🔍 Backtesting VaR – Kupiec Test
- To test if the number of breaches is consistent with the 1% expected violation rate

6. 🔎 Outlier / RNIV Factors
- Returns lower than VaR thresholds are potential outliers or Risk Not in VaR (RNIV) events

7. 📊 Visualization – VaR Breach Timeline
- Example: AAPL 99% VaR and breach days

8. 📊 Compute CVaR
- Captures the average loss beyond the VaR threshold

## 💡 Insights and Interpretation
