# Bank Term Deposit Amount Prediction

![Python](https://img.shields.io/badge/Python-3.10-blue)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-Modeling-orange)
![XGBoost](https://img.shields.io/badge/XGBoost-Gradient%20Boosting-red)
![Task](https://img.shields.io/badge/Task-Regression%20%2B%20Campaign%20Strategy-green)
![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)

Regression and campaign strategy project for estimating expected term deposit value from a bank marketing dataset provided during my internship. Since deposit amounts are not included in the dataset, a realistic `deposit_amount` target is simulated and then modeled.

## Project Goal

The bank can only contact a limited number of clients. Instead of only predicting whether a client may subscribe, this project estimates the expected deposit amount and uses those predictions to prioritize high-value leads.

The final notebook covers:

- Data understanding and cleaning
- Realistic target simulation for `deposit_amount`
- Exploratory data analysis
- Feature engineering
- Linear, regularized, tree-based, and XGBoost regression models
- Hyperparameter tuning
- SHAP and feature-importance based explainability
- Campaign targeting simulation for top-k client selection

## Final Results

Best model: **two-stage XGBoost expected-value model**

1. Predict probability of subscription.
2. Predict positive deposit amount conditional on subscription.
3. Multiply both values to estimate expected deposit per client.

| Metric | Value |
|---|---:|
| RMSE | 798.45 |
| MAE | 359.42 |
| R2 | 0.3578 |
| Subscription classifier ROC-AUC | 0.8078 |
| Subscription classifier PR-AUC | 0.4723 |

Campaign simulation:

| Strategy | Clients Contacted | Actual Total Deposit | Actual Return per Contact |
|---|---:|---:|---:|
| Top 10% | 4,521 | 8.43M | 1,864.37 |
| Top 20% | 9,042 | 10.43M | 1,153.84 |
| Random 20% | 9,042 | 2.77M | 306.31 |

Using the model to target the top 20% of clients produced about **3.77x higher actual deposit value** than random 20% targeting in the simulation.

## Repository Structure

```text
.
├── data/
│   └── raw/
│       └── bank-full.csv
├── docs/
│   ├── methodology.md
│   ├── project_overview.md
│   └── results.md
├── notebooks/
│   └── term_deposit_amount_prediction_final.ipynb
├── outputs/
│   └── .gitkeep
├── reports/
│   └── term_deposit_amount_prediction_report.pdf
├── LICENSE
├── README.md
└── requirements.txt
```

## How to Run

```bash
pip install -r requirements.txt
```

Open and run:

```text
notebooks/term_deposit_amount_prediction_final.ipynb
```

The notebook has already been executed, so GitHub will display the charts, model tables, SHAP summary, residual analysis, and campaign simulation outputs directly.

## Dataset

The dataset was provided during my internship for a banking analytics assignment. It includes client demographic, financial, and marketing campaign variables, but it does not include actual deposit amounts. The target variable in this project is simulated using transparent business rules described in the notebook and methodology document.

## Recommendation

For a campaign budget limited to 20% of clients, the bank should prioritize clients ranked highest by predicted expected deposit. The top 10% is best for efficiency per contact, while the top 20% captures more total expected value under the stated budget.
