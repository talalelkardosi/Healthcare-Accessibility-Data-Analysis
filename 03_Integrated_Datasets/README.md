# Integrated Healthcare Dataset

## Project Overview

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Data Integration & Validation
**Integration Key:** `ISO3 + Year`

This folder contains the integrated country-year dataset assembled from the cleaned outputs of the five project workstreams.

The purpose of this stage is to bring demographic, socioeconomic, healthcare workforce, healthcare capacity, healthcare coverage, health financing, and financial equity indicators together in a standardized structure for subsequent analysis.

## Integration Summary

The integrated dataset passed the structural validation checks performed during the integration process.

| Metric                              |    Result |
| ----------------------------------- | --------: |
| Integrated records                  |    12,855 |
| Total columns                       |        27 |
| Unique ISO3 codes                   |       196 |
| Year range                          | 1960–2025 |
| Duplicate `ISO3 + Year` keys        |         0 |
| Missing values in integration keys  |         0 |
| Indicator value mismatches detected |         0 |

These figures describe the current integrated dataset and the validation checks performed. Further review of indicator definitions, units, data coverage, and analytical suitability is still required before drawing substantive conclusions.

## Integrated Data Sources

The dataset combines seven cleaned task-level datasets.

### 1. Population & Demographics

**Source file:** `demographics_clean.csv`

Includes:

* `Population`
* `Age_0_14_Pct`
* `Age_65_Plus_Pct`
* `Urban_Population_Pct`

### 2. Economy & Education

**Source file:** `socioeconomic_education_clean.csv`

Includes:

* `GDP_Per_Capita_PPP_2021`
* `Secondary_Enrollment_Gross_Pct`
* `Adult_Literacy_Rate`

GDP per capita is measured in constant 2021 international dollars using purchasing power parity (PPP).

### 3. Healthcare Workforce

**Source file:** `healthcare_workforce_clean.csv`

Includes:

* `Doctors_Total`
* `Doctors_Per_10k`
* `Nurses_Midwives_Per_10k`

### 4. Healthcare Capacity

**Source file:** `healthcare_capacity_clean.csv`

Includes:

* `Hospital_Beds_Per_10k`

### 5. Healthcare Coverage

**Source file:** `healthcare_coverage_clean.csv`

Includes:

* `UHC_Service_Coverage_Index`

### 6. Healthcare Financing

**Source file:** `health_financing_clean.csv`

Includes:

* `Health_Exp_Per_Capita_PPP`
* `Health_Exp_Pct_GDP`
* `OOP_Pct_Current_Health_Exp`

### 7. Financial Hardship & Equity

**Source file:** `financial_access_equity_clean.csv`

Includes:

* `Financial_Hardship_Total_Pct`
* `Large_Spending_Pct`
* `Impoverishing_Spending_Pct`
* `Q1_Poorest_Pct`
* `Q2_Pct`
* `Q3_Pct`
* `Q4_Pct`
* `Q5_Richest_Pct`
* `Equity_Gap_Pct_Points`

Financial hardship and equity indicators are based on survey-year observations. They should not be interpreted as a complete annual series for every country.

## Included Files

### Main Integrated Dataset

* `integrated_healthcare_dataset.csv` — the integrated country-year dataset containing the standardized indicators from the seven source datasets.

### Coverage and Analysis Planning

* `indicator_coverage_summary.csv` — available and missing observations, with coverage percentages, for each indicator.
* `pairwise_analysis_coverage.csv` — shared observations available for selected analytical comparisons.

### Validation and Standardization

* `integration_validation_summary.csv` — summary of structural validation results.
* `source_standardization_summary.csv` — summary of the standardization and key checks performed on each source dataset.
* `integration_audit_log.txt` — a record of the integration process and its main validation results.

### Review Records

* `financial_equity_unmatched_review.csv` — nine financial-equity records associated with ISO3 codes not found in the approved country dictionary.

### Reproducibility

* `integration_audit.ipynb` — the notebook containing the integration workflow and validation checks.

## Integration Methodology

The integrated dataset was constructed using the union of unique country-year keys from the seven standardized datasets.

The canonical key is:

`ISO3 + Year`

The integration process:

* Standardizes country identifiers using the approved `country_dictionary_v1.csv`.
* Uses `ISO3` and `Year` as the matching keys.
* Standardizes country names in the integration copies.
* Preserves available indicator values.
* Keeps missing observations as missing values.
* Does not replace missing values with zero.
* Does not interpolate or fill missing healthcare, financial, or socioeconomic indicators.
* Keeps the original task-level source files unchanged.

## Data Quality and Validation

The integration workflow includes checks for:

* Duplicate country-year keys.
* Missing values in integration keys.
* Country-code consistency against the approved dictionary.
* Standardized country names.
* Preservation of source country-year keys.
* Preservation of non-missing indicator counts.
* Exact matching of source indicator values to the corresponding integrated values.
* Coverage and overlap across indicators.

The current integrated dataset passed the structural checks described above.

Passing these checks does not establish that every source measurement is error-free. Indicator definitions, units, source-specific limitations, and suitability for each analytical question must still be reviewed.

## Unmatched Financial Equity Records

Nine records from `financial_access_equity_clean.csv` were excluded from the integrated dataset because their ISO3 codes were not present in the approved country dictionary.

The affected codes are:

* `TKL`
* `WLF`
* `XKX`

These records were preserved separately in `financial_equity_unmatched_review.csv` for review. Their exclusion reflects the project's current country-dictionary rule; it does not, by itself, establish that their financial indicator values are incorrect.

## Data Coverage Limitations

Indicator availability varies across countries and years.

Some demographic indicators have broad coverage, while adult literacy, healthcare workforce measures, hospital capacity, and financial equity indicators have more limited availability in the integrated dataset.

Missing values do not represent zero values.

The number of observations available for each analysis will depend on whether the variables required for that specific question are available for the same country-year or survey-year observation.

Financial hardship indicators are survey-based and should not be treated as a continuous annual series without an appropriate methodological justification.

## Next Steps

The next phase of the project will focus on:

1. Reviewing indicator definitions, measurement units, and source limitations.
2. Conducting exploratory data analysis (EDA).
3. Examining relationships between healthcare coverage, demographic characteristics, socioeconomic conditions, healthcare resources, financing, and financial hardship.
4. Selecting appropriate samples for each analytical question based on actual indicator availability.
5. Producing evidence-based visualizations and analysis summaries.
6. Preparing dashboards and project reporting after the analytical results have been reviewed.

The analysis will distinguish association from causation. Relationships observed in the data will not be interpreted as causal effects without an appropriate research design.

---

**Project:** Global Healthcare Performance & Equity Analysis
**Dataset:** Integrated Healthcare Dataset
**Phase:** Data Integration & Validation
**Canonical Key:** `ISO3 + Year`
