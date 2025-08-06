# ETF Pair Trading with Machine Learning

This project uses an **LSTM**, **XGBoost**, and **Random Forest** models to predict mean-reverting ETF pairs and simulate a trading strategy with out-of-sample testing.

---

## Overview
- **Goal:** Identify ETF pairs that exhibit mean reversion and simulate a trading strategy.  
- **Data:** Yahoo Finance daily prices for ETFs  
- **Train/Test Periods:**  
  - Train: 2015-01-01–2020-01-01 
  - Test: 2020-01-02–2024-12-31

---

## Pair Selection
We analyzed a broad list of ETFs and applied multiple **statistical tests** (cointegration, correlation, z-score distance, clustering, etc.) to identify **statistically significant pairs** likely to mean revert.  
**Selected pairs:**  
- IEMG / EEM  
- ARKK / ARKW  
- TLT / SPTL  
- SHY / VGSH  
- SOXX / ITA  

---

## Features
- **Spread, Z-Score, Rolling Mean, Rolling Std, Volatility**  
- **Lag Features:** Previous 5 days of spread & z-score  
- **Target:** Predict if z-score will move towards 0 (mean reversion)

---

## Models
- **Random Forest Classifier, LSTM, XGBoost**  
- Hyperparameter tuning with GridSearchCV  
- Balanced class weights for handling imbalanced signals  

---

## Trading Simulation
- Start **$100 per pair**  
- Enter trades when model predicts mean reversion and |z-score| ≥ 1.5  
- **Direction:** Short expensive ETF / Long cheap ETF  
- Hold 5 days, then exit  
- No overlapping trades  

**Outputs:**  
- Equity curve per pair and total portfolio  
- Metrics: Return %, Sharpe Ratio, Max Drawdown, Trades  

---

## 🛠️ Requirements
- pandas, numpy, scikit-learn, yfinance, matplotlib, seaborn, scikit-learn, statsmodels, pytorch, xgboost, pip, ipykernel, yfinance
- Install with:
  
  ```bash
  pip install -r environment.yml
  ```
