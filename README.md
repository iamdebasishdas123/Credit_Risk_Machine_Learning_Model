# Credit Risk Analysis Notebook Documentation
- Datasets:- Case_Study1,Case_Study2
- Feature Description :-Features_Target_Description.xlsx
- Jupyter Notebook :-

# Credit Risk Analysis Project

## Overview

This project aims to develop a predictive model to classify prospective customers based on their likelihood of getting approved for credit. The analysis involves data processing, feature selection, model building, and hyperparameter tuning using machine learning techniques. The primary models used in this project include Random Forest, Decision Tree, and XGBoost classifiers.

## Data Collection

Two datasets are imported from Google Sheets using the following URLs:
- [Dataset 1](https://docs.google.com/spreadsheets/d/1Uvpal_TZdr6dEvScP5ulhaICI3MGgwEv/export?format=xlsx)
- [Dataset 2](https://docs.google.com/spreadsheets/d/1RxIn0q6vRET9185H2Bvf3r1mG75--oYc/export?format=xlsx)

These datasets are merged on the `PROSPECTID` column to create a comprehensive dataset for analysis.

## Data Processing and Cleaning

### Handling Missing Values
Columns with a high percentage of missing values are removed. Specifically, columns where more than 10,000 entries are missing are excluded from the dataset.

### Merging Datasets
The datasets are merged on the `PROSPECTID` column to form a unified dataset. This merged dataset is then used for further analysis.

### Collinearity and Multicollinearity
Categorical columns are identified, and a chi-square test is performed to assess their relationship with the target variable (`Approved_Flag`). For numerical columns, the Variance Inflation Factor (VIF) is calculated to check for multicollinearity. Columns with a VIF greater than 6 are iteratively removed. ANOVA tests are conducted to select significant numerical features.

## Feature Selection

The final set of features includes both the numerical columns that passed the VIF and ANOVA tests and the categorical columns.

### Data Encoding
- **Label Encoding**: The `EDUCATION` column is label-encoded based on specific ordinal values.
- **One-Hot Encoding**: Categorical columns such as `MARITALSTATUS`, `GENDER`, `last_prod_enq2`, and `first_prod_enq2` are one-hot encoded.

## Model Building

### Data Splitting
The dataset is split into training and testing sets with an 80-20 ratio using `train_test_split` from scikit-learn.

### Random Forest Classifier
A Random Forest model is trained using 200 estimators. The model's performance is evaluated using accuracy, precision, recall, and F1 score metrics.

### Decision Tree Classifier
A Decision Tree model is trained with a maximum depth of 20 and a minimum sample split of 10. Similar metrics are used for evaluation.

### XGBoost Classifier
An XGBoost model is trained with initial parameters. The target variable (`Approved_Flag`) is label-encoded before training. 

## Hyperparameter Tuning

Hyperparameter tuning for the XGBoost model is conducted using a grid search. The parameter grid includes various values for `n_estimators`, `max_depth`, `learning_rate`, `colsample_bytree`, and `alpha`. The best parameters are determined using cross-validation, and the model's performance is evaluated on the test set.

## Results

The best model achieved an accuracy of approximately 75% on the test set. Detailed metrics for precision, recall, and F1 score for each class are documented in the `Results.xlsx` file.

```
