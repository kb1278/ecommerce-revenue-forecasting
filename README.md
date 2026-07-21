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
- Converted order purchase timestamps into datetime format
- Merged order and payment information using `order_id`
- Checked data types and missing values
- Aggregated transaction-level payment data into monthly revenue
- Excluded September and October 2018 from the modelling dataset to avoid incomplete final periods


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

- Monthly revenue increased substantially during the earlier part of the analysed period before showing fluctuations in the later months.

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
- Month number
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

All rolling statistics were calculated using historical revenue values to avoid using future information when generating features.

These features allowed the model to capture recent revenue trends and historical patterns.

---

# Model Evaluation

Models were evaluated using a chronological six-month holdout test set covering:

**March 2018 to August 2018**

The final six months were held out from model training and used only for evaluating forecasting performance.

## Metrics

### Mean Absolute Error (MAE)

Measures the average absolute difference between actual and predicted revenue.

### Root Mean Squared Error (RMSE)

Measures prediction error while penalising larger forecasting mistakes.

---

## Model Performance

| Model   | Approach                     | MAE (BRL) | RMSE (BRL) |
| ------- | ---------------------------- | --------- | ---------- |
| ARIMA   | Statistical forecasting      | 49,734.35 | 73,659.58  |
| XGBoost | Machine learning forecasting | 90,298.60 | 110,675.97 |

---


# Results

ARIMA achieved the best forecasting performance on the six-month holdout test set.

Compared with XGBoost:

- Reduced MAE by approximately **45%**
- Reduced RMSE by approximately **33%**

The stronger performance of ARIMA suggests that the statistical model was better suited to capturing the underlying revenue trend during this evaluation period.

Although XGBoost used additional time-based features, lag variables and rolling statistics, the relatively small number of monthly observations may have limited its ability to generalise effectively.

The results demonstrate the importance of evaluating both statistical and machine learning approaches rather than assuming that a more complex machine learning model will necessarily produce better forecasts.

---

# Feature Importance

XGBoost feature importance analysis was performed to understand which engineered variables contributed most to the model's predictions.

The analysis examined the relative importance of:

- Historical revenue lag variables
- Rolling revenue statistics
- Time-based features

This provided additional insight into which historical patterns the machine learning model used when generating forecasts.

---

# Business Insights

The forecasting pipeline demonstrates how historical e-commerce transaction data can support forward-looking business decisions.

Potential applications include:

- **Revenue planning:** Forecast expected monthly revenue to support financial planning and budgeting.
- **Sales forecasting:** Identify expected future revenue patterns and support sales target setting.
- **Inventory optimisation:** Use revenue forecasts to help anticipate future demand and inform inventory planning.
- **Operational decision-making:** Support resource allocation and business planning using data-driven revenue expectations.
- **Performance monitoring:** Compare actual revenue against forecasts to identify unexpected changes in business performance.

The model comparison also provides a practical business insight: **the most complex model is not always the best-performing model**. In this project, ARIMA achieved lower forecasting errors than XGBoost, demonstrating the importance of selecting models based on performance on unseen, time-ordered data rather than model complexity alone.



---

# Repository Structure

```
ecommerce-revenue-forecasting/

│
├── ecommerce_revenue_forecasting.ipynb
├── README.md
├── requirements.txt

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

This project demonstrates an end-to-end revenue forecasting workflow, from raw transaction data integration through time-series analysis, feature engineering, model development and evaluation.

Two forecasting approaches were compared using a six-month chronological holdout test set:

- ARIMA - Statistical time-series forecasting
- XGBoost - Machine learning forecasting with engineered time-series features

ARIMA achieved the strongest forecasting performance, with an MAE of 49.7K BRL and an RMSE of 73.7K BRL, compared with XGBoost's MAE of 90.3K BRL and RMSE of 110.7K BRL.

ARIMA achieved approximately 45% lower MAE and 33% lower RMSE than XGBoost.

The results highlight the importance of comparing multiple modelling approaches and selecting the model that performs best on unseen, time-ordered data. While XGBoost provided a flexible feature-based modelling approach, ARIMA was better suited to this dataset and evaluation period.

---


