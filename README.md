# 🚀 Credit Risk Assessment System

An End-to-End Machine Learning Pipeline for Automated Loan Default Prediction using the German Credit Risk Dataset.

## 📌 Project Overview

Financial institutions process thousands of loan applications every month. Traditional credit assessment processes are often manual, time-consuming, and inconsistent, leading to delays in decision-making and increased financial risk.

This project develops a production-ready Credit Risk Assessment System that predicts whether a loan applicant is likely to:

* ✅ Repay the loan (Good Credit)
* ❌ Default on the loan (Bad Credit)

The solution leverages Machine Learning, Feature Engineering, Hyperparameter Tuning, and MLflow Experiment Tracking to deliver accurate, scalable, and interpretable credit risk predictions.

---

## 🎯 Business Objectives

* Predict loan default risk automatically
* Achieve Recall ≥ 75% on default cases
* Support real-time inference (< 1 second)
* Maintain model interpretability for regulatory compliance
* Track experiments and model versions using MLflow
* Recommend the best model for production deployment

---

## 📊 Dataset

### German Credit Risk Dataset

The dataset contains 1,000 loan applicant records with demographic, financial, and loan-related information.

### Features

| Feature          | Description             |
| ---------------- | ----------------------- |
| Age              | Applicant age           |
| Sex              | Male/Female             |
| Job              | Job skill category      |
| Housing          | Own / Rent / Free       |
| Saving Accounts  | Savings account status  |
| Checking Account | Checking account status |
| Credit Amount    | Loan amount requested   |
| Duration         | Loan duration (months)  |
| Purpose          | Purpose of loan         |
| Risk             | Target Variable         |

Target Encoding:

* Good → 0
* Bad → 1

---

## 📈 Exploratory Data Analysis

Performed comprehensive EDA to understand customer behavior and default patterns.

### Visualizations

* Target Distribution Analysis
* Histograms of:

  * Age
  * Credit Amount
  * Duration
* Boxplots by Risk Category
* Correlation Heatmap
* Default Rate by Loan Purpose
* Default Rate by Age Group
* Class Imbalance Analysis

### Key Insights

* Bad-risk applicants tend to request larger loans.
* Longer loan durations increase default probability.
* Younger borrowers exhibit higher default rates.
* Financial stability significantly impacts repayment behavior.

---

## 🛠️ Data Preprocessing

### Missing Value Handling

| Feature          | Strategy         |
| ---------------- | ---------------- |
| Saving Accounts  | Missing → "none" |
| Checking Account | Missing → "none" |

### Encoding

* One-Hot Encoding for categorical variables
* Label Encoding for target variable

### Scaling

* StandardScaler for numerical features

### Train-Test Split

* 80% Train
* 20% Test
* Stratified Sampling
* random_state = 42

---

## ⚡ Feature Engineering

Created domain-driven features to improve predictive performance.

### 1. Credit_to_Duration_Ratio

Credit Amount ÷ Duration

Represents monthly repayment burden.

### 2. Age_Group

Bucketed applicant age groups:

* 18–25
* 26–35
* 36–50
* 50+

Captures non-linear risk patterns.

### 3. High_Risk_Purpose

Flags high-risk loan purposes such as:

* Education
* Vacation/Others
* Repairs

### 4. Account_Stability

Combined financial stability score derived from:

* Savings Account
* Checking Account

---

## 🤖 Models Implemented

### Logistic Regression

Baseline linear classifier with class balancing.

### Decision Tree

Interpretable tree-based model.

### Random Forest

Ensemble learning using multiple decision trees.

### XGBoost

Gradient boosting framework optimized for classification performance.

---

## 🔍 Hyperparameter Tuning

Performed model optimization using:

### Random Forest

* GridSearchCV
* 5-Fold Cross Validation

### XGBoost

* RandomizedSearchCV
* 5-Fold Cross Validation

Optimization Metric:

* Recall

---

## 📊 Model Performance

| Model                 | Accuracy  | Precision | Recall    | F1 Score  | ROC-AUC   |
| --------------------- | --------- | --------- | --------- | --------- | --------- |
| Logistic Regression   | 0.724     | 0.612     | 0.763     | 0.679     | 0.784     |
| Decision Tree         | 0.695     | 0.578     | 0.742     | 0.650     | 0.721     |
| Random Forest         | 0.748     | 0.643     | 0.771     | 0.701     | 0.812     |
| Random Forest (Tuned) | 0.762     | 0.659     | 0.789     | 0.719     | 0.829     |
| XGBoost               | 0.751     | 0.648     | 0.779     | 0.708     | 0.821     |
| **XGBoost (Tuned)** ⭐ | **0.778** | **0.673** | **0.812** | **0.735** | **0.847** |

---

## 🏆 Best Model: XGBoost (Tuned)

### Why XGBoost?

✅ Highest Recall (81.2%)

✅ Best ROC-AUC (0.847)

✅ Strong F1 Score

✅ Fast Inference (<10ms)

✅ Handles complex feature interactions

✅ Production-ready scalability

---

## 📋 MLflow Experiment Tracking

All experiments were tracked using MLflow.

Tracked Information:

* Hyperparameters
* Metrics
* Confusion Matrices
* Model Artifacts
* Run Metadata

### Experiment Name

credit_risk_classification

### Logged Runs

* Logistic Regression
* Decision Tree
* Random Forest
* Random Forest Tuned
* XGBoost
* XGBoost Tuned

---

## 📉 Evaluation Visualizations

Generated:

* Confusion Matrices
* ROC Curves
* Precision-Recall Curve
* Feature Importance Charts
* Recall Comparison
* ROC-AUC Comparison
* Hyperparameter Tuning Results

Total Visualizations: 14+

---

## 🚀 Production Deployment Architecture

Client → API Gateway → FastAPI Service → XGBoost Model → Response

### Technology Stack

* Python
* Scikit-Learn
* XGBoost
* MLflow
* Prometheus
* Grafana

---

## 🔄 Monitoring & Retraining

### Data Drift Detection

Population Stability Index (PSI)

| PSI Range   | Action  |
| ----------- | ------- |
| < 0.10      | Stable  |
| 0.10 – 0.25 | Monitor |
| > 0.25      | Retrain |

### Retraining Triggers

* Recall < 70%
* Significant Feature Drift
* Economic Changes
* Scheduled Refresh (> 6 Months)

---

## 🏅 Key Achievements

* Built End-to-End ML Pipeline
* Engineered 4 Business-Oriented Features
* Compared 4 Classification Models
* Tuned Random Forest & XGBoost
* Tracked 6 MLflow Experiments
* Achieved 81.2% Recall on Defaults
* Achieved 0.847 ROC-AUC
* Designed Production Deployment Strategy
* Real-Time Inference < 10ms

---
