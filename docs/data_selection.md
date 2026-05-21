
**Data Selection**

Goal: This project aims to construct a market-implied credit risk analytics framework linking corporate credit spreads, market regimes, implied default intensity, and simplified CVA estimation. The selected datasets are intended to balance market relevance, data availability, robustness, interpretability, and implementation feasibility.

# Analysis Window

Main analysis period: 2021-05-24 to 2026-05-19
The selected window aims to capture multiple recent market regimes, including:

2021 Q3–Q4  Low-spread risk-on baseline
2022        Aggressive tightening cycle
2023 Q1     Regional banking stress (SVB / Credit Suisse)
2023 Q2–Q4  Credit spread normalization
2024        Soft-landing narrative and spread compression
2025 Q1–Q2  Tariff/trade uncertainty triggered renewed spread widening
2026 Q1     Continued spread volatility under elevated-rate conditions


# Selected Datasets

## Credit Spread Indicators
1. ICE BofA Investment Grade Option-Adjusted Spread (BAMLC0A0CM)
2. High-yield corporate option-adjusted spread (BAMLH0A0HYM2)
3. AAA US Corporate Index Option-Adjusted Spread (BAMLC0A1CAAA)
4. AA US Corporate Index Option-Adjusted Spread (BAMLC0A2CAA)
5. Single-A US Corporate Index Option-Adjusted Spread (BAMLC0A3CA)
6. BBB US Corporate Index Option-Adjusted Spread (BAMLC0A4CBBB)
7. St. Louis Fed Financial Stress Index (weekly, below zero = below-average stress)

## Interest Rate Indicators
1. Yield on 1-year US Treasury constant maturity securities
2. Yield on 2-year US Treasury constant maturity securities
3. Yield on 5-year US Treasury constant maturity securities
4. Yield on 10-year US Treasury constant maturity securities
5. Spread between 10-year and 2-year Treasury yields

## Market Risk Indicators
1. CBOE Volatility Index — the canonical "fear gauge" measuring S&P 500 expected 30-day volatility

## Macro Financial Conditions Indicators
1. Monthly average federal funds rate (percent, not seasonally adjusted)
2. Chicago Fed NFCI (National Financial Conditions Index, weekly, positive = tighter than average)


# Why OAS?
Option-adjusted spread (OAS) was selected as the primary credit spread proxy because it adjusts for embedded bond optionality, captures broad corporate credit conditions, provides stable historical market data, and is suitable for regime and stress analysis.


# Data Sources

Convex Research Desk. (2026)