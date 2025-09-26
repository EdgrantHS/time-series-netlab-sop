# Topic 4: Autocorrelation Analysis

Autocorrelation analysis is a fundamental technique in time series analysis that measures how values in a time series are related to their own past values at different time lags. Understanding autocorrelation patterns helps identify the underlying structure of time series data and is crucial for model selection and forecasting.

## Table of Contents

- [Topic 4: Autocorrelation Analysis](#topic-4-autocorrelation-analysis)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Primary Resources](#primary-resources)
    - [Video Resources](#video-resources)
    - [Interactive Resources](#interactive-resources)
  - [Case Study: Website Traffic Pattern Analysis](#case-study-website-traffic-pattern-analysis)
    - [Scenario](#scenario)
    - [Dataset Description](#dataset-description)
    - [Analysis Tasks](#analysis-tasks)
    - [Expected Deliverables](#expected-deliverables)
    - [Sample Code Framework](#sample-code-framework)
    - [Expected Deliverables](#expected-deliverables-1)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to explain the following concepts:

- Autocorrelation Function (ACF) and Partial Autocorrelation Function (PACF)
- Lag and correlogram interpretation
- Statistical significance in autocorrelation
- Ljung-Box test for autocorrelation
- Pattern recognition for different time series processes

## Learning Resources

### Primary Resources
- [Autocorrelation - Penn State Statistics](https://online.stat.psu.edu/stat510/lesson/2/2.2)
- [Time Series Analysis - ACF and PACF](https://otexts.com/fpp2/acf.html)
- [Statsmodels ACF/PACF Documentation](https://www.statsmodels.org/dev/generated/statsmodels.tsa.stattools.acf.html)

### Video Resources
- [Autocorrelation and Partial Autocorrelation Explained](https://www.youtube.com/watch?v=DeORzP0go5I)
- [Understanding ACF and PACF Plots](https://www.youtube.com/watch?v=ZjaBn93YPWo)

### Interactive Resources
- [ACF and PACF Interactive Tutorial](https://www.mathworks.com/help/econ/autocorrelation-and-partial-autocorrelation.html)

## Case Study: Website Traffic Pattern Analysis

### Scenario
You are working for a news website that wants to understand patterns in their daily page views to optimize content scheduling and server resource allocation. The website has collected 2 years of daily traffic data, and you suspect there might be day-of-week patterns and other temporal dependencies. Your task is to perform a comprehensive autocorrelation analysis to uncover these patterns.

### Dataset Description
```
Data: Daily page views (in thousands)
Time Period: January 2022 - December 2023 (730 days)
Expected Patterns:
- Weekly seasonality (higher traffic on weekdays)
- Potential holiday effects
- Possible trending behavior
- Day-to-day correlation due to viral content
```

### Analysis Tasks

1. **Initial Data Exploration**
   - Load and visualize the daily traffic data
   - Check for obvious patterns, trends, and outliers
   - Create day-of-week and month labels for later analysis
   - Calculate basic statistics and identify any anomalies

2. **Autocorrelation Function Analysis**
   - Compute and plot ACF for up to 50 lags
   - Identify significant autocorrelation coefficients
   - Look for patterns indicating seasonality (peaks at lags 7, 14, 21, etc.)
   - Determine the maximum meaningful lag based on data length

3. **Partial Autocorrelation Function Analysis**
   - Compute and plot PACF for up to 30 lags
   - Compare PACF patterns with ACF patterns
   - Identify potential autoregressive order suggestions
   - Look for cut-off patterns that might indicate AR processes

4. **Seasonal Autocorrelation Analysis**
   - Focus on weekly patterns (lags 7, 14, 21, 28, ...)
   - Create seasonal ACF plots to highlight periodic patterns
   - Calculate autocorrelation for different days of the week separately
   - Examine if autocorrelation patterns change over time

5. **Statistical Testing**
   - Perform Ljung-Box test for different lag groups
   - Test for white noise hypothesis at various significance levels
   - Calculate confidence intervals for autocorrelation coefficients
   - Identify lags with statistically significant correlations

6. **Pattern Interpretation and Business Insights**
   - Interpret what the autocorrelation patterns mean for website traffic
   - Identify optimal content posting schedules based on patterns
   - Determine predictability horizon (how far ahead traffic can be predicted)
   - Provide recommendations for resource planning

### Expected Deliverables

1. **Technical Analysis Report**
   - Jupyter notebook with comprehensive autocorrelation analysis
   - ACF and PACF plots with proper interpretation
   - Statistical test results and significance testing
   - Code comments explaining each step of the analysis

2. **Visual Dashboard**
   - Combined ACF/PACF plots
   - Seasonal decomposition with autocorrelation analysis
   - Heatmap showing correlation patterns by day of week
   - Time series plot with highlighted high-correlation periods

3. **Business Recommendations Document**
   - Executive summary of key autocorrelation findings
   - Implications for content strategy and server planning
   - Suggested timing for major content releases
   - Recommendations for traffic forecasting approach

### Sample Code Framework
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from statsmodels.tsa.stattools import acf, pacf
from statsmodels.stats.diagnostic import acorr_ljungbox
import seaborn as sns

# Load and prepare data
# ... data loading code ...

# Compute ACF and PACF
acf_values, acf_confint = acf(traffic_data, nlags=50, alpha=0.05)
pacf_values, pacf_confint = pacf(traffic_data, nlags=30, alpha=0.05)

# Create plots
fig, (ax1, ax2) = plt.subplots(2, 1, figsize=(12, 8))
# ... plotting code ...

# Statistical testing
ljung_box_results = acorr_ljungbox(traffic_data, lags=10, return_df=True)
# ... testing code ...
```

### Expected Deliverables

1. **Technical Analysis Report**
   - Jupyter notebook with comprehensive autocorrelation analysis
   - ACF and PACF plots with proper interpretation
   - Statistical test results and significance testing
   - Code comments explaining each step of the analysis

2. **Business Recommendations Document**
   - Executive summary of key autocorrelation findings
   - Implications for content strategy and server planning
   - Suggested timing for major content releases
   - Recommendations for traffic forecasting approach

## Assessment Criteria

Students should demonstrate:
- [ ] Correct calculation and plotting of ACF and PACF
- [ ] Proper interpretation of autocorrelation patterns
- [ ] Understanding of statistical significance in autocorrelation
- [ ] Ability to identify seasonal patterns through correlation analysis
- [ ] Application of Ljung-Box test and other diagnostic tests
- [ ] Clear communication of findings and business implications
- [ ] Recognition of different time series process signatures in correlograms