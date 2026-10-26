# Healthcare Coverage & Financing — Data Preparation

## Overview

This folder contains the cleaned healthcare coverage dataset prepared for the Global Healthcare Performance & Equity Analysis graduation project.

## Task Owner

Hassan Mostafa

## Project Objective

Prepare and validate healthcare coverage and financing indicators to support the analysis of healthcare service coverage, health expenditure, and out-of-pocket spending across countries and over time.

## Data Sources

The task uses the following source datasets:

* Universal Health Coverage (UHC) Service Coverage Index.
* Global Health Expenditure Database (GHED).
* `country_dictionary_v1.csv` for standardized country identifiers and names.

## Output Datasets

* `healthcare_coverage_clean.csv`
* `health_financing_clean.csv`

## Expected Variables

### Healthcare Coverage

* `ISO3`
* `Country`
* `Year`
* `UHC_Service_Coverage_Index`

### Healthcare Financing

* `ISO3`
* `Country`
* `Year`
* `Health_Exp_Per_Capita_PPP`
* `Health_Exp_Pct_GDP`
* `OOP_Pct_Current_Health_Exp`

## Data Preparation Rules

* Use the approved country dictionary to standardize country codes and names.
* Use `ISO3` and `Year` as the canonical country-year key.
* Convert data from wide format to long format when required.
* Convert `Year` to integer and indicator columns to appropriate numeric types.
* Preserve missing values as missing.
* Do not replace missing values with zero.
* Do not use interpolation, forward fill, or backward fill.
* Do not modify the original raw datasets.
* Exclude source codes that are not present in the approved country dictionary and document them for review.
* Do not integrate this task with other project datasets at this stage.

## Validation Requirements

The cleaned outputs should be checked for:

* Record counts before and after cleaning.
* Number of unique countries and ISO3 codes.
* Year range.
* Duplicate `ISO3 + Year` keys.
* Missing-value counts and coverage for each indicator.
* Appropriate data types and valid indicator ranges.
* Country-code and country-name consistency with the dictionary.
* Any unmatched codes and documented exclusions.
* Consistency between the CSV outputs, notebook, and cleaning log.

## Deliverables

* `healthcare_coverage_clean.csv` — cleaned healthcare coverage data.
* `health_financing_clean.csv` — cleaned healthcare financing data.
* `coverage_financing_cleaning.ipynb` — reproducible cleaning notebook.
* `cleaning_log.txt` — cleaning steps and validation results.
* `coverage_summary.csv` — summary of indicator coverage, if included in the final submission.

## Important Notes

This task produces task-level cleaned datasets only. Final integration with the other project datasets will be performed separately by the project lead using `ISO3 + Year`.

Missing values must remain missing unless a documented and approved project-level decision specifies otherwise.

---

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Data Preparation & Cleaning
**Task:** Healthcare Coverage & Financing
