
# Potential Questions & Answers
> [!WARNING]
> DO NOT INCLUDE THIS FILE IN THE FINAL PRESENTATION.

> [!NOTE]
> please feel free to append any Q&A you may come across or feel is relevant

## 1. Methodology & Algorithms

**Q: Why did you choose LSTM over standard RNNs or ARIMA?**
* **A:** Financial time series data suffers from the "vanishing gradient" problem when using standard RNNs on long sequences. LSTMs have memory cells that preserve long-term dependencies. ARIMA is linear and cannot capture the complex non-linear patterns we observed in stocks like Tesla.

**Q: Explain the "Attention Mechanism". Why did it help AAPL but hurt MSFT?**
* **A:** Attention allows the model to assign weights to specific days in the past 60 days that are more relevant to today's price. However, Attention works best with clear historical patterns. If a stock moves erratically due to *external* news not present in the price history, Attention can overfit to noise, which is likely why the simpler Agent system outperformed it on MSFT.

**Q: How does the Multi-Agent System actually adjust the price?**
* **A:** It's a risk-management layer. The LSTM gives a raw number. The Technical Agent checks indicators (RSI, Bollinger Bands). The Sentiment Agent checks the news. If they detect "Overbought" or "Negative News" conditions, they lower the confidence score. The Meta-Agent then pulls the LSTM prediction closer to the *current* price to reduce risk.

## 2. Data & Results

**Q: Why did the Agent System perform slightly worse on Tesla (-0.7%)?**
* **A:** Tesla is a highly volatile, "news-driven" stock that often defies technical indicators. Our Technical Agent is designed to be conservative (e.g., betting against overbought conditions). When TSLA goes on a massive run (defying gravity), a conservative Agent will dampen the prediction, resulting in a slightly lower score than the raw Attention model which essentially "chased the trend."

**Q: Your Directional Accuracy is around 53%. Is that good?**
* **A:** In financial ML, anything above 50% is profitable over time. Predicting the exact sign change daily is incredibly difficult due to market noise. However, our $R^2$ (0.95+) shows we are predicting the *trend* and *magnitude* very accurately, which is more important for portfolio management than day trading.

**Q: How robust is the Sentiment Analysis?**
* **A:** We use TextBlob on headlines scraped from FinViz. While effective, it is a "dictionary-based" approach. In the future, we would upgrade this to a Transformer-based sentiment model (like FinBERT) to catch nuances like sarcasm or complex financial jargon that TextBlob might miss.

## 3. Software & Novelty

**Q: What makes this project "Novel"?**
* **A:** Most student projects stop at `model.predict()`. We implemented a **Neuro-Symbolic** approach. We combine the pattern recognition of Deep Learning (Black Box) with the interpretable logic of Trading Rules (Glass Box Agents). This directly addresses the "explainability" crisis in AI finance.

**Q: How did you handle Data Leakage?**
* **A:** We used a strict **Chronological Split** (Training: first 70%, Test: last 15%). We strictly avoided random shuffling, which would destroy time dependency. We also fitted our Scalers (MinMax) *only* on the training data to ensure future information didn't leak into the training process.
