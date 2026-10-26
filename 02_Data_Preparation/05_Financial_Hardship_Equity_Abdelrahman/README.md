# Financial Hardship & Equity — Data Preparation

## Overview

This folder contains the cleaned financial access and equity dataset prepared for the Global Healthcare Performance & Equity Analysis graduation project.

## Task Owner

Abdelrahman

## Project Objective

Prepare and validate financial access and equity indicators to support the analysis of financial hardship related to healthcare and differences in access to healthcare across countries and over time.

## Data Sources

The task uses the source datasets assigned for the financial access and equity analysis, with `country_dictionary_v1.csv` as the reference for standardized country identifiers and names.

## Output Dataset

* `financial_access_equity_clean.csv`

## Expected Columns

* `ISO3`
* `Country`
* `Year`
* Financial access and equity indicators provided by the source dataset.

## Data Preparation Rules

* Use the approved country dictionary to standardize country codes and names.
* Use `ISO3` and `Year` as the canonical country-year key.
* Convert `Year` to integer and indicator columns to appropriate numeric types.
* Preserve missing values as missing.
* Do not replace missing values with zero.
* Do not use interpolation, forward fill, or backward fill.
* Do not modify the original raw datasets.
* Exclude source codes not present in the approved country dictionary and document them for review.
* Do not integrate this task with other project datasets at this stage.

## Validation Requirements

The cleaned dataset should be checked for:

* Record counts before and after cleaning.
* Number of unique countries and ISO3 codes.
* Year range.
* Duplicate `ISO3 + Year` keys.
* Missing-value counts for each indicator.
* Appropriate data types and valid indicator ranges.
* Country-code and country-name consistency with the dictionary.
* Consistency between the cleaned CSV, notebook, and cleaning log.

## Deliverables

* `financial_access_equity_clean.csv` — cleaned dataset.
* `financial_equity_cleaning.ipynb` — reproducible cleaning notebook.
* `cleaning_log.txt` — cleaning steps and validation results.

## Important Notes

This task produces a task-level cleaned dataset only. Final integration with the other project datasets will be performed separately by the project lead using `ISO3 + Year`.

Missing values must remain missing unless a documented and approved project-level decision specifies otherwise.

---

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Data Preparation & Cleaning
**Task:** Financial Hardship & Equity
