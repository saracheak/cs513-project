# TSLA Stock Price Prediction

This repository contains a mini project for **Tesla (TSLA) stock price prediction**, developed for the CS513 course.  
The goal is to compare several machine learning and deep learning models on the same time-series forecasting task and evaluate their performance using regression metrics.

---

## 1. Project Overview

We use historical TSLA price data to build and compare the following models:

1. **K-Nearest Neighbors (KNN)**
2. **Decision Tree Regressor**
3. **Random Forest Regressor**
4. **Multi-Layer Perceptron (MLP)**
5. **Long Short-Term Memory (LSTM) network**

The task is **one-step-ahead regression**: predict the future closing price (or adjusted closing price) based on past values and/or engineered features.

---

## 2. Dataset

- **Ticker:** `TSLA`
- **Source:** Downloaded programmatically (e.g., using `yfinance`) from Yahoo Finance.
- **Typical columns:** `Open`, `High`, `Low`, `Close`, `Adj Close`, `Volume`
- Data is split into **training** and **test** sets in chronological order to respect the time-series nature.

You can modify the date range or sampling frequency directly inside the notebook.

---

## 3. Models and Methods

### 3.1 Traditional Machine Learning Models

Implemented with **scikit-learn**:

- **KNN Regressor**
- **Decision Tree Regressor**
- **Random Forest Regressor**

These models use windowed / feature-engineered input (e.g., past `n` days of prices and/or technical indicators) transformed into a tabular format.

### 3.2 Neural Network Models

Implemented with **TensorFlow / Keras** (or an equivalent deep learning framework):

- **MLP (Fully-Connected Neural Network)**  
  - Several dense layers with non-linear activations.
- **LSTM**  
  - Sequence model taking a time window of past prices and predicting the next value.

---

## 4. Evaluation Metrics

All models are evaluated on the **same test set** using standard regression metrics:

- **MSE** – Mean Squared Error  
- **RMSE** – Root Mean Squared Error  
- **MAE** – Mean Absolute Error  
- **R² score** – Coefficient of determination (interpreted as “accuracy” of regression)

### 4.1 Final Results

The following table summarizes the performance of all models on the test set:

| Model          |   MSE    |  RMSE   |   MAE   | R² (accuracy) |
|----------------|---------:|--------:|--------:|--------------:|
| KNN            | 1520.4441 | 38.9929 | 29.3737 | 0.6800 |
| Decision Tree  | 1404.5598 | 37.4775 | 27.2048 | 0.7044 |
| Random Forest  | 1170.7715 | 34.2165 | 24.7627 | 0.7536 |
| MLP            |  248.7090 | 15.7705 | 12.1681 | 0.9477 |
| LSTM          |  224.6783 | 14.9893 | 11.3035 | 0.9522 |

---

## 5. Key Observations

- All three tree-based models (KNN, Decision Tree, Random Forest) achieve **moderate performance**, with R² between **0.68–0.75**.
- Neural models significantly outperform classical models:
  - **MLP** reduces the error dramatically (MSE ≈ 249, R² ≈ 0.95).
  - **LSTM** achieves the **best performance** overall, with the lowest MSE and highest R² (≈ 0.95).
- This suggests that **non-linear neural architectures**, especially sequence-aware models like LSTM, capture temporal dependencies in stock prices more effectively than simple tree-based regressors.

---

## 6. Repository Structure

```text
.
├── CS513_TSLA.ipynb   # Main Jupyter notebook with data loading, modeling, and results
├── requirements.txt   # Python dependencies
└── README.md          # Project documentation (this file)
