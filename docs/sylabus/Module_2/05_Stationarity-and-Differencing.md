<!-- # Topic 5: Stationarity and Differencing

Stationarity is a fundamental concept in time series analysis that refers to a time series whose statistical properties (mean, variance, and autocorrelation) do not change over time. Many time series models assume stationarity, making it crucial to test for and achieve stationarity through techniques like differencing before applying these models.

## Table of Contents

- [Topic 5: Stationarity and Differencing](#topic-5-stationarity-and-differencing)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Primary Resources](#primary-resources)
    - [Video Resources](#video-resources)
    - [Academic Resources](#academic-resources)
  - [Case Study: Currency Exchange Rate Analysis](#case-study-currency-exchange-rate-analysis)
    - [Scenario](#scenario)
    - [Dataset Description](#dataset-description)
    - [Analysis Tasks](#analysis-tasks)
    - [Expected Deliverables](#expected-deliverables)
    - [Sample Implementation Code](#sample-implementation-code)
    - [Expected Deliverables](#expected-deliverables-1)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to explain the following concepts:

- Stationarity (strict vs weak/covariance stationarity)
- Unit root tests (ADF, KPSS, Phillips-Perron)
- Differencing techniques (first, second, seasonal)
- Integration and I(d) notation
- Visual and statistical identification of stationarity

## Learning Resources

### Primary Resources
- [Stationarity in Time Series - Penn State](https://online.stat.psu.edu/stat510/lesson/4/4.1)
- [Unit Root Tests - statsmodels](https://www.statsmodels.org/dev/examples/notebooks/generated/unitroot_adf.html)
- [Time Series Stationarity](https://otexts.com/fpp2/stationarity.html)

### Video Resources
- [Stationarity in Time Series Explained](https://www.youtube.com/watch?v=oY-j2Wof51c)
- [ADF Test and Stationarity Testing](https://www.youtube.com/watch?v=e9E4RFnvBrY)

### Academic Resources
- [Time Series Analysis: Univariate and Multivariate Methods](https://www.amazon.com/Time-Analysis-Univariate-Multivariate-Methods/dp/0201889722)

## Case Study: Currency Exchange Rate Analysis

### Scenario
You are working as a quantitative analyst for an international trading firm. The company needs to model EUR/USD exchange rates for risk management purposes. However, before building any forecasting models, you need to ensure the data is stationary. Your task is to analyze the stationarity of daily EUR/USD exchange rates and apply appropriate transformations if needed.

### Dataset Description
```
Data: Daily EUR/USD exchange rates
Time Period: January 2019 - December 2023 (5 years)
Frequency: Daily (business days only)
Expected Characteristics:
- Random walk behavior (common in financial markets)
- No clear seasonal patterns
- Possible regime changes due to economic events
- High persistence (strong autocorrelation)
```

### Analysis Tasks

1. **Initial Visual Assessment**
   - Plot the raw exchange rate time series
   - Identify obvious trends, level shifts, or structural breaks
   - Create rolling statistics plots (mean and standard deviation)
   - Look for evidence of changing variance over time

2. **Statistical Stationarity Testing**
   - Perform Augmented Dickey-Fuller test on levels
   - Apply KPSS test to confirm stationarity/non-stationarity
   - Conduct Phillips-Perron test for robustness
   - Test different lag specifications and trend specifications

3. **Autocorrelation Analysis for Stationarity**
   - Plot ACF and PACF of the original series
   - Look for slowly decaying ACF (sign of non-stationarity)
   - Examine if autocorrelations fall within confidence bounds
   - Calculate and interpret sample autocorrelations

4. **Differencing Applications**
   - Apply first differencing (daily returns calculation)
   - Test stationarity of the first-differenced series
   - Apply second differencing if necessary (usually not needed for financial data)
   - Compare the effectiveness of different transformations

5. **Returns Analysis**
   - Calculate log returns: log(Pt) - log(Pt-1)
   - Test stationarity of log returns vs simple returns
   - Examine properties of return series (volatility clustering, etc.)
   - Compare stationarity test results for different return calculations

6. **Advanced Stationarity Analysis**
   - Test for structural breaks using Chow test
   - Apply rolling window stationarity tests
   - Examine sub-period stationarity (pre/post major economic events)
   - Test for cointegration with related currency pairs

### Expected Deliverables

1. **Technical Analysis Report**
   - Comprehensive Jupyter notebook with all stationarity tests
   - Clear documentation of methodology and assumptions
   - Statistical test results with proper interpretation
   - Code for reproducible analysis

2. **Visual Evidence Portfolio**
   - Time series plots of levels and differences
   - Rolling statistics plots showing stability/instability
   - ACF/PACF plots for original and transformed series
   - Q-Q plots and histogram comparisons

3. **Statistical Summary Table**
   ```
   Test Results Summary:
   -------------------
   Original Series:
   - ADF Test: [statistic, p-value, conclusion]
   - KPSS Test: [statistic, p-value, conclusion]
   - PP Test: [statistic, p-value, conclusion]
   
   First Differences (Returns):
   - ADF Test: [statistic, p-value, conclusion]
   - KPSS Test: [statistic, p-value, conclusion]
   - Ljung-Box Test: [statistic, p-value, conclusion]
   ```

4. **Business Recommendations**
   - Data transformation recommendations for modeling
   - Risk management implications of non-stationarity
   - Suggestions for model selection based on stationarity properties
   - Guidelines for ongoing monitoring of stationarity

### Sample Implementation Code
```python
from statsmodels.tsa.stattools import adfuller, kpss
from statsmodels.stats.diagnostic import acorr_ljungbox
import pandas as pd
import numpy as np

def check_stationarity(timeseries, title):
    # ADF Test
    adf_result = adfuller(timeseries)
    
    # KPSS Test  
    kpss_result = kpss(timeseries)
    
    print(f'Results for {title}:')
    print(f'ADF Statistic: {adf_result[0]:.6f}')
    print(f'ADF p-value: {adf_result[1]:.6f}')
    print(f'KPSS Statistic: {kpss_result[0]:.6f}')
    print(f'KPSS p-value: {kpss_result[1]:.6f}')
    
    return adf_result, kpss_result

# Apply to original series and differences
original_tests = check_stationarity(exchange_rates, "Original EUR/USD")
diff_tests = check_stationarity(exchange_rates.diff().dropna(), "First Differences")
```

### Expected Deliverables

1. **Technical Analysis Report**
   - Comprehensive Jupyter notebook with all stationarity tests
   - Clear documentation of methodology and assumptions
   - Statistical test results with proper interpretation
   - Code for reproducible analysis

2. **Business Recommendations**
   - Data transformation recommendations for modeling
   - Risk management implications of non-stationarity
   - Suggestions for model selection based on stationarity properties
   - Guidelines for ongoing monitoring of stationarity

## Assessment Criteria

Students should demonstrate:
- [ ] Correct application and interpretation of stationarity tests
- [ ] Understanding of the difference between ADF and KPSS test hypotheses
- [ ] Proper application of differencing techniques
- [ ] Ability to visually identify stationarity/non-stationarity
- [ ] Understanding of when and why to transform data
- [ ] Recognition of over-differencing problems
- [ ] Clear communication of test results and their implications
- [ ] Practical understanding of stationarity in financial contexts -->