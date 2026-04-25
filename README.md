# ACC102 Track 2: Stock Price Crash Risk & Earnings Management Analysis

## 1. Problem & User
This project examines whether earnings management (measured by accruals) is associated with future stock price crash risk. The target audience is academic researchers and financial analysts interested in firm-level risk and accounting quality.

## 2. Data
- **Source**: WRDS (Compustat, CRSP, CCM Linking Table)
- **Access Date**: April 2026
- **Sample Period**: 2018–2023
- **Key Fields**: at, ni, act, che, lct, dlc, txp, oancf, lt, ceq, csho, prcc_f, permno, date, ret, vol, shrout
- **Note**: WRDS subscription lacks sale, rect, and ppegt. The project uses Total Accruals (Cash Flow method) as the primary measure.
- Data is loaded from local CSV files (not directly from WRDS), so the project can run offline.

## 3. Methods
The Python workflow includes:
1. Data Retrieval from WRDS (or local CSV fallback)
2. Data Cleaning and lagged variable construction
3. Crash Risk Metrics: negative skewness (ncskew), down-to-up volatility (duvol), crash count
4. Accruals Calculation: (ni - oancf) / avg_at, with winsorization
5. Regression Analysis: Panel FE with clustered SE, Fama-MacBeth, VIF diagnostics
6. Visualization: quintile analysis, coefficient comparison, correlation heatmap

## 4. Key Findings
- Total accruals show a positive but statistically insignificant relationship with crash risk (coef = 0.076, p = 0.712). Only control variables like return volatility (sigma) and profitability (roa) are significant.
- "The positive coefficient direction is consistent across Panel FE and Fama-MacBeth specifications, though statistical significance is not achieved in this sample."
- Quintile analysis shows monotonic increase in crash risk from Q1 to Q5

## 5. How to Run
1. Clone this repository
2. Install dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn scipy statsmodels linearmodels scikit-learn
3. Open `acc102_analysis.ipynb` in JupyterLab
4. Run all cells from top to bottom
5. Outputs saved to `figures/` and `tables/`

## 6. Product Link / Demo
- GitHub Repository: [Link to be added after repository creation]
- Demo Video: [Link to be added after recording]

## 7. Limitations & Next Steps
- Limitation: WRDS lacks sale, rect, ppegt, so full Jones Model cannot be implemented. Total accruals used as proxy.
- Next Step: Implement modified Jones Model with complete data
- Next Step: Add Propensity Score Matching (PSM) for causal inference

## 8. AI Use Note
AI tools (kimi/GitHub Copilot, April 2026) were used for code debugging and documentation. Full disclosure is provided in the reflection report.

## 9. Repository Structure
.
├── notebook.ipynb
├── README.md
├── data/
│   ├── compustat_raw.csv
│   ├── crsp_daily.csv
│   └── ccm_link.csv
├── figures/
└── tables/



  
