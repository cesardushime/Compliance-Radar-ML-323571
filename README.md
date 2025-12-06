📘 Compliance Radar — Organizational Risk & Integrity Analysis

Machine Learning for Corporate Compliance Monitoring

Team Members

Student 1, Student 2, Student 3, Student 4
Bachelor’s in Artificial Intelligence & Management — Luiss Guido Carli University

⸻

1. Introduction

This project develops a machine-learning system designed to identify departments that may present a high level of compliance risk within an organization. The analysis is based on the org_compliance_data.db database, which contains detailed information about operational metrics, financial indicators, audit outcomes, managerial characteristics, training activities, and reporting behaviors. By using these variables, the project aims to classify departments as either high-risk or not high-risk and to understand which factors most strongly contribute to this classification.

The purpose of the project is not only to build predictive models but also to provide clear and interpretable insights that can support compliance officers and internal auditors. The final objective is to develop an early-warning tool that improves organizational integrity through data-driven monitoring and informed governance. The work combines statistical analysis, supervised learning, interpretability methods, and ethical reflections on the use of artificial intelligence in compliance settings.

⸻

2. Methods

2.1 Problem Formulation

The central task is formulated as a binary classification problem in which the target variable, called is_high_risk, takes the value 1 when a department is considered high-risk and 0 when it is not. This label is derived from the high_risk_departments table. The classification problem is well suited to the goal of detecting potential compliance issues, because it forces the models to learn which operational, managerial, and audit-related features are associated with increased risk. This formulation also allows us to combine interpretable models with more advanced machine-learning techniques, creating a system that is both transparent and effective.

2.2 Dataset Description

The dataset is stored in a relational database composed of four tables. The main table, departments, contains 709 rows and 37 attributes describing each organizational unit. These attributes include structural information, size, managerial experience, training hours, reporting activity, violations, audit findings, and engagement indicators. The high_risk_departments table includes all units that were previously flagged as high-risk and is used to build the target variable. A smaller table summarizing risk by division, as well as a full data dictionary, support the interpretation and understanding of the dataset.

2.3 Data Cleaning and Integrity Resolution

During the cleaning phase, we identified duplicate department IDs that contained conflicting information. Instead of removing these rows, which would alter the dataset and potentially reduce the accuracy of the target variable, we decided to keep all of them and introduce a new feature called id_conflict. This flag indicates whether a department ID appears multiple times with different characteristics. Keeping all observations ensures that we do not lose information and allows the model to learn from potential instability or inconsistency within a department.

2.4 Feature Engineering

Feature engineering focused on constructing the binary target variable and generating additional attributes that could improve model performance. These include the id_conflict flag and several potential derived metrics, such as reporting gaps, changes in audit scores over time, normalized violation counts, and combined engagement indicators. These engineered features aim to give the models a deeper understanding of the operational context of each department.

2.5 Modelling Strategy

To solve the classification problem, we adopt a modelling strategy that includes both simple and advanced algorithms. The Majority Class Classifier serves as a basic reference, since it always predicts the most common class and allows us to understand the minimum performance any useful model must exceed. Logistic Regression represents the first meaningful model. It is transparent, easy to interpret, and commonly used in risk analysis. To capture more complex patterns in the data, we also train a Random Forest classifier, which aggregates many decision trees, and an XGBoost classifier, which is a gradient boosting method known for delivering high performance on tabular data. Together, these models allow us to compare interpretability, robustness, and predictive accuracy.

2.6 Preprocessing Pipeline

Before model training, all data undergo a structured preprocessing pipeline. The dataset is divided into training and test sets using a stratified split to maintain the same proportion of high-risk departments in both parts. Missing numerical values are replaced with the median, while categorical values are imputed with the most frequent category. Outliers are treated through winsorization or robust scaling when necessary. All categorical variables are transformed using one-hot encoding, and continuous variables are standardized with the StandardScaler to improve model stability and performance. The resulting feature matrix and target vector are then used for all modelling experiments.

2.7 Environment Reproducibility

To make the project reproducible, the repository includes the conda environment configuration, the list of installed packages, and all dependencies required to run the code. This ensures that any user can recreate the same computational environment and obtain identical results.

2.8 System Diagram

A flowchart summarizing the process—from data loading to preprocessing, model training, evaluation, and interpretability—can be included to help readers visualize the entire pipeline.

⸻

3. Experimental Design

The experiments are designed to evaluate and compare the performance of the different classification models. The aim is to determine which model provides the most reliable predictions and to understand how changes in hyperparameters influence performance. To ensure fairness, all models are compared with the Majority Class Baseline and with their own default versions before tuning. A set of evaluation metrics is used to capture different aspects of performance, including accuracy, precision, recall, F1-score, and ROC-AUC. These metrics are particularly important in the compliance context, where failing to detect a high-risk department (a false negative) can lead to serious organizational consequences.

Hyperparameter tuning is conducted through k-fold cross-validation using either GridSearchCV or RandomizedSearchCV. This prevents overfitting and provides a robust estimate of model generalization. The tuning process focuses on key parameters of each model, such as regularization strength for Logistic Regression, tree depth for Random Forest, and learning rate and boosting depth for XGBoost. The best model configuration is selected according to either the F1-score or the ROC-AUC score, depending on the imbalance in the dataset.

⸻

4. Results

The results section reports the performance of each model on the test set after hyperparameter tuning. Overall, all machine-learning models perform significantly better than the Majority Class Baseline, demonstrating that the dataset contains meaningful risk-related patterns. Logistic Regression provides clear interpretability but remains limited by its linear structure. Random Forest improves recall and F1-score, showing its capacity to detect a higher number of high-risk cases. XGBoost achieves the best overall performance, with the highest F1-score and ROC-AUC, indicating strong predictive reliability.

A detailed analysis of confusion matrices shows that Logistic Regression tends to miss more high-risk cases, while Random Forest and XGBoost achieve a better balance between identifying risky departments and avoiding false alarms. ROC curves further confirm the superiority of XGBoost, as it consistently outperforms the other models across all thresholds. To interpret the best-performing model, SHAP values reveal the most influential features, such as violations, audit results, training deficiencies, reporting delays, and department instability signals. These insights provide a clear understanding of why certain units are classified as high-risk and help support transparent decision-making.

⸻

5. Conclusions

5.1 General Conclusions

This project demonstrates that machine learning can be an effective tool for identifying and understanding compliance risks within an organization. The analysis shows that the dataset contains strong predictive signals and that advanced models, particularly XGBoost, can achieve high levels of performance. Random Forest also offers solid results with good interpretability, while Logistic Regression remains useful as a transparent baseline. The SHAP analysis confirms that the models rely on meaningful operational indicators such as violations, audit findings, training quality, and reporting behaviors. These results can support more targeted audits, improved resource allocation, and more effective risk-prevention strategies.

5.2 Limitations and Future Work

Despite the positive results, the project has several limitations. The dataset is static and does not include temporal information, which means we cannot analyze how risk evolves over time. There may also be hidden biases in the data based on inconsistent reporting practices across departments. Furthermore, the evaluation is based on a single organizational dataset, and external validation across different companies or time periods would strengthen the conclusions. Future work could introduce temporal models, integrate NLP features from audit documents, implement monitoring tools to detect model drift, and develop interactive dashboards for real-time risk monitoring.

5.3 Ethical and Governance Considerations

The use of machine learning in compliance introduces important ethical responsibilities. False negatives may expose the organization to reputational or legal risk, while false positives may unfairly label a department as problematic. For this reason, model predictions must always be used as decision-support rather than automatic judgments. Interpretability is essential to guarantee transparency, and SHAP values help explain how each prediction is formed. To ensure responsible use, governance frameworks should include periodic audits of model behavior, monitoring of biases, clear documentation of assumptions, and human oversight. The objective is to enrich compliance processes with data-driven insights while respecting fairness, accountability, and responsible AI principles.