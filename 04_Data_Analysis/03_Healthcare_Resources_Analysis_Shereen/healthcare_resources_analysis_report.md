
# Healthcare Resources Analysis

## 1. Project Overview

This analysis examines the distribution of healthcare resources
across countries and their relationship with Universal Health
Coverage (UHC).

The analysis focuses on three healthcare resource indicators:

- Doctors per 10,000 people.
- Nurses and Midwives per 10,000 people.
- Hospital Beds per 10,000 people.

The UHC Service Coverage Index is used as the main outcome indicator.

## 2. Dataset Overview

The integrated dataset contains:

- 12,855 observations.
- 196 countries.
- 66 years, covering 1960–2025.
- 27 columns.

Healthcare indicator coverage varies across countries and years.

| Indicator | Available Observations | Year Range |
|---|---:|---|
| Doctors Total | 4,293 | 1971–2024 |
| Doctors per 10k | 4,280 | 1971–2024 |
| Nurses and Midwives per 10k | 3,374 | 1990–2023 |
| Hospital Beds per 10k | 2,958 | 2000–2023 |
| UHC Service Coverage Index | 4,680 | 2000–2023 |

Missing values were retained and were not treated as zero.

## 3. Descriptive Statistics

The analysis shows considerable variation in healthcare
resource availability across country-year observations.

| Indicator | Mean | Median | Std. Dev. | Minimum | Maximum |
|---|---:|---:|---:|---:|---:|
| Doctors per 10k | 21.01 | 20.51 | 14.64 | 0.13 | 95.43 |
| Nurses and Midwives per 10k | 49.34 | 42.45 | 38.54 | 0.47 | 208.31 |
| Hospital Beds per 10k | 34.48 | 27.74 | 26.28 | 1.54 | 222.70 |
| UHC Index | 62.78 | 69.00 | 18.49 | 13.00 | 92.00 |

The differences between means and medians, particularly for
nurses and hospital beds, indicate substantial variation in
resource availability.

These statistics describe pooled observations across different
countries and years.

## 4. Healthcare Resources and UHC Correlation

Spearman rank correlation was used to examine the relationship
between healthcare resources and the UHC Service Coverage Index.

| Resource Indicator | Observations | Spearman Correlation | Relationship |
|---|---:|---:|---|
| Doctors per 10k | 2,956 | 0.738 | Strong Positive |
| Nurses and Midwives per 10k | 2,839 | 0.777 | Strong Positive |
| Hospital Beds per 10k | 2,958 | 0.490 | Moderate Positive |

All three relationships were statistically significant
(p < 0.05).

Nurses and midwives showed the strongest positive association
with UHC, followed by doctors. Hospital beds showed a moderate
positive association.

These findings indicate association, not causation.

## 5. Cross-Country Comparison: 2018

The year 2018 was selected because it provided the largest
number of countries with complete data for all four indicators.

A total of 115 countries were included.

### Highest and Lowest UHC Values

- Highest UHC score: Canada (92).
- Lowest UHC score: Niger (35).

### Highest and Lowest Doctor Availability

- Highest: Austria (95.43 doctors per 10k).
- Lowest: Niger (0.37 doctors per 10k).

### Highest and Lowest Nurse and Midwife Availability

- Highest: Switzerland (179.15 per 10k).
- Lowest: Niger (2.26 per 10k).

### Highest and Lowest Hospital Bed Availability

- Highest: Japan (129.30 beds per 10k).
- Lowest: Niger (2.42 beds per 10k).

Niger appeared among the lowest-ranked countries across all
four indicators. This highlights the overlap between low
healthcare resource availability and low UHC coverage in
this comparison.

However, high availability of one resource does not necessarily
correspond to the highest UHC score.

## 6. Trends Over Time

### Doctors

The average doctors-per-10,000 rate generally fluctuated
between approximately 21 and 24 from 2015 to 2023.

It reached 23.59 in 2023. The 2024 average declined to 14.71,
but the number of reporting countries also fell to 70.
Therefore, this decline should not be interpreted as a
confirmed global reduction.

### Nurses and Midwives

The average increased from 44.38 in 2015 to a peak of 53.03
in 2021, then declined to 45.99 in 2023.

The number of reporting countries fell to 75 in 2023,
which affects year-to-year comparability.

### Hospital Beds

The average hospital bed rate remained relatively stable,
generally around 31–34 beds per 10,000 people between
2015 and 2023.

The highest average in this period was 33.77 in 2022.
The number of reporting countries declined over time.

### UHC Service Coverage

The average UHC index increased from 66.17 in 2015
to 68.36 in 2023.

The number of countries remained constant at 195
throughout this period, providing more consistent
year-to-year coverage than the resource indicators.

## 7. Key Findings

1. Healthcare resource availability varies substantially
   across countries.
2. Nurses and midwives had the strongest positive
   association with UHC.
3. Doctors also showed a strong positive association
   with UHC.
4. Hospital beds showed a moderate positive association.
5. Niger appeared among the lowest-ranked countries
   across all four indicators in the 2018 comparison.
6. Average UHC coverage increased gradually between
   2015 and 2023.
7. Resource trends must be interpreted carefully because
   the number of reporting countries changes across years.

## 8. Limitations

- Healthcare indicator coverage is incomplete and varies
  across countries and years.
- The correlation analysis uses repeated country-year
  observations. These observations may not be independent.
- Pooled correlations are exploratory and should not be
  interpreted as causal relationships.
- Changes in yearly averages may reflect changes in the
  countries reporting data rather than actual changes
  in global healthcare resources.
- The analysis does not account for all factors affecting
  UHC, such as healthcare quality, affordability,
  infrastructure, and socioeconomic conditions.
- The 2018 comparison includes only countries with
  complete data for all four indicators.

## 9. Recommendations

- Strengthen healthcare workforce availability,
  particularly nursing and medical personnel.
- Investigate countries with persistently low resource
  availability and UHC coverage.
- Improve the completeness and consistency of
  international healthcare data reporting.
- Consider healthcare access, affordability, and service
  quality alongside resource availability.
- Conduct further country-level and time-series analysis
  before making causal claims.

## 10. Conclusion

The analysis identified positive associations between
healthcare resource availability and Universal Health
Coverage.

Nurses and midwives showed the strongest association
with UHC, followed by doctors, while hospital beds
showed a moderate association.

The 2018 comparison highlighted substantial differences
between countries, while the time-series analysis showed
a gradual increase in average UHC coverage.

Overall, the findings emphasize the importance of
healthcare workforce and infrastructure availability,
while highlighting the need for better data coverage
and further analysis.
