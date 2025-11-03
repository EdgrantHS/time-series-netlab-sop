<!-- # Topic 2: Data Exploration Basics

Data exploration is the initial step in any data analysis project where we examine, clean, and understand the structure and characteristics of our dataset. For time series data, this involves understanding temporal patterns, missing values, data distribution, and basic statistical properties that will guide our subsequent analysis.

## Table of Contents

- [Topic 2: Data Exploration Basics](#topic-2-data-exploration-basics)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Primary Resources](#primary-resources)
    - [Video Resources](#video-resources)
    - [Interactive Resources](#interactive-resources)
  - [Case Study: Exploring Stock Market Data](#case-study-exploring-stock-market-data)
    - [Scenario](#scenario)
    - [Dataset Description](#dataset-description)
    - [Analysis Tasks](#analysis-tasks)
    - [Expected Deliverables](#expected-deliverables)
    - [Expected Deliverables](#expected-deliverables-1)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to explain the following concepts:

- Exploratory Data Analysis (EDA)
- Data profiling and summary statistics
- Missing data patterns in time series
- Data quality assessment techniques
- Basic pandas operations for time series

## Learning Resources

### Primary Resources
- [Pandas Documentation - Getting Started](https://pandas.pydata.org/docs/getting_started/index.html)
- [Python for Data Analysis by Wes McKinney - Chapter 5](https://wesmckinney.com/book/getting-started.html)
- [Time Series Analysis in Python](https://www.machinelearningplus.com/time-series/time-series-analysis-python/)

### Video Resources
- [Exploratory Data Analysis with Pandas](https://www.youtube.com/watch?v=xi0vhXFPegw)
- [Time Series EDA in Python](https://www.youtube.com/watch?v=e8Yw4alG16Q)

### Interactive Resources
- [Kaggle Learn: Data Exploration](https://www.kaggle.com/learn/data-exploration)

## Case Study: Exploring Stock Market Data

### Scenario
You have been provided with a dataset containing daily stock prices for Apple (AAPL) from 2020 to 2023. The dataset includes columns for Date, Open, High, Low, Close, Volume, and Adjusted Close. Your task is to perform a comprehensive exploratory data analysis to understand the characteristics of this time series data.

### Dataset Description
```
Columns: Date, Open, High, Low, Close, Volume, Adj_Close
Shape: ~1000 rows x 7 columns
Time Period: 2020-01-01 to 2023-12-31
Frequency: Daily (business days only)
```

### Analysis Tasks

1. **Data Structure Analysis**
   - Load the data and examine its structure
   - Check data types and convert Date column to datetime if needed
   - Identify the date range and frequency of the data
   - Check for any missing dates or values

2. **Summary Statistics**
   - Generate descriptive statistics for all numeric columns
   - Calculate daily returns (percentage change in closing price)
   - Identify the days with highest and lowest trading volumes
   - Find the maximum daily price range (High - Low)

3. **Data Quality Assessment**
   - Check for missing values and their patterns
   - Identify potential outliers using IQR method
   - Validate that High ≥ Open, Close and Low ≤ Open, Close
   - Ensure Volume values are non-negative

4. **Temporal Pattern Identification**
   - Plot closing prices over time
   - Calculate monthly average returns
   - Identify any obvious trends or seasonal patterns
   - Check for data gaps (missing trading days)

### Expected Deliverables

1. **Jupyter Notebook** with complete EDA containing:
   - Code cells with proper comments
   - Markdown cells explaining findings
   - Summary statistics tables
   - Basic visualizations (line plots, histograms)

2. **Summary Report** (markdown cell) including:
   - Key characteristics of the dataset
   - Data quality issues identified
   - Preliminary observations about price patterns
   - Recommendations for data preprocessing

### Expected Deliverables

1. **Jupyter Notebook** with complete EDA containing:
   - Code cells with proper comments
   - Markdown cells explaining findings
   - Summary statistics tables
   - Basic visualizations (line plots, histograms)

2. **Summary Report** including:
   - Key characteristics of the dataset
   - Data quality issues identified
   - Preliminary observations about price patterns
   - Recommendations for data preprocessing

## Assessment Criteria

Students should demonstrate:
- [ ] Proper use of pandas for data exploration
- [ ] Accurate calculation of summary statistics
- [ ] Identification of data quality issues
- [ ] Clear documentation of findings
- [ ] Basic understanding of financial time series characteristics -->