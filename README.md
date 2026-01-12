

# HR Attrition Analysis & Prediction  
**Rachel Hill-Tsarpelas** | Data Analyst Portfolio Project  
_Date: 2025-12

# HR Retention & Employee Attrition Analysis

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
  
Kaggle: (https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset/data)

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
## Day 1 — Data Overview & Problem Understanding  
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

## Day 2 — Exploratory Data Analysis & Visual Patterns  
**Notebook:** `02_HR_Retention_Visualizations.ipynb`

**Objective:**  
Use exploratory visualizations to identify patterns and group-level differences associated with employee attrition.

**Key Observations:**
- Attrition rates are visibly higher among employees who:
  - Work overtime
  - Are younger or at earlier career stages
  - Belong to certain job roles and departments
- Lower job satisfaction is associated with higher observed attrition
- Linear correlation analysis does not reveal strong relationships with attrition, suggesting that:
  - Key effects are likely non-linear
  - Relationships may depend on combinations of features rather than individual variables

At this stage, the analysis highlights where attrition appears in the data, while indicating that more expressive models are required to understand the underlying drivers.

---

### 3. Machine Learning & Feature Importance  
**`03_HR_Retention_ML.ipynb`**

Key takeaways from modeling:
- **OverTime is the dominant predictor of attrition**, clearly outranking all other features
- Career and compensation variables form the second tier of importance:
  -
  - MonthlyIncome
  - JobLevel
  - Age
  - TotalWorkingYears
- Variables that looked important in EDA (e.g. department, marital status, specific roles) contribute **far less** once multivariate relationships are learned
- The model shifts the explanation of attrition from *who people are* to *how they work and where they are in their career*

This notebook reframes attrition as a **workload–career stage problem**, not primarily a demographic or organizational grouping problem.

---

## EDA vs Machine Learning: Where the Story Changes

A key outcome of this project is the **disconnect between visual intuition and model-based evidence**:

- EDA visuals highlight departments, roles, and demographic groups because these are easy to separate visually
- The machine learning model shows that:
  - Many of these effects are **absorbed by income, experience, and overtime**
  - Once these are controlled for, demographic variables lose explanatory power

This demonstrates why attrition analysis cannot rely on dashboards alone:  
**strong-looking charts do not necessarily reflect causal or predictive importance**.

---

## Implications for Visualization & Power BI

### 📊 Power BI Dashboard (Planned)

The Power BI dashboard will be designed to reflect this distinction:

Planned emphasis:
- Overtime as the primary attrition driver
- Career stage and compensation as secondary drivers
- Departmental and demographic views presented as *context*, not root causes

Explicit design choice:
- Visuals that appear important in isolation will be clearly separated from variables confirmed by the ML model
- This prevents misleading interpretations based purely on categorical comparisons

---

## Why This Project Is Structured This Way
- To show how **EDA can mislead when interpreted alone**
- To demonstrate how **machine learning corrects visual bias**
- To make the analytical reasoning transparent and reproducible

This is an analysis project, not a dashboard-first project.

---

## Author
**Rachel Hill-Tsarpelas**  
Data Analyst | Python | EDA | Machine Learning




---

## Project Structure & Notebooks

### Day 1 – Data Overview & Problem Understanding  
**`01_HR_Retention_Overview.ipynb`**

Focus:
- Introduction to the business problem
- Dataset inspection and structure
- Understanding key variables and data types
- Initial observations relevant for later visualization and modeling

Outcome:
- Solid understanding of the dataset
- Identification of variables likely to influence attrition
- Preparation for focused exploratory analysis

---

### Day 2 – Exploratory Data Analysis & Visualization  
**`02_HR_Retention_Visualizations.ipynb`**

Focus:
- Exploratory data analysis using visualizations
- Attrition patterns across departments, roles, and marital status
- Analysis of work-life balance, overtime, and job-related stress
- Correlation analysis and feature relevance

Outcome:
- Employees working overtime show a clearly higher attrition rate in the visual analysis.
- Attrition is visually concentrated among younger employees and lower job levels, decreasing steadily with increasing seniority.
- Department, job role, and marital-status plots show strong separation, indicating apparent group-level attrition differences in univariate views.

---

### Day 3 – Machine Learning & Prediction  
**`03_HR_Retention_ML.ipynb`**

Focus:
- Data preprocessing and feature preparation
- Handling numerical and categorical variables
- Addressing class imbalance
- Training and evaluating machine learning models

Outcome:
- Predictive modeling of employee attrition
- Evaluation of model performance
- Interpretation of results to support preventive HR actions

---

## Key Insights
- Attrition is strongly associated with **overtime**, **work-life stress**, and **marital status**
- Employees in **sales-related roles** show elevated attrition risk
- Combining demographic and job-related features improves predictive power
- The analysis highlights where **targeted, proactive HR interventions** may be most effective

---

## 📊 Power BI Dashboard (Planned)
*This section will be updated once the Power BI dashboard is finalized.*

Planned dashboard focus:
- Interactive attrition overview
- Department- and role-level filtering
- Visual storytelling of key attrition drivers identified in Python

---

## Results & Business Value
This project demonstrates how HR data can be transformed into actionable insights.  
By combining exploratory analysis with machine learning, the results support a shift from reactive attrition reporting toward **early risk detection and targeted retention strategies**.

---

## Next Steps
- Finalize and publish Power BI dashboard
- Improve model tuning and validation
- Enhance explainability of model outputs for non-technical stakeholders
- Explore additional features or time-based attrition patterns

---

## EDA vs. Machine Learning Perspective
Exploratory data analysis revealed visible patterns across departments and demographic groups.  
However, the machine learning feature importance analysis demonstrates that **workload, compensation, and career progression variables outweigh purely demographic factors** when predicting attrition risk.

This comparison highlights the importance of combining visual exploration with predictive modeling to avoid misleading conclusions based on single-variable relationships.

## Key Insights
- **Overtime is the strongest predictor of employee attrition**, clearly dominating the feature importance ranking
- Compensation- and seniority-related variables such as **monthly income**, **job level**, and **total working years** play a major role in attrition risk
- **Age and career stage** are important contributors, indicating higher attrition risk at specific points in an employee’s professional lifecycle
- While variables such as department or marital status show patterns in exploratory analysis, they are **less influential once multiple factors are considered together in the machine learning model**









---

## Day 2 — Exploratory Visualizations

**Purpose:**  
Explore the data visually to identify patterns and understand which features relate to attrition.  

**What was done:**

- **Target Distribution:** Count of employees who left vs stayed  
- **Univariate Visualizations:** Histograms for age, income, and numeric features  
- **Target-Conditioned Visualizations:**  
  - Attrition vs Overtime  
  - Attrition vs Age  
  - JobRole counts (top 5 roles)  
  - Department counts  
- **Boxplots and Correlation Analysis:** Age vs Attrition, heatmap of numeric correlations  

**Key Insights (examples):**

- Employees working overtime have higher attrition rates  
- Certain departments and job roles show higher attrition percentages  
- Age and income distributions differ between employees who stayed and those who left  

**Files Produced:**

- `02_visualizations.ipynb` — notebook with plots and observations  

---

## Day 3 — Feature Engineering

**Purpose:**  
Create new features to capture employee behavior and improve potential modeling.  

**New Features Created:**

1. **Work_Life_Stress:** Combines overtime, distance from home, and work-life balance rating  
2. **Career_Speed:** Ratio of years at company to age  
3. **Age_Group:** Categorizes employees into age ranges  
4. **Income_Per_Year:** Annual income from monthly salary  
5. **Income_Per_Experience:** Annual income relative to total years worked  
6. **Manager_Dependency:** Ratio of years with current manager to total years at company  

**Notes:**

- Features were created manually using simple, readable Python code  
- Each feature has a clear rationale for how it may relate to attrition  

**Files Produced:**

- `03_feature_engineering.ipynb` — notebook with feature creation  
- `data/processed_hr_for_modeling.csv` — final dataset with engineered features  

---

## How to Use This Repository

1. **Data:**  
   - `data/raw/` — original dataset  
   - `data/processed/` — cleaned and feature-engineered CSVs  

2. **Notebooks:**  
   - `01_data_overview.ipynb` — basic inspection  
   - `02_visualizations.ipynb` — interactive visualizations  
   - `03_feature_engineering.ipynb` — feature creation  

3. **Reports:** Optional CSV summaries (pivot tables, distribution counts)  

**Next Steps:**  
- Use the processed dataset for predictive modeling  
- Evaluate models and interpret feature importance  



## 🧩 Workflow  
1. Data ingestion & SQL exploration  
2. Exploratory data analysis (EDA) & cleaning  
3. Feature engineering  
4. Modeling (baseline + advanced)  
5. Dashboard creation in Power BI  
6. Insights & recommendations  
7. Packaging (GitHub + presentation + dashboard)

## 🔍 Key Findings & Insights  
- **Finding 1**: [Example: Employees with < 2 years since last promotion have X% higher attrition.]  
- **Finding 2**: [Example: MonthlyIncome below €40 k correlates with higher attrition in the Sales department.]  
- **Finding 3**: [Example: Combination of low JobSatisfaction + high WorkLifeBalance issue = high risk.]

## 📈 Model Performance  
- **Baseline model** (Logistic Regression)  
  - ROC-AUC: …  
  - Accuracy: …  
  - Precision / Recall: …  
- **Advanced model** (RandomForest / XGBoost)  
  - ROC-AUC: …  
  - Accuracy: …  
- **Top features**: Feature1, Feature2, Feature3 (with short explanation)

## 📊 Dashboard  
- **Overview page**: KPI cards (Attrition %, Avg Age, Avg Tenure)  
- **Insights page**: Charts by Department, JobRole, Income Band  
- **Prediction page**: Feature importance, “At-risk employees” view, recommendations  
- **Tip**: Screenshot or link to Power BI report file (`.pbix`) is in `/powerbi`.

## ✅ Business Recommendations  
- Recommendation 1: [E.g., Implement targeted retention programmes for employees with <2 years since last promotion in Sales.]  
- Recommendation 2: [E.g., Review compensation bands for high-risk job roles.]  
- Recommendation 3: [E.g., Deploy a dashboard for HR managers to track attrition risk monthly.]


