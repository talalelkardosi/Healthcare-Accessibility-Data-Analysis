
# Socioeconomic & Education Analysis Report

## 1. Project Overview

This analysis investigates the relationships between socioeconomic and educational indicators and Universal Health Coverage (UHC) across countries and years.

The main indicators examined are GDP per capita (PPP), secondary school enrollment, and adult literacy rate.

## 2. Dataset Overview

- Total observations: 12,855
- Total columns: 27
- Countries: 196
- Dataset year range: 1960–2025
- Analysis period: 2000–2023
- Duplicate country-year records: 0

## 3. Data Availability

| Indicator | Available | Missing | Missing (%) |
|---|---:|---:|---:|
| GDP per Capita (PPP) | 6,630 | 6,225 | 48.42% |
| Secondary Enrollment | 6,023 | 6,832 | 53.15% |
| Adult Literacy | 1,102 | 11,753 | 91.43% |
| UHC Service Coverage | 4,680 | 8,175 | 63.59% |

Adult literacy has particularly limited data availability, which affects the representativeness of its analysis.

## 4. Distribution Analysis

### GDP per Capita (PPP)

GDP has a positively skewed distribution (skewness = 1.96). Its mean is 20,418.30, while its median is 11,809.95. This indicates that high-value observations pull the mean upward.

### Secondary Enrollment

Secondary enrollment has a nearly symmetric overall distribution (skewness = -0.08). Its mean is 65.18%, and its median is 70.05%.

Gross enrollment ratios above 100% were retained because they can be legitimate values.

### Adult Literacy

Adult literacy has a negatively skewed distribution (skewness = -1.35). Most available observations are concentrated at higher literacy levels.

Potential outliers were retained because extreme values may represent genuine differences between countries.

## 5. Correlation Analysis

All comparisons use pairwise available observations from 2000 to 2023.

| Comparison | Observations | Countries | Spearman Correlation |
|---|---:|---:|---:|
| GDP vs UHC | 4,450 | 186 | 0.8628 |
| Secondary Enrollment vs UHC | 3,304 | 190 | 0.8262 |
| Adult Literacy vs UHC | 882 | 151 | 0.6794 |

### GDP and UHC

A very strong positive association was observed (Spearman = 0.8628, p < 0.001).

### Secondary Enrollment and UHC

A very strong positive association was observed (Spearman = 0.8262, p < 0.001).

### Adult Literacy and UHC

A strong positive association was observed (Spearman = 0.6794, p < 0.001).

The literacy comparison has a substantially smaller sample, so its results require additional caution.

These correlations describe associations and do not establish causal relationships. Repeated observations from the same countries may also affect the assumptions of conventional significance tests.

## 6. Trends Over Time

Between 2000 and 2023:

- Mean GDP per capita increased from 17,984.10 to 25,399.59, approximately 41.2%.
- Median GDP increased from 9,981.63 to 16,222.86, approximately 62.5%.
- Mean UHC increased from 55.34 to 68.36.
- Median UHC increased from 63 to 72.

In 2023, 185 countries had paired GDP and UHC observations. Their mean GDP was 25,399.59 and their mean UHC index was 68.49.

Yearly averages use the available observations for each indicator independently. Therefore, the number of contributing countries may differ between indicators.

## 7. Key Dashboard Insights

1. GDP per capita showed the strongest observed association with UHC.
2. Secondary school enrollment also showed a very strong positive association with UHC.
3. Adult literacy was positively associated with UHC, but its results were based on substantially fewer observations.
4. Both GDP and UHC generally increased during the analysis period.

## 8. Limitations

- Missing values vary substantially across indicators.
- Adult literacy data has 91.43% missing observations.
- Country coverage changes across years and indicators.
- The analysis is observational and cannot establish causation.
- Repeated country-year observations may not be independent.
- Potential outliers were retained rather than removed without justification.

## 9. Conclusion

The analysis found positive associations between GDP per capita, secondary school enrollment, adult literacy, and UHC service coverage.

GDP per capita showed the strongest association, followed by secondary school enrollment and adult literacy.

These findings highlight the importance of socioeconomic and educational context when examining healthcare coverage. However, missing data, sample representativeness, and the observational nature of the analysis must be considered when interpreting the results.
