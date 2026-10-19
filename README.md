# A Machine Learning Approach to Predicting Electric Vehicle Energy Consumption and Supporting Range Estimation Using Driving Behaviour and Environmental Data

**MSc Data Science Dissertation**
**University of East London (UEL) | Unicaf**

## Project Overview

This project investigates machine-learning approaches for predicting electric vehicle (EV) energy consumption and supporting driving-range estimation using driving behaviour and environmental data.

The research harmonises observations from three EV data sources (on-road and laboratory) and examines predictive accuracy, cross-dataset generalisation and model explainability.

## Datasets

- **Vehicle Energy Dataset (VED)**: naturalistic on-road driving data (three 2013 Nissan Leaf BEVs)
- **BMW i3 Battery and Heating Data in Real Driving Cycles**: on-road trips of a BMW i3
- **Argonne National Laboratory D3**: chassis-dynamometer tests of a 2014 BMW i3

The harmonised dataset contains 575 observations (VED 488, BMW 68, Argonne 19). The original datasets are not redistributed in this repository.

## Machine Learning Methods

Linear Regression, Random Forest, XGBoost and a stacking ensemble were compared. Random Forest was selected as the final model.

## Evaluation

MAE, RMSE, R² and MAPE; five-fold cross-validation; group-aware and leave-one-dataset-out validation; paired bootstrap confidence intervals; SHAP explainability.

## Main Results

Final Random Forest on the 115-observation holdout set:

| Metric | Result |
|---|---|
| R² | 0.446 |
| MAE | 3.032 kWh/100 km |
| RMSE | 4.333 kWh/100 km |
| MAPE | 20.08% |

The holdout set also informed final model selection, so these figures are somewhat optimistic. Performance fell under group-aware validation (R² = 0.180) and leave-one-dataset-out validation (R² from 0.141 to −0.444), indicating limited generalisation across vehicles and data sources.

## Repository Structure

1. `01_VED_EDA.ipynb`: VED preparation, target construction and range estimation
2. `02_BMW_i3_PIPELINE.ipynb`: BMW i3 data processing
3. `03_ARGONNE_PIPELINE.ipynb`: Argonne D3 data processing
4. `04_DATASET_HARMONIZATION.ipynb`: dataset integration and harmonisation
5. `05_MACHINE_LEARNING_PIPELINE.ipynb`: model training, evaluation and explainability

**Run order:** 02 → 03 → 04 → 05, then 01 (its range-estimation section uses outputs from notebook 05).

## Running the Notebooks

The notebooks use absolute Windows paths from the original project folder (`C:\Projects\DS7010_Dissertation\`). To run them elsewhere, recreate this folder structure or replace that path in the path definitions at the top of each notebook.

```
01-Datasets/
    01-VED/        (VED dynamic CSVs and VED_Static_Data_PHEV&EV.xlsx)
    Harmonised/    (created by notebook 04)
02-Processed/      (created by notebooks 02 and 03)
03-Notebooks/      (these five notebooks)
06-Results/        (created by notebook 05)
```

Raw data sources:
- VED: https://github.com/gsoh/VED
- BMW i3: https://doi.org/10.21227/6jr9-5235
- Argonne D3 (2014 BMW i3): https://www.anl.gov/taps/d3-2014-bmw-i3bev

## Software

Python with pandas 3.0.3, NumPy 2.4.6, scikit-learn 1.8.0, XGBoost 3.2.0, Optuna 4.8.0, SHAP 0.52.0, Matplotlib and Jupyter (see `requirements.txt`).

## Limitations

The harmonised sample is small and imbalanced (84.9% VED) and covers only two vehicle models. Feature definitions differ partly between sources, and observations from the same vehicle may be dependent. Range estimates are derived from predicted energy consumption under a nominal 24 kWh battery capacity and are not validated against independent real-world range outcomes.

## Data Attribution

This data is from the Downloadable Dynamometer Database and was generated at the Advanced Mobility Technology Laboratory (AMTL) at Argonne National Laboratory under the funding and guidance of the U.S. Department of Energy (DOE).

## Academic Context

This repository accompanies an MSc Data Science dissertation undertaken through Unicaf and awarded by the University of East London (UEL). The code is provided for academic transparency. Original dataset licensing and attribution requirements remain applicable.
