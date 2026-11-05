# Regional & Income Group Comparative Analysis — Mahmoud

## Objective
Compare global healthcare performance and equity indicators across the `Region` and `Income_Group` categories supplied in `country_dictionary_v1.csv`.

## Inputs
- `integrated_healthcare_dataset.csv` — integrated country-year panel (12,855 rows; 196 ISO3 codes; 1960–2025).
- `country_dictionary_v1.csv` — 196 country records with `Region` and `Income_Group` classifications.

The notebook joins the dictionary to the integrated data by `ISO3` using a left join. The integrated source file is not modified. In this supplied dictionary, PRK (Democratic People's Republic of Korea) has no `Region` or `Income_Group`; its records are retained in the joined dataset but omitted from comparisons that require the missing classification. No classification is imputed.

## Method
### Cross-sectional country comparison
For every indicator, the analysis selects the latest non-missing observation for each country. Each country therefore contributes at most one value per indicator to group summaries and statistical tests. The selected observation's `Reference_Year` is retained and summarized because reporting years are not identical across all indicators or countries.

Group summaries include country count, mean, median, standard deviation, quartiles, range, and reference-year information. Results are split into:
- Region comparisons
- Income-group comparisons

### Statistical testing
- Kruskal–Wallis tests compare all eligible groups for each indicator.
- Epsilon-squared is reported as an effect-size estimate.
- Pairwise follow-up uses two-sided Mann–Whitney U tests.
- Holm correction is applied across omnibus indicator tests within each grouping dimension and across pairwise comparisons within each indicator/grouping-dimension family.

A significant p-value indicates evidence of a distributional difference among groups; it does not establish causation. Country samples are independent at the snapshot level, but the results remain observational and may be affected by differences in data years and coverage.

### Historical descriptive trends
The notebook also calculates annual group medians for 2000–2025. A group-year is reported only when at least three countries have a value. These trend summaries are descriptive. The supplied income-group classification is static in the dictionary and is not reconstructed year by year; do not interpret these trend lines as historical World Bank income-group membership.

## Selected indicators
GDP per capita (PPP), doctors per 10,000, nurses and midwives per 10,000, hospital beds per 10,000, UHC service coverage, health expenditure per capita, health expenditure as a share of GDP, out-of-pocket expenditure share, financial hardship, equity gap, urban population share, secondary enrollment, and adult literacy.

## Key descriptive findings from the supplied data
The following values are medians of each country's latest available observation; they are not necessarily all from the same calendar year.

- **UHC service coverage:** the median is 82.5 for the High income group (64 countries with data) and 43.0 for the Low income group (25 countries). Across regions, EUR is 80.0 (53 countries) and AFR is 48.0 (47 countries).
- **Doctors per 10,000:** regional medians range from 1.86 in AFR (47 countries) to 38.56 in EUR (53 countries). Income-group medians range from 1.34 in Low (25 countries) to 37.20 in High (62 countries).
- **Hospital beds per 10,000:** the regional median is 41.15 in EUR (53 countries) versus 10.00 in AFR (46 countries). Income-group medians range from 6.73 in Low (24 countries) to 34.48 in High (64 countries).
- **Out-of-pocket share of current health expenditure:** the median is 46.27% in Low income countries (25 countries) and 16.21% in High income countries (65 countries). Region medians range from 12.17% in WPR (28 countries) to 43.89% in SEAR (9 countries).
- **Financial hardship:** latest available observations show medians of 36.02% in Low income countries (24 countries) and 10.31% in High income countries (47 countries). The median reference years differ and the measure has less uniform coverage, so this comparison needs additional caution.

These are descriptive contrasts. They should be read alongside country counts and reference years in the CSV outputs, not as direct measures of causality or as proof that every country within a group follows the group median.

## Output files
| File | Description |
|---|---|
| `regional_income_analysis.ipynb` | Reproducible analysis notebook |
| `regional_income_analysis_summary.csv` | Lowest/highest group median and omnibus test summary per indicator |
| `country_indicator_latest_snapshot.csv` | Country-level latest available value per indicator, including reference year |
| `group_comparison_summary.csv` | Combined descriptive statistics for Region and Income_Group |
| `regional_comparison.csv` | Region-level descriptive statistics |
| `income_group_comparison.csv` | Income-group descriptive statistics |
| `indicator_coverage_summary.csv` | Country counts and reference-year span for each indicator |
| `statistical_tests.csv` | Kruskal–Wallis results, Holm-adjusted p-values, and effect sizes |
| `posthoc_pairwise_tests.csv` | Pairwise Mann–Whitney U results and Holm-adjusted p-values |
| `group_trends_2000_2025.csv` | Annual group medians for eligible group-years |
| `validation_summary.csv` | Key and join validation checks |
| `charts/` | Latest-snapshot comparisons and historical descriptive trend charts |

## Running the notebook
Place `integrated_healthcare_dataset.csv` and `country_dictionary_v1.csv` in `03_Integrated_Datasets/` (or in the project root). Open and run `regional_income_analysis.ipynb`. The notebook creates/updates the output CSV files and charts in this task folder. Required Python packages: `pandas`, `numpy`, `scipy`, `statsmodels`, and `matplotlib`.

## Limitations
1. The supplied `Region` and `Income_Group` fields are used as-is; their definitions and reference date are not reconstructed by this analysis.
2. Latest available years vary across indicators and countries. Always consult `Reference_Year` and the year summaries.
3. Financial hardship, equity, and adult literacy are less consistently observed than core healthcare indicators.
4. Group medians conceal country-level variation and within-group inequality.
5. These comparisons are observational and do not support causal claims.
