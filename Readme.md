# Bank Customer Churn Prediction

## Project Overview
Customer churn is a major concern for banks because acquiring new customers is more expensive than retaining existing ones.  
This project demonstrates how machine learning can predict customers likely to leave a bank, enabling proactive retention strategies.

---

## Dataset
The dataset contains demographic, financial, and account-related information for bank customers:

- **Features:**
  - `credit_score`, `country`, `gender`, `age`, `tenure`, `balance`, `products_number`, `credit_card`, `active_member`, `estimated_salary`
- **Target Variable:**
  - `churn` (0 = Customer stayed, 1 = Customer left)
  
**Data Overview:**
- 10,000 records, 12 columns  
- No missing values or duplicates  

---

## Exploratory Data Analysis (EDA)
- Churn distribution shows class imbalance: 7,963 stayed vs 2,037 left.  
- Customers aged 51–60 and those using fewer products are more likely to churn.  
- Feature importance shows `age` and `products_number` as the strongest predictors.

---

## Preprocessing
- **Numerical Features:** MinMaxScaler  
- **Categorical Features:** OneHotEncoder (drop first)  
- **Class Imbalance:** SMOTE (Synthetic Minority Oversampling Technique)  

---

## Modeling
The following models were trained using pipelines:

| Model | Key Notes |
|-------|-----------|
| Logistic Regression | Baseline model with class_weight balanced |
| Random Forest | Slight improvement with SMOTE |
| AdaBoost | Good recall for churned customers |
| Gradient Boosting | Best overall performance; hyperparameter tuning applied |

**Hyperparameter Tuning:**  
- Applied on Gradient Boosting Classifier using GridSearchCV  
- Tuned parameters: `n_estimators`, `learning_rate`, `max_depth`  

---

## Evaluation
- Metrics used: Precision, Recall, F1-score, ROC-AUC  
- Focused on recall and ROC-AUC to identify churned customers accurately  

**Model Performance (after tuning Gradient Boosting):**  

| Model | Precision | Recall | F1-score | ROC-AUC |
|-------|-----------|--------|----------|---------|
| Gradient Boosting (Tuned) | 0.60 | 0.70 | 0.64 | 0.873 |

---

## Insights
- Age is the most significant predictor of churn.  
- Customers with fewer products have a higher likelihood of leaving.  
- Targeting retention strategies to at-risk segments can reduce churn and improve lifetime value.

---

## Business Recommendations
- Focus on customers aged 51–60 and those using fewer banking products.  
- Offer personalized services and cross-selling opportunities.  
- Use predictive churn models for early intervention.

---

## How to Run
1. Clone the repository:  
   ```bash
   git clone <repository-url>
