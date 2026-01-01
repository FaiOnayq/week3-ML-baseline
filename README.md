# Model Card — Week 3 Baseline  

## Problem  
- **Target:** `is_high_value` (binary classification)  
- **Unit of analysis:** Individual user (`user_id`)  
- **Decision enabled:** Identify high-value users for targeted marketing or promotions  

---

## Data  
- **Feature table:** `data/processed/features.csv`  
- **Features used:**  
  - `country` (categorical)  
  - `n_orders` (integer)  
  - `avg_amount` (float)  
  - `total_amount` (float)  
- **Forbidden columns:** `is_high_value`  
- **Optional ID column:** `user_id`  

---

## Splits  
- **Holdout strategy:** Random stratified split  
- **Test size:** `0.2`  
- **Random seed:** `42`  

---

## Metrics (Holdout Set)

| Metric       | Baseline | Model |
|--------------|----------|-------|
| ROC AUC      | 0.5      | 1.0   |
| PR AUC       | 0.2      | 1.0   |
| Accuracy     | 0.8      | 1.0   |
| Precision    | 0.0      | 1.0   |
| Recall       | 0.0      | 1.0   |
| F1 Score     | 0.0      | 1.0   |
| Threshold    | 0.5      | 0.5   |

> **Critical Note**:  
> - Baseline performance using LogisticRegression classifier.  
> - **Model achieves perfect metrics**, indicating **strong evidence of data leakage or overfitting**.  


---

## Reproducibility  
- **Run ID:** `2026-01-01T17-27-09Z__classification__seed42`  
- **Environment:** `models/runs/2026-01-01T17-27-09Z__classification__seed42/env/pip_freeze.txt`  
- **Artifacts:**  
  - `model/model.joblib` — Trained model (joblib)  
  - `schema/input_schema.json` — Input spec (columns, dtypes, constraints)  
  - `tables/holdout_predictions.parquet` — Full holdout predictions  


