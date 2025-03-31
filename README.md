# Stock Price Prediction and Impact Analysis Using LSTM Model

Contributed by :

Sejal Raj (055041)

Vidushi Rawat (055056)

## Objective

The objective of this project is to develop a Long Short-Term Memory (LSTM) based deep learning model to predict the stock prices of NIFTY 50 and Asian Paints Ltd. using historical daily stock market data. The model aims to provide insights into stock price movements and analyze how the performance of Asian Paints Ltd. influences the NIFTY 50 index.

## Problem Statement

Stock price prediction is a complex task due to the dynamic and volatile nature of financial markets. This project seeks to address key questions:

- *Can we accurately predict future stock prices using historical data?*
- *What is the correlation between NIFTY 50 and Asian Paints Ltd. stock movements?*
- *How well does the LSTM model capture stock market trends compared to actual market fluctuations?*

## Analysis and Approach

### Data Collection and Preprocessing

- *Data Source*: Historical stock price data was fetched from Yahoo Finance (yfinance package) for:
  - *Nifty 50 Index (Ticker: ^NSEI)*
  - *Asian Paints Ltd. (Ticker: ASIANPAINT.NS)*
- *Date Range: Data from **2005-01-31 to 2025-01-31* was collected to ensure a comprehensive historical record.
- *Data Focus*:
  - *Closing prices* were used as they provide a reliable snapshot of stock performance.
  - The data was *normalized using MinMaxScaler* to scale values between 0 and 1 for improved model efficiency.

### Sequence Creation for LSTM Model

- *Why Sequences?*
  - Stock price prediction is a *time series problem* where past prices impact future values.
  - LSTM models require sequences of past data to predict future values.
- *Sequence Length*:
  - A *60-day window* was chosen, meaning the model looks at the past 60 days’ closing prices to predict the next day’s price.
- *Data Preparation*:
  - Sequences were created using a *sliding window approach*.
  - Each sequence consists of *60 consecutive closing prices* as input (X), with the *next day's closing price* as the target (y).

### Splitting Data for Training and Testing

- *Train-Test Split*:
  - *80%* of the data was used for *training*.
  - *20%* was reserved for *testing* to evaluate model performance.
- *Data Reshaping*:
  - LSTM models require input data in the shape *(samples, time steps, features)*.

## Building and Configuring the LSTM Model

### Why Use LSTM for Stock Prediction?

- *LSTM networks* are a type of *Recurrent Neural Network (RNN)* capable of learning long-term dependencies.
- They effectively capture *sequential patterns in time-series data*.

### Model Architecture

- *Input Layer*: 60 time steps (past 60 days) with 1 feature (closing price).
- *LSTM Layers*:
  - *Three LSTM layers, each with **50 units*.
  - *Dropout (0.2)* applied after each layer to prevent overfitting.
- *Dense Layers*:
  - *One Dense layer* (25 units, ReLU activation) to introduce non-linearity.
  - *Final Dense layer* (1 unit) to predict the next day's closing price.

### Model Compilation

- *Optimizer: Adam (learning rate = 0.001*).
- *Loss Function: **Mean Squared Error (MSE)* for regression.
- *Evaluation Metric: **Mean Absolute Error (MAE)*.

## Model Training and Evaluation

### Model Training

- The model was trained for *10 epochs*.
- Training time was approximately *13 seconds per epoch*.

### Model Performance

- *Training Loss*: Consistently decreased, indicating effective learning.
- *Validation Loss*: Followed a similar trend, showing good generalization.

## Observations

### NIFTY 50 Prediction

- The model effectively *captured stock price trends*.
- A *prediction lag* was observed, particularly in *highly volatile market conditions*.
- The *predicted vs. actual plot* showed a *strong correlation* but slight underestimation during market peaks.

#### Insights:

1. *Strong Trend Capture*
   - The predicted prices *closely follow actual movements*.
   - The model *aligns well with long-term trends*.
2. *Underestimation During Volatile Periods*
   - Model *lags behind actual prices* during sharp fluctuations (e.g., 2021-2023).
3. *Better Performance in Stable Growth Phases*
   - *Accuracy improves* during stable growth periods.
4. *Lag in Predictions During Market Surges*
   - The model adapts *slowly to sharp upward trends*.

### Asian Paints Ltd. Prediction

- The model *predicted trends well but smoothed fluctuations*.
- It performed better in *long-term trend estimation* rather than short-term spikes.

#### Insights:

1. *Good Overall Trend Estimation*
   - *Predicted prices align well* with actual trends.
2. *Underestimation in High Volatility*
   - Model *struggles with rapid price changes*.
3. *Improved Accuracy in Moderate Price Movements*
   - Predictions were *more reliable in stable periods*.
4. *Lag in Capturing Peaks and Dips*
   - Model takes *time to adjust to sudden price shifts*.

### Comparison of NIFTY 50 & Asian Paints Ltd.

- *Strong Correlation*:
  - Movements in *Asian Paints Ltd. often preceded or coincided with NIFTY 50*.
- *Influence on Market Trends*:
  - *Asian Paints, being a major market player, **significantly impacts the NIFTY 50 index*.

## Managerial Insights

- *Investment Decisions: The model assists investors in **forecasting price trends*.
- *Market Behavior Analysis: The relationship between **Asian Paints Ltd. and NIFTY 50* provides insights into *blue-chip stock influence* on index movement.
- *Limitations*:
  - The model *does not incorporate macroeconomic factors or market sentiment*.
- *Future Enhancements*:
  - *Integration of technical indicators* like RSI, MACD, Bollinger Bands.
  - *Transformer-based models* for improved accuracy.
  - *Sentiment analysis* from news and social media data.

## Project Stats and Technical Specifications

- *Dataset: Historical closing prices of **NIFTY 50 and Asian Paints Ltd.*
- *Date Range: **20 years* (2005-01-31 to 2025-01-31).
- *Train-Test Split: **80% training, 20% testing*.
- *Sequence Length: **60 days*.
- *LSTM Layers: **3 layers, each with 50 units*.
- *Dense Layers: **1 hidden layer (25 units, ReLU activation)*.
- *Optimizer: **Adam (learning rate = 0.001)*.
- *Loss Function: **MSE*.
- *Evaluation Metric: **MAPE (Mean Absolute Percentage Error)*.
- *Model Accuracy*:
  - *Nifty 50 Prediction: **97.42% accuracy*.
  - *Asian Paints Ltd. Prediction: **94.13% accuracy*.

## Conclusion and Future Scope

- The *LSTM model effectively predicted stock prices*, demonstrating strong predictive power.
- *Asian Paints Ltd. significantly influences NIFTY 50*, reinforcing its market impact.
- *Future Scope*:
  - *Incorporating trading volume, sentiment analysis, and economic indicators*.
  - *Experimenting with ensemble models* for better accuracy.
