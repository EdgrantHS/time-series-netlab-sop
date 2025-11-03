# Topic 2: ML Fundamentals and Implementation

This comprehensive topic covers essential machine learning concepts, problem identification, and hands-on implementation of regression and classification algorithms.

## Table of Contents

- [Topic 2: ML Fundamentals and Implementation](#topic-2-ml-fundamentals-and-implementation)
  - [Table of Contents](#table-of-contents)
  - [Expected Knowledge](#expected-knowledge)
  - [Learning Resources](#learning-resources)
    - [Core ML Concepts](#core-ml-concepts)
    - [Supervised Learning Implementation](#supervised-learning-implementation)
  - [Terms](#terms)
  - [Material Summary](#material-summary)
    - [Machine Learning Fundamentals](#machine-learning-fundamentals)
    - [Supervised Learning Implementation](#supervised-learning-implementation-1)
    - [Model Interpretation and Best Practices](#model-interpretation-and-best-practices)
  - [Case Study](#case-study)
  - [Assessment Criteria](#assessment-criteria)

## Expected Knowledge

After this sub module, the student should be able to:

- Distinguish between supervised, unsupervised, and reinforcement learning
- Identify regression vs classification problems
- Understand training/validation/test splits and overfitting
- Implement linear regression using scikit-learn
- Understand classification models and their applications
- Calculate evaluation metrics (RMSE, R², accuracy, confusion matrix)

## Learning Resources

### Core ML Concepts

- Recommended: [Machine Learning Explained (15 min)](https://www.youtube.com/watch?v=ukzFI9rgwfU)
- Optional: [AI vs ML vs Deep Learning](https://www.youtube.com/watch?v=k2P_pHQDlp0)

### Supervised Learning Implementation

- Optional (In-depth): [Machine Learning with Python - Cognitive Class (Modules 1-3)](https://cognitiveclass.ai/courses/machine-learning-with-python)
- Recommended: [Linear Regression in 10 minutes](https://www.youtube.com/watch?v=nk2CQITm_eo)
- Recommended: [ Performance Metrics in Machine Learning Complete Guide](https://neptune.ai/blog/performance-metrics-in-machine-learning-complete-guide)
- [Scikit-learn User Guide](https://scikit-learn.org/stable/modules/linear_model.html#ordinary-least-squares)

## Terms

- **Machine Learning (ML)**: Algorithms that learn from data to make predictions
- **Supervised Learning**: Learning from labeled data to predict new outcomes
- **Regression**: Predicting continuous values (e.g., price, temperature)
- **Classification**: Predicting categories (e.g., spam/not spam)
- **Training Set**: Data used to train the model
- **Test Set**: Data used to evaluate model performance
- **Overfitting**: Model learns training data too well, performs poorly on new data
- **Feature**: Input variable used for prediction
- **Target**: Output variable to predict
- **Linear Regression**: Simplest regression algorithm
- **R-squared (R²)**: Metric measuring model fit (0-1, higher is better)
- **RMSE**: Root Mean Squared Error, measures prediction accuracy in same units as target
- **Scikit-learn**: Python library for machine learning

## Material Summary

This module covers essential machine learning concepts and practical implementation:

### Machine Learning Fundamentals

**Core ML Concepts:**
1. **Types of Machine Learning:**
   ```python
   # Supervised Learning Example
   from sklearn.linear_model import LinearRegression
   from sklearn.model_selection import train_test_split
   
   # Split data into features (X) and target (y)
   X = df[['feature1', 'feature2']]
   y = df['target']
   
   # Split into training and testing sets
   X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
   ```
   
   *This code demonstrates the basic structure of supervised learning: we have features (X) and a target (y), then split the data to train and evaluate our model.*

2. **Problem Type Identification:**
    - Regression problems (continuous output)
      - Examples: predicting house prices, stock prices, temperature
    - Classification problems (categorical output)
      - Examples: email spam detection, image recognition, medical diagnosis

### Supervised Learning Implementation

**Linear Regression Workflow:**
1. **Data Preparation:**
   ```python
   import pandas as pd
   import numpy as np
   from sklearn.linear_model import LinearRegression
   from sklearn.model_selection import train_test_split
   from sklearn.metrics import mean_squared_error, r2_score
   import matplotlib.pyplot as plt
   
   # Load and prepare data
   df = pd.read_csv('data.csv')
   X = df[['independent_variable']]  # Features (must be 2D)
   y = df['dependent_variable']      # Target (1D)
   ```
   
   *This code imports essential libraries and prepares data for machine learning. Note that features (X) must be 2D even for single variables, while the target (y) is 1D.*

2. **Model Training:**
   ```python
   # Split the data
   X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
   
   # Create and train the model
   model = LinearRegression()
   model.fit(X_train, y_train)
   
   # Get model parameters
   print(f"Coefficient: {model.coef_[0]}")
   print(f"Intercept: {model.intercept_}")
   ```
   
   *This code trains a linear regression model and displays the learned parameters. The coefficient shows how much the target changes per unit change in the feature, while the intercept is the y-axis starting point.*

3. **Model Evaluation:**
   ```python
   # Make predictions
   y_pred = model.predict(X_test)
   
   # Calculate evaluation metrics
   mse = mean_squared_error(y_test, y_pred)
   rmse = np.sqrt(mse)
   r2 = r2_score(y_test, y_pred)
   
   print(f"MSE: {mse:.2f}")
   print(f"RMSE: {rmse:.2f}")
   print(f"R²: {r2:.2f}")
   ```
   
   *This code evaluates model performance using three key metrics: MSE (penalty for large errors), RMSE (error in original units), and R² (percentage of variance explained).*

4. **Visualization:**
   ```python
   # Plot actual vs predicted
   plt.figure(figsize=(10, 6))
   plt.scatter(y_test, y_pred, alpha=0.7)
   plt.plot([y_test.min(), y_test.max()], [y_test.min(), y_test.max()], 'r--', lw=2)
   plt.xlabel('Actual Values')
   plt.ylabel('Predicted Values')
   plt.title('Actual vs Predicted Values')
   plt.show()
   
   # Plot regression line
   plt.figure(figsize=(10, 6))
   plt.scatter(X_test, y_test, alpha=0.7, label='Actual')
   plt.plot(X_test, y_pred, color='red', linewidth=2, label='Regression Line')
   plt.xlabel('Feature')
   plt.ylabel('Target')
   plt.legend()
   plt.title('Linear Regression Fit')
   plt.show()
   ```
   
   *These visualizations help assess model quality: the first plot shows how close predictions are to actual values (points near diagonal line = good), while the second shows how well the regression line fits the data.*

### Model Interpretation and Best Practices

**Understanding Results:**
1. **R² Score Interpretation:**
   - R² = 1.0: Perfect fit (rarely achieved in real data)
   - R² = 0.7-0.9: Good fit
   - R² = 0.5-0.7: Moderate fit
   - R² < 0.5: Poor fit, consider other models

2. **Common Pitfalls to Avoid:**
   ```python
   # Always check for linear relationship first
   plt.scatter(X, y)
   plt.show()
   
   # Check for outliers
   print(df.describe())
   
   # Ensure sufficient data
   print(f"Data points: {len(df)}")
   print(f"Features: {X.shape[1]}")
   ```
   
   *These checks help avoid common mistakes: scatter plots reveal if the relationship is actually linear, describe() identifies outliers, and data size checks ensure you have enough samples for reliable results.*

This foundation enables students to identify ML problems, implement basic algorithms, and interpret results effectively.

## Case Study

[This](./case_study/ML0101EN-Reg-Simple-Linear-Regression-Co2.ipynb) case study is based on the "Machine Learning with Python" course on Cognitive Class. The lab notebook provided in the course will be used as a foundation, students are free to extend and enhance it.

## Assessment Criteria

Students should demonstrate:

- [ ] Correct identification of supervised vs unsupervised problems
- [ ] Proper distinction between regression and classification tasks
- [ ] Understanding of linear regression implementation and evaluation
- [ ] Ability to interpret R² scores and RMSE