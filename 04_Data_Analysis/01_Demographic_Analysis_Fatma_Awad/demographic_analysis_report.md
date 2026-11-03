# Demographic Analysis Report

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** 2 – Data Analysis
**Task 01:** Demographic Analysis
**Analyst:** Fatma Awad
**Dataset:** `integrated_healthcare_dataset.csv` (read-only; not modified)

---

## 1. Purpose and Approach

This report summarizes how population size, age structure, and urbanization differ across countries, how these indicators changed over time, and whether they are associated with Universal Health Coverage (UHC) levels.

**Indicators analyzed:** `Population`, `Age_0_14_Pct`, `Age_65_Plus_Pct`, `Urban_Population_Pct`, and (for comparison) `UHC_Service_Coverage_Index`.

**Key method decisions**

- Each observation is identified by `ISO3` + `Year`.
- Missing values were documented only: no zero-filling, no interpolation, no imputation.
- No valid observation was dropped because another indicator was missing.
- Every comparison with UHC uses a single common year, **2023**, the latest year with UHC data.
- Demographic-only cross-country comparisons use the **latest available year (2025)**, which is the latest year for all 194 countries with demographic data.
- Sample size (N) is reported for every statistic and correlation.

---

## 2. Data Quality Summary

| Item | Result |
|---|---|
| Rows × columns | 12,855 × 27 |
| Countries (ISO3) | 196 (all actual countries; no regional aggregates found) |
| Years | 1960–2025 (66 years) |
| Duplicate `(ISO3, Year)` | 0 |
| Demographic indicators missing | 0.40%–0.63% (81 rows) |
| UHC missing | 63.6% (available 2000–2023 only; 4,680 observations, 195 countries) |
| Impossible values | None (percentages within 0–100, population > 0, 0–14 % + 65+ % ≤ 100) |

**Missing data:** The 81 rows with a missing demographic value come almost entirely from three entities: Palestine (30 rows), Niue (26), and Cook Islands (25). Niue and Cook Islands have UHC values but no demographic data, so they drop out of any analysis that needs both.

**Outliers (IQR rule):** Population (13.0% of rows, 39 countries) and the 65+ share (3.5% of rows, 37 countries) were flagged. These are genuine values (very populous countries such as India and China; very old populations such as Japan and Italy), so nothing was removed. Population is strongly right-skewed, so log scale and Spearman correlation are used where appropriate.

---

## 3. Key Demographic Findings (2023 cross-section)

| Indicator | N | Mean | Median | Std | Min | Q1 | Q3 | Max |
|---|---|---|---|---|---|---|---|---|
| Population | 194 | 41,363,695 | 9,155,030 | 149,819,367 | 9,816 | 2,128,681 | 31,188,363 | 1,438,069,596 |
| Age 0–14 (%) | 194 | 26.66 | 25.13 | 10.38 | 10.97 | 17.39 | 36.62 | 49.17 |
| Age 65+ (%) | 194 | 9.76 | 6.99 | 7.09 | 1.57 | 3.69 | 15.51 | 36.36 |
| Urban (%) | 194 | 60.49 | 62.46 | 22.48 | 14.68 | 42.13 | 78.67 | 100.00 |
| UHC Index | 195 | 68.36 | 72.00 | 15.39 | 26.00 | 57.50 | 81.00 | 92.00 |

**What the statistics show**

- **Population is extremely unequal.** The median country has about 9.2 million people, while the mean is 41.4 million, pulled up by a few giants. Values range from about 9.8 thousand (Tuvalu) to 1.44 billion (India), and skewness is 8.3.
- **Child share is bimodal.** One cluster of countries sits around 15–17% and another around 38–40%, so the median (25.1%) falls in a sparse gap between two very different groups.
- **Elderly share is right-skewed.** Most countries are below 8% (median 7.0%), a smaller group sits near 20%, and Japan and Monaco exceed 29%.
- **Urbanization is wide and flat.** It ranges from about 15% to 100%, with no single dominant peak.
- **UHC is moderately high but left-skewed.** The median is 72 with a tail of low-coverage countries (minimum 26).

Charts: `charts/population_distribution.png`, `charts/age_structure_distribution.png`, `charts/urbanization_distribution.png`.

---

## 4. Global Trends and Population Changes (1960–2025)

Between 193 and 194 countries are included in every year, so the trends are not driven by changes in country coverage. Percentages below are population-weighted.

| Indicator | 1960 | 2023 | Change |
|---|---|---|---|
| Total population (sum of countries in dataset) | 3.00 billion | 8.02 billion | +5.02 billion (+167%) |
| Age 0–14 (%) | 37.4 | 25.1 | −12.3 percentage points |
| Age 65+ (%) | 5.0 | 9.9 | +5.0 points (roughly doubled) |
| Urban (%) | 34.1 | 57.2 | +23.1 points |

In 2025 the dataset's total population is about 8.18 billion, the child share is 24.5%, the elderly share is 10.4%, and the urban share is 57.7%.

**Main patterns**

- The child share peaked in the mid-1960s and has declined since, faster after 1990.
- The elderly share rose slowly until about 2010 and has accelerated since.
- Urbanization rose steadily throughout. The population-weighted urban share (57.2% in 2023) is lower than the unweighted country mean (60.5%), because several very populous countries are less urbanized than the typical country.

Chart: `charts/demographic_trends.png`.

---

## 5. Cross-Country Comparison (latest year, 2025)

The latest year is 2025 for all 194 countries and all four indicators, so no cross-year adjustment was needed.

**Ten largest populations:** India (1,464 M), China (1,407 M), United States (342 M), Indonesia (286 M), Pakistan (255 M), Nigeria (238 M), Brazil (213 M), Bangladesh (176 M), Russian Federation (144 M), Ethiopia (135 M). Ethiopia replaces Mexico, which was tenth in 2023.

| Indicator | Highest | Lowest |
|---|---|---|
| Urban (%) | Kuwait, Bahrain, Monaco, Nauru, Singapore (all 100%) | Liechtenstein (14.6), Papua New Guinea (15.8), Samoa (17.5), Malawi (17.6), Niger (18.4) |
| Age 65+ (%) | Monaco (36.0), Japan (30.0), Italy (25.1), Portugal (24.9), Greece (24.4) | Qatar (1.7), UAE (1.8), Zambia (2.0), Chad (2.1), Central African Republic (2.2) |
| Age 0–14 (%) | Central African Republic (48.7), Somalia (46.6), Niger (46.2), Chad (46.0), DR Congo (46.0) | South Korea (10.2), Japan (11.2), Andorra (11.6), Italy (11.7), Singapore (11.7) |

India and China are each more than four times larger than the third-largest country. Countries with the youngest populations are concentrated in Africa, and those with the oldest populations are mainly in Europe and East Asia.

Chart: `charts/top_10_population.png`.

---

## 6. Demographic Indicators vs. UHC (2023, N = 193 countries per comparison)

Only countries with both the demographic indicator and UHC in 2023 are used. Population is analyzed as log10(Population) because of its skew.

| Indicator | N | Pearson r | Spearman ρ | Direction |
|---|---|---|---|---|
| Children 0–14 (%) | 193 | −0.86 | −0.83 | Strong negative (p < 0.001) |
| Elderly 65+ (%) | 193 | 0.67 | 0.75 | Positive, non-linear (p < 0.001) |
| Urbanization (%) | 193 | 0.60 | 0.63 | Positive, widely scattered (p < 0.001) |
| log10(Population) | 193 | −0.08 | −0.03 | No meaningful association (p = 0.24 and 0.65) |

**Answers to the guiding questions**

- **Do more urbanized countries tend to have higher UHC?** Yes, on average, but with wide scatter: at a given urbanization level (for example 60–70%), UHC ranges from about 40 to 85.
- **Do countries with more elderly people differ in UHC?** Yes. UHC is higher where the elderly share is higher. The relationship is steep between roughly 2% and 10% and flattens at higher shares, which is why Spearman is higher than Pearson.
- **Does UHC differ in countries with more children?** Yes. This is the strongest relationship: countries with about 15% children typically score 75–90 on UHC, while those above 40% typically score 30–55.
- **Is there a relationship between population size and UHC?** No evidence of one.

The demographic indicators are strongly related to each other (children vs. elderly ρ = −0.89; children vs. urban ρ = −0.55; elderly vs. urban ρ = 0.45). They largely capture the same underlying pattern of demographic transition and development level, so their associations with UHC are not independent of one another.

**These are correlations, not causal effects.** A higher child share does not by itself lower UHC; it is more plausibly a marker of overall development and income, which likely influence both demographic structure and health coverage.

Charts: `charts/urbanization_vs_uhc.png`, `charts/elderly_population_vs_uhc.png`, `charts/child_population_vs_uhc.png`, `charts/demographic_correlation_heatmap.png`.

---

## 7. Limitations

1. **UHC coverage window.** UHC exists only for 2000–2023, so all UHC comparisons are limited to that period; the 2024–2025 demographic values are never paired with UHC.
2. **Single-year snapshot.** The correlations use the 2023 cross-section only. They do not show whether changes in demographics within a country relate to changes in its UHC.
3. **Correlation, not causation.** No causal conclusions can be drawn. Income, health spending, and institutions are not controlled for in this task.
4. **Overlapping indicators.** The demographic indicators are strongly intercorrelated, so individual effects cannot be separated.
5. **Country-level averages.** Results describe countries, not individuals, and treat a tiny country the same as a very large one in the correlations.
6. **Small and unusual countries.** Micro-states (e.g., Monaco, Nauru) and countries with large migrant workforces (e.g., Qatar, UAE) have unusual age or urbanization values that can influence results.
7. **Missing entities.** Cook Islands and Niue have UHC but no demographic data; Palestine has missing demographic values in several years. Nothing was imputed.
8. **Totals are not world totals.** "Total population" is the sum of the countries in the dataset and may differ slightly from official world figures. Values for the most recent years may be estimates or projections depending on the original source.
9. **Linear fit extrapolation.** In the elderly-share scatter plot, the fitted line rises above 100 at the right edge only because it is a linear extrapolation; UHC is capped at 100.

---

## 8. Key Conclusions

1. The world's population in this dataset grew from about 3.0 billion (1960) to 8.0 billion (2023), while the child share fell by about 12 points and the elderly share roughly doubled. Urbanization rose by about 23 points.
2. Countries differ sharply: very young, less urbanized populations (mostly in Africa) coexist with very old populations (mostly in Europe and East Asia).
3. In 2023, UHC is strongly negatively associated with the share of children (ρ = −0.83) and positively associated with the share of elderly (ρ = 0.75) and urbanization (ρ = 0.63).
4. Population size is not associated with UHC (ρ = −0.03).
5. The associations most likely reflect a shared underlying factor, the stage of demographic transition and development, and should not be read as causal.

---

## 9. Deliverables

```text
01_Demographic_Analysis_Fatma_Awad/
├── demographic_analysis.ipynb
├── demographic_analysis_summary.csv
├── demographic_analysis_report.md
└── charts/
    ├── population_distribution.png
    ├── age_structure_distribution.png
    ├── urbanization_distribution.png
    ├── demographic_trends.png
    ├── top_10_population.png
    ├── urbanization_vs_uhc.png
    ├── elderly_population_vs_uhc.png
    ├── child_population_vs_uhc.png
    └── demographic_correlation_heatmap.png
```
