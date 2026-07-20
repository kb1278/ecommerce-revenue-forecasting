# E-Commerce Revenue Forecasting

## Project Overview

This project builds an end-to-end revenue forecasting pipeline using the **Olist Brazilian E-Commerce dataset**.

The objective was to predict future monthly revenue by comparing two forecasting approaches:

- **ARIMA** - Statistical time-series forecasting model
- **XGBoost** - Machine learning forecasting model using engineered time-series features

The project workflow includes:

- Data integration
- Exploratory time-series analysis
- Revenue aggregation
- Feature engineering
- Model training
- Forecast evaluation using MAE and RMSE
- Feature importance analysis

---

# Business Problem

Accurate revenue forecasting helps e-commerce businesses:

- Improve financial planning
- Support inventory management
- Identify future sales trends
- Make data-driven operational decisions

The goal of this project was to develop a forecasting model capable of predicting future monthly revenue from historical transaction data.

---

# Dataset

**Dataset:** Olist Brazilian E-Commerce Dataset

Source:
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

The dataset contains information about:

- Customer orders
- Payments
- Products
- Sellers
- Delivery performance
- Customer reviews

This project used:

| Dataset | Purpose |
|---|---|
| `olist_orders_dataset.csv` | Order dates and order information |
| `olist_order_payments_dataset.csv` | Revenue and payment values |

---

# Project Workflow

```
                Data Sources
                     |
                     v
       Orders Dataset + Payments Dataset
                     |
                     v
             Data Integration
        (Merge orders and payments)
                     |
                     v
             Data Exploration
       (Data types and missing values)
                     |
                     v
          Revenue Aggregation
      (Monthly revenue calculation)
                     |
                     v
     Exploratory Time-Series Analysis
          (Revenue trends)
                     |
                     v
           Train/Test Split
        (Six-month holdout testing)
                     |
          +----------+----------+
          |                     |
          v                     v
       ARIMA              XGBoost
   Statistical Model   ML Forecasting
                              |
                              v
                  Feature Engineering
              (Lag features + rolling averages)
                     |
                     v
             Model Evaluation
             (MAE and RMSE)
                     |
                     v
            Feature Importance Analysis
```

---

# Technologies Used

## Programming & Data Analysis

- Python
- Pandas
- NumPy
- Matplotlib

## Machine Learning & Statistics

- Statsmodels (ARIMA)
- XGBoost
- Scikit-learn

## Environment

- Jupyter Notebook
- Git & GitHub

---

# Data Preparation

Steps performed:

- Loaded order and payment datasets
- Converted timestamps into datetime format
- Merged order and payment information
- Checked missing values
- Aggregated transaction-level data into monthly revenue

Revenue calculation:

```
Monthly Revenue = Sum(payment_value)
```

---

# Exploratory Analysis

Analysed:

- Monthly revenue trends
- Revenue growth patterns
- Time-series behaviour
- Historical fluctuations

Key observation:

- Revenue increased significantly throughout the analysed period, with strong variations between months.

---

# Forecasting Models

## 1. ARIMA Forecasting

ARIMA was used as a traditional statistical forecasting approach.

Model:

```
ARIMA(1,1,1)
```

The model used historical revenue values to predict future monthly revenue.

---

## 2. XGBoost Forecasting

XGBoost was implemented as a machine learning forecasting approach.

Feature engineering included:

### Time Features

- Year
- Month
- Quarter

### Lag Features

- Previous month revenue
- Two-month lag
- Three-month lag
- Six-month lag

### Rolling Statistics

- Three-month rolling average
- Six-month rolling average
- Three-month rolling standard deviation

These features allowed the model to capture recent revenue trends and patterns.

---

# Model Evaluation

Models were evaluated using a six-month holdout test set.

Metrics:

### Mean Absolute Error (MAE)

Measures the average difference between actual and predicted revenue.

### Root Mean Squared Error (RMSE)

Measures prediction error while penalising larger forecasting mistakes.

---

## Model Performance

| Model | Approach | MAE (BRL) | RMSE (BRL) |
|---|---|---:|---:|
| ARIMA | Statistical forecasting | 502,347.62 | 710,644.07 |
| XGBoost | Machine learning forecasting | 395,933.95 | 599,111.31 |

---

# Results

XGBoost achieved the best forecasting performance.

Compared with ARIMA:

- Reduced MAE by approximately **21%**
- Reduced RMSE by approximately **16%**

The improvement came from using additional forecasting features:

- Lag variables
- Rolling averages
- Time-based features

---

# Feature Importance

XGBoost feature importance analysis was performed to understand which variables contributed most to predictions.

Important features included:

- Historical revenue values
- Lag features
- Rolling revenue trends

This improved model interpretability and helped identify key forecasting drivers.

---

# Business Insights

The forecasting pipeline demonstrated how historical transaction data can be transformed into predictive insights.

Potential business applications:

- Revenue planning
- Sales forecasting
- Budget preparation
- Inventory optimisation
- Operational decision-making

---

# Repository Structure

```
ecommerce-revenue-forecasting/

│
├── ecommerce_revenue_forecasting.ipynb
├── README.md
├── requirements.txt
│
└── images/
    ├── revenue_trend.png
    ├── arima_forecast.png
    ├── xgboost_forecast.png
    └── feature_importance.png
```

---

# Installation

Install required libraries:

```bash
pip install pandas numpy matplotlib scikit-learn statsmodels xgboost
```

---

# Running the Project

Clone the repository:

```bash
git clone https://github.com/kb1278/ecommerce-revenue-forecasting.git
```

Open the notebook:

```
ecommerce_revenue_forecasting.ipynb
```

Run all cells to reproduce the analysis and forecasting results.

---

# Conclusion

This project demonstrates an end-to-end machine learning forecasting workflow, from raw transaction data integration through model development and evaluation.

By comparing ARIMA and XGBoost models, the project showed that machine learning-based forecasting with engineered time-series features provided stronger revenue predictions for this dataset.

---


