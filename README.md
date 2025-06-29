# 🔍 Customer Churn Prediction – Job Simulation Project

This project is part of a job simulation exercise aimed at helping a fictional energy company predict customer churn over the next 3 months. Using real-world-like customer data, the goal is to identify at-risk clients and inform retention strategies.

---

## 🧠 Objective

Build a predictive model to classify whether a customer is likely to churn in the next 3 months, and identify the key drivers of churn to guide business decision-making.

---

## 📁 Dataset Overview

### `client_data.csv`
Contains customer-level data including:
- `id`: Customer ID
- `cons_12m`, `cons_last_month`: Electricity consumption
- `net_margin`, `margin_gross_pow_ele`: Profitability indicators
- `date_activ`, `date_renewal`: Contract timing
- `has_gas`, `channel_sales`, `origin_up`: Customer attributes
- `churn`: **Target variable** – whether the client churned in the next 3 months

### `price_data.csv`
Contains monthly pricing details:
- `id`: Customer ID
- `price_date`: Date of price record
- `price_off_peak_var`, `price_peak_var`: Energy price (variable)
- `price_off_peak_fix`, `price_peak_fix`: Power price (fixed)

---

## ⚙️ Approach

1. **Data Preprocessing**
   - Merged datasets using `id`
   - Converted date fields to time-based features (e.g., tenure, months until renewal)
   - Removed low-variance and irrelevant columns
   - Handled class imbalance using SMOTE and/or class weights

2. **Feature Engineering**
   - Created derived features like:
     - `cons_vs_forecast_ratio`
     - `net_margin_per_kwh`
     - `contract_remaining_days`
   - Identified top features using tree-based models

3. **Modeling**
   - Trained classification models (Logistic Regression, Random Forest, XGBoost)
   - Evaluated with **Accuracy, Precision, Recall, F1-Score, ROC-AUC**
   - Tuned threshold for better recall due to imbalanced target

4. **Insights**
   - Churn is primarily driven by **profitability, consumption, and tenure**
   - **Price sensitivity** plays a minor role
   - Initial model had high accuracy but poor recall, leading to further tuning

---

## 📊 Key Results

| Metric     | Value |
|------------|--------|
| Accuracy   | 90.4% |
| Precision  | 76.7% |
| Recall     | 6.3% |
| F1-Score   | 11.6% |

> Despite high accuracy, low recall indicated the need to improve churn detection — crucial for retention strategies.

---

## 💼 Business Recommendation

Focus retention efforts on low-margin and low-consumption customers. Improving recall, even modestly, could lead to significant cost savings and increased customer lifetime value.

## 📁 Folder Structure
```
├── data/
│ ├── client_data.csv
│ ├── Data_description.csv
│ └── price_data.csv
├── Tasks/
│ ├── Model_Answer.ipynb
│ ├── What_i_tried.ipynb
├── output.png
├── README.md
└── requirements.txt
```

## 🧪 Next Steps

- Improve recall using threshold tuning and ensemble methods
- Analyze churn by customer segments (e.g., low vs high margin)
- Explore time-series trends in consumption and pricing

---

## 🛠️ Tech Stack

- Python (Pandas, NumPy, Scikit-learn, Matplotlib, Seaborn)
- VS code Jupyter Notebook
- Git/GitHub

---
