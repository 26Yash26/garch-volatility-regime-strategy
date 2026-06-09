# GARCH Volatility Regime Strategy

## Overview

This project explores the use of GARCH-based volatility forecasting to identify and classify market volatility regimes in the S&P 500 (SPY).

The primary objective is to build a reliable regime detection framework capable of forecasting future market conditions without look-ahead bias. These forecasts can then be used as inputs for regime-adaptive trading strategies that dynamically adjust their behavior according to prevailing market conditions.

While the current adaptive momentum implementation serves as a proof of concept, the main focus of this project is the development and validation of a robust volatility regime classification system.

---

## Motivation

Financial markets behave differently during low-volatility, normal, and high-volatility environments. Trading strategies that perform well in one regime often underperform in another.

Accurately identifying market regimes in advance can enable:

* Dynamic risk management
* Adaptive position sizing
* Regime-specific signal generation
* Improved portfolio allocation
* Enhanced downside protection during turbulent periods

This project investigates whether GARCH forecasts can provide a reliable foundation for such regime-aware systems.

---

## Methodology

1. **ARCH-LM Test**

   * Verify the presence of conditional heteroskedasticity in SPY returns.

2. **GARCH Model Selection**

   * Fit and compare candidate GARCH models.
   * Select the best specification using information criteria and residual diagnostics.

3. **Rolling Volatility Forecasting**

   * Generate one-day-ahead volatility forecasts using a walk-forward framework.
   * Eliminate look-ahead bias by using only information available at prediction time.

4. **Regime Classification**

   * Convert volatility forecasts into:

     * Low Volatility
     * Medium Volatility
     * High Volatility
   * Use rolling percentile-based thresholds to adapt to changing market conditions.

5. **Strategy Integration**

   * Use predicted regimes to drive adaptive trading rules.
   * Compare against traditional static momentum benchmarks.

---

## Results

### Volatility Forecasting Performance

The GARCH framework demonstrates strong predictive ability for future volatility and successfully identifies volatility regimes with high accuracy.

| Metric                                   | Value |
| ---------------------------------------- | ----- |
| Regime Classification Accuracy           | 87.1% |
| F1 Score                                 | 0.82  |
| Cohen's Kappa                            | 0.75  |
| Forecast–Realised Volatility Correlation | 0.917 |
| Volatility Forecast RMSE                 | 1.73% |

### Key Findings

* Strong ARCH effects were detected in SPY returns.
* GARCH models successfully captured volatility clustering.
* Volatility forecasts exhibited strong correlation with realised volatility.
* Regime classification achieved high out-of-sample accuracy.
* The framework reliably distinguishes between low-, medium-, and high-volatility environments.

These results suggest that GARCH-based forecasting provides a strong signal for market regime identification.

---

## Current Status

The volatility forecasting and regime classification components have been successfully validated and demonstrate strong predictive performance.

A preliminary regime-adaptive momentum strategy was implemented as an initial application of these forecasts. While the current strategy does not consistently outperform a static benchmark, this does not diminish the value of the regime classification framework itself.

The project is actively being extended to investigate:

* Regime-specific momentum parameters
* Dynamic position sizing
* Volatility targeting
* Regime-aware portfolio allocation
* Machine learning models conditioned on predicted regimes
* Multi-asset regime-adaptive strategies

The central research question remains:

> Given accurate volatility regime forecasts, what is the most effective way to convert that information into trading alpha?

---

## Future Work

Planned improvements include:

* EGARCH and GJR-GARCH models
* Hidden Markov Models for regime detection
* Regime-conditioned factor investing
* Reinforcement learning for adaptive decision-making
* Cross-asset regime forecasting
* Alternative volatility measures and realized volatility estimators

---

## Technologies

* Python
* Pandas
* NumPy
* Statsmodels
* ARCH
* Scikit-Learn
* Plotly
* yFinance

---

## Setup

```bash
pip install -r requirements.txt
jupyter notebook garch_regime_strategy.ipynb
```

---

## Data

Daily SPY market data is downloaded automatically using yFinance.

Sample Period:

* 2021 – 2025

No manual data download is required.
