# Merton-Model
An extended Merton Model for valuation of corporate financial claims under alternative capital structures.
# Valuation of Corporate Financial Claims Under Alternative Capital Structures: An Extended Application of the Merton Model

## Project Overview

This project applies the Merton structural credit risk model to analyse the valuation of corporate financial claims under alternative capital structures.

Vedanta Limited is used as the case study. The model estimates the company's asset value and asset volatility using observed market equity value and historical equity volatility.

It further extends the traditional Merton framework by separating financial claims into senior debt, subordinated debt and equity using a priority-based valuation approach.

## Key Features

- Automated historical stock price retrieval using Yahoo Finance.
- Estimation of equity volatility using historical market data.
- Calibration of asset value and asset volatility.
- Valuation of senior debt, subordinated debt and equity.
- Risk-neutral probability of default estimation.
- Alternative capital structure analysis.
- Debt, volatility, maturity and leverage sensitivity analysis.
- Interactive capital structure simulator.

## Methodology

The model uses the Black-Scholes-Merton framework to estimate asset value and asset volatility.

It then applies a priority-based claims waterfall to estimate the values of senior debt, subordinated debt and equity.

## Tools and Technologies

- Python
- Google Colab
- NumPy
- Pandas
- SciPy
- Matplotlib
- yfinance
- ipywidgets

## Case Study

Company: Vedanta Limited  
Ticker: VEDL.NS  
Valuation Date: 31 March 2026

## Important Assumptions and Limitations

- Total debt is treated as a unified default threshold during calibration.
- Senior and subordinated claims are separated after calibration.
- A representative three-year maturity is used.
- Risk-neutral probability of default is not a real-world default forecast.
- Alternative capital structure scenarios hold asset value and asset volatility constant.

## Research Objective

The objective is to demonstrate how structural credit risk modelling can be extended to understand the valuation of different financial claims and the impact of alternative capital structures.

## Disclaimer

This is an academic research project and does not constitute investment advice or a credit rating.
