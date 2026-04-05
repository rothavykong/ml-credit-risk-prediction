# Loan Default Risk Prediction & Business Intelligence Dashboard

**Tools:** Python · Scikit-learn · SQL · Power BI · DAX · SQLite

## Project Overview

Banks lose billions of dollars every year approving loans to applicants who default. This project builds a machine learning model that predicts whether a loan applicant will default before the loan is issued, and translates those predictions into a business intelligence dashboard that helps risk managers make smarter lending decisions.

Using 300,000+ real loan applicants from the [Home Credit Default Risk dataset](https://www.kaggle.com/competitions/home-credit-default-risk), this project covers the full data science pipeline — from raw data cleaning all the way to an interactive Power BI dashboard showing real dollar impact.

## Key Results

| Metric | Value |
|--------|-------|
| ROC-AUC | 0.75 |
| Recall (at threshold 0.40) | 81% |
| Defaulters correctly identified | 4,026 out of 4,965 |
| Estimated losses prevented | ~$777 Million |
| Total loan portfolio screened | ~$6 Billion |

> At threshold 0.40, the model catches 81 out of every 100 actual defaulters before the loan is issued.

## Business Problem

Making inaccurate lending decisions leads to two types of costly mistakes:

- **False Negatives** — approving a borrower who defaults. Average loss: $300,000 per loan (60% of $500,000)
- **False Positives** — rejecting a borrower who would have repaid. Average opportunity cost: $40,000 per loan (8% of $500,000)

The cost of a false negative is **7.5x more expensive** than a false positive, which is why we prioritized recall over precision and chose a lower threshold of 0.40.

## Datasets

| Table | Description | Rows |
|-------|-------------|------|
| `application_train` | Main applicant demographics and loan info | 307,511 |
| `bureau` | Credit history with other financial institutions | 1,716,428 |
| `previous_application` | Past loan applications at Home Credit | 1,670,214 |
| `installments_payments` | Monthly payment history on previous loans | 13,605,401 |

## What I Built

### 1. Machine Learning Model (Python)
- Merged 4 raw datasets into one modeling table
- Handled missing values using MAR/MCAR/MNAR classification strategy
- Engineered 6 key features to reduce multicollinearity
- Trained Logistic Regression with GridSearchCV and class_weight='balanced'
- Tuned decision threshold to 0.40 to maximize recall

### 2. SQL Star Schema
- Designed a 5 table star schema with FACT_LOAN_APPLICANT at the center
- Built dimension tables for applicant demographics, credit history, installment behavior and previous applications
- All tables connected through SK_ID_CURR as the unique key

### 3. Power BI Dashboard (4 pages)
- **Page 1 — Executive Summary:** Dynamic KPI cards driven by a What-If threshold slider showing defaulters caught, losses prevented, opportunity cost and net savings
- **Page 2 — Applicant Risk Profiles:** Default rate broken down by education, income type, gender and family status
- **Page 3 — Behavioral Signals:** Credit history and payment behavior patterns that predict default
- **Page 4 — Financial Cost Analysis:** Threshold trade-off curve showing the relationship between losses prevented and opportunity cost across all thresholds

### 4. DAX Measures
Built 7 dynamic DAX measures including:
- `Defaulters Caught` and `Defaulters Missed` — update live with threshold slider
- `Losses Prevented ($)` — true positives × $500,000 × 60% loss rate
- `Opportunity Cost ($)` — false positives × $500,000 × 8% interest rate
- `Net Savings ($)` — bottom line financial impact at any threshold
- `Total Loans at Risk ($)` — total portfolio exposure at current threshold
- `Model Recall` — dynamic recall % at current threshold

## Key Engineered Features

| Feature | Description | Why It Matters |
|---------|-------------|----------------|
| `ANNUITY_INCOME_RATIO` | Monthly payment as % of income | Measures payment burden |
| `LOAN_INCOME_RATIO` | Loan amount as % of income | Measures total debt burden |
| `BUREAU_DEBT_UTILIZATION` | Credit used vs credit limit | High utilization signals financial stress |
| `INST_AVG_DELAY` | Average days late on payments | Past late payments predict future default |
| `PREV_APPROVAL_RATE` | % of past applications approved | Banks' historical judgment of this applicant |
| `EXT_SOURCE_2/3` | External credit bureau risk scores | Strong independent default predictors |

## Project Structure

```
loan-default-risk/
    ├── Project_Report.ipynb          # Full modeling pipeline
    ├── powerbi_exports/              # Cleaned CSV files for Power BI
    │     ├── application_train.csv
    │     ├── bureau.csv
    │     ├── installments_payments.csv
    │     ├── previous_application.csv
    │     └── model_output.csv
    ├── Loan_Default_Risk_Dashboard.pdf  # Dashboard PDF export
    ├── screenshots/                  # Dashboard page screenshots
    │     ├── page1_executive_summary.png
    │     ├── page2_risk_profiles.png
    │     ├── page3_behavioral_signals.png
    │     └── page4_financial_analysis.png
    └── README.md
```

## How to Run

### Requirements
```
pip install pandas numpy matplotlib seaborn scikit-learn
```

### Steps
1. Download the 4 raw CSV files from [Kaggle](https://www.kaggle.com/competitions/home-credit-default-risk)
2. Place them in the same folder as `Project_Report.ipynb`
3. Open `Project_Report.ipynb` in Jupyter Notebook
4. Run all cells top to bottom
5. The cleaned CSV files will be exported to the `powerbi_exports` folder automatically
6. Open `Loan_Default_Risk_Dashboard.pbix` in Power BI Desktop and refresh the data source to point to your exported CSV files

## Tools & Technologies

| Category | Tool |
|----------|------|
| Data manipulation | Python, Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Machine learning | Scikit-learn |
| Database | SQLite, SQL |
| Business Intelligence | Power BI Desktop |
| Dashboard calculations | DAX |

## Acknowledgements

Dataset: Home Credit Default Risk — sourced from [Kaggle](https://www.kaggle.com/competitions/home-credit-default-risk).

AI-assisted code review (Claude, ChatGPT) was used during development to validate implementation patterns and explore feature engineering strategies. All modeling decisions, feature selection rationale, and analytical conclusions are our own work.
