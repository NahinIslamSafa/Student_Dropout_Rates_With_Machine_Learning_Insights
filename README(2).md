# Reducing Student Dropout Rates With Machine Learning Insights

## Project Overview

This project investigates factors associated with student dropout risk among students from private universities in Bangladesh using questionnaire-based data and supervised machine learning.

The study uses approximately 450 valid responses collected through a psychologist-validated questionnaire containing 43 items across demographic, academic, psychological, social, lifestyle, and performance-related dimensions.

Four supervised machine learning models were developed and evaluated:

- Decision Tree
- Random Forest
- XGBoost
- CatBoost

The project also applies feature selection and SHAP-based analysis to identify influential variables and understand how selected features contribute to model predictions.

---

## Problem Statement

Student dropout is influenced by more than academic performance alone. Personal, psychological, social, health, adjustment, and satisfaction-related factors can also be associated with a student's risk of leaving university.

Many existing approaches rely primarily on institutional or academic records. This project explores a broader questionnaire-based approach incorporating academic and non-academic dimensions within the context of private universities in Bangladesh.

---

## Objectives

The project aims to:

1. Predict student dropout risk using questionnaire-based data.
2. Compare multiple supervised machine learning models.
3. Identify influential factors associated with model predictions.
4. Apply feature selection to reduce the feature space and examine feature stability.
5. Use SHAP analysis to improve the interpretability of model predictions.
6. Provide analytical insights that could support future student-retention and early-warning initiatives.

---

## Dataset

The study collected approximately 450 valid responses from students at several private universities in Bangladesh.

The questionnaire contained 43 items across six broad dimensions:

- Demographic background
- Academic and institutional factors
- Psychological adjustment
- Academic life conditions
- Social and lifestyle factors
- Student performance

The questionnaire was reviewed and validated by a professional psychologist before data collection.

Participation was voluntary and anonymous, and the final dataset did not contain personal identifiers.

### Data Availability

The participant-level dataset is not intended to be publicly distributed through this repository.

Although the collected responses were anonymous, the dataset contains individual-level demographic, psychological, academic, social, lifestyle, and other questionnaire responses. This repository therefore focuses on the analysis workflow, methodology, visualizations, and findings rather than publicly distributing the participant-level data.

---

## Methodology

The proposed dropout prediction system follows a three-layer framework:

```text
Data Acquisition
       ↓
Data Processing
       ↓
Machine Learning
```

### Data Acquisition

Data were collected through a psychologist-validated questionnaire containing 43 items across six dimensions: demographic background, academic and institutional factors, psychological adjustment, academic life conditions, social and lifestyle factors, and performance.

### Data Processing

The responses were cleaned, encoded, and converted into a structured dataset suitable for machine learning. Categorical responses were numerically encoded, and continuous features were normalized where necessary. An 80%/20% train-test split was used, with preprocessing fitted only on the training data to avoid data leakage. A consistent feature registry and fixed random seed were used to support reproducibility.

### Machine Learning

Four supervised learning models were trained and compared on the processed dataset:

- Decision Tree Classifier
- Random Forest Classifier
- XGBoost Classifier
- CatBoost Classifier

Model performance was evaluated using accuracy, precision, recall, and F1-score.

### Data Preprocessing

The collected responses were cleaned and transformed into a structured dataset suitable for machine learning. The preprocessing included:

- Removal of invalid or incomplete entries
- Missing-value imputation
- Categorical and ordinal encoding
- Numerical feature transformation

An 80/20 train-test split was used, with preprocessing fitted only on the training data to avoid data leakage. A fixed random seed and consistent feature registry were used to support reproducibility.

---

## Machine Learning Models

Four supervised classification models were trained and compared:

| Model | Role |
|---|---|
| Decision Tree | Interpretable baseline model |
| Random Forest | Ensemble classification model |
| XGBoost | Gradient boosting classification model |
| CatBoost | Gradient boosting model designed for efficient categorical-data handling |

Model performance was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion matrices

---

## Model Evaluation

Using tree-based feature selection, the models achieved the following results:

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| Decision Tree | 80% | 0.78 | 0.82 | 0.79 |
| Random Forest | **87%** | **0.85** | **0.88** | **0.86** |
| XGBoost | 85% | 0.83 | 0.86 | 0.84 |
| CatBoost | 86% | 0.84 | 0.87 | 0.85 |

Random Forest achieved 87% accuracy on the evaluated held-out test set, with 0.85 precision, 0.88 recall, and 0.86 F1-score.

Additional 5-fold cross-validation and statistical tests were conducted to examine differences in model performance. The thesis reports a Friedman test p-value of 0.005. Pairwise comparisons reported significant differences between Random Forest and Decision Tree, and between Random Forest and XGBoost, while the difference between Random Forest and CatBoost was not statistically significant.

---

## Feature Selection & Model Interpretability

A three-stage interpretability process was applied:

1. Tree-based Feature Importance
2. Recursive Feature Elimination (RFE)
3. SHAP (SHapley Additive Explanations)

### Tree-Based Feature Importance

Random Forest feature importance highlighted several influential variables, including:

- Program Satisfaction Level
- Father's Education
- Relationship Satisfaction
- Overall Health
- Classmate Cooperation
- Adjustment Difficulty

### Recursive Feature Elimination (RFE)

RFE was used to identify feature subsets and examine feature stability across the evaluated models.

Six common features were identified for further analysis:

- Program Satisfaction Level
- Father's Education
- Relationship Satisfaction
- Overall Health
- Classmate Cooperation
- Adjustment Difficulty

### SHAP Analysis

SHAP analysis was conducted for all four classifiers using the six stable features identified through RFE.

The analysis was used to examine both the contribution and direction of selected features in model predictions.

---

## Key Findings

The feature-selection and SHAP analyses consistently highlighted several factors associated with predicted dropout risk.

### Influential Factors

The most frequently highlighted factors included:

- Relationship Satisfaction
- Adjustment Difficulty
- Program Satisfaction Level
- Overall Health
- Classmate Cooperation
- Father's Education

### SHAP-Based Observations

The SHAP analysis indicated that:

- Lower relationship satisfaction was associated with higher predicted dropout risk.
- Poorer health was associated with higher predicted dropout risk.
- Greater adjustment difficulty was associated with higher predicted dropout risk.
- Higher program satisfaction was associated with lower predicted dropout risk.
- Stronger classmate cooperation was associated with lower predicted dropout risk.

These findings describe patterns identified by the trained models and should not be interpreted as evidence of direct causal relationships.

---

## Feature Selection Results

The project also examined how different feature-selection strategies affected Random Forest performance:

| Feature Configuration | Random Forest Accuracy |
|---|---:|
| Without feature selection | 85% |
| Tree-based feature importance | **87%** |
| RFE-selected features | 86% |
| Common RFE features | 80% |

The results illustrate a trade-off between reducing the feature set and retaining predictive performance.

The RFE + SHAP workflow provided a more interpretable analysis by focusing attention on a smaller group of stable features while examining their contribution to model predictions.

---

## Statistical Validation

To further examine differences among the four models, 5-fold cross-validation results were subjected to statistical testing.

The thesis reports:

- Friedman test: **p = 0.005**
- Random Forest vs Decision Tree: **p = 0.0109**
- Random Forest vs XGBoost: **p = 0.0440**
- Random Forest vs CatBoost: **p = 0.7749**

The reported statistical analysis indicates that model performance differed across the evaluated algorithms, while the difference between Random Forest and CatBoost was not statistically significant in the reported pairwise comparison.

---

## Limitations

Several limitations should be considered when interpreting the results:

- The dataset contains approximately 450 responses, which limits how broadly the findings can be generalized.
- The data is based on self-reported questionnaire responses and may therefore be affected by reporting or self-assessment bias.
- The study focuses on students from several private universities in Bangladesh and may not represent all university students or educational contexts.
- The modelling experiments focus on classical machine learning algorithms and do not evaluate more advanced architectures such as deep learning.
- The analysis is based primarily on questionnaire data and does not incorporate institutional data such as detailed academic records, attendance, or learning-management-system activity.

---

## Ethical Considerations

The project involved human-subject questionnaire data and therefore considered privacy, confidentiality, and responsible use.

The questionnaire was psychologist-validated, participation was voluntary and anonymous, and the final dataset did not contain personal identifiers.

The proposed system is intended as an analytical support tool rather than an autonomous decision-maker. Any real-world implementation would require appropriate human review, responsible data access, and clear data-retention policies.

---

## Tools & Technologies

### Programming & Data Analysis

- Python
- Pandas
- NumPy

### Machine Learning

- Scikit-learn
- XGBoost
- CatBoost

### Explainability & Feature Analysis

- SHAP
- Recursive Feature Elimination (RFE)
- Tree-based Feature Importance

### Visualization

- Matplotlib
- Seaborn

### Development Environment

- Google Colab

---

## Potential Application

The analytical framework developed in this project can serve as a foundation for future student-retention and early-warning systems.

Future work could incorporate:

- Larger and more diverse datasets
- Data from additional universities
- Institutional academic records
- Attendance information
- Learning-management-system activity
- Additional machine learning approaches
- More advanced explainability techniques
- Periodic model updates using new student cohorts

Any future implementation should preserve appropriate privacy protections and maintain human oversight.

---

## Disclaimer

The predictions and relationships identified in this project are based on the collected questionnaire data and trained machine learning models. They should not be interpreted as definitive explanations or causal determinants of student dropout.

Any real-world student-support system based on this work should use model predictions as decision-support information alongside appropriate human judgment and institutional policies.

---

