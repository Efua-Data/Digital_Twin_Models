# Digital_Twin_Models

Digital Twin Models for personalised simulation of diabetic and hypertensive medication efficacy
## Overview

This research investigates whether patient-specific digital twin models can personalise the simulation of diabetic and hypertensive medication efficacy using data available in a resource-constrained clinical setting.

The central finding is that **data structure, rather than model complexity, is the primary constraint on personalisation**. A single clinical snapshot cannot provide enough information to reliably identify individual treatment-response parameters, whereas longitudinal, dose-aware data substantially improves parameter recovery and predictive performance.

## Research Question

Can routinely collected clinical data from a Ghanaian healthcare setting identify patient-specific parameters required for personalised digital twin modelling of diabetes and hypertension treatment response?

## Methodology

- Retrospective, de-identified electronic medical record cohort: **441 records / 378 unique patients**
- Conditions: Type 2 diabetes, hypertension, and their comorbidity
- Modified **Bergman minimal model** for glucose dynamics
- Simplified physiological blood-pressure model for hypertension
- Drug-effect modules using population-level pharmacodynamic parameters
- Differential Evolution for parameter estimation
- Temporal holdout validation for longitudinal data
- Evaluation using RMSE, MAPE, R², Lin's CCC, Bland–Altman analysis, and parameter-recovery metrics
- Controlled three-arm experiment comparing:
  1. Real-world snapshot data
  2. Idealised longitudinal dose-aware data
  3. Longitudinal data with model misspecification

## Key Findings

### 1. Real-world snapshot data could not support reliable personalisation

Using the as-captured clinical data:

| Outcome | R² |
|---|---:|
| Fasting glucose | -0.015 |
| Systolic BP | -0.005 |
| Diastolic BP | -0.015 |

The negative/near-zero R² values indicate that the model could not outperform a simple cohort-mean prediction under the available data structure.

### 2. Longitudinal dose-aware data substantially improved performance

With repeated observations and recorded treatment doses:

| Outcome | R² | CCC |
|---|---:|---:|
| Fasting glucose | 0.898 | 0.950 |
| HbA1c | 0.860 | 0.930 |
| Systolic BP | 0.864 | 0.932 |
| Diastolic BP | 0.763 | 0.851 |

The controlled comparison showed that the same modelling framework can personalise trajectories when the data contain sufficient longitudinal information.

### 3. Identifiability was a central limitation

The study found that a full patient-specific parameter vector could not be reliably estimated from a single observation. In particular, **Emax and EC50 exhibited a trade-off**, demonstrating that good trajectory prediction does not necessarily mean that clinically meaningful individual parameters have been recovered.

### 4. Confounding by indication matters

Patients receiving more intensive treatment often had worse observed biomarkers because treatment escalation was associated with greater disease severity. Without dated treatment changes and longitudinal measurements, the data could not reliably distinguish treatment effects from the severity that prompted treatment.

## Main Contribution

The research provides a controlled demonstration that **digital twin personalisation depends on data identifiability and clinical data structure, not simply on selecting a more sophisticated model**.

It also proposes a minimal data specification for future real-world implementation:

- A baseline or low-dose measurement
- Repeated measurements across a treatment/dose change
- Medication doses recorded in standard units
- Dated clinical observations

These requirements primarily involve **clinical documentation and workflow**, rather than new technological infrastructure.

## Limitations

The study does **not** claim clinical validation of digital twins in real patients. Parameter recovery in the longitudinal experiment was performed against known simulated ground truth. Therefore, the results demonstrate methodological feasibility and identify the data requirements needed for future real-world validation.

## Future Work

The next step is to validate the framework using real longitudinal clinical records containing dated treatment changes and medication doses. Such data would allow patient-specific calibration to be tested prospectively in real clinical populations.

## Technologies

**Python · SciPy · Statistical Modelling · Machine Learning · Digital Twins · Pharmacometric Modelling · Healthcare Analytics**
