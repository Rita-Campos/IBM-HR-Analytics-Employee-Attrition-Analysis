 📊 IBM HR Analytics — Employee Attrition Analysis

![Feature Importance](outputs/feature_importance.png)

---

 📋 Project Overview

This project performs an end-to-end **exploratory and statistical analysis** of the IBM HR Analytics Employee Attrition dataset, available publicly on [Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset).

The central business question is:
> **What factors drive employee attrition at IBM, and can we predict which employees are likely to leave?**

This project was developed with the assistance of **Claude (Anthropic AI)** as a learning tool. All code was run, tested, and understood by me — I worked through each phase step by step, correcting errors, interpreting outputs, and making decisions about the analysis. Claude helped me structure the project, debug issues, and understand statistical concepts I was learning for the first time.

---

 🗂️ Project Structure

```
IBM HR Analytics & Employee Attrition/
├── Data/
│   └── WA_Fn-UseC_-HR-Employee-Attrition.csv
├── Notebooks/
│   ├── IBM_HR_Attrition_Project.ipynb
│   └── outputs/
│       ├── attrition_by_dept.png
│       ├── attrition_by_role.png
│       ├── salary_distribution.png
│       ├── correlation_heatmap.png
│       ├── satisfaction_boxplot.png
│       ├── overtime_attrition.png
│       ├── feature_importance.png
│       ├── confusion_matrix.png
│       ├── residuals.png
│       └── IBM_HR_Attrition_Report.xlsx
└── README.md
```

---

🎯 Objectives

- Load and explore the IBM HR dataset (1,470 employees, 35 variables)
- Perform exploratory data analysis (EDA) to identify attrition patterns
- Run statistical tests to validate findings
- Build regression models to understand what drives attrition
- Train a machine learning model to predict at-risk employees
- Export a formatted Excel report with all findings

---
 🛠️ Tools & Libraries

| Library | Purpose |
|---|---|
| `pandas` | Data loading, cleaning, and manipulation |
| `numpy` | Numerical calculations and array operations |
| `matplotlib` | Chart creation and customization |
| `seaborn` | Statistical visualizations |
| `scipy` | Statistical tests (t-test, chi-square, ANOVA) |
| `statsmodels` | Logistic and OLS regression with full summaries |
| `scikit-learn` | Random Forest model, train/test split, evaluation |
| `openpyxl` | Formatted Excel report generation |

---

 📊 Analysis Phases

 Phase 1 — Setup & Data Loading
- Loaded the dataset with pandas
- Encoded the target variable (`Attrition`: Yes→1, No→0)
- Dropped 4 constant columns with no analytical value

 Phase 2 — Exploratory Data Analysis
- Overall attrition rate: **16.1%** (237 out of 1,470 employees)
- Overtime workers leave at **3x the rate** of non-overtime workers (30.5% vs 10.4%)
- Sales department has the highest attrition by department
- Correlation analysis identified top numeric predictors of attrition

 Phase 3 — Statistical Testing
| Test | Variable | Result | P-Value |
|---|---|---|---|
| T-test | Salary vs Attrition | Significant ✅ | < 0.001 |
| Chi-square | Overtime vs Attrition | Significant ✅ | < 0.001 |
| Chi-square | Department vs Attrition | Significant ✅ | 0.0045 |
| ANOVA | Job Satisfaction across Depts | Not Significant ❌ | 0.6053 |

 Phase 4 — Regression Modelling
- **Logistic Regression** (statsmodels): Overtime is the strongest predictor (coef = +1.46, p < 0.001). Higher salary, satisfaction, work-life balance, tenure and age all significantly reduce attrition risk.
- **OLS Regression**: Job level and total working years are the strongest predictors of monthly income.
- **Residual analysis**: Q-Q plot confirms residuals are normally distributed — model assumptions met. 5 outliers identified and justified (experienced employees significantly underpaid).

 Phase 5 — Visualizations
6 professional charts covering:
- Attrition by department and job role
- Salary distribution by attrition outcome
- Full correlation heatmap
- Satisfaction scores comparison
- Overtime vs attrition impact

 Phase 6 — ML Prediction
- **Model:** Random Forest Classifier (200 trees, balanced class weights)
- **Accuracy:** 82% overall
- **Recall for leavers:** 28% — model correctly flags 13 out of 47 at-risk employees
- **Top predictors:** MonthlyIncome (0.137), Age (0.121), TotalWorkingYears (0.100)

---

 🔑 Key Findings

1. **Overtime is the single biggest cultural driver** — employees working overtime are 3x more likely to leave
2. **Salary matters most to the ML model** — MonthlyIncome is the #1 feature importance score (0.137)
3. **Younger, less experienced employees are the highest flight risk** — Age and TotalWorkingYears rank 2nd and 3rd
4. **Attrition is structural, not cultural** — satisfaction scores rank near the bottom of feature importance, while financial and demographic variables dominate
5. **5 outliers identified** — all share a pattern of experienced employees significantly underpaid for their seniority, two of whom left the company

---

 ⚠️ Model Limitations

- The dataset is imbalanced (84% stayed, 16% left) which limits recall on the minority class
- The model is best used as a **risk scoring tool** rather than a binary predictor
- Possible improvements: SMOTE oversampling, XGBoost, or lowering the classification threshold from 0.5 to 0.3

---

 🤖 AI Assistance Disclosure

This project was built with the support of **Claude by Anthropic** as a learning and guidance tool. Claude helped with:
- Structuring the project phases and choosing appropriate methods
- Explaining statistical concepts (ANOVA, chi-square, logistic regression, residuals)
- Debugging errors during development
- Suggesting professional chart styling and report formatting

All code was **executed, tested, and understood by me**. I corrected errors independently, interpreted all outputs, made analytical decisions, and can explain every part of this project. Claude served as a mentor and teacher throughout — similar to following a structured course with an interactive tutor.

---

 📁 Dataset

- **Source:** [IBM HR Analytics Employee Attrition — Kaggle](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **Size:** 1,470 employees, 35 variables
- **Missing values:** None
- **License:** Public domain / open for educational use

---

 👩‍💻 Author

**Rita Campos**
- GitHub: [github.com/Rita-Campos](https://github.com/Rita-Campos)
