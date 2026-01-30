# AI-Powered-Financial-Fraud-Detection-System
AI-Powered Financial Fraud Detection System 🛡️ | XGBoost Model trained on 6M+ transactions achieving 99.7% Recall. Features custom engineering to detect balance discrepancies.

# 🛡️ AI-Powered Financial Fraud Detection System

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Library](https://img.shields.io/badge/Library-XGBoost-orange)
![Status](https://img.shields.io/badge/Status-Completed-green)

## 📌 Executive Summary
This project focuses on predicting fraudulent transactions in a financial dataset containing **6 million+ entries**. By engineering domain-specific features and utilizing an **XGBoost Classifier**, the model achieved a **Recall of 99.7%**, ensuring that virtually all fraudulent attempts are detected while maintaining high precision to minimize customer friction.

## 💼 Business Problem
Financial fraud aims to profit by taking control of customer accounts and emptying funds. The challenge is:
1.  **Huge Data Volume:** 6M+ transactions with only 0.1% fraud cases (Severe Class Imbalance).
2.  **Hidden Patterns:** Fraudsters use sophisticated methods to mask their tracks.
3.  **Cost of Error:** Missing a fraud case (False Negative) costs money; flagging a real user (False Positive) costs reputation.

## 🛠️ Tech Stack
* **Language:** Python
* **Data Manipulation:** Pandas, NumPy
* **Visualization:** Seaborn, Matplotlib
* **Machine Learning:** XGBoost (Extreme Gradient Boosting)
* **Evaluation:** Scikit-Learn (Confusion Matrix, Classification Report)

## 🔍 Key Solution Approaches

### 1. Advanced Feature Engineering 🧠
Instead of blindly feeding data, I created business-logic features:
* **`errorBalanceOrg`:** Calculated the discrepancy between the transaction amount and the pre/post-transaction balances. *Result: This became the #1 predictor of fraud.*
* **`hour_of_day`:** Extracted from the `step` column to identify peak fraud hours (often during low-traffic times).

### 2. Handling Class Imbalance ⚖️
Used `scale_pos_weight` within XGBoost to penalize the model heavily for missing fraud cases, rather than using synthetic oversampling (SMOTE), which preserved the integrity of the original data distribution.

## 📊 Results & Performance

| Metric | Score | Business Impact |
| :--- | :--- | :--- |
| **Recall** | **99.7%** | We catch 997 out of every 1000 fraud attempts. |
| **Precision** | **82%** | High trust; fewer genuine customers get blocked. |
| **AUC-ROC** | **0.99** | Excellent separation between Fraud and Non-Fraud. |

### Confusion Matrix
![Confusion Matrix](Place_Your_Image_Link_Here)
*(The model missed only 5 fraud cases out of 1643)*

## 🚀 Strategic Recommendations
Based on the model insights, the following actions are proposed:
1.  **Kill Switch Rule:** Automatically reject any transfer where `oldBalance - amount != newBalance`.
2.  **Dynamic 2FA:** Trigger OTP verification for transactions with a fraud probability score between 0.5 and 0.8.

## 📂 Project Structure

---
**Author:** Devyansh Thakur

**Connect:** www.linkedin.com/in/devyansh-thakur-8abb6335b
