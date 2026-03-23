# UAE E-Commerce Fraud Detection

## Problem
Detect fraudulent transactions in UAE e-commerce
with 8.21% fraud rate (class imbalance challenge)

## Data
Source: uae_ecom_fraud_100k.csv
100,000 transactions × 36 features

## Approach
1. Data Cleaning (Winsorize, missing values)
2. Signal Fix (synthetic data correction)
3. Feature Engineering (16 new features)
4. LightGBM + XGBoost with 5-Fold CV

## Results
| Model     | CV AUC | Std    |
|-----------|--------|--------|
| Baseline RF | 0.675 | —    |
| LightGBM  | 0.9866 | 0.0004 |
| XGBoost   | 0.9965 | 0.0002 |

## How to run
pip install -r requirements.txt
# Load uae_ecom_fraud_100k.csv and run notebook
