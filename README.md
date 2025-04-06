# Mayoclinic Datathon 2025

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
- Discharged from the ICU within 24-hours

### Table Structure

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
| abnormal_troponi          | INTEGER   | Indicator for patients with abnormal troponin levels                                     |

## Discretionary Considerations
