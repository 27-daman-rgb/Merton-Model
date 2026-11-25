# Valuation of Corporate Financial Claims Under Alternative Capital Structures
### An Extended Application of the Merton Model

## 1. Project Overview

This project develops an extended application of the **Merton Structural Credit Risk Model** to analyse the valuation of corporate financial claims under alternative capital structures.

The model uses **Vedanta Limited** as a case study and applies Python-based financial modelling to estimate the company's asset value and asset volatility using observed market equity value and historical equity volatility.

It further extends the standard Merton framework by separating corporate financial claims into:

- Senior Debt
- Subordinated Debt
- Equity

The project also examines how changes in debt levels, asset volatility and maturity affect the value of these claims.

The model is implemented in Python and includes automated market data retrieval, numerical calibration, sensitivity analysis and an interactive capital structure simulator.

---

## 2. Research Objectives

The main objectives of this project are:

1. To apply the Merton structural credit risk framework to a publicly listed company.
2. To estimate unobservable corporate asset value and asset volatility using market information.
3. To estimate the model-implied values of senior debt, subordinated debt and equity.
4. To calculate distance to default and risk-neutral probability of default.
5. To examine the impact of alternative capital structures on financial claim values.
6. To perform sensitivity analysis under different volatility, maturity and leverage assumptions.
7. To develop an interactive Python-based model for analysing corporate financial claims.

---

## 3. Understanding the Merton Model

The Merton Model is a structural credit risk model based on the Black-Scholes option pricing framework.

It treats a company's equity as a call option on the value of its assets, with debt acting as the exercise price.

At the debt maturity date:

- If the company's asset value exceeds its debt obligations, debt holders are paid and shareholders receive the remaining value.
- If the company's asset value is below its debt obligations, the company defaults and equity holders receive nothing.

The model estimates the value of corporate assets and the risk associated with debt repayment.

### Standard Merton Equations

**Equity Value**

E = V × N(d1) − D × e^(-rT) × N(d2)

**First term**

d1 = [ln(V/D) + (r + 0.5 × σV²) × T] / (σV × √T)

**Second term**

d2 = d1 − σV × √T

**Equity Volatility**

σE = (V/E) × N(d1) × σV

Where:

| Symbol | Meaning |
|---|---|
| V | Market value of company assets |
| E | Market value of equity |
| D | Total debt |
| r | Continuously compounded risk-free rate |
| T | Debt maturity |
| σV | Asset volatility |
| σE | Equity volatility |
| N(.) | Cumulative standard normal distribution |

The model calibrates asset value and asset volatility by matching the theoretical equity value and equity volatility with observed market data.

---

## 4. Extension: Valuation of Financial Claims

The project extends the standard Merton framework by separating financial claims according to their priority in the capital structure.

The assumed payment priority is:

1. Senior Debt
2. Subordinated Debt
3. Equity

Let:

- S = Senior Debt
- J = Subordinated Debt
- D = S + J = Total Debt

The claims are valued using a common maturity and a priority-based payoff structure.

### A. Senior Debt

Senior debt holders have the highest repayment priority.

Their value is calculated as:

Senior Debt Value = S × e^(-rT) − Put(V, S)

### B. Subordinated Debt

Subordinated debt holders receive payment only after senior debt obligations are satisfied.

Subordinated Debt Value = Call(V, S) − Call(V, S + J)

### C. Equity

Equity holders receive the residual value after all debt obligations have been satisfied.

Equity Value = Call(V, S + J)

### D. Reconciliation

The model checks whether the estimated values of all financial claims reconcile with the estimated asset value.

Total Claims = Senior Debt Value + Subordinated Debt Value + Equity Value

Total Claims should equal Estimated Asset Value, subject to numerical precision.

---

## 5. Credit Risk Indicators

The model calculates two important credit risk indicators.

### Distance to Default

The model uses d2 as its risk-neutral default-distance measure.

A higher positive d2 indicates a lower model-implied probability of default under the selected assumptions.

### Risk-Neutral Probability of Default

Risk-neutral probability of default is calculated as:

PD = N(-d2)

This represents the probability of the company's asset value falling below the debt threshold at maturity under the risk-neutral model framework.

It should not be interpreted as an actual or real-world forecast of corporate default.

---

## 6. Technology Stack

The project uses the following tools and Python libraries:

| Technology | Application |
|---|---|
| Python | Core programming and financial modelling |
| NumPy | Numerical calculations |
| Pandas | Financial data handling and analysis |
| SciPy | Numerical optimisation and calibration |
| yfinance | Historical stock market data retrieval |
| Matplotlib | Financial charts and visualisation |
| ipywidgets | Interactive input form and simulator |
| Google Colab | Development and execution environment |

---

## 7. Model Architecture and Workflow

The model follows a structured process.

### Step 1: Company Input Form

The user enters:

- Company name
- Yahoo Finance ticker
- Valuation date
- Historical volatility start and end dates
- Shares outstanding
- Senior debt
- Subordinated debt
- Representative debt maturity
- Government bond yield

All financial amounts are entered in INR crore and shares outstanding in crore shares.

### Step 2: Historical Market Data Retrieval

The model automatically retrieves historical share prices through Yahoo Finance.

It uses:

- Closing price (Close) to calculate market capitalisation.
- Adjusted closing price (Adj Close) to calculate historical equity volatility.

Historical equity volatility is estimated using daily logarithmic returns and annualised using 252 trading days.

### Step 3: Market Equity Calculation

Market equity is calculated as:

Market Equity = Share Price × Shares Outstanding

### Step 4: Risk-Free Rate Conversion

The effective annual government bond yield is converted into a continuously compounded risk-free rate:

r = ln(1 + y)

Where y is the annual government bond yield expressed as a decimal.

### Step 5: Asset Value and Asset Volatility Calibration

The model uses SciPy's least-squares optimisation to estimate:

- Asset Value
- Asset Volatility

The calibration matches the theoretical equity value and equity volatility with their observed market values.

### Step 6: Financial Claims Valuation

The estimated asset value and asset volatility are used to calculate the values of:

- Senior Debt
- Subordinated Debt
- Equity

### Step 7: Credit Risk Analysis

The model calculates distance to default and risk-neutral probability of default.

### Step 8: Alternative Capital Structure Analysis

The model examines debt scenarios of:

- 75% of base debt
- 100% of base debt
- 125% of base debt
- 150% of base debt

### Step 9: Sensitivity Analysis

The model performs four types of analysis:

- Debt sensitivity
- Asset volatility sensitivity
- Maturity sensitivity
- Leverage sensitivity

### Step 10: Interactive Capital Structure Simulator

An interactive simulator allows users to change:

- Debt multiplier
- Asset volatility
- Maturity

The model recalculates financial claim values and displays the resulting claim distribution.

---

## 8. Case Study: Vedanta Limited

The model uses Vedanta Limited as the case study.

| Parameter | Input |
|---|---:|
| Company | Vedanta Limited |
| Yahoo Finance Ticker | VEDL.NS |
| Valuation Date | 31 March 2026 |
| Share Price Date | 30 March 2026 |
| Historical Share Price | ₹654.80 |
| Shares Outstanding | 391.0388 crore |
| Senior Debt | ₹10,648 crore |
| Subordinated Debt | ₹0 crore |
| Total Debt | ₹10,648 crore |
| Representative Maturity | 3 years |
| Government Bond Yield | 6.85% |

The debt input is based on the selected annual-report borrowing figures for continuing operations. The equity and debt measurement basis should be considered when interpreting the results.

### Market and Calibration Results

| Parameter | Estimated Value |
|---|---:|
| Market Equity | ₹256,052.21 crore |
| Historical Equity Volatility | 37.5356% |
| Estimated Asset Value | ₹264,780.80 crore |
| Estimated Asset Volatility | 36.2982% |
| Model Equity Value | ₹256,052.21 crore |
| Equity Calibration Error | Approximately 0% |
| Volatility Calibration Error | Approximately 0% |

### Valuation of Financial Claims

| Financial Claim | Model Value |
|---|---:|
| Senior Debt | ₹8,728.60 crore |
| Subordinated Debt | ₹0 crore |
| Equity | ₹256,052.21 crore |
| Total Claims | ₹264,780.80 crore |
| Estimated Asset Value | ₹264,780.80 crore |

The model's financial claims reconcile with the estimated asset value, subject to numerical precision.

### Credit Risk Results

| Indicator | Result |
|---|---:|
| Distance to Default (d2) | 5.1132 |
| Risk-Neutral PD | Approximately 0.000016% |

The displayed probability is very small and may appear as 0.00% when rounded to two decimal places. It is not an actual zero probability.

---

## 9. Alternative Capital Structure Analysis

The model examines how changing debt levels affects the estimated value of equity and senior debt.

| Debt Scenario | Total Debt (₹ crore) | Equity Value (₹ crore) |
|---|---:|---:|
| 75% | 7,986 | 258,234.35 |
| 100% | 10,648 | 256,052.21 |
| 125% | 13,310 | 253,870.06 |
| 150% | 15,972 | 251,687.91 |

Under the selected assumptions, increasing debt reduces the modelled value of equity.

This happens because equity holders receive the residual value after debt holders' claims are satisfied.

The scenarios hold asset value and asset volatility constant. They therefore represent hypothetical capital structure comparisons rather than fully recalibrated forecasts.

---

## 10. Sensitivity Analysis

The project includes the following sensitivity analyses.

### Debt Sensitivity

Examines the impact of different debt levels on senior debt, subordinated debt and equity values.

### Asset Volatility Sensitivity

Studies how changes in asset volatility influence the value of different financial claims and the model-implied default probability.

### Maturity Sensitivity

Examines the effect of changing the representative maturity on the estimated values of financial claims.

### Leverage Sensitivity

Studies how changes in the debt multiplier affect the company's capital structure and equity value.

The sensitivity analyses hold other selected model inputs constant unless specifically varied.

---

## 11. Key Research Findings

The application of the extended Merton framework to Vedanta Limited demonstrates the following:

1. Asset value and asset volatility can be estimated by calibrating the Merton model to observed market equity value and historical equity volatility.
2. Senior debt, subordinated debt and equity can be valued separately using a priority-based claims structure.
3. The model-estimated value of senior debt is lower than its face value under the selected assumptions.
4. A higher debt level reduces the modelled value of equity when asset value and asset volatility are held constant.
5. Asset volatility and maturity influence the valuation of corporate financial claims.
6. The model produces a very low risk-neutral probability of default under the selected company inputs.

---

## 12. Model Assumptions and Limitations

The model is based on several simplifying assumptions:

1. Total debt is treated as one unified default threshold during standard Merton calibration.
2. Senior and subordinated claims are separated after calibration using a common-maturity priority waterfall.
3. The model assumes a lognormal asset-value process.
4. Asset volatility and the risk-free rate are assumed to remain constant over the model horizon.
5. Risk-neutral probability of default is not a real-world default forecast.
6. A representative three-year maturity simplifies the company's actual debt maturity schedule.
7. Alternative capital structure scenarios hold asset value and asset volatility constant rather than recalibrating them.
8. Debt priority must be supported by contractual information. Unsecured debt is not automatically subordinated.
9. Historical market data retrieved through Yahoo Finance may be affected by adjustments and subsequent data revisions.
10. The consistency of the equity market capitalisation and annual-report debt measurement basis must be considered.

These limitations should be considered when interpreting the results.

---

## 13. How to Run the Project

### Option 1: Google Colab

1. Download the Jupyter Notebook from this repository.
2. Open [Google Colab](https://colab.research.google.com/).
3. Upload the `.ipynb` file.
4. Run the notebook.
5. Enter the company information and financial inputs in the interactive form.
6. Submit the form to execute the model.

The notebook installs the required Python libraries when executed.

### Option 2: Local Python Environment

Clone the repository:

```bash
git clone https://github.com/YOUR-USERNAME/merton-model-corporate-valuation.git
```

Move into the project folder:

```bash
cd merton-model-corporate-valuation
```

Install the dependencies:

```bash
pip install -r requirements.txt
```

Run the Python script:

```bash
python Merton_Model.py
```

Note: The interactive input form and simulator are designed for a Jupyter or Google Colab environment. The notebook is the recommended way to run the complete interactive version.

---

## 14. Project Structure

```text
merton-model-corporate-valuation/
│
├── README.md
├── Merton_Model_Vedanta.ipynb
├── Merton_Model.py
├── requirements.txt
└── .gitignore
```

---

## 15. Disclaimer

This project has been developed for academic research and educational purposes.

The model outputs depend on the selected market data, financial inputs and theoretical assumptions. They should not be treated as investment recommendations, credit ratings or guarantees of a company's ability to meet its financial obligations.

---

## 16. Author

**Developed as part of a PGDM Finance research project.**

Research Topic: Valuation of Corporate Financial Claims Under Alternative Capital Structures: An Extended Application of the Merton Model.

**Focus Areas:** Financial Modelling | Credit Risk Analysis | Python | Corporate Finance | Structural Credit Risk Modelling
