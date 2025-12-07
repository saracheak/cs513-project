# Stock Price Prediction using Deep Learning & Multi-Agent Validation

**CS 513: Knowledge Discovery and Data Mining - Final Project**

## Project Overview

This project implements a comprehensive stock price prediction system that combines deep learning architectures with a novel **Agentic Validation Framework**.

We attempt to solve the volatility problem in financial forecasting by comparing three neural network architectures (ANN, LSTM, and Attention-based LSTM) and augmenting their predictions with a **Multi-Agent System** (Technical & Sentiment Agents). The system analyzes historical data and news sentiment for major tech stocks (AAPL, TSLA, MSFT) to predict next-day closing prices.

## Key Features

-   **Deep Learning Models:**
    -   **ANN:** Baseline regression model.
    -   **LSTM:** Captures temporal dependencies in time-series data.
    -   **Attention-LSTM:** Weighs the importance of specific historical time steps.
-   **Multi-Agent System (Agentic Models):**
    -   **Technical Agent:** Validates predictions against RSI, MACD, and Bollinger Bands.
    -   **Sentiment Agent:** Analyzes news headlines using `TextBlob` to gauge market mood.
    -   **Meta-Agent:** Synthesizes signals to adjust the final price prediction based on confidence scores.
-   **Advanced Feature Engineering:** Includes 15 technical indicators (SMA, EMA, ATR, OBV, etc.).

## Technologies Used

-   **Language:** Python 3.10+
-   **Deep Learning:** TensorFlow / Keras
-   **Data Source:** `yfinance` (Yahoo Finance API) & Web Scraping (FinViz)
-   **Sentiment Analysis:** `TextBlob`
-   **Data Processing:** Pandas, NumPy, Scikit-learn
-   **Visualization:** Matplotlib, Seaborn

## Results Summary

Our experiments demonstrated that the **Agent-Enhanced** system effectively corrects neural network "hallucinations" in volatile conditions.
-   **Average Improvement:** The Agent system improved $R^2$ scores by an average of **6.07%** over the Attention-LSTM baseline.
-   **Best Case:** Microsoft (MSFT) saw an **11.53%** improvement in accuracy when Agent validation was applied.

## Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/saracheak/cs513-project.git
    cd cs513-project
    ```

2.  **Install dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

3.  **Run the Notebook:**
    Open the Jupyter Notebook to execute the training pipeline.
    ```bash
    jupyter notebook
    ```

## Troubleshooting: Kernel & Environment Issues

If you run into errors regarding "Module not found" or version conflicts, it is highly recommended to create a dedicated Virtual Environment (`venv`) and link it to your Jupyter Kernel.

### Step 1: Create a Virtual Environment
Run the following command in your project terminal:

**For Mac/Linux:**
```bash
python3 -m venv venv
source venv/bin/activate
````

**For Windows:**

```bash
python -m venv venv
.\venv\Scripts\activate
```

### Step 2: Install Requirements

Once the environment is activated, install the libraries:

```bash
pip install -r requirements.txt
```

### Step 3: Add the Environment to Jupyter

To ensure the notebook uses *this specific* environment:

```bash
python -m ipykernel install --user --name=venv --display-name "Python (Stock Prediction)"
```

### Step 4: Select the Kernel

1.  Open the `.ipynb` file in Jupyter Notebook or VS Code.
2.  Go to **Kernel** -\> **Change Kernel**.
3.  Select **"Python (Stock Prediction)"** from the list.
4.  Restart the kernel and run all cells.

## Authors

  - Ravisara Cheakdkaipejchara
  - Vaibhav Achuthananda
  - Zhishan Yuan

## License

This project is open-source and available under the MIT License.
