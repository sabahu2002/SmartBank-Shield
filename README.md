# UAE E-Commerce Fraud Detection

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Machine Learning](https://img.shields.io/badge/ML-Supervised-orange)
![Status](https://img.shields.io/badge/Status-Completed-success)

---

## Project Overview

This project aims to detect fraudulent transactions in UAE e-commerce platforms using machine learning.

The dataset contains **100,000 transactions** with a fraud rate of **8.21%**, making it a **highly imbalanced classification problem**.

The objective is to build a **production-aware fraud detection system** that balances fraud detection effectiveness with customer experience.

---

##  Problem Statement

E-commerce platforms need to identify fraudulent transactions without blocking legitimate users.

### Key Challenges

* Severe class imbalance
* High cost of false negatives (missed fraud)
* High cost of false positives (customer friction)

---

## Dataset

* Source: `uae_ecom_fraud_100k.csv`
* Size: 100,000 rows × 36 features

### Each row represents:

A single transaction including user behavior, payment information, and risk indicators.

---

##  Project Workflow

```
Raw Data → Cleaning → Feature Engineering → Encoding → SMOTE → Modeling → Evaluation → Deployment
```

---

##  Methodology

### 1. Data Cleaning

* Handled missing values
* Winsorized outliers
* Removed corrupted signals

### 2. Feature Engineering

* Created 16 behavioral and risk-based features

### 3. Encoding

* One-Hot Encoding (avoids false ordering issues)

### 4. Handling Class Imbalance

* Applied SMOTE on training data only

### 5. Models Used

* Logistic Regression (Baseline)
* Random Forest
* LightGBM
* XGBoost  (Final Model)

### 6. Evaluation Strategy

* Train/Test split (no data leakage)
* Cross-validation on training data only
* Threshold tuning on validation set
* Test set used only once for final evaluation

---

##  Model Performance

| Model               | AUC Score  |
| ------------------- | ---------- |
| Logistic Regression | 0.6849     |
| Random Forest       | 0.6232     |
| LightGBM            | 0.6322     |
| XGBoost            | **0.7010** |

---

##  Key Insights (EDA)

### Strong Predictors

* `user_prev_chargebacks`
* `ip_risk_score`
* `user_is_high_risk`

### Behavioral Patterns

* Fraud increases between **00:00–06:00**
* New accounts (<30 days) are higher risk
* Large transaction amounts increase fraud probability

### Weak Signal

* Payment method alone has low predictive power

---

##  Business Deployment Strategy

### Model

**XGBoost Classifier**

### Decision Threshold

```
prob >= 0.60 → Flag for manual review  
prob <  0.60 → Approve automatically  
```

### Performance at Threshold 0.60

* Recall: 37.2%
* Precision: 18.9%
* F1 Score: 0.2505

### Business Impact

* Improves fraud detection
* Reduces unnecessary customer friction

---

##  Experiment Improvements

* Removed data leakage issues
* Fixed incorrect feature engineering
* Applied SMOTE correctly (train only)
* Improved validation strategy
* Reduced overfitting
* Added fair model comparison

---

##  Future Enhancements

* Real-time fraud detection using Kafka / Spark
* Streamlit dashboard for monitoring
* Human-in-the-loop feedback system
* Continuous model retraining
* A/B testing for threshold optimization
* Segment-based models (high vs low value transactions)

---

##  How to Run

```bash
pip install -r requirements.txt
```

### Steps

1. Download dataset: `uae_ecom_fraud_100k.csv`
2. Place it in the project root directory
3. Run the main notebook

---

##  Project Structure

```
fraud-detection/
│
├── README.md
├── requirements.txt
├── notebooks/
│   └── uae_ecom_fraud.ipynb
├── slides/
│   └── Fraud-Detection-System.pdf
├── figures/
    └── final_evaluation.png
    └── advanced_model_dashboard.png
    └── eda_dashboard.png
└── data/
 └── uae_ecom_fraud_100k.csv
     
```

---

##  Limitations & Ethics

* Model may introduce bias depending on data
* False positives may affect legitimate users
* Requires human review for critical decisions
* Data privacy must be preserved in production

---

##  Team

* Saba'a Hussien
* Noor Reda
* Marah Al-najar
* Bashar Bayatna
* Anas Oweis

---

##  Key Takeaway

A well-structured machine learning pipeline with proper evaluation and realistic deployment strategy is more valuable than overly complex models.

---

##  Future Demo (Optional)

* Streamlit application
* Fraud monitoring dashboard
