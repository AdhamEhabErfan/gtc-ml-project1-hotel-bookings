# GTC-ML-Project-1: Hotel Booking Data Cleaning & Preprocessing

## Overview
This project is part of the GTC ML curriculum and focuses on developing a robust data cleaning and preprocessing pipeline for a hotel booking cancellation prediction problem. The objective is **not** to build the final model, but to ensure the data is clean, well-understood, and ready for machine learning modeling.

---

## Dataset
- **Source:** Property Management System (PMS)
- **Filename:** `hotel_bookings.csv`
- **Description:** Raw hotel booking records including details such as guests, booking dates, stays, and booking status.

---

## Project Steps

### 1. Exploratory Data Analysis (EDA)
- Loaded the dataset and generated summary statistics.
- Used visualizations (missingno matrix, heatmap) to assess missing values.
- Detected outliers in key numeric columns using boxplots and the IQR method.
- Identified major data quality issues (missing values, extreme outliers, duplicates, data types).

### 2. Data Cleaning
- **Missing Values:**
  - For categorical/ID columns like `company` and `agent`, filled missing values with `0` to indicate unknown.
  - For `country`, imputed missing values with the most frequent country.
  - For `children`, imputed missing values with the median value.
- **Duplicates:** Removed exact duplicate rows.
- **Outliers:** Capped extreme values in `adr` (Average Daily Rate) at 1000 to prevent skewed results.
- **Data Types:** Ensured date columns are stored as datetimes, not strings.

### 3. Feature Engineering & Preprocessing
- Created new features:
    - `total_guests`: Sum of adults, children, and babies per booking.
    - `total_nights`: Total nights (weekend + weeknights).
    - `is_family`: Flag if booking includes children or babies.
- **Encoding:**
    - One-Hot Encoded low-cardinality categorical variables (e.g., `meal`, `market_segment`).
    - For high-cardinality features (like `country`), grouped infrequent entries as "Other."
- **Removed Data Leakage:**
    - Dropped `reservation_status` and `reservation_status_date` columns, as these are not available at prediction time.
- **Train-Test Split:**
    - Split the processed data into training and testing sets (80/20 split, `random_state=42`).

---

## Repository Structure

```
.
├── hotel_bookings.csv            # Original dataset
├── Hotel_Bookings_EDA_Cleaning.ipynb  # Main Colab notebook
├── README.md                     # This file
```

---

## How to Reproduce

1. Clone/download this repository.
2. Open `Hotel_Bookings_EDA_Cleaning.ipynb` in [Google Colab](https://colab.research.google.com/) or your preferred environment.
3. Run all cells. Adjust paths if running locally.
4. The notebook performs:
    - EDA & visualization
    - Data cleaning & type fixes
    - Feature engineering & encoding
    - Data split & export of final datasets

---

## Key Learnings

- Careful, iterative data cleaning and EDA are critical for well-performing ML pipelines.
- Proper handling of missing values, duplicates, and outliers early reduces potential modeling issues.
- Removing data leakage sources is a fundamental best practice.
- Systematic notebook documentation is valuable for reproducibility and future collaboration.

---

## Credits
This project was completed as part of the GTC ML Program.
