# Module 2 (Time Series): Data Exploration, Visualization, and Introduction to Python Notebooks
Author: **Christopher Satya Fredella Balakosa**

## Introduction to Time Series Analysis with Python
### 1. Introduction
A **Time Series** is a sequence of data points collected or recorded at specific time intervals such as daily temperature, monthly sales, or yearly population growth.

Time series analysis allows us to **understand patterns over time** and **forecast future values**.

It is widely used in economics, finance, weather prediction, IoT sensors, and machine learning.

Time series task typically include:
- Cleaning and preparing time-based data
- Identifying trends and seasonality
- Checking stationarity
- Building forecasting model (ARIME, Prophet, LSTM, etc)

---

### 2. How Time Series Analysis Works
#### Step-by-Step Concept

1. **Data Loading and Cleaning**
  - Import data using pandas, handle missing values, and parse dates properly.
  - Example: 
  ```python=
data = pd.read_csv('air_passengers.csv', parse_dates=['Month'],,index_col='Month'
data.info()
```

2. **Exploration**
  - Visualize and describe the data to understand its shape, trends, and possible anomalies.
  ```python=
data.plot(figsize(10,5))
```

3. **Decomposition**
  - Seperate data into components :
       - **Trend** (Long-term direction).
       - **Seasonality** (Repeating cycles).
       - **Residual** (Random noise).

4. **Correlation Analysis**
  - Use **ACF** and **PACF** plots to understand the relationship between current and lagged vlues.

5. **Stationary Check**
  - A stationary series has constant mean and variance over time.
  - Required for many statistical forecasting models.

6. **Visualization and Documentation**
- Visualizing trends helps interpret model behavior and communicate findings effectively.

---

### 3. Data Loading and Cleaning
#### Example
```python=
import pandas as pd
import matplotlib.pyplot as plt

df = pd.read_csv('air_passengers.csv', parse_dates=['Month'], index_col='Month')
df = df.fillna(method='ffill')  # Forward fill missing values
print(df.head())
```

#### Why Cleaning Matters?
| Problem | Example | Solution |
|------|----------------|--------------|
| **Missing Values** | Missing days in temperature data | Interpolate or forward-fill |
| **Irregular Intervals** | Skipped timestamps | Resample using `.resample('D')` |
| **Outliers** | Spikes in readings | Use Interquartile Range (IQR) or Z-Score |

---

### 4. Seasonal Decomposition
Decomposition separates the time series into interpretable parts:

| Component | Description| Visualization |
|------|----------------|--------------|
| **Trend** | Long-term increase or decrease | Smooth line |
| **Seasonality** | Repeating cycle or pattern | Peaks every fixed interval |
| **Residual** | Random noise | Irregular variations |
#### Example:
```python=
from statsmodels.tsa.seasonal import seasonal_decompose
result = seasonal_decompose(df['Passengers'], model='additive')
result.plot()
plt.show()
```

---

### 5. ACF and PACF Plots

#### What Are They?
| Plot | Full Name | Purpose |
|------|----------------|--------------|
| **ACF** | Autocorrelation Function | Shows correlation between current value and its past values |
| **PACF** | Partial Autocorrelation Function | Shows correlation after removing influence of earlier lags |

Mathematically, for ACF:
$$
\rho_k = 
\frac{
\sum_{t = k + 1}^{N} (y_t - \bar{y})(y_{t-k} - \bar{y})
}{
\sum_{t = 1}^{N} (y_t - \bar{y})^2
}
$$

Where:
- $( \rho_k )$: Autocorrelation at lag \( k \)
- $( y_t )$: Value at time \( t \)
- $( \bar{y} )$: Mean of the series
- $( N )$: Number of observations

For PACF:
$$
y_t = \phi_{k1} y_{t-1} + \phi_{k2} y_{t-2} + \dots + \phi_{kk} y_{t-k} + \epsilon_t
$$

Then:

$$
PACF(k) = \phi_{kk}
$$

Where:
- $( \phi_{kk} )$: Coefficient at lag \( k \)
- $( \epsilon_t )$: Error term

#### Example:
```python=
from statsmodels.graphics.tsaplots import plot_acf, plot_pacf

plot_acf(df['Passengers'], lags=30)
plot_pacf(df['Passengers'], lags=30)
plt.show()
```

#### Interpretation
- Slow decay in ACF → data is non-stationary.
- PACF cuts off after lag k → may indicate AR(k) process.

### 6. Stationarity Testing

Many models (like ARIMA) assume the series is **stationary**, meaning its statistical properties do not change over time.
#### Check Visually
Plot rolling mean and variance:
```python=
rolling_mean = df['Passengers'].rolling(12).mean()
rolling_std = df['Passengers'].rolling(12).std()

plt.plot(df['Passengers'], label='Original')
plt.plot(rolling_mean, label='Rolling Mean')
plt.plot(rolling_std, label='Rolling Std')
plt.legend()
plt.show()
```

#### Check Statistically (ADF Test)
```python=
from statsmodels.tsa.stattools import adfuller
result = adfuller(df['Passengers'])
print('ADF Statistic:', result[0])
print('p-value:', result[1])
```

#### Interpretation:
- ` p-value < 0.05 ` → Stationary
- ` p-value ≥ 0.05 ` → Non-stationary → apply differencing:
```python=
df_diff = df['Passengers'].diff().dropna()
```

### 7. Time Series Visualization

Visualization is key to understanding and communicating insights.

#### Basic Line Plot
```python=
plt.figure(figsize=(10,5))
plt.plot(df['Passengers'])
plt.title('Monthly Air Passengers')
plt.xlabel('Year')
plt.ylabel('Number of Passengers')
plt.grid(True)
plt.show()
```

#### Seasonal Plot
```python=
import seaborn as sns
df['Year'] = df.index.year
df['Month'] = df.index.month
sns.lineplot(x='Month', y='Passengers', hue='Year', data=df)
```

#### Rolling Statistics
Helps identify trend and volatility changes.
```python=
df['RollingMean'] = df['Passengers'].rolling(window=12).mean()
plt.plot(df[['Passengers', 'RollingMean']])
```

---

### 8. Best Practices for Documentation

| Step | Best Practice | Example |
|--------|-------------|-------------|
| **Version Control** | Track your analysis scripts. | Use Github |
| **Commenting** | Explain logic in code. | `# Test for Stationarity using ADF` |
| **Data Provenance** | Record dataset source and preprocessing. | “Dataset: AirPassengers (Box & Jenkins, 1976)” |
| **Reproducibility** | Include dependencies. | `requirements.txt` |
| **Summary Report** | Provide insight and visual explanation. | Markdown or Jupyter Notebook |

---

### 9. Summary

| Concept | Key Function | 
|------|--------------|
| **Load & Clean Data** | `pd.read_csv()`, `fillna()` | 
| **Decomposition** | `seasonal_decompose()` | 
| **Correlation** | `plot_acf()`, `plot_pacf()` | 
| **Stationarity** | `adfuller()` | 
| **Visualization** | `plt.plot()`,`sns.lineplot()` | 
| **Documentation** | Comments, Git, Reproducibility | 

```
Load Data → Clean → Visualize → Decompose → Check Stationarity → Interpret → Document
```

---
### Key Takeaway

> Time series analysis helps us see the story behind data over time patterns, cycles, and trends and prepares the foundation for accurate forecasting and decision-making.

A good time series analyst is both a detective (finding patterns) and a storyteller (communicating insights).

---

**Recommended Reading**
- Hyndman, R.J., & Athanasopoulos, G. (2021). *Forecasting: Principles and Practice* (3rd ed.)
- Jason Brownlee. *Introduction to Time Series Forecasting with Python*. Machine Learning Mastery
- Box, G.E.P., Jenkins, G.M., & Reinsel, G.C. (2016). *Time Series Analysis: Forecasting and Control. Wiley*
- Time Series Guide https://pandas.pydata.org/pandas-docs/stable/user_guide/timeseries.html
