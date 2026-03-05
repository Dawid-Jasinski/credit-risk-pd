# Credit Risk Modelling – Probability of Default (PD)

This repository contains a complete end‑to‑end project focused on developing a Probability of Default (PD) model using real‑world consumer credit data.  
The project follows a standard model development workflow used in banking: **exploratory analysis, data quality assessment, preprocessing, model estimation, evaluation, and interpretation**.

The work replicates procedures applied in credit risk departments, with emphasis on transparency, interpretability, and analytical rigor.

---

## 📘 Project Structure
credit-risk-pd/
│
├── data/
│   └── cs-training.csv
│
└── notebooks/
├── 01_eda.ipynb        # Exploratory Data Analysis
└── 02_model.ipynb      # Logistic Regression & Random Forest models

---

## 🎯 Objective

The goal of this project is to estimate PD (Probability of Default) in a 24‑month horizon based on:

- demographic information,
- income and indebtedness metrics,
- credit utilization,
- historical payment performance.

A binary target variable (`SeriousDlqin2yrs`) identifies whether a customer experienced **90+ days past due** within the next two years.

---

## 📊 Data Summary

- **150 000 observations**
- **11 predictor variables**
- Mix of demographic, behavioral, and financial attributes
- Target variable:  
  `1` – default in next 24 months  
  `0` – no default  

Key data challenges addressed in preprocessing:

- Missing values in income (~29.7k)
- Missing dependents (~3.9k)
- System-generated erroneous values (`98`) in delinquency variables
- Outliers in debt ratio and utilization measures

---

## 🛠️ Preprocessing

Performed according to credit risk modelling standards:

- Median imputation for `MonthlyIncome`
- Zero-imputation for `NumberOfDependents`
- Clipping `NumberOfTime…PastDue` variables to max value of 10  
  (to replace system code `98`)
- Removal of technical index column
- Consistent handling of outliers

All transformations are documented in `01_eda.ipynb`.

---

## 📈 Models

Two models were estimated:

### **1. Logistic Regression (baseline model)**
- Transparent and fully interpretable
- Industry-standard for PD modelling

**Performance:**
- **AUC:** 0.8145  
- **Gini:** 0.6289  

Key predictors (positive impact on PD):
- `NumberOfTimes90DaysLate`
- `NumberOfTime30-59DaysPastDueNotWorse`
- `NumberOfTime60-89DaysPastDueNotWorse`

Negative impact:
- `age`
- `NumberOfOpenCreditLinesAndLoans`  
- Financial variables show smaller influence.

---

### **2. Random Forest (alternative model)**

Used to assess potential improvement from non-linear modelling.

**Performance:**
- **AUC:** 0.8638  
- **Gini:** 0.7276  

Most important features:
- `RevolvingUtilizationOfUnsecuredLines`
- payment delinquency variables (90/60/30 days)
- `age` as a secondary predictor

Random Forest outperforms Logistic Regression but is less interpretable — a typical trade-off in credit risk.

---

## 📉 Evaluation

The models were assessed using:

- **ROC–AUC**
- **Gini coefficient**
- Classification matrix
- Coefficient analysis (LogReg)
- Feature importance (RF)

Notebooks contain visualizations:
- ROC curves
- Feature importance barplots

---

## 🏦 Key Business Insights

- Payment history is the strongest determinant of default risk.  
- High utilization of unsecured credit lines strongly correlates with elevated PD.  
- Older customers and those with established credit histories tend to show lower PD.  
- Non-linear models capture additional risk patterns not revealed by linear models.

---

## 📝 Technologies Used

- Python (Pandas, NumPy, Scikit-Learn, Matplotlib)
- Jupyter/VS Code
- GitHub

---

## 📄 Author

Project completed as part of a credit risk modelling portfolio by  
**Dawid Jasiński**  
Junior Data Analyst – econometrics & data analytics student

---

## 📂 Future Extensions

Possible next steps:

- Scorecard development (weight-of-evidence & binning)
- PD calibration
- Reject inference
- Stability and population drift analysis
- Model monitoring dashboard (Power BI)

---
