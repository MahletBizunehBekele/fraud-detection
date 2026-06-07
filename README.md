# Fraud Detection for E-Commerce and Bank Transactions

## Project Overview

This project focuses on improving fraud detection for both e-commerce transactions and bank credit card transactions. The objective is to build a robust fraud detection pipeline that addresses the challenges of highly imbalanced datasets while providing actionable business insights through data analysis, feature engineering, and machine learning.

The project is developed as part of Adey Innovations Inc.'s initiative to strengthen fraud prevention capabilities across multiple transaction streams.

---

## Business Problem

Fraudulent transactions can lead to significant financial losses and damage customer trust. Traditional evaluation metrics such as accuracy are often misleading in fraud detection because fraudulent transactions represent only a small percentage of all transactions.

This project aims to:

* Detect fraudulent transactions accurately.
* Minimize false positives that inconvenience legitimate customers.
* Minimize false negatives that allow fraudulent transactions to go undetected.
* Generate interpretable insights to support business decision-making.

---

## Datasets

### 1. Fraud_Data.csv

E-commerce transaction dataset containing:

* User information
* Device information
* Purchase details
* Browser and source information
* IP addresses
* Fraud labels

### 2. IpAddress_to_Country.csv

IP address range mapping dataset used to enrich transaction records with country information.

### 3. creditcard.csv

Credit card transaction dataset containing anonymized PCA-transformed features and fraud labels.

---

## Project Structure

```text
fraud-detection/

├── .github/
│   └── workflows/
│       └── unittests.yml
│
├── .vscode/
│   └── settings.json
│
├── data/
│   ├── raw/
│   └── processed/
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
├── models/
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

## Task 1: Data Analysis and Preprocessing

### Data Cleaning

* Checked and handled missing values.
* Removed duplicate records.
* Corrected data types for timestamps and numerical fields.

### Exploratory Data Analysis

* Univariate analysis of key variables.
* Bivariate analysis between features and fraud labels.
* Class imbalance assessment for both datasets.

### Geolocation Integration

* Converted IP addresses to integer format.
* Performed IP-to-country mapping using range-based lookup.
* Analyzed fraud patterns across countries.

### Feature Engineering

Created the following fraud-related features:

* `time_since_signup`
* `hour_of_day`
* `day_of_week`
* `transaction_count`
* `time_since_last_transaction`

### Data Transformation

* One-hot encoding of categorical variables.
* Standardization of numerical features using StandardScaler.

### Class Imbalance Handling

Applied SMOTE (Synthetic Minority Oversampling Technique) on the training set to address severe class imbalance.

Before SMOTE:

| Class          |  Count |
| -------------- | -----: |
| Legitimate (0) | 93,502 |
| Fraud (1)      |  9,814 |

After SMOTE:

| Class          |  Count |
| -------------- | -----: |
| Legitimate (0) | 93,502 |
| Fraud (1)      | 93,502 |

SMOTE was selected because it balances the dataset without discarding majority-class observations.

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Imbalanced-learn
* Jupyter Notebook

---

## Future Work

### Task 2

* Train machine learning models.
* Compare model performance using fraud-focused metrics.
* Evaluate models using confusion matrix, precision, recall, F1-score, ROC-AUC, and PR-AUC.

### Task 3

* Apply SHAP explainability techniques.
* Identify the most influential fraud indicators.
* Generate actionable business recommendations.

---

## Author

Mahi 


