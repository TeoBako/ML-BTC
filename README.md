#  BTC Price Prediction Using Machine Learning

This project applies various Machine Learning models to predict Bitcoin's next-day price or market direction using a range of historical financial indicators.

The following models are used:
-  Linear Regression
-  LSTM (Long Short-Term Memory Neural Network)
-  Random Forest Classifier

Each model is implemented in a separate Jupyter Notebook using local `.csv` files for training and testing.

---

##  Project Structure


---

##  Data Used

The models use a combination of cryptocurrency and macroeconomic data. The following CSV files were used:

- `BTC-USD.csv`: Daily Bitcoin prices and volume
- `S&P 500.csv`: S&P 500 index prices
- `NASDAQ.csv`: Nasdaq index prices
- `GOLD.csv`: Gold price per ounce
- `DXY.csv`: U.S. Dollar Index
- `TNX.csv`: 10-Year Treasury Note Yield
- `VIX.csv`: Volatility Index (VIX)

Each CSV file contains:
- `Date`: Timestamp of the data point
- `Price`: Daily closing price
- `Vol.` (for BTC only): Daily volume

---

##  Models Overview

### 1. Linear Regression
- **Goal**: Predict the **next-day BTC closing price**
- **Features**: 1-day lag of macroeconomic indicators (S&P 500, NASDAQ, GOLD, etc.) and technical indicators
- **Type**: Regression
- **Output**: Continuous predicted price
- **Evaluation**: MAE, MSE, R²

### 2. LSTM (Long Short-Term Memory)
- **Goal**: Predict the **next-day BTC closing price** using sequential data
- **Features**: Same as above — 1-day lag of macro indicators and technical indicators
- **Preprocessing**:
  - Data scaled using MinMaxScaler
  - Reshaped into 3D arrays for LSTM input
- **Type**: Time series regression
- **Output**: Continuous predicted price
- **Evaluation**: MAE, MSE
  
### 3. Random Forest Classifier
- Goal: Predict **BTC next-day return category** based on macro and price data
- The return (R) is calculated as the percentage change from today's price to tomorrow's price
- Multiclass classification based on return ranges:

| Return (R) Range         | Label         |
|--------------------------|---------------|
| R < -2%                  | Strong Sell   |
| -2% ≤ R < -0.5%          | Sell          |
| -0.5% ≤ R ≤ 0.5%         | Neutral       |
| 0.5% < R ≤ 2%            | Buy           |
| R > 2%                   | Strong Buy    |

- Output: One of the five classes above
- Evaluation: Accuracy, Confusion Matrix, Classification Report


