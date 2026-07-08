# Results

## Best Model

The strongest model is a two-stage XGBoost expected-value model:

1. A classifier estimates subscription probability.
2. A regressor estimates positive deposit amount for likely subscribers.
3. The final expected deposit is calculated as probability multiplied by predicted positive amount.

## Test Performance

| Metric | Value |
|---|---:|
| RMSE | 798.45 |
| MAE | 359.42 |
| R2 | 0.3578 |
| Subscription classifier ROC-AUC | 0.8078 |
| Subscription classifier PR-AUC | 0.4723 |

## Campaign Simulation

| Strategy | Clients Contacted | Actual Total Deposit | Actual Return per Contact |
|---|---:|---:|---:|
| Top 10% | 4,521 | 8.43M | 1,864.37 |
| Top 20% | 9,042 | 10.43M | 1,153.84 |
| Random 20% | 9,042 | 2.77M | 306.31 |

The top-20% model-based strategy produced about 3.77x more actual deposit value than contacting a random 20% of clients.

## Recommendation

If the campaign objective is maximum return per contact, prioritize the top 10%. If the objective is total deposit capture under a 20% contact budget, prioritize the top 20%.

