# Financial Crime Risk Modeling (AML)
**Champion vs. Challenger Framework for Imbalanced Credit Card Fraud**

### Objective
To identify fraudulent credit card transactions within a highly imbalanced dataset (0.17% fraud rate) using tree-based machine learning algorithms. 

### Methodology
* **Data Engineering:** Handled 28 anonymized PCA vectors and utilized `RobustScaler` to mathematically neutralize extreme financial outliers in transaction amounts without distorting vector distances.
* **Imbalance Mitigation:** Deployed **SMOTE** (Synthetic Minority Over-sampling Technique) exclusively on the training split to generate a mathematically balanced dataset (50/50) while strictly preventing data leakage into the real-world test set.
* **Model Selection:** Utilized a **Champion vs. Challenger** architecture, benchmarking an Extreme Gradient Boosting (XGBoost) baseline against a Random Forest classifier. 
* **Hyperparameter Tuning:** Executed `GridSearchCV` optimized specifically for the **F1-Score** to prioritize risk mitigation (Recall) while heavily suppressing false positive customer alerts (Precision).

### The Results (The Plot Twist)
While XGBoost initially performed well, it showed slight overfitting on the synthetic SMOTE data, leading to a high false-positive rate. 

The tuned **Random Forest** ultimately won the Champion title. By allowing the trees to grow deeper (`max_depth=20`) and increasing the estimator count, it stabilized against the complex financial data. 

**Final Model Performance (Random Forest):**
* **F1-Score:** 0.83
* **Recall:** 86% (Successfully caught 74 out of 84 actual criminals)
* **Precision:** 81% (Drastically reduced false alarms for safe customers)
