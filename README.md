# Ensemble Forecasting Model

This repository contains a Python-based ensemble machine learning model that predicts:

- Total energy consumption
- Average temperature
- Average humidity
- CO₂ levels

It uses:
- Random Forest
- XGBoost
- Linear Regression

## Run Instructions

1. Install dependencies:
pip install pandas numpy scikit-learn xgboost matplotlib

2. Run the model

The model reads data, performs feature engineering, trains the ensemble, and outputs performance metrics and visual plots.
## Dataset

The dataset is too large to host on GitHub.  
You can download it from [this Google Drive link](https://drive.google.com/file/d/19J2wmJw6NGHFBgIW1squGpfHRlG97w6-/view?usp=sharing).
## 📊 Dataset Description

This project uses a preprocessed version of the **PLEIAData** dataset, collected from smart buildings in the PHOENIX Horizon 2020 project. It contains high-resolution, time-aligned sensor readings from three residential buildings (Blocks A, B, and C) over a full year (2021).

 Key Features

-  Power Consumption
  - Real energy usage data from three blocks
  - Column: `dif_cons_real`

-  Environmental Parameters
  - Indoor temperature (multiple sensors): `temp_sensor_1`, `temp_sensor_2`, `temp_sensor_3`
  - Relative humidity: `hrmed`
  - CO₂ concentration: `V17` → renamed to `CO2_ppm`
  - Weather data: solar radiation, wind speed, ambient temperature

- Timestamp Alignment
  - All sources are resampled to **hourly intervals**
  - Merged on a common `Date` column

 Preprocessing Steps

- Merged 8+ data sources into one unified DataFrame
- Generated:
  - `total_consumption` = sum of Block A + B + C
  - `average_temperature` and `average_humidity`
  - **Lag features** at 1, 2, 6, 12, and 24-hour intervals
  - **Rolling mean** features over 6 and 12 hours
  - **Time encodings**: `hour_sin`, `hour_cos`, `dayofweek`, `month`

 Forecasting Targets

The model forecasts the following key environmental and energy metrics:

- `total_consumption`
- `average_temperature`
- `average_humidity`
- `CO2_ppm`

 Dataset Citation

> A. Martínez Ibarra, A. González-Vidal, and A. Skarmeta,  
> *"PLEIAData: Consumption, HVAC, Temperature, Weather and Motion Sensor Data for Smart Buildings"*,  




