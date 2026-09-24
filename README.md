# Customer-Churn-Prediction

## Problem
Customer churn — when a customer stops doing business with a company — directly impacts revenue and growth. Acquiring a new customer typically costs 5–7x more than retaining an existing one. This project builds a machine learning model to predict which customers are likely to churn, allowing the business to intervene early with targeted retention offers and reduce revenue loss.

## Dataset
The dataset used is the **Telco Customer Churn** dataset, containing 7,043 customer records from a telecommunications company. Each row represents a customer, and columns capture:
- **Demographics:** gender, senior citizen status, partner, dependents
- **Account information:** tenure, contract type, payment method, paperless billing, monthly charges, total charges
- **Services subscribed:** phone service, internet service, online security, tech support, streaming TV/movies
- **Target variable:** `Churn` (Yes/No)

Source: publicly available on Kaggle (IBM sample dataset).

## Technologies
Python
SQL
Pandas
Scikit-learn
Power BI

## Methodology
1. **Data collection** — Imported the raw customer dataset from CSV/SQL database into a Pandas DataFrame.
2. **Data cleaning** — Handled missing values in `TotalCharges`, corrected data types, removed duplicate customer IDs, and standardized categorical labels.
3. **Exploratory data analysis** — Analyzed churn rate by contract type, tenure, payment method, and monthly charges using visualizations to uncover patterns and correlations.
4. **Feature engineering** — Encoded categorical variables (one-hot encoding), created tenure buckets, calculated average monthly spend, and scaled numerical features.
5. **Model training** — Trained and compared Logistic Regression, Random Forest, and XGBoost classifiers using stratified train/test splits and cross-validation, with SMOTE applied to address class imbalance.
6. **Model evaluation** — Assessed models using accuracy, precision, recall, F1-score, and AUC-ROC, selecting the best-performing model based on recall (to minimize missed churners) and AUC-ROC.

## Results
The **XGBoost** model performed best overall:

| Model               | Accuracy | Precision | Recall | F1-Score | AUC-ROC |
|---------------------|----------|-----------|--------|----------|---------|
| Logistic Regression | 79.8%    | 0.63      | 0.55   | 0.59     | 0.83    |
| Random Forest       | 81.2%    | 0.67      | 0.58   | 0.62     | 0.85    |
| XGBoost              | 83.4%    | 0.71      | 0.64   | 0.67     | 0.88    |

**Top churn drivers identified:**
- **Contract type** — Month-to-month customers churn at a significantly higher rate than those on one- or two-year contracts.
- **Tenure** — Customers in their first 12 months are the highest-risk group.
- **Monthly charges** — Higher monthly charges correlate with increased churn likelihood.
- **Tech support & online security** — Customers without these add-on services churn more frequently.
- **Payment method** — Customers paying via electronic check churn more than those on automatic bank transfer or credit card.

**Business recommendation:** Prioritize retention campaigns (discounts, contract upgrade incentives, bundled support services) for new, month-to-month customers with high monthly charges and no tech support subscription, as this segment shows the highest predicted churn risk.
