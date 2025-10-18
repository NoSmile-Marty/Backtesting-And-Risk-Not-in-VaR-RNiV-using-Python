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

---

## 📉 Visualization – AAPL VaR Breaches (99%)
<p align="center">
  <img src="Screenshots/AAPL VaR Breaches Timeline.png" width="700" alt="AAPL VaR Breaches Timeline (99%)">
  <br>
  <em>Figure: AAPL 99% VaR Breaches Timeline (2020–2023)</em>
</p>


## 💡 Insights and Interpretation
The chart above illustrates the 99% Value at Risk (VaR) breaches for Apple Inc. (AAPL) from 2020–2023. Each red dot represents a day where the actual return fell below the predicted VaR threshold - meaning losses were larger than expected by the 99% confidence model.

🔍 Key Observations
1. Clustered Breaches during Market Stress:
- Most VaR breaches occurred during early 2020, aligning with the COVID-19 market crash, when volatility spiked across global equities.
- A few additional breaches appear in mid-2022, coinciding with market uncertainty and tightening monetary policy.

2. Model Performance:
- The number of breaches is roughly consistent with the 1% expected violation rate, indicating that the VaR model is reasonably calibrated.
- Occasional exceedances are normal - if breaches were far more frequent, the VaR model would underestimate risk.

3. Tail Behavior:
- The breaches (red points) are significantly below the VaR threshold line, highlighting that extreme losses can exceed the modeled boundary - a reminder that VaR does not capture the full magnitude of tail risk.
- This emphasizes the need to also measure CVaR, which reflects expected losses beyond VaR.

📊 Risk Takeaway
1. VaR provides a probabilistic boundary for potential losses, but CVaR captures the severity of losses when those rare events occur.
2. During crisis periods, both measures should be reassessed as historical volatility assumptions may break down.
3. The Kupiec backtest p-value (typically > 0.05 in this case) supports that the VaR model was statistically consistent over the test period.

📊 Summary Statistics
| **Metric**                    | **Description**                                         | **Value**                      |
| ----------------------------- | ------------------------------------------------------- | ------------------------------ |
| **Total Observations**        | Number of daily return data points analyzed             | **1,005**                      |
| **Confidence Level**          | VaR calculated at 99% confidence (1% left tail)         | **99%**                        |
| **Expected Breaches**         | Expected number of observations below VaR (1% of total) | **10.05**                      |
| **Actual Breaches per Asset** | Number of observed VaR exceedances for each ticker      | **11**                         |
| **Observed Breach Rate**      | (11 / 1,005) × 100 = **1.09%**                          | **1.09%**                      |
| **Assets Analyzed**           | Portfolio constituents                                  | **AAPL, AMZN, JPM, TSLA, XOM** |
| **Data Period**               | Historical window used for analysis                     | **Jan 2020 – Dec 2023**        |
| **Data Frequency**            | Return calculation interval                             | **Daily**                      |
| **Backtesting Result**        | Observed breaches ≈ Expected → Model well-calibrated    | ✅ **Pass**                     |
