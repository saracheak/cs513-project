# High-Frequency Trading Price Prediction

## CS 513 - Knowledge Discovery & Data Mining

---

## Repository Structure

```
.
├── demo-aapl.ipynb                          # Main demonstration notebook
├── README.md                                # This file
├── LOBSTER_SampleFile_AAPL_2012-06-21_1/   # Apple sample data
├── LOBSTER_SampleFile_AMZN_2012-06-21_1/   # Amazon sample data
├── LOBSTER_SampleFile_GOOG_2012-06-21_1/   # Google sample data
├── LOBSTER_SampleFile_INTC_2012-06-21_1/   # Intel sample data
└── LOBSTER_SampleFile_MSFT_2012-06-21_1/   # Microsoft sample data
```

Each LOBSTER folder contains:

- `*_message_*.csv` - Order flow events (submissions, cancellations, executions)
- `*_orderbook_*.csv` - Limit order book snapshots
- `LOBSTER_SampleFiles_ReadMe.txt` - Data format documentation

---

## Dataset Details

### LOBSTER (Limit Order Book System - The Efficient Reconstructor)

**Source:** Academic sample data from NASDAQ Historical TotalView-ITCH  
**Date:** June 21, 2012  
**Stocks:** AAPL, AMZN, GOOG, INTC, MSFT  
**Format:** CSV files with millisecond timestamps

**Message File Columns:**

- `Time` - Seconds after midnight (millisecond precision)
- `Type` - Event type (1=New order, 2=Cancellation, 3=Deletion, 4=Execution)
- `Order_ID` - Unique order identifier
- `Size` - Number of shares
- `Price` - Price × 10,000 (e.g., $91.14 = 911400)
- `Direction` - 1=Buy, -1=Sell

**Orderbook File Columns:**

- `Ask_Price_1` - Best ask price
- `Ask_Size_1` - Volume at best ask
- `Bid_Price_1` - Best bid price
- `Bid_Size_1` - Volume at best bid

---

## Methodology

### 1. Feature Engineering

We extract the following features from raw order book data:

**Price-Based:**

- Mid-price: `(Ask + Bid) / 2`
- Bid-ask spread
- Price returns and volatility

**Volume-Based:**

- Order imbalance: `(Bid_Volume - Ask_Volume) / Total_Volume`
- Total depth at best prices
- Rolling volume averages

**Event-Based:**

- Order submission rate
- Cancellation frequency
- Execution indicators

**Temporal:**

- Rolling means (100-event window)
- Momentum indicators
- Volatility measures

### 2. Model Architecture

**Baseline ANN (Current Demo):**

```
Input (10 features) → Dense(64) → Dense(32) → Dense(16) → Output(2 classes)
Activation: ReLU
Optimizer: Adam
Loss: Binary Cross-Entropy
```

**Planned Extensions:**

- LSTM for sequential pattern recognition
- CNN-LSTM hybrid (DeepLOB architecture)
- Attention mechanisms

### 3. Evaluation Metrics

- **Classification Accuracy** (vs. 50% random baseline)
- **Precision/Recall/F1-Score** for UP/DOWN predictions
- **Confusion Matrix** analysis
- **Feature Importance** rankings
