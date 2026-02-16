# Customer Churn Prediction Project

## Business Problem

Customer churn represents a significant revenue risk for subscription-based businesses. The goal of this project is to identify which customers are most likely to churn and understand the key drivers behind attrition using machine learning models. These insights can help the business prioritize retention efforts and reduce revenue loss.

---

## Key Results

- XGBoost achieved a cross-validated ROC-AUC of approximately 0.90, outperforming baseline models.
- Customers without add-on security services had churn rates over 27 percentage points higher than those with security services.
- Shorter tenure and higher monthly fees were among the strongest predictors of churn.

---

## How to Run This Project

1. Clone this repository to your local machine.
2. Install required packages (scikit-learn, pandas, numpy, matplotlib, xgboost).
3. Open the Jupyter Notebook file in your coding environment.
4. Run the notebook cells sequentially (data cleaning → feature engineering → modeling → evaluation).
5. Review model performance metrics and feature importance outputs.

---

## Limitation / Risk

This model is trained on historical data and assumes customer behavior patterns remain stable over time. If pricing structures, product bundles, or market conditions change significantly, the model’s performance may decline and require retraining and monitoring.
