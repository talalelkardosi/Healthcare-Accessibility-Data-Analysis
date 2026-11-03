# Financial Hardship and Equity in Healthcare: Empirical Cross-Country Analysis

**Project:** Healthcare Accessibility & Financial Protection Cross-Country Study  
**Phase:** Phase 2 — Exploratory & Inferential Data Analysis  
**Analyst:** Abdelrahman (Task 5 Lead)  
**Dataset Analyzed:** `03_Integrated_Datasets/integrated_healthcare_dataset.csv` (Central Integrated Repository)  

---

## 1. Executive Summary & Research Questions

### Primary Research Question
> **How are healthcare-related financial hardship and equity indicators distributed across countries, and how are they associated with essential healthcare service coverage, out-of-pocket health expenditure, and macroeconomic development?**

### Core Findings at a Glance
1. **Severe Pro-Rich Inequality**: Financial hardship is heavily concentrated among the poorest segments of society. Across 1,038 country-year surveys, an average of **54.69%** of individuals in the poorest wealth quintile (Q1) experience financial hardship, compared to only **2.65%** in the richest quintile (Q5), yielding an average **Equity Gap of 52.05 percentage points** (Friedman $\chi^2 = 3301.95, p < 0.0001$).
2. **Impoverishment Drives Total Hardship**: Total financial hardship (`Financial_Hardship_Total_Pct`, mean 20.56%) is overwhelmingly driven by impoverishing health spending (`Impoverishing_Spending_Pct`, mean 16.93%, Spearman $\rho = 0.9703, p < 0.0001$). Large health spending without impoverishment (`Large_Spending_Pct`) affects only 3.63% of the population on average and represents a distinct financing phenomenon (Spearman $\rho = 0.3550$).
3. **Strong Structural Buffers**: Total financial hardship exhibits a robust negative non-linear relationship with economic prosperity ($\rho = -0.7061$ against GDP per capita PPP) and universal health coverage ($\rho = -0.6219$ against UHC Service Coverage Index), alongside a strong positive association with health financing reliance on out-of-pocket expenditure ($\rho = 0.5797$). These associations remain statistically significant ($p < 0.0001$) even when restricting analysis cross-sectionally to the latest available survey per country.

---

## 2. Dataset Scope, Coverage, and Missingness Architecture

The central integrated dataset (`integrated_healthcare_dataset.csv`) contains **12,855 rows** spanning **196 countries** over a 66-year temporal window (1960–2025). 

Because financial hardship data originates from nationally representative household income and expenditure surveys rather than annual administrative time series, its coverage structure is non-continuous:
* **Target Sample Size**: **1,079 country-year observations** across **165 countries** spanning 39 survey years (1985–2024).
* **Missingness Context**: While 91.61% of total dataset rows lack financial hardship measurements, this reflects the absence of household surveys in non-survey years rather than data corruption.
* **Excluded Entities**: In strict adherence to project integration governance, 9 observations associated with 3 non-standard ISO3 codes (`XKX` [Kosovo], `TKL` [Tokelau], and `WLF` [Wallis and Futuna]) remain documented in `financial_equity_unmatched_review.csv` and were excluded from this analysis pending official dictionary mapping.

### Pairwise Common Analytical Samples
* **Financial Hardship vs. UHC Coverage Index**: $N = 981$ observations across 159 countries (2000–2023).
* **Financial Hardship vs. OOP Health Spending (% CHE)**: $N = 973$ observations across 158 countries (2000–2023).
* **Financial Hardship vs. GDP per Capita PPP**: $N = 1,066$ observations across 161 countries (1990–2024).

---

## 3. Verified Indicator Definitions, Units, and Mathematical Coherence

| Indicator Name | Measurement Unit | Verified Source Definition | Analytical Notes |
| :--- | :--- | :--- | :--- |
| `Financial_Hardship_Total_Pct` | % of total population | WHO SDG 3.8.2 (2025 Definition): Population affected by catastrophic or impoverishing health payments. | Exactly equals `Large_Spending_Pct` + `Impoverishing_Spending_Pct` ($|\Delta| \le 0.04$ pp due to WHO rounding). |
| `Large_Spending_Pct` | % of total population | WHO SDG 3.8.2 (Component 1): Population incurring OOP health costs exceeding household budget capacity without crossing the poverty line. | Measures large non-impoverishing health spending. |
| `Impoverishing_Spending_Pct` | % of total population | WHO SDG 3.8.2 (Component 2): Population pushed into or deeper into poverty by OOP health payments. | Measures impoverishing health spending. |
| `Q1_Poorest_Pct` to `Q5_Richest_Pct` | % of quintile population | Incidence of financial hardship within each national wealth quintile ($Q1$ = lowest 20% income/wealth, $Q5$ = highest 20%). | The unweighted arithmetic mean of $Q1$ through $Q5$ matches `Financial_Hardship_Total_Pct`. |
| `Equity_Gap_Pct_Points` | Percentage points (pp) | Project-derived absolute gradient: `Q1_Poorest_Pct - Q5_Richest_Pct`. | Positive values denote higher hardship among the poor. |
| `UHC_Service_Coverage_Index` | Unitless index (0–100) | WHO SDG 3.8.1: Coverage of essential health services. | External comparator from macro health systems. |
| `OOP_Pct_Current_Health_Exp` | % of CHE | WHO GHED: Direct out-of-pocket payments as a share of current health spending. | Macro financing metric; distinct from household incidence. |
| `GDP_Per_Capita_PPP_2021` | Constant 2021 Int. $ (PPP) | World Bank WDI: Gross domestic product per capita adjusted for purchasing power parity. | Log-distributed macroeconomic welfare metric. |

---

## 4. Key Empirical Findings

### 4.1. Financial Hardship Distributions & Component Dynamics
* **Distributional Characteristics**:
  * `Financial_Hardship_Total_Pct`: Mean = **20.56%** | Median = **16.61%** | IQR = **15.59%** | Range = **0.00% – 77.45%** (Right-skewed = 1.31).
  * `Impoverishing_Spending_Pct`: Mean = **16.93%** | Median = **12.57%** | IQR = **14.28%** | Range = **0.00% – 73.89%** (Right-skewed = 1.55).
  * `Large_Spending_Pct`: Mean = **3.63%** | Median = **3.06%** | IQR = **3.04%** | Range = **0.00% – 15.85%** (Right-skewed = 1.34).
* **Component Dynamics**:
  * Impoverishing spending accounts for **82.3%** of total hardship incidence worldwide ($\rho = 0.9703, p < 0.0001$), while Large Spending displays a moderate correlation ($\rho = 0.3550, p < 0.0001$).
  * The highest recorded total hardship levels occur in low-income economies (Burundi 2006: 77.45%; Niger 2007: 74.51%; Viet Nam 1992: 71.55%), whereas several middle-income economies exhibit elevated non-impoverishing `Large_Spending_Pct` (e.g., Egypt 2019: 15.85%; Lebanon 1999: 14.58%; Bangladesh 2022: 14.13%).

### 4.2. Equity Across Wealth Quintiles & The Equity Gap
* **Quintile Breakdown** ($N = 1,038$ surveys across 162 countries):
  * **Q1 (Poorest 20%)**: Mean = **54.69%** (Median = 53.42%) | **Q2**: Mean = **29.32%** (Median = 18.79%) | **Q3**: Mean = **11.87%** (Median = 4.02%) | **Q4**: Mean = **5.20%** (Median = 1.90%) | **Q5 (Richest 20%)**: Mean = **2.65%** (Median = 1.38%).
* **Hypothesis Testing**:
  * Paired Friedman test ($\chi^2 = 3301.95, p < 0.0001$), Kruskal-Wallis test ($H = 2846.52, p < 0.0001$), and Wilcoxon signed-rank test ($W = 246.00, p = 9.14 \times 10^-171$) confirm a steep downward hardship gradient as wealth rises.
* **The Equity Gap Anatomy**:
  * **Positive Equity Gap ($Q1 > Q5$)**: Present in **1,032 of 1,038 surveys (99.42%)**, averaging **52.05 percentage points**, driven almost entirely by Q1 hardship ($\rho = 0.9867$).
  * **Negative Equity Gap ($Q1 < Q5$)**: Observed in only **4 surveys (0.39%)**: Somalia 2016 (-22.09 pp), Somalia 2017 (-28.91 pp), Uzbekistan 2003 (-0.14 pp), and Zimbabwe 2017 (-9.56 pp), reflecting foregone care among the poorest due to severe liquidity constraints.

### 4.3. Associations with External Health System & Economic Indicators
1. **UHC Service Coverage Index**: Full sample ($N = 981, 159$ countries) Spearman $\rho = -0.6219$ ($p = 4.68 \times 10^-106$); Latest survey per country ($N = 159$) $\rho = -0.5323$ ($p = 5.18 \times 10^-13$).
2. **Out-of-Pocket Expenditure (% CHE)**: Full sample ($N = 973, 158$ countries) Spearman $\rho = 0.5797$ ($p = 2.02 \times 10^-88$); Latest survey per country ($N = 158$) $\rho = 0.5587$ ($p = 2.38 \times 10^-14$).
3. **GDP per Capita, PPP (Constant 2021 Int. $)**: Full sample ($N = 1,066, 161$ countries) Spearman $\rho = -0.7061$ ($p = 1.04 \times 10^-161$), Pearson $r$ with $\log_{10}(\text{GDP}) = -0.7158$; Latest survey per country ($N = 161$) $\rho = -0.5835$ ($p = 4.56 \times 10^-16$).

---

## 5. Summary Table of Empirical Statistical Tests

| Indicator 1 | Indicator 2 | Test / Metric | N Obs | N Countries | Years | Statistic | P-Value | Direction & Strength |
| :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- |
| `Large_Spending_Pct` | `Financial_Hardship_Total_Pct` | Spearman $\rho$ | 1,056 | 162 | 1985–2024 | 0.3550 | $1.04 \times 10^-32$ | Moderate Positive |
| `Impoverishing_Spending_Pct` | `Financial_Hardship_Total_Pct` | Spearman $\rho$ | 1,056 | 162 | 1985–2024 | 0.9703 | $< 10^-300$ | Near-Perfect Positive |
| `Large_Spending_Pct` | `Impoverishing_Spending_Pct` | Spearman $\rho$ | 1,056 | 162 | 1985–2024 | 0.1708 | $2.35 \times 10^-8$ | Weak Positive |
| `Q1`–`Q5` Quintiles | Wealth Quintile Distribution | Friedman $\chi^2$ | 1,038 | 162 | 1985–2024 | 3,301.95 | $< 10^-300$ | Monotonic Pro-Rich Gradient |
| `Q1_Poorest_Pct` | `Q5_Richest_Pct` | Wilcoxon $W$ | 1,038 | 162 | 1985–2024 | 246.00 | $9.14 \times 10^-171$ | Significant Paired Gap |
| `Equity_Gap_Pct_Points` | `Financial_Hardship_Total_Pct` | Spearman $\rho$ | 1,038 | 162 | 1985–2024 | 0.7066 | $8.70 \times 10^-158$ | Strong Positive |
| `Financial_Hardship_Total_Pct` | `UHC_Service_Coverage_Index` | Spearman $\rho$ | 981 | 159 | 2000–2023 | -0.6219 | $4.68 \times 10^-106$ | Strong Negative |
| `Financial_Hardship_Total_Pct` | `OOP_Pct_Current_Health_Exp` | Spearman $\rho$ | 973 | 158 | 2000–2023 | 0.5797 | $2.02 \times 10^-88$ | Moderate-to-Strong Positive |
| `Financial_Hardship_Total_Pct` | `GDP_Per_Capita_PPP_2021` | Spearman $\rho$ | 1,066 | 161 | 1990–2024 | -0.7061 | $1.04 \times 10^-161$ | Strong Negative (Log-Linear) |
| `Financial_Hardship_Total_Pct` | `UHC_Index (Latest Survey)` | Cross-Sectional $\rho$ | 159 | 159 | 2000–2023 | -0.5323 | $5.18 \times 10^-13$ | Robust Negative |
| `Financial_Hardship_Total_Pct` | `OOP % CHE (Latest Survey)` | Cross-Sectional $\rho$ | 158 | 158 | 2000–2023 | 0.5587 | $2.38 \times 10^-14$ | Robust Positive |
| `Financial_Hardship_Total_Pct` | `GDP PPP (Latest Survey)` | Cross-Sectional $\rho$ | 161 | 161 | 1990–2024 | -0.5835 | $4.56 \times 10^-16$ | Robust Negative |

---

## 6. Direct Answers to Step 10 Core Analysis Questions (Questions 1–9)

1. **How is the Financial Hardship indicator distributed across countries and survey years?**
   * Across $N = 1,079$ surveys in 165 countries (1985–2024), `Financial_Hardship_Total_Pct` is right-skewed (skewness = 1.31), with a mean of **20.56%**, a median of **16.61%** (IQR = 15.59%), ranging from **0.00%** (Niue 2015) to **77.45%** (Burundi 2006). Among the 137 countries with $\ge 2$ surveys over time, hardship decreased between the first and last survey in 84 countries (61.3%) and increased in 53 countries (38.7%), with a mean longitudinal change of -3.42 percentage points.

2. **Are there clear differences between the different financial hardship components?**
   * Yes. `Impoverishing_Spending_Pct` (Component 2: mean **16.93%**, median **12.57%**) is the dominant driver of total hardship (Spearman $\rho = 0.9703, p < 0.0001$), accounting for 82.3% of total financial hardship on average. Conversely, `Large_Spending_Pct` (Component 1: mean **3.63%**, median **3.06%**) has a moderate correlation with total hardship ($\rho = 0.3550$) and a weak correlation with impoverishing spending ($\rho = 0.1708$), confirming that the two components capture distinct vulnerability mechanisms.

3. **How do values differ across the five population wealth quintiles after verifying definitions?**
   * Source verification confirms that `Q1_Poorest_Pct` through `Q5_Richest_Pct` measure the incidence (%) of financial hardship within each wealth quintile. There is a steep downward gradient from poorest to richest: **Q1 = 54.69%**, **Q2 = 29.32%**, **Q3 = 11.87%**, **Q4 = 5.20%**, and **Q5 = 2.65%** (Friedman $\chi^2 = 3301.95, p < 0.0001$).

4. **What is the meaning of the Equity Gap in the data, and how is it distributed?**
   * `Equity_Gap_Pct_Points` is defined as `Q1_Poorest_Pct - Q5_Richest_Pct` (in percentage points). Across $N = 1,038$ surveys (162 countries), it averages **52.05 pp** (median **50.59 pp**, range **-28.91 pp to 99.75 pp**). It is positive ($Q1 > Q5$) in **99.42%** of surveys (1,032/1,038), zero in 2 surveys (0.19%), and negative in 4 surveys (0.39%: Somalia 2016 & 2017, Uzbekistan 2003, Zimbabwe 2017).

5. **Is there an association between financial hardship and healthcare service coverage (UHC)?**
   * Yes. Across $N = 981$ common observations (159 countries, 2000–2023), `Financial_Hardship_Total_Pct` and `UHC_Service_Coverage_Index` show a strong negative correlation (Spearman $\rho = -0.6219, p = 4.68 \times 10^-106$), which holds in the latest-survey cross-section ($N = 159, \rho = -0.5323, p = 5.18 \times 10^-13$).

6. **Is there an association between financial hardship and direct out-of-pocket (OOP) expenditure?**
   * Yes. Across $N = 973$ common observations (158 countries, 2000–2023), `Financial_Hardship_Total_Pct` is positively correlated with `OOP_Pct_Current_Health_Exp` (Spearman $\rho = 0.5797, p = 2.02 \times 10^-88$; latest-survey cross-section $N = 158, \rho = 0.5587, p = 2.38 \times 10^-14$).

7. **Is there a relationship between financial hardship and GDP per capita (PPP)?**
   * Yes. Across $N = 1,066$ common observations (161 countries, 1990–2024), `Financial_Hardship_Total_Pct` shows a strong negative non-linear correlation with `GDP_Per_Capita_PPP_2021` (constant 2021 international $ PPP): Spearman $\rho = -0.7061$ ($p = 1.04 \times 10^-161$), and Pearson $r = -0.7158$ with $\log_{10}(\text{GDP})$.

8. **What are the main limitations resulting from missing data and varying survey years?**
   * Financial hardship data is survey-based (`ISO3 + Survey_Year`) and unavailable in 91.61% of total panel rows; 23 surveys lack component breakdowns and 41 lack quintile breakdowns. Because artificial interpolation and forward/backward filling are prohibited, pooled correlations weight frequently surveyed countries more heavily, and associations cannot be interpreted as causal effects.

9. **What are the top two or three findings to feature in the Final Dashboard?**
   * **Chart 1 (`equity_quintiles_comparison.png`)**: Highlights the **52.05 pp** average equity gap between the poorest quintile (54.69%) and richest quintile (2.65%).
   * **Chart 2 (`financial_hardship_vs_uhc.png` & `financial_hardship_vs_oop.png`)**: Demonstrates how expanding UHC service coverage ($\rho = -0.622$) while reducing OOP reliance ($\rho = 0.580$) protects households.
   * **Chart 3 (`financial_hardship_vs_gdp_ppp.png`)**: Shows the log-linear macroeconomic buffering effect of GDP per capita PPP ($\rho = -0.706$).
