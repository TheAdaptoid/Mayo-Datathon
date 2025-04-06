---
tags:
  - hackathon
  - research
  - python
  - sql
  - google
  - healthcare
aliases:
  - Mayo Hackathon
  - Datathon
---

# Abstract

## Key Terms

- **Sepsis**: A life-threatening condition where the body's response to infection causes tissue damage, organ failure, or death.
- **Troponin-T**: A protein found in heart muscle, released into the bloodstream when the heart is damaged, often used to diagnose heart attacks.

# Introduction

## Problem Statement

In patients with sepsis and no documented prior heart disease in MIMIC-IV, is an elevated troponin T level during the ICU stay associated with increased in-hospital mortality compared to those with normal troponin T levels?

## Importance / Relevance

Sepsis is a life-threatening condition, and early risk stratification is crucial for improving patient outcomes. While troponin T is traditionally a cardiac biomarker, its elevation in sepsis patients without prior heart disease may indicate underlying organ dysfunction and increased mortality risk. Identifying this association can help refine clinical decision-making and prioritize high-risk patients for intensive monitoring. This study aims to provide insights into whether troponin T levels can serve as a prognostic marker in sepsis management.

# Data Extraction, Transformation, and Analysis

## Extract, Transform, Load

### Inclusion Criteria

- Admitted with a prior diagnosis of Sepsis
- Admitted to an ICU
- Has at least *one* Troponin-T lab test
- Has a recorded discharge reason

### Exclusion Criteria

- Has any prior heart condition
- Does not have any Troponin-T lab tests
- Discharged from the ICU within 24-hours

### Main Table Structure

| Column Name               | Data Type | Description                                                                              |
| ------------------------- | --------- | ---------------------------------------------------------------------------------------- |
| patientunitstayid         | INTEGER   | Surrogate key for ICU Stay                                                               |
| hospitalid                | INTEGER   | Surrogate key for the hospital associated with the patient unit stay                     |
| unittype                  | VARCHAR   | Type of ICU Unit                                                                         |
| unitadmitsource           | VARCHAR   | Source of admission to ICU                                                               |
| gender                    | VARCHAR   | Gender of the patient                                                                    |
| age                       | INTEGER   | Age of the patient                                                                       |
| ethnicity                 | VARCHAR   | Ethnicity of the patient                                                                 |
| unitdischargeoffset_hours | FLOAT     | Number of hours from admission to discharge                                              |
| max_troponi               | FLOAT     | Maximum troponin level recorded                                                          |
| non_cardiac_patient       | INTEGER   | Indicator for patients without history of caridac issues or admission for cardiac issues |
| expired                   | INTEGER   | Indicator for patients who expired while in the ICU                                      |

### Predictors Table

| Column Name | Data Type | Description |
| ----------- | --------- | ----------- |
|             |           |             |

## Discretionary Considerations

### Elevated Troponin-T Level Definition

We chose to assign any patient with a Troponin-T value greater than 0.01 ng/mL as having an *abnormal* amount of Troponin-T in their blood. And for patients with multiple Troponin-T lab tests, we chose to only use the value of their *highest* Troponin-T lab test result.

### Early Discharges

To focus on longer term outcomes, patients who were discharged from the ICU (alive or expired) within 24-hours of admittance were not included in our study.

### eICU vs MIMIC-IV

After conducting some initial EDA and research, we decided to switch the primary dataset from MIMIC-IV to eICU. The sourcing methodology for the eICU database aligned better with our interests than that of the MIMIC-IV database.

## Exploratory Data Analysis

### Potential Issues and Biases

#### Survivorship Bias

Patients who died before a Troponin-T measurement could be acquired may be excluded from our curated dataset, and could lead to underestimating its true prognostic value.

#### Selection Bias

The our curated dataset includes only ICU patients, as such, our conclusions may not hold true for *non-ICU admitted* patients.

### Visualizations

- Needs Work

# Conclusion

## Chi-Square

text

## Odds Ratio

text

## Logistic Regression

text

## Interpretation

text

# Discussion

## Limitations

text

## Next Steps

text
