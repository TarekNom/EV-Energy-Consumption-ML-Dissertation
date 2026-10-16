# A Machine Learning Approach to Predicting Electric Vehicle Energy Consumption and Supporting Range Estimation Using Driving Behaviour and Environmental Data

**MSc Data Science Dissertation**

**University of East London (UEL) | Unicaf**

## Project Overview

This project investigates machine-learning approaches for predicting real-world electric vehicle (EV) energy consumption and supporting driving-range estimation using driving behaviour and environmental data.

The research integrates observations from three EV data sources and examines predictive accuracy, cross-dataset generalisation, and model explainability.

## Datasets

- **Vehicle Energy Dataset (VED)** — Real-world vehicle driving data.
- **BMW i3 Dataset** — EV driving and energy consumption observations.
- **Argonne National Laboratory D3** — Vehicle dynamometer testing data.

The original datasets are not redistributed in this repository.

## Machine Learning Methods

The study evaluates:

- Linear Regression
- Random Forest
- XGBoost
- Stacking Ensemble

Random Forest was selected as the primary model for further analysis.

## Evaluation

The analysis uses:

- Mean Absolute Error (MAE)
- Root Mean Squared Error (RMSE)
- Coefficient of Determination (R²)
- Mean Absolute Percentage Error (MAPE)
- Cross-validation and cross-dataset evaluation
- SHAP explainability analysis

## Main Results

The selected Random Forest model achieved the following results on the pooled holdout set:

| Metric | Result |
|---|---|
| R² | 0.446 |
| MAE | 3.032 kWh/100 km |
| RMSE | 4.333 kWh/100 km |
| MAPE | 20.08% |

These results should be interpreted alongside the study's group-aware and cross-dataset evaluations, which revealed limitations in model generalisation.

## Repository Structure

1. `01_VED_EDA.ipynb` — VED exploration and preparation
2. `02_BMW_i3_PIPELINE.ipynb` — BMW i3 data processing
3. `03_ARGONNE_PIPELINE.ipynb` — Argonne D3 data processing
4. `04_DATASET_HARMONIZATION.ipynb` — Dataset integration and harmonisation
5. `05_MACHINE_LEARNING_PIPELINE.ipynb` — Model training, evaluation and explainability

## Software

Python, pandas, NumPy, scikit-learn 1.8.0, XGBoost, Optuna, SHAP, Matplotlib and Jupyter Notebook.

## Limitations

The study uses a relatively small harmonised sample and has limitations related to vehicle coverage, dataset heterogeneity and potential dependence between observations. The range estimates are derived from observed energy consumption rather than validated against independent real-world range outcomes.

## Academic Context

This repository accompanies an MSc Data Science dissertation undertaken through Unicaf in partnership with the University of East London (UEL).

The code is provided for academic transparency and reproducibility. Original dataset licensing and attribution requirements remain applicable.
