\# Individual Contribution



\## What did you personally contribute the most?



I contributed most heavily to feature engineering and model development. I created aggregated features such as stream\_count and add\_on\_count, grouped tenure and age into meaningful buckets, and removed non predictive identifiers and low variation variables. I also led the hyperparameter tuning process using cross validation to optimize model performance, particularly for the XGBoost model.



---



\## What is one decision or approach you personally advocated for and why?



I advocated for using XGBoost as the primary model instead of relying solely on Random Forest. My reasoning was that boosting methods sequentially reduce error and often perform better on structured tabular data with nonlinear relationships. This decision improved cross validated ROC AUC performance and provided clearer feature importance insights that translated well into business recommendations.



---



\## Lessons Learned and What I Would Improve



One major lesson was the importance of comparing training performance to cross-validation performance to properly diagnose overfitting. It reinforced how bias variance tradeoffs directly impact real world reliability.



If given more time, I would expand hyperparameter tuning to include additional regularization and imbalance-handling parameters such as gamma, scale\_pos\_weight, and L1/L2 penalties.

