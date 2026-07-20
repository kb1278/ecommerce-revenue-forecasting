# E-Commerce Revenue Forecasting

## Project Overview

This project develops a time-series forecasting model to predict future monthly revenue for an e-commerce business using historical transaction data.

Using the **Olist Brazilian E-Commerce dataset**, transaction-level sales data was transformed into monthly revenue trends. Forecasting models were developed to identify future revenue patterns and support business decision-making around planning, budgeting, and inventory management.

---

## Business Problem

E-commerce companies need accurate revenue forecasts to:

- Improve financial planning
- Support inventory decisions
- Identify seasonal demand patterns
- Optimise marketing and operational strategies

The objective of this project was to build a forecasting model capable of predicting future monthly revenue based on historical sales performance.

---

## Dataset

**Dataset:** Olist Brazilian E-Commerce Dataset

Source:
https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce

The dataset contains:

- Customer information
- Orders
- Payments
- Products
- Reviews
- Sellers
- Delivery information

Key tables used:

| Table | Description |
|---|---|
| orders | Order dates and order status |
| order_payments | Payment values and transaction details |
| products | Product information |
| customers | Customer details |

---

# Project Workflow

## 1. Data Preparation

Steps performed:

- Loaded multiple datasets using Pandas
- Converted timestamps into monthly periods
- Joined order and payment tables
- Aggregated transaction-level data into monthly revenue
- Checked missing values and data quality

Example metric created:

```
Monthly Revenue = Sum(payment_value)
```

---

# 2. Exploratory Data Analysis

Analysed:

- Revenue growth trends
- Monthly seasonality
- Revenue fluctuations
- Historical sales patterns

Key findings:

- Revenue increased significantly during the dataset period
- Customer purchasing behaviour showed seasonal patterns
- Monthly aggregation provided a clearer view of business performance

---

# 3. Feature Engineering

Created forecasting features including:

- Monthly revenue
- Lag variables
- Rolling averages
- Time-based features

Example features:

| Feature | Description |
|---|---|
| lag_1 | Previous month's revenue |
| lag_3 | Revenue from three months earlier |
| rolling_mean | Moving average revenue |
| month | Calendar month |

---

# 4. Forecasting Models

## Prophet Model

Developed a time-series forecasting model using Prophet.

Prophet was selected because it handles:

- Trend changes
- Seasonality
- Business time-series patterns

## XGBoost Model

Developed an additional machine learning forecasting approach using XGBoost regression.

Features included:

- Historical revenue values
- Lag features
- Rolling statistics
- Calendar features

---

# 5. Model Evaluation

Models were evaluated using:

### Mean Absolute Error (MAE)

Measures the average difference between predicted and actual revenue.

### Root Mean Squared Error (RMSE)

Measures prediction error while giving more weight to larger mistakes.

Example results:

| Model | MAE | RMSE |
|---|---:|---:|
| Prophet | 260K BRL | 314K BRL |
| XGBoost | TBD | TBD |

---

# Results & Insights

The forecasting model successfully captured historical revenue patterns and provided future revenue predictions.

Business insights:

- Revenue demonstrated strong growth over the analysed period
- Forecasting can support future budgeting and operational planning
- Time-series modelling provides valuable visibility into expected sales performance

---

# Technologies Used

### Programming
- Python

### Data Analysis
- Pandas
- NumPy
- Matplotlib

### Machine Learning
- Prophet
- XGBoost
- Scikit-learn

### Development
- Jupyter Notebook
- Git & GitHub

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
    ├── forecast_results.png
    └── model_metrics.png
```

---

# How to Run

Clone the repository:

```bash
git clone https://github.com/kb1278/ecommerce-revenue-forecasting.git
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Launch Jupyter Notebook:

```bash
jupyter notebook
```

Open:

```
ecommerce_revenue_forecasting.ipynb
```

---

# Future Improvements

Potential improvements:

- Deploy forecasting model using Streamlit
- Add automated data pipelines using dbt and BigQuery
- Experiment with additional forecasting algorithms
- Add real-time revenue monitoring dashboard

---

# Author

**Kulwinder Bhamra**

GitHub: https://github.com/kb1278
