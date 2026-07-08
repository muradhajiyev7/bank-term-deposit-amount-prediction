# Project Overview

## Objective

Build a regression-based machine learning model that estimates how much a client is likely to deposit in a term deposit product, then use the predictions to guide campaign targeting under a limited marketing budget.

## Business Context

Marketing teams often need more than a yes/no subscription prediction. A client with a high subscription probability may still represent a low expected deposit amount, while another client with moderate probability may be more valuable because the expected deposit is higher.

This project treats the problem as an expected-value ranking task:

- Estimate expected term deposit amount per client.
- Rank clients by predicted value.
- Compare top-k targeting against random targeting.
- Recommend a campaign strategy based on return per contact and total expected value.

## Dataset

The dataset was provided during my internship for a banking analytics assignment. Because the dataset does not contain actual term deposit amounts, the `deposit_amount` target is simulated for modeling and strategy evaluation.

## Key Deliverables

- Clean, executed final notebook
- Model comparison across regression approaches
- Pre-campaign modeling setup
- SHAP and feature importance interpretation
- Campaign simulation with top-10%, top-20%, and random-20% strategies
- Summary report
