# hr-attrition-analysis
Predict which employees are likely to leave. 

# HR Attrition Analysis & Prediction  
**Rachel Hill-Tsarpelas** | Data Analyst Portfolio Project  
_Date: YYYY-MM-DD_

## 🎯 Project Overview  
### Objective  
> Predict which employees are likely to leave and provide actionable insights to reduce attrition — using HR data, machine learning, and interactive dashboards.

### Business Context  
Describe the business scenario:  
> For a European-based company (e.g., Germany) in [industry: manufacturing / services / tech], retaining talent is critical. High attrition causes costs in hiring, training, knowledge‐loss. This project analyses HR data, builds a prediction model, and delivers insights and a Power BI dashboard to support HR decision-making.

## 📊 Dataset  
- **Source**: [Dataset name], Kaggle link (or other).  
- **Rows & Columns**: e.g. ~14,000 employees, 35 features including Age, Department, MonthlyIncome, JobRole, YearsAtCompany, etc.  
- **Target**: `Attrition` (Yes/No)  
- **Notes**: (Any caveats: synthetic, generic region, etc.)


# HR Attrition Project

## Project Overview

This project explores employee attrition using the IBM HR dataset. The goal is to understand key drivers of attrition and prepare the data for predictive modeling. The project is structured in three phases:

1. **Data Overview (Day 1)** – basic inspection and summary  
2. **Exploratory Visualizations (Day 2)** – target-based visual exploration  
3. **Feature Engineering (Day 3)** – creating new features to enhance model performance  

The project demonstrates **Python data analysis skills**, including pandas, matplotlib, seaborn, and Plotly.

---

## Day 1 — Data Overview

**Purpose:**  
Perform a basic inspection and understand the structure of the data.  

**What was done:**

- Loaded the dataset and checked rows/columns  
- Identified numeric, categorical, and boolean-like columns  
- Checked for missing values — none found  
- Inspected the target column (`Attrition`) — class imbalance (~16% attrition)  
- Identified Yes/No columns (`Attrition`, `OverTime`, `Over18`) to convert to boolean later  
- Generated summary statistics for numeric columns (`Age`, `MonthlyIncome`, `YearsAtCompany`, etc.)  
- Noted that some numeric columns (like `Education`, `WorkLifeBalance`) are actually categorical  

**Files Produced:**

- `01_data_overview.ipynb` — notebook with all Day 1 analysis and comments  
- Optionally, `data/cleaned.csv` for use in Day 2  

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

## 🛠 Tools & Technologies  
- SQL (SQLite/PostgreSQL) — exploratory and feature engineering  
- Python (pandas, scikit-learn, SHAP) — modelling & explainability  
- Power BI Desktop — interactive dashboard  
- GitHub — code + project hosting  
- (Optional) Microsoft Azure — for future scale-up

## 🧠 How to Run This Project  
1. Clone this repo: `git clone https://github.com/your-username/hr-attrition-analysis`  
2. Install required Python packages: `pip install -r requirements.txt`  
3. Open `notebooks/01_data_overview.ipynb` and run step-by-step.  
4. Export `data/cleaned.csv` then open `powerbi/HR_Attrition.pbix` in Power BI Desktop.  
5. Explore the dashboard or publish to Power BI Service (if you have a licence).  
6. Check the presentation `reports/HR_Attrition_Summary.pptx` for a one-pager you can share with stakeholders.

## 📁 Repository Structure  
