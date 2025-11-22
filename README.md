# 🧑‍💼 Employee Retention Prediction at Salifort Motors

---

## 🎯 Overview

The goal of this project was to create a machine learning model, specifically a **Random Forest Classifier**, to **predict whether an employee would leave Salifort Motors** (`left` vs. `stay`). This project utilized a dataset containing self-reported employee information gathered from a recent survey.

The final Random Forest model achieved approximately **98% accuracy** and a high **Recall of 93%** for predicting employee departure, successfully identifying the factors most important in separating employees who stay from those who leave.

Based on the model, **last evaluation score**, **tenure (time spent at the company)**, and **number of projects** were the most influential features in determining an employee’s likelihood of leaving the company.

---

## 🏢 Business Understanding

Salifort Motors is experiencing a **high rate of employee turnover**, which is financially costly and undermines corporate culture goals.

The objective was to understand **what factors encourage employees to leave** in order to develop targeted, data-driven HR strategies to **increase long-term employee retention**. A strong predictive model allows the company to shift from reactive measures to proactive intervention.

---

## 📊 Data Understanding

| Column Name | Type | Description |
| :--- | :--- | :--- |
| `satisfaction_level` | int64 | The employee’s self-reported satisfaction level [0-1] |
| `last_evaluation` | int64 | Score of employee's last performance review [0–1] |
| `number_project` | int64 | Number of projects employee contributes to |
| `average_monthly_hours` | int64 | Average number of hours employee worked per month |
| `time_spend_company` (renamed to `tenure`) | int64 | How long the employee has been with the company (years) |
| `work_accident` | int64 | Whether or not the employee experienced an accident while at work |
| `left` (Target Variable) | int64 | Whether or not the employee left the company |
| `promotion_last_5years` | int64 | Whether or not the employee was promoted in the last 5 years |
| `department` | str | The employee's department |
| `salary` | str | The employee's salary (low, medium, or high) |

* **Source**: Internal HR survey data (`HR_capstone_dataset.csv`).
* **Size**: ~15,000 unique employee records.
* **Data Preparation**:
    * Categorical features (`department`, `salary`) were one-hot encoded.
    * A new feature, **`overworked`** (employees working >200 hours/month), was engineered.
    * Duplicates were identified and removed.

---

## 💻 Modeling and Evaluation

### Model Used: Random Forest Classifier

A Random Forest Classifier with 100 decision trees was selected for its ability to handle feature non-linearity, robustness to outliers, and its excellent feature importance reporting capabilities.

### Feature Importance

The chart below visualizes the factors that contributed most to the model's predictive power:


<img width="491" height="278" alt="image" src="https://github.com/user-attachments/assets/370416e3-c884-44b1-ac07-bc8db7e387eb" />


The **Top 3 most important factors** were:
1.  **`last_evaluation`** (performance review score)
2.  **`number_project`**
3.  **`tenure`** (time spent at the company)

### Performance Metrics

| Metric | Score | Description |
| :--- | :--- | :--- |
| **Accuracy** | ~98% | Overall correctness of predictions. |
| **Precision** (for `left=1`) | ~96% | Of all predicted leavers, how many actually left. |
| **Recall** (for `left=1`) | **~93%** | Of all employees who *actually left*, how many were correctly identified. (Crucial for an HR intervention model). |

---

## 💡 Conclusion and Recommendations

The model successfully identifies employees at high risk of departure and pinpoints the key underlying issues.

### Actionable Recommendations for HR:

1.  **Cap Project Workload**: Since a high **`number_project`** is a major driver of turnover, consider implementing a policy to **cap the number of projects** an employee can work on simultaneously to prevent burnout and maintain focus.
2.  **Target 4-5 Year Tenure Group**: Investigate and address the high turnover observed among employees with **four to five years of tenure**. This could involve targeted **promotion cycles**, retention bonuses, or dedicated career development planning before this critical period.
3.  **Review Evaluation-Hours Correlation**: Since **`last_evaluation`** and **`overworked`** are both highly influential, the company must ensure that high evaluation scores are not solely reserved for employees who work excessive hours. Evaluation criteria should reflect quality and efficiency, not just time spent.
4.  **Acknowledge and Reward High Hours**: If long hours are necessary, implement clear compensation or recognition programs to mitigate the negative impact of being **`overworked`**.

### Future Work

* **Clustering**: Apply a K-means clustering model to segment employees based on their feature values (e.g., satisfaction, evaluation, hours) to define specific "at-risk" profiles (e.g., "Burnout Risk," "Low-Satisfaction/Low-Effort").
* **Predicting Satisfaction**: Build a separate regression model to predict an employee's **`satisfaction_level`** based on other inputs, providing insight into which variables can be manipulated to boost satisfaction *before* turnover occurs.
