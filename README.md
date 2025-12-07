# 📘 **Compliance Radar — Organizational Risk & Integrity Analysis**

### *Machine Learning for Corporate Compliance Monitoring*

**Team Members:**
Student 1, Student 2, Student 3, Student 4
Bachelor’s in Artificial Intelligence & Management — Luiss Guido Carli University

---

# **1. Introduction**

This project develops a machine-learning system designed to identify departments with elevated compliance risk. Using the `org_compliance_data.db` database, which contains operational, managerial, audit, reporting, and engagement metrics, we classify each department as either *high-risk* or *not high-risk*.

The aim is not only to build predictive models but also to provide interpretable insights for compliance officers through statistical analysis, supervised learning, and responsible AI practices. The final goal is to develop an early-warning tool that supports organizational integrity and governance.

---

# **2. Methods**

## **2.1 Problem Formulation**

The task is formulated as a binary classification problem, where the target variable `is_high_risk` equals 1 for departments included in the `high_risk_departments` table and 0 otherwise. The objective is to learn which operational and managerial characteristics are associated with elevated compliance risk.

---

## **2.2 Dataset Description**

The database contains four tables.
The main table, **departments**, includes **709 rows and 37 attributes**, covering:

* organizational structure
* managerial experience
* violations and incidents
* audit outcomes
* reporting and engagement indicators
* training activity
* operational and risk scores

The `dept_id` is preserved for reporting and interpretability but is not used as a predictive feature.

---

## **2.3 Data Cleaning and Integrity Resolution**

* Duplicate `dept_id` values were identified. Since these represent meaningful inconsistencies rather than errors, all records were kept to preserve information.
* Missing values in numerical features were imputed using the median.
* Missing categorical values were imputed using the most frequent category.
* No rows were removed, maintaining dataset completeness.

---

## **2.4 Feature Engineering**

Completed feature engineering steps:

* Construction of the `is_high_risk` target variable from the high-risk department list.
* Binary-like columns were inspected and converted to Boolean types when strictly containing 0/1 values; otherwise, they were treated as categorical.
* Ordinal experience variables (`manager_experience_level`, `supervisor_experience_level`) were retained as ordered numeric variables (0–4).
* Rating-based operational metrics (1–5 scales) were kept as numeric ordered values.
* `dept_id` was retained only for reporting, grouping, and visualization but excluded from modeling.

---

## **2.5 Modelling Strategy**

The modelling approach will include:

* Majority Class Baseline
* Logistic Regression
* Random Forest
* XGBoost

This provides a balance between interpretability and performance.

---

## **2.6 Preprocessing Pipeline**

Current preprocessing progress:

* Missing value imputation completed.
* Conversion of binary-like features completed.
* Ordinal and rating-scale features validated and retained as numeric variables.
* Numerical distributions analyzed.
* Outlier identification completed using histograms and boxplots.
* Categorical variables identified for upcoming encoding.
* Numerical variables prepared for future scaling and transformation.
* `dept_id` excluded from all preprocessing and modeling steps.

Placeholders for images:

* **Feature distributions**
  `![Distributions](images/distributions_numeric.png)`

* **Boolean feature distributions by high-risk status**
  `![Boolean Distributions](images/distributions_by_high_risk.png)`

* **Boxplots for outlier detection**
  `![Outliers](images/outliers_boxplots.png)`

Additional preprocessing (encoding, scaling, train-test split) will be completed before model training.

---

## **2.7 Environment Reproducibility**

The repository includes environment configuration files and a structured directory layout (data/, notebooks/, images/, models/), ensuring reproducibility of all results.

---

## **2.8 System Diagram**

A workflow diagram illustrating the process from data loading to interpretation will be included:

`![System Diagram](images/system_diagram.png)`

---

# **3. Experimental Design**

Model performance will be evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* ROC-AUC

Stratified train-test splitting and cross-validation will be used to ensure robustness. Hyperparameter tuning will be performed using grid search or randomized search depending on model complexity.

---

# **4. Results**

This section will report model performance once training and evaluation are completed.
Planned figures include:

* Confusion matrices
* ROC curves
* Feature importance plots
* SHAP value explanations

Placeholders:

`![Confusion Matrix](images/confusion_matrix.png)`
`![ROC Curve](images/roc_curve.png)`
`![SHAP Summary](images/shap_summary.png)`

---

# **5. Conclusions**

## **5.1 General Conclusions**

The project demonstrates the potential of machine learning to support compliance risk identification. Interpretability is prioritized to help decision-makers understand key drivers of risk and use model outputs responsibly.

---

## **5.2 Limitations and Future Work**

Key limitations include the static nature of the data, potential inconsistencies in reporting across departments, and the absence of temporal trends. Future steps may include:

* temporal models
* interactive dashboards
* integration of text-based audit reports
* model drift monitoring
* external validation on new datasets

---

## **5.3 Ethical and Governance Considerations**

Compliance-risk prediction requires transparency, fairness, and human oversight. Predictions must not be used as automatic judgments. Interpretability tools such as SHAP will be employed to ensure responsible use and support informed decision-making.

