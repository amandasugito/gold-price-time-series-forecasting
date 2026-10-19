# 📈 Gold Price Time Series Forecasting — Statistical and Machine Learning Models

## 📌 Project Overview

This project analyzes and forecasts gold prices using time series analysis and machine learning techniques in R.

The project explores historical gold price movements and compares four forecasting approaches: Exponential Smoothing (ETS), Autoregressive Integrated Moving Average (ARIMA), Extreme Gradient Boosting (XGBoost), and Neural Network Autoregression (NNAR).

The objective is to identify a suitable forecasting model by evaluating its performance on held-out test data.

## 🎯 Project Objectives

- Explore historical gold price movements and trends.
- Prepare and visualize time series data.
- Examine stationarity in the gold price series.
- Build and compare ETS and ARIMA forecasting models.
- Experiment with XGBoost using historical lag features.
- Evaluate NNAR models with different configurations.
- Compare forecasting performance using RMSE, MAE, and MAPE.
- Generate a 30-period gold price forecast using the selected ETS model.

## 📂 Dataset

The dataset contains **1,061 observations** of historical gold market prices covering March 2022 to March 2026.

| Attribute | Description |
|---|---|
| Total observations | 1,061 |
| Data frequency | Daily market observations |
| Period | March 2022 – March 2026 |
| `Date` | Observation date |
| `Price` | Gold price |
| `Open` | Opening price |
| `High` | Highest price |
| `Low` | Lowest price |
| `Vol.` | Trading volume |
| `Change %` | Percentage price change |

The analysis primarily uses the `Price` column as the target time series.

## 🧹 Data Preparation

The data preparation process includes:

- Importing the CSV dataset into R.
- Converting the `Date` column into a date format.
- Removing commas from price values and converting them to numeric data.
- Sorting observations chronologically in ascending order.
- Checking for missing values.
- Converting the price series into a time series object.
- Splitting the observations chronologically into 80% training data and 20% testing data.

A chronological split is used to preserve the time order of the observations.

## ⚙️ Features

- Historical gold price visualization.
- Price distribution analysis.
- Time series stationarity testing.
- First-order differencing.
- ETS model development and parameter tuning.
- ARIMA model identification and diagnostic testing.
- XGBoost hyperparameter experiments.
- Lag feature engineering for XGBoost.
- NNAR model comparison.
- Forecast evaluation using RMSE, MAE, and MAPE.
- Thirty-period future forecasting using the selected ETS model.

## 🛠️ Technologies Used

- **R** — Statistical computing and analysis.
- **R Markdown** — Reproducible analysis and reporting.
- **readr** — Data import.
- **dplyr** — Data manipulation.
- **ggplot2** — Data visualization.
- **forecast** — ETS, ARIMA, and NNAR modeling.
- **tseries** — Time series stationarity testing.
- **xgboost** — Gradient boosting regression.
- **Metrics** — Forecast error evaluation.
- **lmtest** — Statistical testing.

## 📊 Analysis and Results

### 1️⃣ Exploratory Data Analysis

The exploratory analysis examines the historical gold price trend and price distribution.

The notebook's visual interpretation identifies a pronounced upward trend beginning around 2024. The observed trend motivates the investigation of differencing and forecasting models that can accommodate changing price levels.

### 2️⃣ Stationarity Testing

The analysis examines stationarity in variance and mean.

- **Variance:** The notebook interprets the power transformation test as insufficient evidence to reject its stated null hypothesis.
- **Mean:** The Augmented Dickey-Fuller (ADF) test on the original price series reports a p-value of 0.8394, indicating insufficient evidence of stationarity.
- **First Differencing:** The differenced series reports an ADF p-value of 0.01 in the notebook, supporting the use of first-order differencing in the ARIMA experiments.

### 3️⃣ ETS Model

Several Exponential Smoothing configurations are evaluated, including ETS(M,N,N), ETS(A,A,N), and ETS(A,Ad,N), followed by parameter tuning.

The notebook reports that the tuned **ETS(A,A,N)** model with alpha = 0.47 and beta = 0.01 achieves the lowest reported MAPE of **6.26%** among the tested ETS configurations.

The selected model is also used to generate a 30-period forecast.

### 4️⃣ ARIMA Model

The analysis compares multiple ARIMA specifications, including ARIMA(0,1,0), ARIMA(1,1,0), ARIMA(0,1,1), ARIMA(1,1,1), and an automatically selected ARIMA model.

The notebook reports a MAPE of **16.32%** for ARIMA(0,1,1). Residual significance, normality, and white noise tests are also examined to assess model adequacy.

The final project conclusion does not select an ARIMA model as the preferred model.

### 5️⃣ XGBoost Model

XGBoost is implemented as a regression model using historical prices as lagged input features.

The experiments compare different combinations of lag features, including:

- Lag 1, 2, and 3.
- Lag 1, 2, 3, 7, and 14.
- Lag 1, 2, 3, 7, 14, and 30.

The notebook reports that the combination of lag 1, 2, 3, 7, 14, and 30 achieves a MAPE of **16.43%** in its lag comparison experiment.

Hyperparameter experiments also examine different values of `max_depth` and `nrounds`.

### 6️⃣ NNAR Model

Neural Network Autoregression (NNAR) models are evaluated using different configurations, including NNAR(1,1), NNAR(3,5), NNAR(5,10), NNAR(10,10), NNAR(15,15), and NNAR(20,20).

The models are compared using forecast accuracy metrics. The final project conclusion identifies ETS as the preferred approach.

### 7️⃣ Overall Findings

Based on the conclusions reported in the analysis:

- ETS provides the strongest reported forecasting result among the approaches discussed.
- The tuned ETS(A,A,N) model achieves a reported MAPE of 6.26%.
- ARIMA and XGBoost provide alternative forecasting approaches but have higher reported MAPE values in their respective experiments.
- NNAR provides an additional neural-network-based benchmark.

The reported metrics come from the notebook's experiments. A rigorous comparison across all model families requires ensuring that each model is evaluated on the same testing period and under a consistent forecasting setup.

## 📂 Project Structure

```text
gold-price-time-series-forecasting/
├── README.md
├── gold price forecasting.Rmd
└── dataset/
    └── datats.csv
```

The filenames above are recommended names for organizing the repository. Rename the original files accordingly if you use this structure.

## 🚀 How to Run

1. Install R and RStudio.
2. Clone or download the repository.
3. Open `gold-price-time-series-forecasting.Rmd` in RStudio.
4. Install the required R packages if they are not already installed.
5. Update the CSV file path in the R Markdown document to match the repository location.
6. Run the code chunks sequentially or render the document.
7. Review the visualizations, model comparisons, diagnostic tests, and forecast outputs.

The analysis requires the CSV dataset and the R packages used in the notebook.

## 👩‍💻 Author
**Amanda Sugito**
**Vanessa Santoso**

Human Computer Interaction academic project at BINUS University.


## ⚠️ Limitations

- **Historical Data:** The analysis uses historical gold prices, which may not capture unexpected market events.
- **Univariate Forecasting:** The primary models focus on historical prices and do not comprehensively incorporate external economic variables.
- **Model Assumptions:** Each forecasting method has assumptions and limitations that can affect its performance.
- **Forecast Uncertainty:** Future forecasts are estimates and are not guaranteed to match actual market prices.
- **Model Comparison:** Reported error metrics should be compared cautiously unless all models use an identical testing period and forecasting setup.

## 📝 Disclaimer

This project was developed for academic and educational purposes as part of a time series analysis study.

The forecasts are statistical estimates based on historical data and should not be interpreted as financial advice, investment recommendations, or guarantees of future gold prices. Actual market prices may differ substantially from the predictions.
