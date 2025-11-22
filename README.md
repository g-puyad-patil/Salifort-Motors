# Employee Turnover Prediction for Salifort Motors HR 📊

## Project Overview

This project was conducted for Salifort Motors to analyze employee data and develop a predictive model to forecast employee turnover. The goal was to provide the Human Resources and Senior Leadership teams with data-driven insights to mitigate the high costs and operational disruptions associated with staff departures.

Using employee survey data, a **Decision Tree** classification model was built to predict the binary outcome of whether an employee will leave the company. The final model achieved an accuracy of **96.2%**, successfully highlighting key variables like `satisfaction_level` and `average_monthly_hours` as primary drivers of turnover.

***

## Business Understanding

The primary stakeholder is the **Salifort Motors Senior Leadership Team**. The company is facing a high rate of employee turnover, which is financially costly due to the required investment in recruitment, training, and onboarding new staff.

The business problem is to **increase employee retention**. By predicting which employees are at the highest risk of leaving and identifying the underlying reasons, the HR department can intervene proactively with targeted retention strategies, ultimately saving the company time and money while fostering a better work environment.

***

## Data Understanding

The analysis utilized the `HR_capstone_dataset.csv` provided by Salifort Motors' Human Resources department.

* **Size:** 14,999 rows (employee records) and 10 columns.
* **Target Variable:** `left` (1 = employee left, 0 = employee stayed).
* **Key Features:** `satisfaction_level`, `last_evaluation`, `number_project`, `average_monthly_hours`, `time_spend_company`, `department`, and `salary`.
* **Exploratory Data Analysis (EDA) Insights:**
    * A significant portion of employees who left the company reported both **low satisfaction levels** and **very high average monthly hours**.
    * Employees who left often fell into distinct clusters related to their **number of projects** (e.g., those with very few projects *and* those with too many).
* **File:** `HR_capstone_dataset.csv`

***

## Modeling and Evaluation

### Approach
This is a **binary classification problem**. I chose to build and evaluate a **[Model Type]** model. The data was preprocessed using techniques such as feature encoding for categorical variables (`department`, `salary`) and splitting the data into training and test sets.

### Model Performance
The final model was evaluated on the test set using standard classification metrics:

| Metric | Result | Interpretation |
| :--- | :--- | :--- |
| **Accuracy** | `96.2%` | Overall correctness of the model's predictions. |
| **Precision** | `87.0 %` | Out of all predicted departures, how many were actually correct (important for minimizing false alarms). |
| **Recall** | `90.4 %` | Out of all actual departures, how many did the model correctly identify (important for capturing at-risk employees). |
| **F1 Score** | `[88.7%]` | The harmonic mean of Precision and Recall. |

### Feature Importance (for Tree-Based Models)
The following features were found to be the most influential in predicting employee departure:

1.  **`satisfaction_level`**
2.  **`time_spend_company`**
3.  **`average_monthly_hours`**



***

## Conclusion and Recommendations

The predictive model successfully identifies employees at high risk of turnover, providing a valuable tool for HR intervention.

### Key Insights
* **Satisfaction is Critical:** Low satisfaction is the single strongest predictor of departure.
* **Workload Management:** Employees with **[Your Key Finding, e.g., 6 or 7 projects]** or those logging extremely high hours show a significantly increased likelihood of leaving.

### Recommendations
1.  **Targeted Retention Programs:** Implement an alert system based on the model's high-risk predictions to identify and intervene with employees before they decide to leave.
2.  **Workload Management:** Audit and re-distribute workloads in departments with high average monthly hours (e.g., **[Department Name]**) to prevent burnout.
3.  **Satisfaction Survey Follow-Up:** Conduct detailed follow-up interviews with employees in the low satisfaction/high hours group to understand their specific pain points.

***

## Future Steps

* **Clustering:** Apply an **unsupervised learning method (e.g., K-means)** to the data to identify natural, actionable groupings (clusters) of employees based on their work habits and reported scores.
* **Causal Inference:** Explore more complex models to determine the direct causal effect of specific interventions (like raising salary or reducing projects) on the probability of retention.
* **Model Deployment:** Explore deploying the model to a production environment where it can intake new employee data in real-time.

***

### Technologies and Files Used

| File/Tool | Purpose |
| :--- | :--- |
| **Python** | Primary programming language |
| **Pandas, NumPy** | Data manipulation and numerical operations |
| **Scikit-learn** | Model building, training, and evaluation |
| **XGBoost, Statsmodels** | Advanced statistical and machine learning modeling |
| **Matplotlib, Seaborn** | Exploratory Data Analysis and visualization |
| `[Your Notebook Name].ipynb` | Full project code for EDA, modeling, and evaluation |
| `Executive_Summary.pdf` | One-page summary of findings for non-technical stakeholders |
