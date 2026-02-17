# Value-at-Risk Forecasting with Realized Volatility Measures

In this project, we forecast one-day-ahead Value-at-Risk for SPY daily log-returns at confidence levels $\alpha = 1$%, $\alpha = 5$% and $\alpha = 10$%, using intraday-based volatility measures (realized volatility `rv5` and bipower variation `bv`).
We compare three model families:  
(i) **GARCH(1,1)**  
(ii) **HAR-RV**  
(iii) **Quantile Regression**


This repository contains the notebooks to reproduce the analysis, feature engineering, model selection, and backtesting described in the accompanying report : [report.pdf](report/report.pdf).

---

## Project highlights

- Documents volatility clustering and long-memory patterns via ACF plots of `|log_ret|` and `log(rv5)`.
- Builds interpretable features, like  multi-horizon volatility features from `log(rv5)` and jump proxy: `J_t = max(rv5_t - bv_t, 0)` to capture discontinuous moves.
- Uses no-look-ahead chronological split: first 80% train, last 20% test, with rolling forecasting during tuning. 
- Evaluates VaR forecasts with:
  - Empirical violation rate coverage.
  - Quantile loss
  - Kupiec unconditional coverage test
  - A composite score for hyperparameter selection across the 3 alphas

---

## Results

All three approaches pass the Kupiec test at 5% significance on the test set for **$\alpha$ ∈ {1%, 5%, 10%}**, with overall performance favoring **HAR-RV** in this project’s composite ranking.
 



