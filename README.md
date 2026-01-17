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
The objective of this project is to understand why employees leave, which factors are most strongly associated with attrition, and how data-driven insights can support targeted retention strategies.

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

### Part 1 — Data Overview & Problem Understanding  
**Notebook:** `01_HR_Retention_Overview.ipynb`

**Objective:**  
Establish a high-level understanding of the HR attrition dataset and identify variables that are plausibly related to employee turnover.

**Key Findings:**  
- The dataset is clean, structured, and requires minimal preprocessing  
- Employee attrition is a minority class (~16%), which will need to be addressed during modeling  
- Features naturally group into interpretable domains:  
  - Career stage: Age, JobLevel, TotalWorkingYears  
  - Compensation: MonthlyIncome  
  - Work conditions: OverTime, WorkLifeBalance  
- Several features are highly correlated (e.g., JobLevel, Income, Experience), which has implications for interpretation later  
- Some numerically encoded variables (e.g., Education, WorkLifeBalance) are categorical in nature and will be treated accordingly  

This notebook establishes which variables are plausible drivers, without making claims about importance yet.

---

### Part 2 — Exploratory Data Analysis & Visual Patterns  
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

### Part 3 — Machine Learning & Feature Importance  
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
  - WorkLifeStress and OverTime appear among the most influential predictors  
  - Compensation-related features (e.g., MonthlyIncome, Income per Experience) also rank highly despite weak linear correlations  
-  EDA-only patterns (department, age, marital status) appear visually strong but are less predictive once modeled jointly

This notebook highlights that attrition drivers are model-dependent and non-linear, and that no single feature dominates across all analytical perspectives.

---
## Model Performance

| Model              | Accuracy | Precision (Attrition) | Recall (Attrition) | F1 (Attrition) |
|-------------------|---------|----------------------|------------------|----------------|
| Decision Tree      | 0.75    | 0.34                 | 0.60             | 0.43           |
| Logistic Regression| 0.74    | 0.35                 | 0.68             | 0.46           |
| Random Forest      | 0.82    | 0.44                 | 0.55             | 0.49           |

---
## Key Takeaways
- Attrition patterns differ depending on whether they are examined visually, via correlation, or through predictive modeling  
- Random Forest highlights work-life stress and overtime as key attrition drivers more strongly than linear models, signaling where HR should focus retention efforts. 
- Correlation analysis alone is insufficient for identifying attrition drivers in this dataset  
- Model choice materially affects how attrition risk is interpreted

---

## EDA vs. Machine Learning Perspective
A key outcome of this project is the distinction between visual intuition and model-based evidence.

- Exploratory visualizations highlight departments, roles, and demographic groups because these are easy to compare visually  
- However, machine learning results show that many of these apparent effects are absorbed by variables related to:  
  - Workload (OverTime, WorkLifeStress)  
  - Compensation  
  - Career stage  

Once these factors are accounted for, several demographic and organizational variables lose predictive importance.  

This comparison demonstrates why attrition analysis cannot rely on dashboards alone:  
- strong-looking visual patterns do not necessarily translate into predictive importance.

The Power BI dashboard reflects this distinction by treating departments and demographics as contextual filters, while positioning workload and stress as primary explanatory drivers.

---

## Power BI Dashboard — Operationalizing Attrition Risk

### Objective

While the Python notebooks focus on exploratory analysis, feature relationships, and predictive modeling, the Power BI dashboard is designed to operationalize those findings. It answers the critical question:  

> **Where should HR focus attention to reduce attrition risk?**

---

### Design Principles

The interactive dashboard moves beyond replicating EDA charts. Its design focuses on:

- Attrition rates rather than raw counts
- Workload, stress, and compensation — the strongest predictors from machine learning models
- Risk concentration over averages
- Dynamic visuals and KPIs for slicers such as gender and job role

---

### Key Visuals and Interactions

- **KPIs**:  
  - **Total Employees**
  - **Attrition Rate** (filtered by role, department, etc.)
  - **Average Work-Life Stress** (filtered)

- **Bar + Line Combo**:  
  - Job Role → Total Employees + Attrition Rate  
  This chart shows the relationship between job roles, total employees, and their attrition rates, enabling HR to prioritize roles with both high attrition and significant workforce size.

- **Scatter Plot**:  
  - Monthly Income vs WorkLifeStress → Attrition size  
  This plot highlights the interaction between income, stress levels, and attrition. The **bubble size** represents the number of employees in each point, and the **color** denotes stress bands.

- **Stress Band**:  
  A bar chart showing total attrition by stress levels. This visual emphasizes the non-linear relationship between stress and attrition, where higher stress levels are linked to a sharp increase in attrition risk.

- **Small Multiples**:  
  A marital status bar chart, providing a breakdown of attrition rates by marital status across various filters.

- **Department × Overtime Attrition Matrix**:  
  A heatmap visualizing the interaction between department and overtime, highlighting areas with both high overtime and high attrition.

---

### Data Preparation & Measures

Data was prepared using Power Query to ensure consistent formatting, readable labels, and stable inputs for analysis. Columns were cleaned and standardized, and derived fields such as stress level groupings were created to support clearer visual interpretation.

Key metrics (e.g. Attrition Rate, Average Work-Life Stress) were implemented as dynamic measures, allowing all visuals and KPIs to respond consistently to filters such as job role, department, and gender.

The data model was intentionally kept simple to prioritize clarity and interpretability for HR users, ensuring that insights remain transparent and easy to explore rather than obscured by unnecessary structural complexity.

---

### Visualization Design & Business Goals

The dashboard design integrates insights from exploratory data analysis (EDA) and machine learning (ML) models to provide actionable HR insights. It focuses on identifying where attrition risk is highest and guiding targeted retention efforts.

- **Stress Levels by Department**: Initial donut visuals showed uniform stress levels across departments. However, combining compensation, job roles, and overtime highlighted stress as a critical driver when these factors interact.

- **Compensation vs. Stress Scatter Plot**: This visual illustrates once more the non-linear relationship between these three most significant factors. Higher attrition correlates with higher stress and either low or high compensation, reflecting the ML model’s findings.

- **Role in EDA**: *Sales roles were flagged as high-risk in EDA, even though ML didn’t prioritize them. They are included as contextual filters to enable deeper exploration by HR.

### How Visuals Support HR Decision-Making
The visuals are designed to help HR prioritize areas for intervention:
- High-Risk Roles & Departments: The scatter plot and stress band show that high stress and low compensation drive attrition, enabling HR to target retention strategies based on these insights.
- Tailored Retention Strategies: Slicers (e.g., gender, job role) enable HR to drill down into specific demographics, helping tailor retention strategies based on stress or compensation disparities.
- The job role attrition chart helps HR prioritize roles with both high attrition and large headcounts, ensuring retention efforts are impactful.

This ensures the dashboard directly supports data-driven HR decision-making.

---

### Summary & Key Takeaways

The Power BI dashboard serves as an interactive tool to operationalize the findings from EDA and machine learning. It answers the critical question:  
> **Where should HR focus attention to reduce attrition risk?**

- **Key Insights**:  
  - Focus on workload (overtime), stress, and compensation as primary drivers of attrition risk.
  - Use contextual slicers (e.g., role, department, gender) to fine-tune retention strategies.
  - Prioritize high-risk job roles and departments with elevated attrition.

This makes the dashboard a dynamic decision-support tool for HR, guiding them in identifying and addressing attrition hotspots effectively.

---

## Lessons Learned

1. **Scaling Issues**:  
   During preprocessing, I initially scaled features in the wrong order, which affected the results. After identifying this, I corrected the scaling order in the pipeline, ensuring the models could learn from the data correctly.

2. **Handling Missing Data (NAs)**:  
   A divide-by-zero error introduced unexpected `NaN` values in certain columns. I handled this by implementing checks to avoid division by zero in the pipeline, ensuring no missing data affected the model.

3. **Data Cleaning Limitations**:  
   While the data was cleaned for the purpose of this analysis, it was artificially pre-processed before being imported. Although this was necessary for quick analysis, it did not showcase my full data cleaning capabilities, which could have been demonstrated with more involved preprocessing.

---

**Actionable HR Implications**  

- **Overtime-focused interventions**: Use the dashboard to identify roles and teams where overtime coincides with high attrition. Prioritize workload rebalancing or overtime caps in these areas.
- **Targeted work–life stress mitigation**: Direct retention programs toward employees and roles exhibiting high work–life stress.
- **Headcount-adjusted prioritization**: Focus retention efforts on roles with high attrition rates and large employee populations.
- **Role-specific retention strategies**: Treat Sales and HR roles as priority segments for intervention. Tailor actions by gender or role.
- **Monitoring early warning signals**: Track overtime and stress levels over time to see if retention efforts are having an impact.


# HR Attrition Analysis & Prediction  
**Rachel Hill-Tsarpelas** | Data Analyst Portfolio Project  
Date: 2025-12.

## Project Overview
This project investigates employee attrition with the goal of identifying patterns, risk factors, and actionable insights that can support HR decision-making. The analysis follows a structured, multi-day workflow covering data understanding, visualization-driven exploration, and machine learning modeling.

The project is intentionally built step by step to reflect a realistic data analysis process:  
from understanding the business problem, through exploratory analysis, to predictive modeling and finally to key takeaways presented in a dashboard.

---

## Business Problem
Employee attrition represents a significant cost and organizational challenge.  
The objective of this project is to understand why employees leave, which factors are most strongly associated with attrition, and how data-driven insights can support targeted retention strategies.

---

## Dataset
The dataset consists of anonymized HR data including:  
- Demographics (Age, MaritalStatus, etc.).  
- Job and career variables (JobLevel, JobRole, TotalWorkingYears, YearsAtCompany).  
- Compensation (MonthlyIncome).  
- Work conditions (OverTime, WorkLifeBalance).  
- Attrition (target variable).  

1470 rows and 35 columns.

Kaggle: [IBM HR Analytics Attrition Dataset](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data).

---

## Tools & Technologies
- **Python**  
  - pandas  
  - numpy  
  - matplotlib  
  - seaborn  
  - scikit-learn  
- **Jupyter Notebook**  
- **Power BI**.

---

## Project Structure & Notebooks

### Part 1 — Data Overview & Problem Understanding  
**Notebook:** `01_HR_Retention_Overview.ipynb`.

**Objective:**  
Establish a high-level understanding of the HR attrition dataset and identify variables that are plausibly related to employee turnover.

**Key Findings:**  
- The dataset is clean, structured, and requires minimal preprocessing.  
- Employee attrition is a minority class (~16%), which will need to be addressed during modeling.  
- Features naturally group into interpretable domains:  
  - Career stage: Age, JobLevel, TotalWorkingYears.  
  - Compensation: MonthlyIncome.  
  - Work conditions: OverTime, WorkLifeBalance.  
- Several features are highly correlated (e.g., JobLevel, Income, Experience), which has implications for interpretation later.  
- Some numerically encoded variables (e.g., Education, WorkLifeBalance) are categorical in nature and will be treated accordingly.  

This notebook establishes which variables are plausible drivers, without making claims about importance yet.

---

### Part 2 — Exploratory Data Analysis & Visual Patterns  
**Notebook:** `02_HR_Retention_Visualizations.ipynb`.

**Objective:**  
Use exploratory visualizations to identify patterns and group-level differences associated with employee attrition.

**Key Observations:**  
- Attrition rates are visibly higher among employees who:  
  - Work overtime.  
  - Are younger or at earlier career stages.  
  - Belong to certain job roles (Sales) and not the department with the most overall employees (Research & Development).  
- Lower job satisfaction is associated with higher observed attrition.  
- Linear correlation analysis does not reveal strong relationships with attrition, suggesting that:  
  - Key effects are likely non-linear.  
  - Relationships may depend on combinations of features rather than individual variables.  

At this stage, the analysis highlights where attrition appears in the data, while indicating that more expressive models are required to understand the underlying drivers.

---

### Part 3 — Machine Learning & Feature Importance  
**Notebook:** `03_HR_Retention_ML.ipynb`.

**Objective:**  
Evaluate multiple machine learning models for employee attrition and identify which factors remain important once multivariate and non-linear relationships are learned.

**Modeling Summary:**  
- Three models were trained and compared: Logistic Regression, Decision Tree, and Random Forest.  
- Performance was evaluated using accuracy, precision, recall, and F1 score for the attrition class.  
- Random Forest achieved the strongest overall performance, with the highest accuracy, precision, and F1 score.  
- Logistic Regression showed higher recall for attrition, indicating better sensitivity but weaker overall balance.  
- Decision Tree underperformed relative to the other models.

**Feature Signals Across Models:**  
- Linear correlation analysis shows no strong relationships with attrition, reinforcing earlier findings that attrition is not driven by simple linear effects.  
- Feature importance varies by model, reflecting differences in how each method captures structure in the data.  
- In the Random Forest model specifically:  
  - WorkLifeStress and OverTime appear among the most influential predictors.  
  - Compensation-related features (e.g., MonthlyIncome, Income per Experience) also rank highly despite weak linear correlations.  
- EDA-only patterns (department, age, marital status) appear visually strong but are less predictive once modeled jointly.

This notebook highlights that attrition drivers are model-dependent and non-linear, and that no single feature dominates across all analytical perspectives.

---

## Model Performance

| Model               | Accuracy | Precision (Attrition) | Recall (Attrition) | F1 (Attrition) |
|--------------------|----------|------------------------|--------------------|----------------|
| Decision Tree       | 0.75     | 0.34                   | 0.60               | 0.43           |
| Logistic Regression | 0.74     | 0.35                   | 0.68               | 0.46           |
| Random Forest       | 0.82     | 0.44                   | 0.55               | 0.49           |

---

## Key Takeaways
- Attrition patterns differ depending on whether they are examined visually, via correlation, or through predictive modeling.  
- Random Forest highlights work-life stress and overtime as key attrition drivers more strongly than linear models, signaling where HR should focus retention efforts.  
- Correlation analysis alone is insufficient for identifying attrition drivers in this dataset.  
- Model choice materially affects how attrition risk is interpreted.

---

## EDA vs. Machine Learning Perspective
A key outcome of this project is the distinction between visual intuition and model-based evidence.

- Exploratory visualizations highlight departments, roles, and demographic groups because these are easy to compare visually.  
- However, machine learning results show that many of these apparent effects are absorbed by variables related to:  
  - Workload (OverTime, WorkLifeStress).  
  - Compensation.  
  - Career stage.  

Once these factors are accounted for, several demographic and organizational variables lose predictive importance.

This comparison demonstrates why attrition analysis cannot rely on dashboards alone:  
- strong-looking visual patterns do not necessarily translate into predictive importance.

The Power BI dashboard reflects this distinction by treating departments and demographics as contextual filters, while positioning workload and stress as primary explanatory drivers.

---

## Power BI Dashboard — Operationalizing Attrition Risk

### Objective
While the Python notebooks focus on exploratory analysis, feature relationships, and predictive modeling, the Power BI dashboard is designed to operationalize those findings. It answers the critical question:

*Where should HR focus attention to reduce attrition risk?*

---

### Design Principles
The interactive dashboard moves beyond replicating EDA charts. Its design focuses on:

- Attrition rates rather than raw counts.  
- Workload, stress, and compensation — the strongest predictors from machine learning models.  
- Risk concentration over averages.  
- Dynamic visuals and KPIs for slicers such as gender and job role.

---

### Key Visuals and Interactions
- **KPIs**:  
  - **Total Employees**.  
  - **Attrition Rate** (filtered by role, department, etc.).  
  - **Average Work-Life Stress** (filtered).

- **Bar + Line Combo**:  
  - Job Role → Total Employees + Attrition Rate.  
  This chart shows the relationship between job roles, total employees, and their attrition rates, enabling HR to prioritize roles with both high attrition and significant workforce size.

- **Scatter Plot**:  
  - Monthly Income vs WorkLifeStress → Attrition size.  
  This plot highlights the interaction between income, stress levels, and attrition. The bubble size represents the number of employees in each point, and the color denotes stress bands.

- **Stress Band**:  
  A bar chart showing total attrition by stress levels. This visual emphasizes the non-linear relationship between stress and attrition, where higher stress levels are linked to a sharp increase in attrition risk.

- **Small Multiples**:  
  A marital status bar chart, providing a breakdown of attrition rates by marital status across various filters.

- **Department × Overtime Attrition Matrix**:  
  A heatmap visualizing the interaction between department and overtime, highlighting areas with both high overtime and high attrition.

---

### Data Preparation & Measures
Data was prepared using Power Query to ensure consistent formatting, readable labels, and stable inputs for analysis. Columns were cleaned and standardized, and derived fields such as stress level groupings were created to support clearer visual interpretation.

Key metrics (e.g. Attrition Rate, Average Work-Life Stress) were implemented as dynamic measures, allowing all visuals and KPIs to respond consistently to filters such as job role, department, and gender.

The data model was intentionally kept simple to prioritize clarity and interpretability for HR users, ensuring that insights remain transparent and easy to explore rather than obscured by unnecessary structural complexity.

---

### Visualization Design & Business Goals
The dashboard design integrates insights from exploratory data analysis (EDA) and machine learning (ML) models to provide actionable HR insights. It focuses on identifying where attrition risk is highest and guiding targeted retention efforts.

- **Stress Levels by Department**: Initial donut visuals showed uniform stress levels across departments. However, combining compensation, job roles, and overtime highlighted stress as a critical driver when these factors interact.

- **Compensation vs. Stress Scatter Plot**: This visual illustrates once more the non-linear relationship between these three most significant factors. Higher attrition correlates with higher stress and either low or high compensation, reflecting the ML model’s findings.

- **Role in EDA**: *Sales roles were flagged as high-risk in EDA, even though ML didn’t prioritize them. They are included as contextual filters to enable deeper exploration by HR.*

---

### How Visuals Support HR Decision-Making
The visuals are designed to help HR prioritize areas for intervention:
- High-risk roles and departments: The scatter plot and stress band show that high stress and low compensation drive attrition, enabling HR to target retention strategies based on these insights.  
- Tailored retention strategies: Slicers (e.g. gender, job role) enable HR to drill down into specific demographics, helping tailor retention strategies based on stress or compensation disparities.  
- The job role attrition chart helps HR prioritize roles with both high attrition and large headcounts, ensuring retention efforts are impactful.

This ensures the dashboard directly supports data-driven HR decision-making.

---

### Summary & Key Takeaways
The Power BI dashboard serves as an interactive tool to operationalize the findings from EDA and machine learning. It answers the critical question:

*Where should HR focus attention to reduce attrition risk?*

- **Key Insights**:  
  - Focus on workload (overtime), stress, and compensation as primary drivers of attrition risk.  
  - Use contextual slicers (e.g. role, department, gender) to fine-tune retention strategies.  
  - Prioritize high-risk job roles and departments with elevated attrition.

This makes the dashboard a dynamic decision-support tool for HR, guiding them in identifying and addressing attrition hotspots effectively.

---

## Lessons Learned
1. **Scaling Issues**:  
   During preprocessing, I initially scaled features in the wrong order, which affected the results. After identifying this, I corrected the scaling order in the pipeline, ensuring the models could learn from the data correctly.

2. **Handling Missing Data (NAs)**:  
   A divide-by-zero error introduced unexpected NaN values in certain columns. I handled this by implementing checks to avoid division by zero in the pipeline, ensuring no missing data affected the model.

3. **Data Cleaning Limitations**:  
   While the data was cleaned for the purpose of this analysis, it was artificially pre-processed before being imported. Although this was necessary for quick analysis, it did not showcase my full data cleaning capabilities, which could have been demonstrated with more involved preprocessing.

---

**Actionable HR Implications**  
- **Overtime-focused interventions**: Use the dashboard to identify roles and teams where overtime coincides with high attrition. Prioritize workload rebalancing or overtime caps in these areas.  
- **Targeted work–life stress mitigation**: Direct retention programs toward employees and roles exhibiting high work–life stress.  
- **Headcount-adjusted prioritization**: Focus retention efforts on roles with high attrition rates and large employee populations.  
- **Role-specific retention strategies**: Treat Sales and HR roles as priority segments for intervention. Tailor actions by gender or role.  
- **Monitoring early warning signals**: Track overtime and stress levels over time to see if retention efforts are having an impact.


