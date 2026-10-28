# Exploratory Data Analysis & Statistical Analysis

## Project Overview

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Phase 2 — Exploratory Data Analysis & Data Analysis

## Overview

This directory contains the analytical work produced by the five team members after the completion of the initial data preparation, standardization, and integration phase.

The purpose of this phase is to explore the available data, investigate relationships between healthcare coverage and its demographic, socioeconomic, healthcare-system, and financial dimensions, and produce evidence-based findings that will support the project's final dashboards and report.

The analysis will use the integrated dataset and its supporting validation and coverage reports as the primary starting point.

## Primary Analytical Dataset

`03_Integrated_Datasets/integrated_healthcare_dataset.csv`

The integrated dataset contains 12,855 country-year records and 27 columns, covering 1960–2025.

The canonical matching key is:

`ISO3 + Year`

The integrated dataset preserves the available values from the seven standardized source datasets. Indicator availability varies by country and year, so each analysis must select observations based on the variables required for its specific research question.

## Team Workstreams

### Task 1 — Demographic Analysis

**Task Owner:** Fatma Awad

Focus:

* Population size and demographic structure.
* Population aged 0–14 years.
* Population aged 65 years and above.
* Urban population percentage.
* Relationships between demographic characteristics and healthcare service coverage.

Expected outputs:

* `demographic_analysis.ipynb`
* `demographic_analysis_summary.csv`
* Relevant analytical charts.
* A concise findings and limitations report.

### Task 2 — Socioeconomic & Education Analysis

**Task Owner:** Aya Nasr

Focus:

* GDP per capita, PPP (constant 2021 international dollars).
* Secondary school enrollment.
* Adult literacy.
* Relationships between socioeconomic and education indicators and healthcare coverage or financing.

Expected outputs:

* `socioeconomic_analysis.ipynb`
* `socioeconomic_analysis_summary.csv`
* Relevant analytical charts.
* A concise findings and limitations report.

Adult literacy has substantially lower data availability than the other indicators. Its findings must therefore be interpreted with attention to sample size and coverage.

### Task 3 — Healthcare Resources Analysis

**Task Owner:** Shereen

Focus:

* Total doctors.
* Doctors per 10,000 population.
* Nurses and midwives per 10,000 population.
* Hospital beds per 10,000 population.
* Relationships between healthcare workforce, system capacity, and service coverage.

Expected outputs:

* `healthcare_resources_analysis.ipynb`
* `healthcare_resources_analysis_summary.csv`
* Relevant analytical charts.
* A concise findings and limitations report.

Indicator definitions, units, and source limitations must be reviewed before interpreting results.

### Task 4 — Healthcare Coverage & Financing Analysis

**Task Owner:** Hassan Mostafa

Focus:

* Universal Health Coverage Service Coverage Index.
* Current health expenditure per capita, PPP.
* Current health expenditure as a percentage of GDP.
* Out-of-pocket expenditure as a percentage of current health expenditure.
* Relationships between healthcare service coverage, health expenditure, and financial protection.

Expected outputs:

* `coverage_financing_analysis.ipynb`
* `coverage_financing_analysis_summary.csv`
* Relevant analytical charts.
* A concise findings and limitations report.

PPP-adjusted international dollars must be distinguished from nominal US dollars and local currencies. Percentage indicators must retain their source definitions.

### Task 5 — Financial Hardship & Equity Analysis

**Task Owner:** Abdelrahman

Focus:

* Total financial hardship.
* Large healthcare spending.
* Impoverishing healthcare spending.
* Financial hardship across consumption quintiles.
* Equity gap measures.
* Relationships between financial hardship, healthcare coverage, and relevant socioeconomic or financing indicators.

Expected outputs:

* `financial_equity_analysis.ipynb`
* `financial_equity_analysis_summary.csv`
* Relevant analytical charts.
* A concise findings and limitations report.

Financial hardship and equity observations are based on survey years. They must not be treated as continuous annual observations when no survey data exist for a given year.

## Common Analytical Workflow

All team members should follow a consistent workflow:

1. Define a specific research question.
2. Identify the indicators needed to answer it.
3. Review indicator definitions, units, source limitations, and data coverage.
4. Select the observations for which the required indicators are available.
5. Examine distributions, missingness, outliers, and potential data-quality issues.
6. Produce appropriate descriptive statistics and visualizations.
7. Conduct statistical comparisons or association analyses when justified by the data.
8. Interpret the results in context and document relevant limitations.
9. Save reproducible code, analytical outputs, charts, and a concise written summary.

## Data Handling Rules

* Treat the integrated dataset as the project's central analytical starting point.
* Keep original raw datasets and task-level cleaned datasets unchanged.
* Do not replace missing values with zero.
* Do not invent, interpolate, or extrapolate missing healthcare, financial, or socioeconomic measurements.
* Do not treat missing observations as evidence of zero activity.
* Do not assume all indicators are available for every country and year.
* Use observations appropriate to the specific research question.
* Preserve the distinction between annual data and survey-year observations.
* Document any exclusions, transformations, or additional assumptions.
* Do not overwrite the integrated master dataset with analysis-specific subsets.

## Statistical Interpretation

Analytical results should distinguish association from causation.

A correlation or statistical association does not, by itself, establish that one factor causes another.

Where appropriate, document:

* The number of observations used.
* The number of countries represented.
* The time period covered.
* Missing-data limitations.
* Important measurement and comparability limitations.
* The statistical methods used and their assumptions.

Conclusions must be supported by the observed data and the analysis performed.

## Expected Deliverables

Each team member should submit:

* A reproducible Jupyter Notebook.
* A CSV containing relevant analytical summaries or results, where appropriate.
* Clear and appropriately labeled analytical charts.
* A concise report describing the research questions, methods, principal findings, and limitations.

The team lead will review the individual outputs, consolidate the findings, and coordinate the next stage of dashboard development and project reporting.

## Project Roadmap

1. Data Preparation & Cleaning — completed at task level.
2. Data Integration & Structural Validation — completed for the current integration version.
3. Exploratory Data Analysis & Statistical Analysis — current phase.
4. Results Consolidation and Interpretation.
5. Dashboard Development.
6. Final Reporting and Presentation.

## Important Note

The successful structural validation of the integrated dataset does not establish that every source measurement is error-free or that every indicator is suitable for every analysis. Source definitions, units, coverage, and analytical assumptions must be reviewed before conclusions are drawn.

---

**Project:** Global Healthcare Performance & Equity Analysis
**Phase:** Exploratory Data Analysis & Data Analysis
**Primary Dataset:** `integrated_healthcare_dataset.csv`
**Canonical Key:** `ISO3 + Year`
