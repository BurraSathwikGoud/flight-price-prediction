# ✈️ Flight Price Prediction using Machine Learning

## 📌 Project Overview
Flight ticket prices are highly dynamic and influenced by multiple factors such as airline, journey date, stops, and duration.  
This project aims to build a machine learning model to predict flight prices based on historical data.

---

## 🎯 Objective
To analyze flight data and build a predictive model that can estimate ticket prices, helping users make informed travel decisions.

---

## 📊 Dataset Features
The dataset contains the following features:

- Airline
- Date of Journey
- Source
- Destination
- Route
- Departure Time
- Arrival Time
- Duration
- Total Stops
- Additional Information
- Price (Target Variable)

---

## 🛠️ Data Preprocessing

The following preprocessing steps were performed:

- Handled missing values using `dropna()`
- Removed duplicate records
- Feature engineering:
  - Extracted **day and month** from Date_of_Journey
  - Extracted **hour and minute** from time columns
  - Converted **Duration into minutes**
- Dropped unnecessary columns:
  - `Route` (redundant with Source, Destination, and Stops)
  - `Additional_Info` (low variance, mostly "No info")
- Applied **One-Hot Encoding** for categorical variables

---

## ⚠️ Handling Outliers

Outliers were analyzed but **not removed**, based on the following reasoning:

- Extreme values in flight prices represent **real-world scenarios** such as:
  - Night flights 🌙
  - Premium airlines ✈️
  - Long-duration journeys ⏳
- Removing these values would lead to **loss of important information**

👉 Therefore, outliers were retained to preserve real-world data patterns.

---

## ⚠️ Feature Scaling

Feature scaling (StandardScaler) was **not applied** because:

- Tree-based models such as:
  - Decision Tree  
  - Random Forest  
  - XGBoost  
  **do not depend on feature scaling**
- These models split data based on feature thresholds, not distance

👉 Hence, skipping scaling improves simplicity without affecting performance.

---

## 🤖 Models Used

The following regression models were implemented:

- Linear Regression
- Decision Tree Regressor
- Random Forest Regressor
- XGBoost Regressor

---

## 📈 Model Performance

| Model                 | R² Score |
|----------------------|---------|
| Linear Regression    | ~58%    |
| Decision Tree (Tuned)| ~78%    |
| Random Forest (Tuned)| 83.03%  |
| XGBoost (Tuned)      | **~84% ⭐** |

---

## 🏆 Final Model

**XGBoost Regressor** was selected as the final model because:

- It achieved the highest R² score (~84%)
- Effectively captures non-linear relationships
- Includes regularization to reduce overfitting
- Performs efficiently on structured tabular data

---

## ⚙️ Hyperparameter Tuning

GridSearchCV was used to optimize model performance.

### Best Parameters (XGBoost):{'learning_rate': 0.1, 'max_depth': 7, 'n_estimators': 100, 'subsample': 0.8}