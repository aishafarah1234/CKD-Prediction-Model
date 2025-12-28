# CKD-Prediction-Model
A machine learning approach to Chronic Kidney Disease (CKD) risk prediction using patient health indicators and drug toxicity features.

This project develops and evaluates machine learning models to predict Chronic Kidney Disease (CKD) risk levels using a combination of clinical patient data and drug-related toxicity features. The goal is to identify high-risk individuals early and support safer clinical decision-making when prescribing potentially nephrotoxic medications.

## Project Structure
```text
CKD-Prediction-Model/
│
├─ CKD Prediction Model.ipynb     # Jupyter notebook with EDA, feature selection, model training, and evaluation
├─ environment.yml                # Conda environment file with all dependencies for reproducibility
├─ requirements.txt               # Optional pip requirements file
├─ data/                          # Folder containing raw and processed datasets
├─ xgb_ckd_top_features.pkl       # Trained XGBoost model saved for future predictions or API deployment
```

## Dataset
The dataset was obtained from Kaggle and contains 1,500 patient records with 37 features, including:
- Clinical variables: age, blood urea, serum creatinine, diabetes, hypertension
- Drug-related variables: drug name, nephrotoxic label, toxicity and pharmacokinetic indicators
- Outcome variable: CKD risk level (low, moderate, high)

All records were complete with no missing values.

## Exploratory Data Analysis (EDA)
EDA was conducted to understand relationships between features and CKD risk:
1. Univariate statistical tests
   - t-tests for numerical variables
   - Chi-square tests for categorical variables

2. Visualisation
   - Boxplots for key numerical features
   - Count plots for categorical variables

Significant predictors included:
- Clinical markers such as blood urea, serum creatinine, and diabetes
- Drug-related toxicity measures such as kidney cell viability, serum creatinine change, and nephrotoxic drug exposure

## Data Preprocessing
- String categorical variables (gender, drug_name) were one-hot encoded
- Binary clinical indicators (diabetes, hypertension, nephrotoxic_label) were retained as numeric values
- Numerical features were scaled only for Logistic Regression
- Stratified k-fold cross-validation was used to preserve class distributions

## Machine Learning Models
Three models were trained and evaluated using 5-fold stratified cross-validation:
1. Logistic Regression - baseline, interpretable linear model
2. Random Forest - bagging-based ensemble model
3. XGBoost - gradient boosting with regularization

Evaluation metrics:
1. Accuracy
2. Precision (macro)
3. Recall (macro)
4. F1-score (macro)
5. ROC AUC (one-vs-rest)

## Feature Selection & Model Refinement
Based on EDA findings, a reduced feature set was constructed using:
- Key clinical risk factors
- Core kidney function biomarkers
- One-hot encoded drug exposure variables

XGBoost was retrained using only these selected features.

Performance improved across all metrics, demonstrating that:
1. The model was not overfitted
2. Identified features were genuinely informative
3. Both clinical conditions and drug-related factors play a crucial role in CKD risk

## Results Summary
- XGBoost outperformed all models, achieving near-perfect performance across all evaluation metrics
- Tree-based models significantly outperformed Logistic Regression due to their ability to capture nonlinear relationships and feature interactions
- Feature selection improved interpretability without sacrificing predictive performance

## Clinical Relevance
This model highlights the importance of:
- Monitoring high-risk biomarkers in patients with diabetes or hypertension
- Exercising caution when prescribing nephrotoxic drugs
- Using data-driven tools to support early CKD risk stratification

The findings support improved clinical decision-making by integrating patient health status with drug toxicity risk.
