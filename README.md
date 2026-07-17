# 🛒 eCommerce Messy Data Cleaning & Analysis Project

## 📌 Project Overview
This project focuses on the end-to-end **Data Cleaning** and **Exploratory Data Analysis (EDA)** of a messy eCommerce dataset (`ecommerce_messy.csv`). Raw data in real-world business scenarios is often incomplete, inconsistent, and contains anomalies. This repository demonstrates how to systematically handle missing values, correct syntax/formatting issues, parse mixed date formats, and detect/remove outliers using statistical methods.

## 🛠️ Tech Stack & Libraries
- **Language:** Python 3.x
- **Libraries:** 
  - `pandas` (Data manipulation & cleaning)
  - `numpy` (Numerical operations)
  - `matplotlib` & `seaborn` (Data visualization)

## 🧼 Data Cleaning Workflow & Steps

### 1. Handling Missing Values
- Identified and removed null/NaN rows across the dataset using `.dropna()` to ensure data integrity for calculations.

### 2. Type Casting & Text Standardization
- Converted `customer_id` into an integer type.
- Cleaned and capitalized categorical columns (`category`, `payment_method`, `city`).
- Resolved formatting inconsistencies and abbreviations:
  - **Category:** Fixed typos like `Cloth` ➔ `Clothing`, `Elec` ➔ `Electronics`, and `Home` ➔ `Home & garden`.
  - **Payment Method:** Handled ambiguous data (e.g., converted `Cc` to `Unknown`).
  - **City:** Mapped shortcuts to full names (e.g., `La` ➔ `Los Angeles`, `Ny` ➔ `New York`).

### 3. Mixed Date Parsing
- Handled challenging mixed-format string columns for both `order_date` and `delivery_date`.
- Utilized `pd.to_datetime()` with `errors='coerce'` and `dayfirst=True` to safely standardize timestamps.

### 4. Outlier Detection & Removal (IQR Method)
- Cleaned monetary fields by stripping currency symbols (`$`) and text labels (`bucks`), transforming `price` and `quantity` into numeric types.
- Used the **Interquartile Range (IQR)** method to filter out extreme outliers in both Price and Quantity distributions.
- Visualized distributions before/after using Boxplots to confirm data normalization.

---

## 📊 Key Insights & Visualizations

### 📉 Price and Quantity Distribution
The data distribution was reviewed using boxplots to pinpoint anomalies in ordering behaviors.

### 💰 Total Sales Revenue by Category
After preparing the clean data, an aggregation was performed to discover which product categories generated the highest overall value:

| Category | Total Price ($) |
| :--- | :--- |
| **Electronics** | 879,233.30 |
| **Clothing** | 862,246.52 |
| **Home & Garden** | 592,590.64 |
| **Tech** | 294,421.74 |
| **Toys** | 285,147.56 |

*Electronics and Clothing are the clear driving revenue sectors for this eCommerce platform.*

---

## 🚀 How to Run the Code
1. Clone this repository.
2. Ensure you have the dataset named `ecommerce_messy.csv` in your workspace.
3. Run the Jupyter Notebook or Python script:
```python
import pandas as pd
# Run the cleaning blocks to generate the cleaned_ecommerce.csv
