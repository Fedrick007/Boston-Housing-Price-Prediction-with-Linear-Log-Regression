# 🏠 Boston Housing Price Prediction with Linear & Log Regression

## 📌 Project Overview

This project analyzes housing prices in **Boston, Massachusetts (1970s)** using the classic **Boston Housing Dataset**.  
We build and evaluate **multivariable linear regression models**, diagnose model assumptions using **residual analysis**, improve performance with **log transformation**, and use the final model to **estimate property prices under different scenarios**.

The focus is not only prediction accuracy, but also **model interpretability, diagnostics, and real-world reasoning**.

---

## 🎯 Project Objectives

- Explore and understand the Boston housing dataset
- Build a multivariable linear regression model
- Evaluate coefficients and residuals
- Improve model performance using log transformation
- Compare training vs test (out-of-sample) performance
- Predict prices for hypothetical properties

---

## 🗂️ Dataset Description

- Observations: 506  
- Features: 13  
- Target: `PRICE` (Median house price in $1000s)

### Feature Summary

| Feature | Description |
|------|------------|
| CRIM | Per capita crime rate |
| ZN | Proportion of residential land zoned |
| INDUS | Proportion of non-retail business acres |
| CHAS | Near Charles River (1 = Yes, 0 = No) |
| NOX | Nitric oxide concentration (pollution) |
| RM | Average number of rooms |
| AGE | Proportion of old houses |
| DIS | Distance to employment centers |
| RAD | Highway accessibility |
| TAX | Property tax rate |
| PTRATIO | Students per teacher |
| B | Proportion of Black population |
| LSTAT | % lower-status population |
| PRICE | Median house price (target) |

---

## 🔍 Exploratory Data Analysis (EDA)

- Checked for missing values and duplicates
- Generated descriptive statistics
- Visualized distributions and relationships using Seaborn and Plotly

### Key Observations

- House prices are right-skewed
- Strong relationships observed with:
  - Number of rooms (`RM`)
  - Poverty level (`LSTAT`)
  - Pollution (`NOX`)

---

## 🧠 Model 1: Multivariable Linear Regression (Original PRICE)

### Model Formulation

PRICE = θ₀ + θ₁RM + θ₂NOX + θ₃DIS + … + θ₁₃LSTAT

### Steps

- Split data into 80% training and 20% testing
- Trained a linear regression model
- Evaluated coefficients and residuals

### Findings

- Residuals showed skewness and heteroscedasticity
- Model failed to generalize
- Test R² was **negative**, indicating very poor out-of-sample performance

---

## 🔁 Model Improvement: Log Transformation

### Motivation

Linear regression assumes:
- Symmetric errors
- Constant variance

The `PRICE` variable violated these assumptions.

### Solution

Apply a log transformation to the target:

log(PRICE) = θ₀ + θ₁RM + θ₂NOX + … + θ₁₃LSTAT

---

## 📊 Model 2: Regression with Log Prices

### Improvements Observed

- Reduced skewness
- Better-behaved residuals
- Improved interpretability (percentage effects)

### Out-of-Sample Performance

| Model | Test R² |
|----|--------|
| Original PRICE | −4.63 |
| Log(PRICE) | 0.74 |

➡️ The log-price model generalizes far better.

---

## 🔍 Coefficient Interpretation (Log Model)

With a log-transformed target:

- Coefficients represent approximate **percentage changes** in price.

Examples:
- RM (Rooms): Positive → More rooms increase price
- CHAS (River proximity): Positive → River-side houses are more valuable
- PTRATIO: Negative → Worse school quality lowers prices
- LSTAT: Strongly negative → Wealthier neighborhoods raise prices

---

## 🧪 Residual Analysis

- Residual mean close to 0
- Skewness closer to 0 after log transformation
- Residuals more randomly scattered

This confirms improved model assumptions.

---

## 🏡 Scenario-Based Property Valuation

### Average Property Baseline

Created a baseline house using **mean feature values**.

### Custom Property Scenario

Evaluated a property with:
- Next to the river
- 8 rooms
- Moderate distance to town
- High pollution (NOX at 75th percentile)
- Low poverty (LSTAT at 25th percentile)
- Moderate school crowding

Quantiles ensure realistic, data-driven inputs.

---

## 💰 Price Prediction

- Predicted log price using the trained log model
- Reversed transformation using `np.exp()`
- Obtained a realistic estimated property value

---

## 🧠 Key Learnings

- Regression assumptions matter
- Residual analysis is critical
- Log transformation can dramatically improve performance
- Test R² is the true measure of model quality
- Models should support reasoning, not just prediction

---

## 🛠️ Tools & Libraries

- Python
- Pandas, NumPy
- Seaborn, Matplotlib
- Plotly
- Scikit-learn

---

## 🚀 Conclusion

By transforming the target variable and validating assumptions, we converted a failing regression into a robust and interpretable model capable of realistic house price estimation.

This project demonstrates strong fundamentals in:
- Regression modeling
- Model evaluation
- Statistical reasoning
- Applied machine learning

---

## 🔮 Future Improvements

- Ridge and Lasso regression
- Polynomial features
- Cross-validation
- Feature scaling
- Deployment as a web application

---

## 👤 Author

Fedrick Samuek W - Software Engineer, Chennai, India.
