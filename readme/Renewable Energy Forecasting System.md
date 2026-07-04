# ⚡ Project : Renewable Energy Forecasting System

## 📌 Overview

This project focuses on forecasting key components of a renewable energy system:

- ⚡ Electricity Load (Demand)
- 🌬 Wind Power Generation
- ☀ Solar Power Generation

In addition, the project extends beyond traditional forecasting by analyzing the **energy imbalance** between demand and renewable supply.

The goal is to compare **statistical models** and **machine learning models** in a real-world energy forecasting setting.

---

## 🎯 Objectives

- Build accurate time series forecasting models
- Engineer temporal features (lags, rolling statistics, calendar effects)
- Compare:
  - Naive baseline models
  - Statistical models (SARIMAX)
  - Machine Learning models (XGBoost)
- Evaluate performance across different energy sources
- Analyze system-level **energy imbalance**

---

## 📊 Dataset

The dataset includes hourly energy system data from:

- October 2018 → September 2020

### Variables:
- `load` — electricity demand
- `wind` — wind power generation
- `solar` — solar power generation

---

## 🧠 Feature Engineering

To capture temporal dependencies, the following features were created:

### 🔁 Lag Features
- 1-hour lag
- 2-hour lag
- 24-hour lag (daily seasonality)
- 168-hour lag (weekly seasonality)

### 📈 Rolling Features
- Rolling mean (24h)
- Rolling standard deviation (24h)

### 📅 Calendar Features
- Hour of day
- Day of week
- Month

---

## 🧪 Models Implemented

### 📉 Baseline Model
- Naive forecast using `load_lag_24`

### 📊 Statistical Model
- SARIMAX with exogenous variables:
  - wind
  - solar
  - calendar features

### 🚀 Machine Learning Model
- XGBoost Regressor
- Hyperparameters tuned for time series regression

---

## 📈 Results (Load Forecasting)

| Model        | MAE   | RMSE  |
|--------------|-------|-------|
| Naive Lag-24 | 3313  | 4988  |
| SARIMAX      | 5117  | 5883  |
| XGBoost      | 342   | 446   |

---

## 🔍 Key Insights

- Load demand exhibits strong daily seasonality
- SARIMAX underperforms due to redundancy with lag-based features
- XGBoost captures nonlinear relationships effectively
- Wind is highly stochastic, while solar is highly deterministic
- Load lies in between in terms of predictability

---

## ⚡ Energy Imbalance Analysis

A system-level analysis was performed:


Imbalance = Load - (Wind + Solar)


### Findings:
- Renewable generation does not fully cover demand
- Solar drives strong daily patterns
- Wind provides partial smoothing but remains volatile

---

## 📊 Tools & Technologies

- Python
- Pandas, NumPy
- Scikit-learn
- XGBoost
- Statsmodels
- Matplotlib

---

## 🚀 Key Takeaway

This project demonstrates that **machine learning models significantly outperform classical statistical models** in renewable energy forecasting tasks due to their ability to capture nonlinear relationships and complex temporal interactions.

---

## 📌 Future Work

- Multi-step forecasting (24h ahead)
- Deep learning models (LSTM, GRU)
- Deployment as real-time forecasting system
- Energy storage simulation (battery integration)
