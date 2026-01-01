# Model Card — Week 3 Baseline

## Problem
- **Target:** `is_high_value` (binary classification)  
- **Unit of analysis:** Individual user (`user_id`)  
- **Decision enabled:** Identify high-value users for targeted marketing or promotions  

## Data
- **Feature table:** `data/processed/features.csv`  
- **Dataset hash (sha256):** `123743223b535a87a4f28979ddec5b57d5d347c4c0c8bd8f5ab17e95ce460273`  
- **Features used:**  
  - `country` (categorical)  
  - `n_orders` (integer)  
  - `avg_amount` (float)  
  - `total_amount` (float)  
- **Forbidden columns:** `is_high_value`  
- **Optional ID column:** `user_id`  

## Splits
- **Holdout:** Random stratified, `test_size=0.2`, `seed=42`  

## Metrics (holdout)
| Metric       | Baseline | Model |
|--------------|----------|-------|
| ROC AUC      | 0.5      | 1.0   |
| PR AUC       | 0.2      | 1.0   |
| Accuracy     | 0.8      | 1.0   |
| Precision    | 0.0      | 1.0   |
| Recall       | 0.0      | 1.0   |
| F1 Score     | 0.0      | 1.0   |
| Threshold    | 0.5      | 0.5   |

**Notes:**  
- The baseline model performs poorly (random for ROC AUC, zero precision/recall).  
- The model shows perfect metrics on holdout (`roc_auc=1.0`), which strongly suggests **data leakage or overfitting** as the predict on same training dataset. This should be investigated before deployment.  

## Limitations
- Extremely high holdout performance likely indicates overfitting or leakage.  
- Limited feature set may not capture all relevant drivers of high-value behavior.  
- No temporal or sequential modeling; assumes independent user behavior.  

## Monitoring sketch
- Monitor model predictions for drift in positive rate over time.  
- Track precision/recall on new incoming data to detect performance degradation.  
- Audit feature distributions and check for any new unseen categories in `country`.  

## Reproducibility
- **Run id:** `2026-01-01T17-27-09Z__classification__seed42`  
- **Git commit:** `<paste commit>`  
- **Environment:** `models/runs/2026-01-01T17-27-09Z__classification__seed42/env/pip_freeze.txt`  
- **Artifacts:**  
  - Model: `model/model.joblib`  
  - Schema: `schema/input_schema.json`  
  - Holdout predictions: `tables/holdout_predictions.parquet`  

