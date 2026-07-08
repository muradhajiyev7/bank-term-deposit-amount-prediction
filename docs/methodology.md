# Methodology

## Data Cleaning

The workflow keeps `unknown` as an explicit category instead of dropping those rows. In a marketing campaign setting, missing or unknown profile information can itself carry useful signal.

The model is designed for pre-campaign lead prioritization, so the feature set uses information available before outreach:

- `y`: this is the subscription outcome used only for target simulation and validation.
- `duration`: this is only known after the call, so it is not suitable for pre-campaign lead prioritization.

## Target Simulation

The internship-provided dataset does not include real deposit amounts. The notebook simulates `deposit_amount` as follows:

- Clients with `y = no` receive `deposit_amount = 0`.
- Clients with `y = yes` receive a positive amount based on plausible drivers:
  - account balance
  - age
  - job category
  - education
  - loan and housing indicators
  - previous campaign behavior
  - campaign intensity and recency
- Random noise is added to avoid creating an unrealistically deterministic target.
- Final values are clipped to a realistic range to reduce extreme simulated outliers.

## Feature Engineering

Additional features include:

- age buckets
- previous contact flag
- campaign recency flag
- cleaned `pdays`
- contact rate
- positive balance flag
- log positive balance
- combined loan or housing flag

## Modeling

The notebook evaluates:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Random Forest Regressor
- Hist Gradient Boosting Regressor
- XGBoost Regressor
- Two-stage XGBoost expected-value model

The two-stage model performed best because the target is zero-inflated: many clients have zero deposit, while subscribers have positive deposit amounts.

## Evaluation

The project uses:

- RMSE
- MAE
- R2
- residual analysis
- predicted vs actual scatter plot
- campaign decile analysis
- strategy simulation against random targeting

## Explainability

Model interpretation uses:

- linear model coefficients
- XGBoost feature importance
- permutation importance
- SHAP global and individual explanations
