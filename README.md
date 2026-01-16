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

### Part 1 — Data Overview & Problem Understanding  
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
  - **WorkLifeStress** and **OverTime** appear among the most influential predictors  
  - Compensation-related features (e.g., MonthlyIncome, Income per Experience) also rank highly despite weak linear correlations  
-  EDA-only patterns (department, age, marital status) appear visually strong but are less predictive once modeled jointly

This notebook highlights that attrition drivers are **model-dependent and non-linear**, and that no single feature dominates across all analytical perspectives.

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
**strong-looking visual patterns do not necessarily translate into predictive importance.**

The Power BI dashboard reflects this distinction by treating departments and demographics as **contextual filters**, while positioning workload and stress as **primary explanatory drivers**.

---

## Power BI Dashboard — Operationalizing Attrition Risk

### Objective

While the Python notebooks focus on exploratory analysis, feature relationships, and predictive modeling, the **Power BI dashboard** is designed to **operationalize** those findings. It answers the critical question:  

> **Where should HR focus attention to reduce attrition risk?**

---

### Design Principles

The interactive dashboard moves beyond replicating EDA charts. Its design focuses on:

- **Attrition rates** rather than raw counts
- **Workload**, **stress**, and **compensation** — the strongest predictors from machine learning models
- **Risk concentration** over averages
- **Dynamic visuals** and **KPIs** for slicers such as **gender** and **job role**

---

### Key Visuals and Interactions

- **KPIs**:  
  - **Total Employees**
  - **Attrition Rate** (filtered by role, department, etc.)
  - **Average Work-Life Stress** (filtered)

- **Bar + Line Combo**:  
  - **Job Role** → **Total Employees** + **Attrition Rate**  
  This chart shows the relationship between job roles, total employees, and their attrition rates, enabling HR to prioritize roles with both high attrition and significant workforce size.

- **Scatter Plot**:  
  - **Monthly Income** vs **WorkLifeStress** → **Attrition size**  
  This plot highlights the interaction between income, stress levels, and attrition. The **bubble size** represents the number of employees in each point, and the **color** denotes stress bands.

- **Stress Band**:  
  A **bar chart** showing total attrition by **stress levels**. This visual emphasizes the non-linear relationship between stress and attrition, where higher stress levels are linked to a **sharp increase in attrition risk**.

- **Small Multiples**:  
  A **marital status bar chart**, providing a breakdown of attrition rates by marital status across various filters.

- **Department × Overtime Attrition Matrix**:  
  A **heatmap** visualizing the interaction between department and overtime, highlighting areas with both high overtime and high attrition.

---

### Data Preparation & Measures

Data was prepped using **Power Query** to clean and standardize columns (e.g., fixing decimals, renaming). New columns were created for visual clarity, such as **shortened names** and **stress level bins**.

**DAX Measures** were written for dynamic calculations, and these measures were stored in a separate table for best practice. Instead of creating an artificial **star schema**, the model retained simplicity and clarity, ensuring the dashboard remained intuitive for HR professionals.

---

### Thought Process Behind Visualization Design

The dashboard design was informed by the exploratory data analysis (EDA) and machine learning results:

- **Initial Donut Visuals**:  
  Donut charts were used to show **stress levels by department**, which revealed a relatively uniform distribution. When focusing on **income**, **job roles**, and **overtime**, the **patterns** started to emerge, highlighting **stress** as a key driver when combined with these factors.

- **Scatter Plot (Compensation vs. Stress)**:  
  A scatter plot was selected to examine the interaction between **work-life stress** and **compensation**. By using **bubble size** for attrition concentration, it was easy to spot **non-linear trends** where stress levels combined with low or high compensation lead to significantly higher attrition risk.

- **Role in EDA**:  
  **Sales roles** were identified as a high-risk group in the **EDA phase**. While **machine learning** didn’t rank them as the most influential, they were still highlighted in the dashboard as a **contextual filter** for HR teams to explore deeper.

---

### Linking Visuals to Business Goals

Each visual ties back to the overarching goal of providing **actionable insights** to HR:

- **Highlighting High-Risk Roles and Departments**:  
  The **scatter plot** and **bar charts** make it easy for HR to identify which **job roles** and **departments** are at high risk for attrition, particularly when combining **workload** (overtime), **stress**, and **compensation** data.

- **Tailored Retention Strategies**:  
  By using slicers (e.g., **gender**, **job role**), HR can drill down into specific **demographics** or **roles**. This allows for more targeted retention strategies, ensuring that attrition interventions are tailored based on **specific factors** like **gender** or **career stage**.

---

### Summary & Key Takeaways

The **Power BI dashboard** serves as an interactive tool to operationalize the findings from **EDA** and **machine learning**. It answers the critical question:  
> **Where should HR focus attention to reduce attrition risk?**

- **Key Insights**:  
  - Focus on **workload** (overtime), **stress**, and **compensation** as primary drivers of attrition risk.
  - Use **contextual slicers** (e.g., role, department, gender) to fine-tune retention strategies.
  - Prioritize high-risk **job roles** and departments with **elevated attrition**.

This makes the **dashboard** a **dynamic decision-support tool** for HR, guiding them in identifying and addressing attrition hotspots effectively.

---

## Lessons Learned

1. **Scaling Issues**:  
   During preprocessing, I initially scaled features in the wrong order, which affected the results. After identifying this, I corrected the scaling order in the pipeline, ensuring the models could learn from the data correctly.

2. **Handling Missing Data (NAs)**:  
   A divide-by-zero error introduced unexpected `NaN` values in certain columns. I handled this by implementing checks to **avoid division by zero** in the pipeline, ensuring no missing data affected the model.

3. **Data Cleaning Limitations**:  
   While the data was cleaned for the purpose of this analysis, it was **artificially pre-processed** before being imported. Although this was necessary for quick analysis, it did not showcase my full **data cleaning capabilities**, which could have been demonstrated with more involved preprocessing.

---

**Actionable HR Implications**  

- **Overtime-focused interventions**: Use the dashboard to identify roles and teams where overtime coincides with high attrition. Prioritize workload rebalancing or overtime caps in these areas.
- **Targeted work–life stress mitigation**: Direct retention programs toward employees and roles exhibiting high work–life stress.
- **Headcount-adjusted prioritization**: Focus retention efforts on roles with high attrition rates and large employee populations.
- **Role-specific retention strategies**: Treat Sales and HR roles as priority segments for intervention. Tailor actions by gender or role.
- **Monitoring early warning signals**: Track overtime and stress levels over time to see if retention efforts are having an impact.

---

### Final Thoughts

This project highlights the value of **integrating EDA, machine learning, and Power BI** to provide comprehensive insights into attrition patterns. Through this structured approach, HR professionals can make **data-driven decisions** to improve retention, focusing their efforts where attrition risk is highest.










## Power BI Dashboard — Operationalizing Attrition Risk

### Objective

While the Python notebooks focus on exploratory analysis, feature relationships, and predictive modeling, the Power BI page is designed to **operationalize those findings**.

Rather than repeating EDA-style charts, the dashboard answers a different question:

> **Where should HR focus attention right now to reduce attrition risk?**

---

### Design Principles

Rather than replicating EDA visuals, the interactive dashboard focuses on:

- Attrition **rates** rather than raw counts
- Workload, stress, and compensation — the strongest model-supported drivers
- Risk **concentration**, not averages
- KPIs and dynamic visuals based on slicers to target gender and job role.

---

### Key Visuals and Interactions

- **KPIs**: Total Employees, Attrition Rate, Avg Work-Life Stress  
- **Slicers**: Gender, Job Role  
- **Bar + Line Combo**: Job Role → Total Employees + Attrition Rate  
- **Scatter Plot**: Monthly Income vs WorkLifeStress → Attrition size  
- **Stress Band**: Displays total attrition bar  
- **Small Multiples**: Marital Status bar chart  
- **Matrix**: Department × Overtime → Attrition Rate

---

### Data Preparation & Measures

The data was prepped using **Power Query** to ensure that decimals and names were standardized. Separate columns were created for visuals, such as shortening long names and binning stress levels for better display. In addition, **DAX measures** were written for dynamic calculations, and a separate table was created to store these measures for best practice. 

Rather than creating an artificial star schema, which wasn’t necessary for this analysis, I ensured that the structure was clean and intuitive, double-checking the setup for consistency.

---

### Visualizations

The visualizations focus on **key data insights** rather than simply aesthetic appeal. Each visual reflects the most interesting and actionable patterns identified from the data and the modeling process. For instance, the **scatter plot** highlights the relationship between **monthly income** and **work-life stress**, with attrition size as the point size, directly reflecting the insights gained from machine learning models.

**Thought Process Behind Visualization Design**
- Initial Donut Visuals (Stress Levels by Department)
  Initially, I used donut charts to show the **distribution of stress levels** across all departments. These visuals revealed that **stress levels were relatively consistent across departments**. However, this general pattern shifted when I started focusing on specific variables, such as **compensation (MonthlyIncome)**, **job roles**, and **overtime**. These factors started to **unveil patterns and relationships** that weren’t immediately obvious from the overall department breakdown.
- Scatter Plot for Compensation vs. Stress:  
  A **scatter plot** was chosen to represent the relationship between **compensation**, **work-life stress**, and **attrition**. The scatter plot allowed me to capture **non-linear relationships** between these variables, with **bubble size representing attrition concentration**. This was especially useful in revealing that **stress, combined with compensation**, had a significant impact on attrition, with higher stress levels showing a strong concentration of attrition risk, especially in certain income bands.
- Role in EDA:  
  Sales roles were particularly notable in the **exploratory data analysis (EDA)** phase. While not directly contributing to machine learning (ML) insights, **Sales roles** had clear indicators of higher attrition in the **EDA visuals**. This insight carried over into the dashboard design and **served as a contextual filter** for HR to explore further, even though the exact drivers weren’t as significant in the ML model.

---

### Linking Visuals to Business Goals

The goal of the visuals was to provide HR with actionable insights on **where attrition risk is most concentrated**, and what **drivers** (such as **workload, compensation, stress levels, and job roles**) are contributing to that risk. 

Each visual was designed with the following business objectives in mind:

- **Highlighting high-risk roles and departments**: The scatter plot and bar charts helped HR **identify roles** and **departments** with **high attrition risk** based on **workload** (overtime), **compensation**, and **stress**.
  
- **Identifying employee groups requiring tailored retention strategies**: By using slicers (e.g., gender, job role) in Power BI, I made sure HR could drill down into specific **socioeconomic factors** or **job categories** to craft targeted **retention strategies**. These filters reflect the notion that even if socioeconomic factors (like gender) didn’t **directly cause attrition**, they might require **slightly different action plans** to address their unique needs.






### Summary & Key Takeaways

The **Power BI dashboard** synthesizes the findings from exploratory data analysis (EDA) and machine learning (ML) into actionable insights for HR. Specifically, it answers critical questions regarding:

- **Where to focus attention**: The dashboard highlights which departments, roles, and demographic groups have the highest attrition rates.
- **The strongest predictors of attrition**: It highlights workload (Overtime), stress levels, and compensation-related variables that are most predictive of attrition.
- **Actionable insights**: HR teams can take immediate actions based on the KPIs and slicers, such as addressing **workload issues**, adjusting **compensation**, or offering **stress relief programs** to employees in specific departments or roles.

This makes the Power BI dashboard not just a **static reporting tool**, but an **interactive decision-making resource** that drives retention strategies.

---



### Final Thoughts

The **EDA** phase provides the **initial insights**, **ML** identifies the most influential factors driving attrition, and **Power BI** enables HR professionals to take **data-driven actions** based on those insights. By combining all three, this project offers a comprehensive approach to understanding and mitigating employee attrition.







### Key Visuals & Rationale

**KPI Summary (Top Panel)**  
- Headcount  
- Attrition Rate (filtered)  
- Average Work-Life Stress (filtered)  

These KPIs provide immediate context and reinforce that all insights are filter-aware.

---

**Attrition Rate & Headcount by Job Role (Bar + Line Chart)**  
This visual identifies job roles that combine:
- Elevated attrition risk (rate)
- Meaningful organizational impact (headcount)

This distinction supports prioritization:  
high attrition in small roles signals niche risk, while moderate attrition in large roles signals broader operational risk.

---

**Compensation × Stress × Attrition (Scatter Plot)**  
This multivariate view explores the interaction between:
- Monthly income
- Work-life stress
- Attrition concentration

Bubble size encodes attrition count, while color represents stress bands, revealing non-linear patterns consistent with machine learning findings.

---

**Attrition by Stress Band and maritial status, small multiples (Bar Chart)**  
This chart demonstrates that attrition accelerates once stress crosses defined thresholds, reinforcing the conclusion that stress acts as a non-linear driver rather than a gradual linear factor.

---

**Department × Overtime Attrition Matrix (Heatmap)**  
This matrix provides an operational view of attrition risk by combining departmental context with workload pressure.

Conditional formatting highlights attrition hotspots where overtime and turnover coincide — an insight that static Python charts are less effective at conveying.

---

### Relationship to Machine Learning Results

A central outcome of this project is the contrast between **visual intuition** and **model-based evidence**.

While some variables appear visually prominent in isolation (e.g., department or demographic groupings), machine learning models consistently assign greater importance to:

- Workload indicators (Overtime, Work-Life Stress)
- Compensation-related features
- Career stage variables

The Power BI dashboard reflects this distinction by treating departments and demographics as **contextual filters**, while positioning workload and stress as **primary explanatory drivers**.

---

---

### Takeaway

The Power BI dashboard does not attempt to validate the machine learning models directly.  
Instead, it translates model insights into a **decision-oriented, interactive view** that helps HR stakeholders identify where attrition risk is most concentrated and actionable.

---

## What This Dashboard Does *Not* Show

To maintain analytical integrity, the dashboard intentionally avoids:

- **Raw attrition counts without context**  
  Counts alone can overemphasize large groups and obscure true risk.

- **Correlation-only visuals**  
  Visual patterns are not presented as causal explanations without model support.

- **Overly granular slicing**  
  Excessive breakdowns that add noise without improving decision-making were deliberately excluded.

---

## Lessons Learned

During this project, several **technical challenges** and **hurdles** emerged that refined my workflow:

1. **Scaling Issues**  
   Initially, I scaled data in the wrong step of the pipeline, which caused feature engineering issues later. After realizing this mistake, I revised the pipeline, ensuring the proper sequencing to maintain model accuracy.

2. **Handling Missing Data (NAs)**  
   A divide-by-zero error resulted in unexpected `NaN` values, which I resolved by implementing checks for zeroes before proceeding with calculations.

3. **Data Cleaning Limitations**  
   While the data was cleaned in preparation for analysis, it was **artificially** cleaned before import, meaning it wasn’t a showcase of my cleaning abilities. This was a necessary step, but it could have been more explicitly shown in the workflow.

---

**Actionable HR Implications**

- **Overtime-focused interventions:** Use the dashboard to identify roles and teams where overtime coincides with high attrition and prioritize workload rebalancing, staffing adjustments, or overtime caps in these areas.
- **Targeted work–life stress mitigation:** Direct retention programs toward employees and roles exhibiting elevated work–life stress rather than applying uniform, organization-wide initiatives.
- **Headcount-adjusted prioritization:** Focus retention efforts on roles that combine high attrition rates with large employee populations to maximize organizational impact.
- **Role-specific retention strategies:** Treat Sales and Human Resources roles as priority segments for intervention, while tailoring actions by gender and role where attrition magnitude differs.
- **Monitoring early warning signals:** Use changes in vertime and stress distributions over time as leading indicators to evaluate whether retention initiatives are having measurable effects.

   


### Data Exploration vs. Dashboard Design

- **Shift from EDA to Dashboard**:  
  The exploratory phase highlighted **general patterns**, like **overtime-related attrition** and certain **stress level distributions**. However, once I transitioned to the dashboard design phase, I was more focused on **concentrating HR’s attention** on **specific risk areas**. For example, the **Sales roles** and their **interaction with stress levels and compensation** were emphasized as high-risk areas to target for HR intervention. 

- **Visualizing Machine Learning Insights**:  
  The insights from machine learning solidified that **workload (overtime)** and **stress** were the key factors driving attrition, so the dashboard was designed with these as **primary drivers**, while using **job roles, department, and demographic filters** to offer additional **contextual analysis**. 

The dashboard visually reflects this by treating **workload** and **stress** as primary drivers of attrition, while offering **interactive filters** to explore how **departments** and **job roles** contribute to these risks.

---

o
---



