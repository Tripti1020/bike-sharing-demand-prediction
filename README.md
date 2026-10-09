<<<<<<< HEAD
# Bike Sharing Demand Prediction

Predicts the number of bikes rented per hour from weather, time and calendar features. The project covers data cleaning, EDA, feature engineering, statistical checks (OLS) and a comparison of three regression models.

## Problem statement
A bike-sharing service needs to know how many bikes will be rented each hour so it can keep enough bikes available. This project builds and compares regression models that predict hourly rental demand.

## Dataset
- 8,760 hourly records (one year) and 14 columns
- Target: `Rented Bike Count`
- Features: date, hour, temperature, humidity, wind speed, visibility, dew point temperature, solar radiation, rainfall, snowfall, season, holiday, functioning day
- File: `data/1776241192-P4-Bike_Sharing_Demand_Prediction.csv`

## Tech stack
Python, Pandas, NumPy, Scikit-learn, Statsmodels, Seaborn, Matplotlib, Jupyter Notebook

## Approach
1. **Cleaning and feature engineering:** renamed columns, converted dates, extracted month and weekday/weekend, one-hot encoded categorical variables.
2. **EDA:** studied demand by hour, month, season, temperature and functioning day.
3. **Statistical checks:** used OLS and correlation analysis to find multicollinearity between Temperature and Dew Point Temperature, then removed Dew Point.
4. **Target transformation:** applied a square-root transform to reduce right skew and the effect of outliers.
5. **Modelling:** 75:25 train-test split (`random_state=0`). Compared Linear Regression, Random Forest and Gradient Boosting, with 5-fold cross-validation.
6. **Evaluation:** predictions were squared back to real bike counts before computing test-set metrics.

## Key findings from EDA
- Weekday demand peaks at 7-9 AM and 5-7 PM (commute hours).
- Demand is highest from May to October and lowest in winter.
- Rentals are strongest around 25 degrees C.
- Non-functioning days show almost no rentals.

## Results (test set, real bike counts)

| Model | Test R2 | RMSE (bikes/hr) | MAE (bikes/hr) | 5-fold CV R2 |
|---|---|---|---|---|
| Linear Regression | 0.765 | 312.9 | 212.6 | 0.774 |
| Gradient Boosting | 0.887 | 217.0 | 142.4 | 0.901 |
| **Random Forest** | **0.910** | **193.3** | **109.7** | **0.926** |

- Random Forest reduced RMSE by about 38% compared with Linear Regression.
- Top predictors in Random Forest: Temperature, Humidity and Functioning Day.
- Limitation: Random Forest fits the training data much more closely than the test data (train R2 about 0.99), so some overfitting remains. Tuning `max_depth` or `min_samples_leaf` would be the next step.

## How to run
```bash
git clone https://github.com/Tripti1020/bike-sharing-demand-prediction.git
pip install -r requirements.txt
jupyter notebook Bike_Sharing_Demand_Prediction.ipynb
```
Run all cells from top to bottom. Make sure the CSV path in the notebook matches the `data/` folder.

## Project structure
```
.
|-- Bike_Sharing_Demand_Prediction.ipynb
|-- data/
|   `-- 1776241192-P4-Bike_Sharing_Demand_Prediction.csv
|-- requirements.txt
`-- README.md
```

## Possible improvements
- Hyperparameter tuning (GridSearchCV or RandomizedSearchCV)
- Try XGBoost or LightGBM
- Time-based train-test split instead of a random split
- Deploy a small Streamlit app for live predictions

## Author
Tripti | MCA, Kurukshetra University
=======
# bike-sharing-demand-prediction
>>>>>>> aa4c47d9c888970e54d7eefca8e6bc25d19d6694
