# Topic 1: Notebooks and Data Basics

This topic combines Python notebook setup with essential data importing and exploration using pandas.

## Table of Contents

- [Topic 1: Notebooks and Data Basics](#topic-1-notebooks-and-data-basics)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Python Installation](#python-installation)
    - [Python Notebooks](#python-notebooks)
    - [Data Handling with Pandas](#data-handling-with-pandas)
  - [Terms](#terms)
  - [Material Summary](#material-summary)
    - [Environment Setup](#environment-setup)
    - [Data Fundamentals with Pandas](#data-fundamentals-with-pandas)
    - [Documentation and Best Practices](#documentation-and-best-practices)
  - [Case Study: Complete Data Pipeline](#case-study-complete-data-pipeline)
    - [Task Requirements](#task-requirements)
    - [Expected Deliverables](#expected-deliverables)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to:

- Set up Python notebooks in VS Code or Google Colab
- Import data using pandas
- Use basic pandas operations (head, shape, info, describe)
- Create simple visualizations

## Learning Resources

### Python Installation

- Highly Suggested: [Python Installation for Windows](https://youtu.be/TNAu6DvB9Ng?si=cV-NjA3YsUMC8MSg)
  - It is suggested to install Python 3.12 because many libraries used in data science are compatible with this version.

### Python Notebooks

- Recommended: [Python Notebooks in VS Code](https://www.youtube.com/watch?v=DA6ZAHBPF1U)
- Optional: [Getting Started with Google Colab](https://www.youtube.com/watch?v=inN8seMm7UI)

### Data Handling with Pandas

- Optional (In-depth): [Python for Data Science - Cognitive Class](https://cognitiveclass.ai/courses/python-for-data-science)
- [Pandas 10 minutes tutorial](https://pandas.pydata.org/docs/user_guide/10min.html)
- [Basic Data Exploration with Pandas](https://www.youtube.com/watch?v=xi0vhXFPegw)

## Terms

- **Jupyter Notebook**: Cell-based interactive environment for running code in chunks
- **DataFrame**: 2D labeled data structure in pandas, like a spreadsheet
- **Pandas**: Python library for data manipulation and analysis
- **Missing Values (NaN)**: Absent or undefined data points
- **CSV**: Comma-Separated Values file format for tabular data

## Material Summary

This module covers the foundational skills needed for data science work:

### Environment Setup

**Python Installation Process:**

1. Download Python 3.12 from the [official website](https://www.python.org/ftp/python/3.12.7/python-3.12.7-amd64.exe)
2. Run the installer with "Add Python to PATH" option checked
3. Verify installation using command prompt: `python --version`
4. Install pip package manager (usually included with Python)
5. Test pip functionality: `pip --version`

**Notebook Environment Configuration:**

1. **VS Code Setup:**

   - Install VS Code from official website
   - Install Python extension from VS Code marketplace
   - Install Jupyter extension for notebook support
   - Create new `.ipynb` file to start working
   - Configure Python interpreter path
   - install necessary libraries using pip:
     ```bash
     pip install pandas numpy matplotlib seaborn jupyter
     ```

2. **Google Colab Alternative:**
   - Access https://colab.research.google.com
   - Sign in with Google account
   - Create new notebook from interface
   - Understand runtime limitations and GPU access
   - Learn file upload and download procedures
   - Install additional libraries using `!pip install package_name` in code cells
     - For example, to install pandas: `!pip install pandas numpy matplotlib seaborn`

### Data Fundamentals with Pandas

**Data Loading Workflow:**

1. Import necessary libraries:

   ```python
   import pandas as pd
   import numpy as np
   import matplotlib.pyplot as plt
   ```

2. Load CSV files:
   ```python
   # Basic CSV loading
   df = pd.read_csv('filename.csv')
   ```

**Essential Data Exploration Steps:**

1. **Initial Data Inspection:**

   ```python
   # View first 5 rows
   print(df.head())

   # View last 5 rows
   print(df.tail())

   # Get dimensions (rows, columns)
   print(f"Dataset shape: {df.shape}")

   # List all column names
   print(f"Columns: {df.columns.tolist()}")
   ```

2. **Data Quality Assessment:**

   ```python
   # Check data types and non-null counts
   print(df.info())

   # Count missing values per column
   print(df.isnull().sum())

   # Check percentage of missing values
   print((df.isnull().sum() / len(df)) * 100)

   # Examine data types in detail
   print(df.dtypes)
   ```

3. **Statistical Overview:**

   ```python
   # Generate statistical summary for numerical columns
   print(df.describe())

   # Count unique values for a specific column
   print(df['column_name'].value_counts())

   # Count unique values per column
   print(df.nunique())

   # Calculate correlation matrix
   correlation_matrix = df.corr()
   print(correlation_matrix)

   # Basic visualization
   df.hist(figsize=(12, 8))
   plt.show()
   ```

4. **Data Filtering and Selection:**

   ```python
   # Select specific columns
   subset = df[['column1', 'column2']]

   # Filter rows based on condition
   filtered_df = df[df['age'] > 30]

   # Multiple conditions
   filtered_df = df[(df['age'] > 30) & (df['survived'] == 1)]

   # Check unique values
   print(df['column_name'].unique())
   ```

### Documentation and Best Practices

**Notebook Organization:**

1. Use markdown cells for explanations and section headers
2. Add comments to code cells explaining logic
3. Use descriptive variable names
4. Organize code in logical sections
5. Include conclusions and insights in markdown

**Troubleshooting Common Issues:**

1. File path problems and working directory confusion
2. Missing library installations and import errors
3. Data encoding issues with special characters
4. Memory limitations with large datasets
5. Version compatibility between pandas and Python

This foundation prepares students for more advanced machine learning concepts in subsequent modules.

## Case Study: Complete Data Pipeline

### Task Requirements

**Setup:**

1. Choose VS Code or Google Colab for your environment
2. Create a new Python notebook

**Part A: Data Exploration with Titanic Dataset:**

1. Import the Titanic dataset from Kaggle: https://www.kaggle.com/c/titanic/data
2. Load the data using pandas
3. Explore the dataset structure:
   - Use `df.head()` to view first 5 rows
   - Use `df.shape` to see dimensions
   - Use `df.info()` to check data types and missing values
   - Use `df.describe()` for statistical summary

**Documentation:**

- Use markdown cells to document each step
- Explain what each operation reveals about the data
- Document preprocessing decisions and their rationale

### Expected Deliverables

- Working Python notebook
- Screenshots showing successful notebook setup
- Summary of data exploration findings

## Assessment Criteria

Students should demonstrate:

- [ ] Successful notebook environment setup
- [ ] Correct data import using pandas
- [ ] Proper use of pandas exploration methods (head, shape, info, describe)
- [ ] Basic visualization creation
