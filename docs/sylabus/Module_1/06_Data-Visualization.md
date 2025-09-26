<!-- # Topic 6: Data Visualization for Time Series

Effective visualization is crucial for time series analysis as it helps identify patterns, trends, seasonality, outliers, and relationships that might not be apparent from summary statistics alone. This topic covers specialized plotting techniques for time series data using Python libraries like Matplotlib, Seaborn, and Plotly.

## Table of Contents

- [Topic 6: Data Visualization for Time Series](#topic-6-data-visualization-for-time-series)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Primary Resources](#primary-resources)
    - [Video Resources](#video-resources)
    - [Interactive Resources](#interactive-resources)
  - [Case Study: Energy Consumption Dashboard](#case-study-energy-consumption-dashboard)
    - [Scenario](#scenario)
    - [Dataset Description](#dataset-description)
    - [Visualization Tasks](#visualization-tasks)
    - [Expected Deliverables](#expected-deliverables)
    - [Sample Visualization Code](#sample-visualization-code)
    - [Expected Deliverables](#expected-deliverables-1)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to explain the following concepts:

- Time series specific visualization techniques
- Interactive dashboard creation with Plotly/Dash
- Seasonal plots and decomposition visualization
- Multi-series comparison techniques
- Best practices for time series visual design

## Learning Resources

### Primary Resources
- [Matplotlib Time Series Visualization](https://matplotlib.org/stable/gallery/recipes/common_date_problems.html)
- [Seaborn Time Series Plots](https://seaborn.pydata.org/tutorial/timeseries.html)
- [Plotly Time Series](https://plotly.com/python/time-series/)

### Video Resources
- [Time Series Visualization in Python](https://www.youtube.com/watch?v=8mrm1QhW8mE)
- [Advanced Matplotlib for Time Series](https://www.youtube.com/watch?v=3Xc3CA655Y4)

### Interactive Resources
- [Python Graph Gallery - Time Series](https://python-graph-gallery.com/time-series-plot/)
- [Plotly Dash Time Series Examples](https://dash.plotly.com/dash-core-components/graph)

## Case Study: Energy Consumption Dashboard

### Scenario
You are working for a smart city initiative that monitors electricity consumption patterns across different districts. The city has collected hourly electricity consumption data for residential, commercial, and industrial sectors over the past 2 years. Your task is to create a comprehensive visualization dashboard that helps city planners understand consumption patterns and make informed decisions about energy infrastructure.

### Dataset Description
```
Data: Hourly electricity consumption (MWh) by sector
Time Period: January 2022 - December 2023
Sectors: Residential, Commercial, Industrial
Granularity: Hourly measurements (17,520 data points per sector)
Expected Patterns:
- Daily cycles (higher consumption during day)
- Weekly patterns (different weekday vs weekend usage)
- Seasonal variations (heating/cooling demands)
- Special events and holidays impact
```

### Visualization Tasks

1. **Overview Visualizations**
   - Create a master time series plot showing all three sectors
   - Design a summary dashboard with key metrics
   - Build monthly and yearly aggregation views
   - Implement toggle functionality for different time granularities

2. **Pattern Analysis Plots**
   - Seasonal decomposition plots for each sector
   - Day-of-week consumption patterns (box plots or violin plots)
   - Hour-of-day consumption profiles (line plots by sector)
   - Monthly seasonal comparison plots (overlaying years)

3. **Comparative Analysis**
   - Sector-wise consumption share pie charts over time
   - Correlation heatmaps between sectors
   - Lag plots to identify relationships between sectors
   - Scatter plots of temperature vs consumption (if weather data available)

4. **Distribution and Anomaly Visualization**
   - Histograms and density plots of consumption by sector
   - Box plots identifying outliers and extreme consumption days
   - Calendar heatmaps showing consumption intensity
   - Rolling statistics plots (mean, std, min, max)

5. **Interactive Dashboard Elements**
   - Date range selectors for zooming into specific periods
   - Sector selection checkboxes
   - Hover tooltips with detailed information
   - Brushing and linking between related plots

6. **Advanced Visualizations**
   - 3D surface plots showing consumption by hour-of-day and day-of-year
   - Polar plots for cyclical patterns (24-hour, weekly cycles)
   - Small multiples showing consumption patterns by month
   - Animation showing consumption evolution over time

### Expected Deliverables

1. **Static Visualization Portfolio**
   - Collection of publication-ready matplotlib/seaborn plots
   - Each plot with proper titles, labels, and legends
   - Consistent color scheme and styling across all plots
   - Annotations highlighting key insights

2. **Interactive Dashboard**
   - Plotly Dash or Streamlit application
   - Multiple tabs or pages for different analysis aspects
   - User controls for data filtering and plot customization
   - Export functionality for reports

3. **Visualization Code Library**
   - Reusable functions for common time series plots
   - Custom styling and theme definitions
   - Automated report generation scripts
   - Documentation and examples for each visualization type

### Sample Visualization Code
```python
import matplotlib.pyplot as plt
import seaborn as sns
import plotly.express as px
import plotly.graph_objects as go
from plotly.subplots import make_subplots
import pandas as pd

# Set styling
plt.style.use('seaborn-v0_8-whitegrid')
sns.set_palette("husl")

# Basic time series plot
def plot_consumption_overview(df, sectors):
    fig, ax = plt.subplots(figsize=(15, 8))
    for sector in sectors:
        ax.plot(df.index, df[sector], label=sector, linewidth=1.5)
    
    ax.set_title('Electricity Consumption by Sector', fontsize=16, fontweight='bold')
    ax.set_xlabel('Date', fontsize=12)
    ax.set_ylabel('Consumption (MWh)', fontsize=12)
    ax.legend()
    ax.grid(True, alpha=0.3)
    
    return fig, ax

# Seasonal heatmap
def create_seasonal_heatmap(df, sector):
    # Reshape data for heatmap
    hourly_patterns = df.groupby([df.index.month, df.index.hour])[sector].mean().unstack()
    
    plt.figure(figsize=(12, 8))
    sns.heatmap(hourly_patterns, cmap='YlOrRd', cbar_kws={'label': 'Consumption (MWh)'})
    plt.title(f'{sector} Consumption Patterns by Month and Hour')
    plt.xlabel('Hour of Day')
    plt.ylabel('Month')
    
    return plt.gcf()

# Interactive plot with Plotly
def create_interactive_dashboard(df):
    fig = make_subplots(
        rows=2, cols=2,
        subplot_titles=('Time Series', 'Daily Patterns', 'Monthly Trends', 'Distribution'),
        specs=[[{"secondary_y": True}, {"type": "polar"}],
               [{"colspan": 2}, None]]
    )
    
    # Add traces for each sector
    for sector in df.columns:
        fig.add_trace(
            go.Scatter(x=df.index, y=df[sector], name=sector),
            row=1, col=1
        )
    
    fig.update_layout(height=800, showlegend=True)
    return fig
```

### Expected Deliverables

1. **Static Visualization Portfolio**
   - Collection of publication-ready matplotlib/seaborn plots
   - Each plot with proper titles, labels, and legends
   - Consistent color scheme and styling across all plots
   - Annotations highlighting key insights

2. **Interactive Dashboard**
   - Plotly Dash or Streamlit application
   - Multiple tabs or pages for different analysis aspects
   - User controls for data filtering and plot customization
   - Export functionality for reports

## Assessment Criteria

Students should demonstrate:
- [ ] Proficiency with matplotlib, seaborn, and plotly for time series
- [ ] Ability to choose appropriate visualization types for different purposes
- [ ] Creation of clear, informative, and aesthetically pleasing plots
- [ ] Implementation of interactive elements and user controls
- [ ] Understanding of visual design principles for data presentation
- [ ] Ability to identify patterns and insights through visualization
- [ ] Creation of comprehensive visualization documentation
- [ ] Integration of multiple visualization techniques in a cohesive dashboard -->