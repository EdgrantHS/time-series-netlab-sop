<!-- # Topic 3: Trends and Seasonality Decomposition

Time series decomposition is the process of breaking down a time series into its constituent components: trend, seasonality, and residual (or irregular) components. Understanding these components is crucial for time series analysis as it helps identify underlying patterns and informs modeling decisions.

## Table of Contents

- [Topic 3: Trends and Seasonality Decomposition](#topic-3-trends-and-seasonality-decomposition)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Primary Resources](#primary-resources)
    - [Video Resources](#video-resources)
    - [Academic Resources](#academic-resources)
  - [Case Study: Retail Sales Analysis - E-commerce Company](#case-study-retail-sales-analysis---e-commerce-company)
    - [Scenario](#scenario)
    - [Dataset Description](#dataset-description)
    - [Analysis Tasks](#analysis-tasks)
    - [Expected Deliverables](#expected-deliverables)
    - [Sample Code Structure](#sample-code-structure)
    - [Expected Deliverables](#expected-deliverables-1)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to explain the following concepts:

- Time series decomposition (additive vs multiplicative)
- Trend, seasonality, and residual components
- Seasonal patterns and cyclical patterns
- Using statsmodels for decomposition
- Interpreting decomposition plots

## Learning Resources

### Primary Resources
- [Time Series Decomposition - statsmodels](https://www.statsmodels.org/dev/examples/notebooks/generated/tsa_decomposition.html)
- [Time Series Analysis: Seasonal Decomposition](https://otexts.com/fpp2/decomposition.html)
- [Python Time Series Decomposition](https://machinelearningmastery.com/decompose-time-series-data-trend-seasonality/)

### Video Resources
- [Time Series Decomposition Explained](https://www.youtube.com/watch?v=4R2xYJEZuBU)
- [Seasonal Decomposition in Python](https://www.youtube.com/watch?v=e8Yw4alG16Q)

### Academic Resources
- [Introduction to Time Series and Forecasting - Brockwell & Davis](https://link.springer.com/book/10.1007/978-3-319-29854-2)

## Case Study: Retail Sales Analysis - E-commerce Company

### Scenario
You work as a data analyst for an e-commerce company that sells seasonal products. The company has collected 3 years of daily sales data and wants to understand the underlying patterns to improve inventory management and sales forecasting. Your task is to decompose the sales time series and provide insights about trends and seasonal patterns.

### Dataset Description
```
Data: Daily sales revenue (in thousands USD)
Time Period: January 2021 - December 2023
Expected Patterns: 
- Annual seasonality (holiday shopping)
- Weekly seasonality (weekend vs weekday patterns)
- Potential growth trend
- Special events (Black Friday, Christmas, etc.)
```

### Analysis Tasks

1. **Data Preparation**
   - Load and clean the daily sales data
   - Handle any missing values or outliers
   - Create proper datetime index
   - Plot the raw time series to visually inspect patterns

2. **Trend Analysis**
   - Apply moving averages (7-day, 30-day) to identify trends
   - Use linear regression to quantify the overall growth trend
   - Identify any structural breaks or trend changes
   - Calculate trend component using different methods

3. **Seasonality Detection**
   - Perform seasonal decomposition using both additive and multiplicative models
   - Identify annual seasonal patterns (which months have highest/lowest sales)
   - Detect weekly seasonality (weekday vs weekend patterns)
   - Use autocorrelation plots to confirm seasonal periods

4. **Component Analysis**
   - Compare the magnitude of trend vs seasonal components
   - Analyze the residual component for remaining patterns
   - Identify any outliers or anomalies in the residuals
   - Calculate the proportion of variance explained by each component

5. **Business Insights**
   - Determine peak and off-peak selling periods
   - Quantify the growth rate of the business
   - Identify special events' impact on sales
   - Provide recommendations for inventory planning

### Expected Deliverables

1. **Technical Analysis**
   - Jupyter notebook with complete decomposition analysis
   - Visualization of original series and all components
   - Comparison of additive vs multiplicative models
   - Statistical measures of component strength

2. **Business Report** including:
   - Executive summary of key findings
   - Seasonal pattern description and business implications
   - Trend analysis and growth projections
   - Recommendations for business strategy

3. **Visualizations**
   - Time series plot with trend overlay
   - Seasonal decomposition plots
   - Seasonal subseries plots (monthly/weekly patterns)
   - Residual analysis plots

### Sample Code Structure
```python
# Import libraries
import pandas as pd
import matplotlib.pyplot as plt
from statsmodels.tsa.seasonal import seasonal_decompose
import seaborn as sns

# Load and prepare data
# ... data loading code ...

# Perform decomposition
decomposition_add = seasonal_decompose(sales_data, model='additive', period=365)
decomposition_mult = seasonal_decompose(sales_data, model='multiplicative', period=365)

# Visualize components
# ... plotting code ...

# Analyze residuals
# ... residual analysis ...
```

### Expected Deliverables

1. **Technical Analysis**
   - Jupyter notebook with complete decomposition analysis
   - Visualization of original series and all components
   - Comparison of additive vs multiplicative models
   - Statistical measures of component strength

2. **Business Report** including:
   - Executive summary of key findings
   - Seasonal pattern description and business implications
   - Trend analysis and growth projections
   - Recommendations for business strategy

## Assessment Criteria

Students should demonstrate:
- [ ] Correct implementation of seasonal decomposition
- [ ] Proper interpretation of trend and seasonal components
- [ ] Ability to choose appropriate decomposition model
- [ ] Clear visualization of time series components
- [ ] Translation of statistical findings into business insights
- [ ] Understanding of residual analysis and its importance -->