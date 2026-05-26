# Regime-Conditional Credit Risk and XVA Framework

An end-to-end quantitative credit risk project built from scratch, covering credit spread decomposition, market regime detection, implied PD term structures, and CVA/DVA/BCVA estimation — developed to study the interaction between market regimes, credit spreads, implied default risk, and counterparty valuation adjustments.


## Project Overview

This project constructs a market-implied credit risk framework using publicly available data, organized into six analytical notebooks:

| Notebook | Topic | Key Methods |
|----------|-------|-------------|
| 01 | Data Processing | Data cleaning, missing value treatment |
| 02 | Spread Decomposition | OLS regression, rolling betas |
| 03 | Regime Detection | Gaussian HMM, K=4 states |
| 04 | Implied PD Term Structure | Hazard rate calibration |
| 05 | CVA / DVA Estimation | Vasicek, Hull-White, MC, UCVA/UDVA/BCVA |
| 06 | Stress Testing | Scenario analysis, $\delta$ CVA quantification |


## Key Results

- Identified four distinct credit market regimes (Risk-On, Normalization, Event-Driven Stress, Macro Tightening) via Gaussian HMM, with average durations of 40–123 trading days
- Demonstrated that VIX-spread and NFCI-spread correlations vary substantially across regimes, highlighting the limitations of static linear models
- Calibrated regime-conditional implied PD term structures: IG 5Y cumulative PD ranges from 6.82% (Risk-On) to 11.31% (Macro Tightening)
- Estimated BCVA on a $100M 5Y IRS: ranges from -$25,286 (Risk-On) to +$33,723 (Macro Tightening), with sign reversal driven by exposure asymmetry under inverted yield curve regimes


## Technical Stack
- Credit spread decomposition and factor analysis
- Gaussian Hidden Markov Models (HMM)
- Hazard rate and implied PD calibration
- Vasicek and Hull-White short-rate modeling
- Monte Carlo simulation for exposure estimation
- UCVA / UDVA / BCVA computation
- Credit DV01 and stress testing
- Regime-conditional risk analysis


## Repository Structure
notebooks/
|-- 01_data_processing.ipynb
|-- 02_spread_decomposition.ipynb
|-- 03_regime_detection.ipynb
|-- 04_implied_pd_term_structure.ipynb
|-- 05_xva_framework.ipynb
|-- 06_stress_testing.ipynb

data/
|-- raw/
|-- processed/

docs/
|-- data_selection.md


## Data Sources

All data sourced from publicly available sources:

- **ICE BofA OAS indices** (downloaded via Convex / sourced from FRED): AAA, IG, BBB, HY corporate spreads
- **US Treasury yields** (downloaded via Convex / sourced from FRED): 1M to 10Y constant maturity
- **Market indicators**: VIX, NFCI, St. Louis FSI, Fed Funds Rate

Sample period: 2021-06-01 to 2026-05-20  
Frequency: Daily (OAS, yields, VIX); 
           Weekly (NFCI, FSI); 
           Monthly (Fed Funds)

Data files must be downloaded separately from Convex (convextrade.com) and placed in data/raw/. See docs/data_selection.md for the full list of required series.


## Methodological Notes

**Recovery Rate**: Uniform 40% (LGD = 60%).

**HMM Model Selection**: K=4 selected over statistically preferred K=5 on the basis of regime stability — K=5 produces two states with average duration < 2 days and nearly identical feature vectors, indicating overfitting.

**IRS Valuation**: Fixed-rate payer, $100M notional, 5Y tenor. ATM par swap rates computed separately for each regime using the corresponding regime-conditional yield curve. Exposure simulated via Hull-White one-factor model (1,000 paths, monthly steps).

**CVA Framework**: Unilateral CVA (UCVA), DVA (UDVA), and Bilateral CVA (BCVA) with survival probability adjustments. Counterparty: BBB-rated. Own entity: IG-rated.


## Disclaimer

This project is for educational and demonstration purposes only. All data is publicly available. No proprietary data, models, or methods from any financial institution are used or referenced.