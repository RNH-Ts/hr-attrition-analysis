# HR Attrition Analysis & Prediction  
**Rachel Hill-Tsarpelas** | Data Analyst Portfolio Project  
Date: 2025-12

## Project Overview
This project investigates employee attrition with the goal of identifying patterns, risk factors, and actionable insights that can support HR decision-making. The analysis follows a structured, multi-day workflow covering data understanding, visualization-driven exploration, and machine learning modeling.

The project is intentionally built step by step to reflect a realistic data analysis process:  
from understanding the business problem, through exploratory analysis, to predictive modeling and finally to key takeaways presented in a dashboard.

---

## Business Problem
Employee attrition represents a significant cost and organizational challenge.  
The objective of this project is to understand **why employees leave**, **which factors are most strongly associated with attrition**, and **how data-driven insights can support targeted retention strategies**.

---

## Dataset
The dataset consists of anonymized HR data including:  
- Demographics (Age, MaritalStatus, etc.)  
- Job and career variables (JobLevel, JobRole, TotalWorkingYears, YearsAtCompany)  
- Compensation (MonthlyIncome)  
- Work conditions (OverTime, WorkLifeBalance)  
- Attrition (target variable)  

1470 rows and 35 columns  

Kaggle: [IBM HR Analytics Attrition Dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data)

---

## Tools & Technologies
- **Python**  
  - pandas  
  - numpy  
  - matplotlib  
  - seaborn  
  - scikit-learn  
- **Jupyter Notebook**  
- **Power BI** 

---

## Project Structure & Notebooks

### Day 1 — Data Overview & Problem Understanding  
**Notebook:** `01_HR_Retention_Overview.ipynb`

**Objective:**  
Establish a high-level understanding of the HR attrition dataset and identify variables that are plausibly related to employee turnover.

**Key Findings:**  
- The dataset is clean, structured, and requires minimal preprocessing  
- Employee attrition is a **minority class (~16%)**, which will need to be addressed during modeling  
- Features naturally group into interpretable domains:  
  - **Career stage:** Age, JobLevel, TotalWorkingYears  
  - **Compensation:** MonthlyIncome  
  - **Work conditions:** OverTime, WorkLifeBalance  
- Several features are **highly correlated** (e.g., JobLevel, Income, Experience), which has implications for interpretation later  
- Some numerically encoded variables (e.g., Education, WorkLifeBalance) are categorical in nature and will be treated accordingly  

This notebook establishes **which variables are plausible drivers**, without making claims about importance yet.

---

### Day 2 — Exploratory Data Analysis & Visual Patterns  
**Notebook:** `02_HR_Retention_Visualizations.ipynb`

**Objective:**  
Use exploratory visualizations to identify patterns and group-level differences associated with employee attrition.

**Key Observations:**  
- Attrition rates are visibly higher among employees who:  
  - Work overtime  
  - Are younger or at earlier career stages  
  - Belong to certain job roles (Sales) and not the department with the most overall employees (Research & Development)  
- Lower job satisfaction is associated with higher observed attrition  
- Linear correlation analysis does not reveal strong relationships with attrition, suggesting that:  
  - Key effects are likely non-linear  
  - Relationships may depend on combinations of features rather than individual variables  

At this stage, the analysis highlights where attrition appears in the data, while indicating that more expressive models are required to understand the underlying drivers.

---

### Day 3 — Machine Learning & Feature Importance  
**Notebook:** `03_HR_Retention_ML.ipynb`

**Objective:**  
Evaluate multiple machine learning models for employee attrition and identify which factors remain important once multivariate and non-linear relationships are learned

**Modeling Summary:**  
- Three models were trained and compared: Logistic Regression, Decision Tree, and Random Forest  
- Performance was evaluated using accuracy, precision, recall, and F1 score for the attrition class  
- Random Forest achieved the strongest overall performance, with the highest accuracy, precision, and F1 score  
- Logistic Regression showed higher recall for attrition, indicating better sensitivity but weaker overall balance  
- Decision Tree underperformed relative to the other models

**Feature Signals Across Models:**  
- Linear correlation analysis shows no strong relationships with attrition, reinforcing earlier findings that attrition is not driven by simple linear effects  
- Feature importance varies by model, reflecting differences in how each method captures structure in the data  
- In the Random Forest model specifically:  
  - **WorkLifeStress** and **OverTime** appear among the most influential predictors  
  - Compensation-related features (e.g., MonthlyIncome, Income per Experience) also rank highly despite weak linear correlations  
- Several variables that appeared visually salient during EDA contribute less consistently once modeled jointly

This notebook highlights that attrition drivers are **model-dependent and non-linear**, and that no single feature dominates across all analytical perspectives.

---

## Key Takeaways
- Attrition patterns differ depending on whether they are examined visually, via correlation, or through predictive modeling  
- Random Forest surfaces workload- and compensation-related features more strongly than linear models  
- Correlation analysis alone is insufficient for identifying attrition drivers in this dataset  
- Model choice materially affects how attrition risk is interpreted

---

## EDA vs. Machine Learning Perspective
A key outcome of this project is the distinction between **visual intuition** and **model-based evidence**.

- Exploratory visualizations highlight departments, roles, and demographic groups because these are easy to compare visually  
- However, machine learning results show that many of these apparent effects are absorbed by variables related to:  
  - Workload (OverTime, WorkLifeStress)  
  - Compensation  
  - Career stage  

Once these factors are accounted for, several demographic and organizational variables lose predictive importance.  

This comparison demonstrates why attrition analysis cannot rely on dashboards alone:  
**strong-looking visual patterns do not necessarily translate into predictive or explanatory importance.**

---

## Power BI Dashboard (Planned)
The Power BI dashboard will be designed to reflect this distinction between EDA and machine learning findings.

**Dashboard design principles:**  
- Workload and career-stage indicators presented as primary drivers  
- Departmental and demographic views provided as contextual filters, not root causes  
- Clear separation between:  
  - Variables that appear important visually  
  - Variables confirmed through predictive modeling  

This section will be updated once the Power BI dashboard is finalized.

---

## Model Performance

| Model              | Accuracy | Precision (Attrition) | Recall (Attrition) | F1 (Attrition) |
|-------------------|---------|----------------------|------------------|----------------|
| Decision Tree      | 0.75    | 0.34                 | 0.60             | 0.43           |
| Logistic Regression| 0.74    | 0.35                 | 0.68             | 0.46           |
| Random Forest      | 0.82    | 0.44                 | 0.55             | 0.49           |

---

## Key Insights

- **WorkLifeStress** and **OverTime** are the strongest predictors of attrition in Random Forest  
- Low compensation relative to experience (**Income per Experience**) can drive turnover  
- Certain roles (e.g., Sales) and frequent business travel show elevated attrition risk  
- EDA-only patterns (department, age, marital status) appear visually strong but are less predictive once workload and compensation are accounted for

---

## Business Recommendations (Planned)

- Provide workload support or manage overtime for high-risk employees  
- Review compensation structures to align pay with experience and role  
- Focus retention efforts on high-risk roles and employees with elevated WorkLifeStress  
- Use dashboards to monitor attrition risk dynamically across departments and job roles




