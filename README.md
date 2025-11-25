# Stock Price Prediction System - (ANN vs. LSTM)

## Project Overview

Predicting stock market trends is a complex task due to the volatility and non-linear nature of financial data. This project tackles the problem by leveraging:

- Feature Engineering: Calculation of technical indicators (RSI, MACD, Bollinger Bands, etc.) to feed the ANN.
- Sequence Modeling: Utilizing LSTM's ability to learn long-term dependencies in time-series data.
- Comparative Analysis: rigorous evaluation of both models using statistical metrics ($R^2$, RMSE, MAPE).

## Key Features

- Automated Data Pipeline: Fetches live/historical data using the yfinance API.
- Advanced Feature Engineering: Manually implements technical indicators from scratch using Pandas:
    - Moving Averages: SMA (10, 50), EMA (12, 26)
    - Momentum: RSI (14), MACD, Signal Line
    - Volatility: Bollinger Bands, Average True Range (ATR)
    - Volume: On-Balance Volume (OBV)
- Dual Architecture Approach:
    - ANN: A deep feed-forward network optimized for regression on engineered features.
    - LSTM: A recurrent network optimized for sequential pattern recognition.
- Visualization Suite: Generates EDA plots, correlation heatmaps, loss curves, and prediction overlays.

## Technologies Used

- **Language:** Python
- **Deep Learning:** TensorFlow / Keras
- **Data Manipulation:** Pandas, NumPy
- **Visualization:** Matplotlib, Seaborn
- **Data Source:** Yahoo Finance (yfinance)

## Installation

1. Clone the repository:

```
git clone https://github.com/saracheak/cs513-project.git
cd cs513-project
```

2. Install dependencies:
   It is recommended to use a virtual environment.

```
pip install -r requirements.txt
```

## Usage

The main logic is contained within stock_prediction_project.ipynb.

By default, The notebook is configured to analyze Apple (AAPL), Tesla (TSLA), Microsoft (MSFT), Amazon (AMZN), and JP Morgan (JPM). You can modify the tickers list in the script to analyze other stocks.

## Results & Performance

The system outputs a comparative table for each stock analyzed. Typical metrics generated include:

- MAE (Mean Absolute Error)
- RMSE (Root Mean Squared Error)
- MAPE (Mean Absolute Percentage Error)
- $R^2$ Score

### Sample Visualization

The script generates plots showing the "Actual vs. Predicted" prices, allowing you to visually inspect how well the LSTM captures trends compared to the ANN.

## Project Structure

├── stock_prediction_project.ipynb # Main source code (Data prep, Modeling, Eval)
├── requirements.txt # Python dependencies
├── LICENSE # Project Licensed
└── README.md # Project documentation

## License

This project is open-source and available under the MIT License.
