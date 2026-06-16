# Fraud Detection for E-Commerce and Bank Transactions

## Project Overview

This project develops an end-to-end fraud detection system for both e-commerce transactions and bank credit card transactions. The goal is to identify fraudulent activity while minimizing false positives and false negatives in highly imbalanced datasets.

The project was completed for Adey Innovations Inc. and includes data preprocessing, feature engineering, machine learning model development, and model explainability using SHAP.

---

## Business Problem

Fraudulent transactions create significant financial losses and negatively impact customer trust. Since fraudulent transactions represent only a small fraction of all transactions, traditional accuracy metrics are insufficient for evaluation.

This project aims to:

* Detect fraudulent transactions effectively.
* Reduce false positives that affect legitimate customers.
* Reduce false negatives that allow fraud to go undetected.
* Provide explainable fraud predictions to support business decisions.

---

## Datasets

### Fraud_Data.csv

E-commerce transaction dataset containing:

* User information
* Device information
* Purchase details
* Browser and traffic source information
* IP addresses
* Fraud labels

### IpAddress_to_Country.csv

IP address range mapping dataset used for geolocation enrichment.

### creditcard.csv

Credit card transaction dataset containing anonymized PCA-transformed features and fraud labels.

---

## Project Structure

```text
fraud-detection/

├── .github/
│   └── workflows/
│       └── unittests.yml
│
├── data/
│   ├── raw/
│   └── processed/
│
├── models/
│   ├── logistic_regression.pkl
│   ├── random_forest.pkl
│   ├── credit_logistic_regression.pkl
│   └── credit_random_forest.pkl
│
├── notebooks/
│   ├── eda-fraud-data.ipynb
│   ├── eda-creditcard.ipynb
│   ├── feature-engineering.ipynb
│   ├── modeling.ipynb
│   └── shap-explainability.ipynb
│
├── src/
├── tests/
├── scripts/
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Task 1: Data Analysis and Preprocessing

### Data Cleaning

* Handled missing values.
* Removed duplicate records.
* Corrected data types for timestamps and numerical features.

### Exploratory Data Analysis

* Univariate feature analysis.
* Bivariate analysis against fraud labels.
* Class imbalance assessment for both datasets.

### Geolocation Integration

* Converted IP addresses into integer format.
* Performed range-based IP-to-country mapping.
* Analyzed fraud patterns by country.

### Feature Engineering

Created:

* `time_since_signup`
* `hour_of_day`
* `day_of_week`
* `transaction_count`
* `time_since_last_transaction`

### Data Transformation

* One-hot encoded categorical variables.
* Standardized numerical features.
* Applied SMOTE on training data only.

---

## Task 2: Model Building and Training

### Models Evaluated

#### Logistic Regression (Baseline)

Used as an interpretable baseline model.

#### Random Forest (Ensemble Model)

Used to capture non-linear fraud patterns and interactions between features.

### Evaluation Metrics

Models were evaluated using:

* F1 Score
* AUC-PR (Area Under Precision-Recall Curve)
* Confusion Matrix

### Fraud Dataset Results

| Model               | F1 Score | AUC-PR |
| ------------------- | -------: | -----: |
| Logistic Regression |    0.173 |  0.094 |
| Random Forest       |    0.678 |  0.649 |

### Model Selection

Random Forest significantly outperformed Logistic Regression and was selected as the final model for fraud prediction.

---

## Task 3: Model Explainability

### Feature Importance

Built-in Random Forest feature importance was analyzed to identify the most influential fraud indicators.

### SHAP Analysis

Generated:

* SHAP Summary Plot
* Local prediction explanations
* Individual fraud case analysis

### Top Fraud Drivers

The most influential fraud indicators included:

* time_since_signup
* transaction_count
* purchase_value
* hour_of_day
* country-related features

### Business Recommendations

1. Apply additional verification for purchases occurring shortly after account creation.
2. Monitor accounts with unusually high transaction frequency.
3. Implement country-based fraud risk scoring.
4. Flag unusually large or suspicious purchase amounts for secondary review.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Imbalanced-learn
* SHAP
* Joblib
* Jupyter Notebook

---

## Key Findings

* Fraud datasets are highly imbalanced and require specialized handling techniques.
* SMOTE significantly improved minority-class representation during training.
* Random Forest substantially outperformed Logistic Regression on fraud detection tasks.
* Behavioral transaction features were stronger fraud indicators than demographic features.
* Explainable AI techniques provided actionable business insights beyond predictive performance.

---

## Author

**Mahi**
