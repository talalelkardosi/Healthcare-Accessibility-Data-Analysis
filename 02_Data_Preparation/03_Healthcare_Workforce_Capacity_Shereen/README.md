# Healthcare Workforce & Capacity — Data Preparation

## Overview

This folder contains the cleaned healthcare workforce and capacity datasets prepared for the Global Healthcare Performance & Equity Analysis graduation project.

## Task Owner

Shereen

## Data Scope

This task focuses on healthcare workforce and system capacity indicators that help describe the availability of healthcare personnel and resources across countries and over time.

## Output Datasets

* `healthcare_workforce_clean.csv`
* `healthcare_capacity_clean.csv`

## Supporting Files

* `healthcare_resources_cleaning.ipynb` — reproducible data preparation and cleaning notebook.
* `cleaning_log.txt` — documentation of cleaning steps, validation checks, and relevant findings.

## Data Preparation Principles

* Use the approved `country_dictionary_v1.csv` as the reference for country identifiers and names.
* Use `ISO3` and `Year` as the canonical country-year key.
* Preserve missing values as missing; do not replace them with zero.
* Do not interpolate, forward-fill, or backward-fill missing healthcare indicators.
* Keep raw source datasets unchanged.
* Validate data types, missing values, duplicate keys, and country-code mappings.
* Document excluded or unmatched source codes for review.

## Validation Requirements

The cleaned datasets should be checked for:

* Consistent ISO3 country identifiers.
* Integer `Year` values.
* Duplicate records using the appropriate country-year key.
* Numeric indicator columns.
* Missing-value patterns and indicator coverage.
* Consistency between the cleaned outputs, notebook, and cleaning log.

## Project Integration

These datasets will be reviewed alongside the other project datasets during the integration phase. Final integration will be performed by the project lead using `ISO3 + Year`.

## Important Notes

This folder contains task-level outputs only. It does not represent the final integrated analytical dataset.

Missing healthcare values must remain missing unless a documented and approved project-level decision specifies otherwise.

---

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Data Preparation & Cleaning
**Task:** Healthcare Workforce & Capacity
