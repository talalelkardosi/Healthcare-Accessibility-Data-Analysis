# Economy & Education — Data Preparation

## Overview

This folder contains the cleaned socioeconomic and education dataset prepared for the Global Healthcare Performance & Equity Analysis graduation project.

## Task Owner

Aya Nasr

## Data Sources

The dataset was prepared using the following World Bank indicators:

* GDP per capita, PPP (constant 2021 international $)
* School enrollment, secondary (% gross)
* Literacy rate, adult total (% ages 15 and above)

The country dictionary `country_dictionary_v1.csv` was used as the reference for country names and ISO3 codes.

## Output Dataset

`socioeconomic_education_clean.csv`

### Columns

* `ISO3`
* `Country`
* `Year`
* `GDP_Per_Capita_PPP_2021`
* `Secondary_Enrollment_Gross_Pct`
* `Adult_Literacy_Rate`

## Data Preparation

* Converted the source data from wide format to long format.
* Standardized country identifiers using ISO3 codes.
* Merged indicators using `ISO3` and `Year`.
* Preserved missing values without imputation or interpolation.
* Retained secondary enrollment values above 100%, as gross enrollment can legitimately exceed 100%.
* Removed country-year rows where all three indicators were missing.
* Excluded source codes not present in the approved country dictionary and documented them for review.

## Validation Summary

* Final records: 8,634
* Countries/entities: 194
* Year range: 1970–2025
* Duplicate `ISO3 + Year` keys: 0
* Missing values were preserved.
* No negative GDP values were found.
* Adult literacy values were within the 0–100 range.

## Deliverables

* `socioeconomic_education_clean.csv` — cleaned dataset
* `economy_education_cleaning.ipynb` — reproducible cleaning notebook
* `cleaning_log.txt` — cleaning and validation log
* `unmatched_codes_review.csv` — unmatched source codes for review

## Important Notes

This dataset is prepared for later integration with the project's other datasets. Final integration will be performed separately using the canonical key `ISO3 + Year`.

Missing values were not filled, interpolated, or replaced with zero.

---

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Data Preparation & Cleaning
