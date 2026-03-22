# Credit Risk Modelling – Probability of Default (PD)

Author: Dawid Jasiński 
---
Technologies: Python, pandas, numpy, scikit-learn
---
Source: kaggle.com
---
## 🧠 Project Overview

This project focuses on predicting the probability of default using machine learning models. The analysis compares a Logistic Regression model with a Random Forest classifier to evaluate differences in predictive performance and practical usefulness in a credit risk context.

## 📁 Repository Structure
```
/notebooks
   credit-risk-pd.ipynb
/data
   cs-training.csv
/report
   report_credit-risk-pd.html
   report_credit-risk-pd.pdf
```

## 🎯 Objective

The main goal is to identify borrowers who are likely to default and evaluate models not only statistically, but also from a business perspective, where different types of errors have different costs.

## 📂 Dataset

The dataset contains borrower-level financial and behavioral variables such as:

Income
Credit utilization
Debt-related metrics
Delinquency history (late payments)

Target variable:

default (1 = default, 0 = non-default)

The dataset is imbalanced, with approximately 6–7% defaults.

## ⚙️ Models
Logistic Regression
Used as a baseline model
Interpretable and widely applied in credit risk
Random Forest
Ensemble model capturing non-linear relationships
Used to improve predictive performance
## 📏 Evaluation Metrics

To properly evaluate model performance on imbalanced data, the following metrics were used:

AUC (Area Under ROC Curve)
Gini coefficient (calculated as: Gini = 2 × AUC − 1)
Confusion Matrix
## 📊 Results

Logistic Regression
- AUC: ~0.81
- Gini: ~0.62

Random Forest
- AUC: ~0.864
- Gini: ~0.727

The Random Forest model outperforms Logistic Regression in terms of predictive accuracy.

## 🔍 Confusion Matrix Analysis

A key part of the analysis focuses on the business implications of classification errors:

False Negatives (FN): actual defaulters predicted as non-defaulters
False Positives (FP): non-defaulters predicted as defaulters

The Random Forest model significantly reduces the number of False Negatives compared to Logistic Regression, meaning it is more effective at identifying risky clients.

From a business perspective:

Missing a defaulter (FN) is more costly than rejecting a good client (FP)
Therefore, reducing FN is a priority
## 🔍 Feature Importance

The most important predictors in the Random Forest model include:

Delinquency-related variables (late payments)
Credit utilization

These variables have the strongest influence on default prediction.

## 📌 Key Takeaways
Random Forest provides better predictive performance than Logistic Regression
AUC and Gini are appropriate metrics for imbalanced classification problems
Model evaluation should consider business costs, not only statistical accuracy
Reducing False Negatives is critical in credit risk modeling

