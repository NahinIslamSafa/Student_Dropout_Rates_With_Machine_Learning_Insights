## Student Dropout Rates With Machine Learning

## Project Overview

This project analyzes questionnaire-based data from approximately 450 students at private universities in Bangladesh to identify factors associated with student dropout risk.

The data covers demographic, academic, psychological, social, and lifestyle factors. The project applies machine learning to predict dropout risk and uses feature selection and explainability techniques to understand the factors influencing model predictions.

## Methodology

**Data Preprocessing → Feature Selection → Model Training → Model Evaluation → Explainability**

The analysis includes four supervised machine learning models:

- Decision Tree
- Random Forest
- XGBoost
- CatBoost

Feature importance, Recursive Feature Elimination (RFE), and SHAP were used to investigate model interpretability.

## Results

Random Forest achieved the highest accuracy among the evaluated models at **87%**.

The analysis identified several influential factors, including:

- Relationship Satisfaction
- Adjustment Difficulty
- Program Satisfaction Level
- Overall Health
- Classmate Cooperation
- Father's Education Level

The SHAP analysis further examined how these factors contributed to dropout predictions across the different models.

## Tools & Skills

- Python
- Pandas
- Scikit-learn
- XGBoost
- CatBoost
- SHAP
- Matplotlib
- Machine Learning
- Feature Selection
- Model Evaluation
- Explainable AI

## Project Files

- `Google colab files/` — Machine learning and explainability notebooks
- `Images/` — Key analysis visualizations
- `CSV file (1).csv` — Project dataset
