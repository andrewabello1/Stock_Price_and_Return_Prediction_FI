# 📈 Stock Price & Return Prediction with Linear Regression (NVDA)

This project explores the difference between predicting **stock prices** and predicting **stock returns** using NVIDIA (NVDA) historical data.

The goal is to understand why price prediction can be misleading and why financial modeling should focus on returns instead.

---

## 🚀 Project Overview

In this notebook, I:

- Downloaded NVDA historical data using `yfinance`
- Created technical features using moving averages
- Built two linear regression models:
  - 📊 Price Prediction Model
  - 📉 Return Prediction Model
- Compared model performance and interpretation
- Predicted the next-day return

---

## 📊 Part 1 — Price Prediction

### Features:
- Close price
- 5-day Moving Average (MA_5)
- 10-day Moving Average (MA_10)
- 20-day Moving Average (MA_20)

### Target:
- Next-day closing price (`Close.shift(-1)`)

### Result:
- Very high R² (~0.97+)

This high R² is misleading because stock prices are highly persistent.  
The model mainly learns that tomorrow’s price is close to today’s price.

---

## 📉 Part 2 — Return Prediction

### Return Definition:
```python
Return = Close.pct_change()

### Features:
- Today’s return
- 5-day moving average of returns
- 10-day moving average of returns
- 20-day moving average of returns

### Target:
- Target = Return.shift(-1)

### Result:
- MAE ≈ 0.022
- R² ≈ 0.01

The low R² is expected. Financial returns are noisy and difficult to predict.
This reflects a more realistic modeling approach.

### Libraries Used:
- Python
- pandas
- numpy
- scikit-learn
- yfinance
- matplotlib
