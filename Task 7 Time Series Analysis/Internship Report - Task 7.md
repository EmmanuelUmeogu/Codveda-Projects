

# 📈 Task 1: Time Series Analysis

## **Objective**

Analyze and model a time-series dataset to forecast future values (e.g., stock prices, sales).

---

## **Steps Taken**

### 🔹 1. Data Loading & Visualization

* Loaded the dataset using **pandas**.
* Converted the date column into a **datetime format** and set it as the index.
* Plotted the time series to observe overall trends and patterns.

---

### 🔹 2. Time Series Decomposition

* Decomposed the series into **Trend, Seasonality, and Residual** using `seasonal_decompose` from **statsmodels**.
* Observed repeating cycles (seasonality) and long-term growth/decline (trend).

---

### 🔹 3. Smoothing Techniques

* Applied **Moving Average** smoothing to reduce noise.
* Used **Exponential Smoothing (SES, Holt’s Linear, Holt-Winters)** for short-term forecasting.

---

### 🔹 4. Forecasting with ARIMA/SARIMA

* Checked for **stationarity** using Augmented Dickey-Fuller (ADF) test.
* Differenced the series if necessary.
* Identified ARIMA parameters (`p, d, q`) using **ACF/PACF plots**.
* Built an **ARIMA/SARIMA model** for forecasting.

---

### 🔹 5. Model Evaluation

* Compared forecasted values with actual data.
* Used metrics such as **RMSE (Root Mean Square Error)** to evaluate accuracy.
* Visualized predicted vs. actual values.

---

## **Findings**

* Time series showed clear **trend and seasonal components**.
* ARIMA/SARIMA outperformed simple smoothing methods in capturing long-term dynamics.
* Forecasts aligned well with actual test data, suggesting reliability for future predictions.

---

## **Tools Used**

* Python
* **pandas** → data manipulation
* **matplotlib, seaborn** → visualization
* **statsmodels** → decomposition, ARIMA/SARIMA
* **scikit-learn** → metrics (RMSE, MAE)

