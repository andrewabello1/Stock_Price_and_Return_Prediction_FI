# Stock Price & Return Prediction (NVDA)

This project compares **stock price prediction** vs **stock return prediction** using linear regression on NVIDIA (NVDA) historical data.

---

## Overview

- Downloaded NVDA data using `yfinance`
- Created technical features (moving averages)
- Built two regression models:
  - Predicting next-day **price**
  - Predicting next-day **return**
- Evaluated and compared performance

---

## Part 1 — Price Prediction

**Features**
- Close price  
- MA_5  
- MA_10  
- MA_20  

**Target**
- `Close.shift(-1)` (next-day price)

**Result**
- R² ≈ 0.97  

High R² is misleading because stock prices are highly persistent.  
The model mostly learns that tomorrow’s price is close to today’s price.

---

## Part 2 — Return Prediction

**Return Definition**
- `Close.pct_change()`

**Features**
- Today’s return  
- MA_5 (of returns)  
- MA_10 (of returns)  
- MA_20 (of returns)

**Target**
- `Return.shift(-1)` (next-day return)

**Results**
- MAE ≈ 0.022  
- R² ≈ 0.01  

Low R² reflects the realistic difficulty of predicting financial returns.

---

## Tools

- Python  
- pandas  
- numpy  
- scikit-learn  
- yfinance  

---

## Key Insight

Price prediction can appear highly accurate due to persistence in price levels.  
Return prediction provides a more realistic view of market predictability.
