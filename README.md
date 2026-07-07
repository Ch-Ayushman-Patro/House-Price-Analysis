<div align="center">

# House Price Analysis

### End-to-End Data Science Project with Visual Analytics & Machine Learning

[![Python](https://img.shields.io/badge/Python-3.11-blue.svg)](https://www.python.org/) ![Tableau](https://img.shields.io/badge/Tableau-Desktop-orange?logo=tableau&logoColor=white) ![scikit-learn](https://img.shields.io/badge/scikit--learn-1.0+-green?logo=scikitlearn&logoColor=white) ![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-F37626?logo=jupyter&logoColor=white) ![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-150458?logo=pandas&logoColor=white)

---

</div>

An end-to-end data analysis and machine learning project that combines an **interactive Tableau dashboard** for visual exploration with a **Python-based Jupyter notebook** for building a baseline house price prediction model. The project uses a real-estate dataset of **14,619 property records** spanning mid-2016, covering a wide range of residential features such as living area, lot size, grade, condition, and proximity to schools and airports.

---

## Table of Contents

- [Project Overview](#-project-overview)
- [High-Level Architecture](#-high-level-architecture)
- [Repository Structure](#-repository-structure)
- [Dataset Summary](#-dataset-summary)
- [Dashboard Preview](#-dashboard-preview)
- [Baseline Model Results](#-baseline-model-results)
- [Future Improvements](#-future-improvements)
- [Contributing](#-contributing)
- [Contact](#-contact)

---

## Project Overview

This project addresses two complementary goals:

1. **Visual Exploration:** An interactive Tableau dashboard surfaces key patterns in the housing data (price distributions, grade breakdowns, feature relationships) so stakeholders can explore trends without writing code.
2. **Predictive Modelling:** A Jupyter notebook walks through the full ML pipeline from data loading, cleaning, exploratory analysis, feature scaling, model training, and evaluation to culminating in a Linear Regression baseline that explains ~60 % of price variance.

<div align="center">

| Component | Tool | Purpose |
|-------------|---------|-----------|
| `House-Price-Dashboard/` | Tableau Desktop | Interactive visual analytics & exploration |
| `House-Price-Prediction/` | Python · scikit-learn | EDA + baseline regression model |

</div>

---

## High-Level Architecture

```
┌──────────────────────────────────────────────┐
│    house-price-dataset (14,619 records)      │
└──────────────────┬───────────────────────────┘
                   │
         ┌─────────┴─────────┐
         │                   │
         ▼                   ▼
┌──────────────────┐  ┌────────────────┐
│    Tableau       │  │     Python     │
│  Interactive     │  │  ML Notebook   │
│   Dashboard      │  │                │
└──────────────────┘  └──────┬─────────┘
                             │
                             ▼
                      ┌─────────────────┐
                      │  Data Cleaning  │
                      └─────────┬───────┘
                                │
                                ▼
                           ┌───────┐
                           │  EDA  │     
                           └────┬──┘
                                │
                                ▼
                      ┌──────────────────┐
                      │     Feature      │
                      │     Scaling      │
                      └─────────┬────────┘
                                │
                                ▼
                      ┌──────────────────┐
                      │      Linear      │
                      │     Regression   │
                      └─────────┬────────┘
                                │
                                ▼
                      ┌──────────────────┐
                      │    Evaluation    │
                      │     R² = 60%     │
                      └──────────────────┘
```

---

## Repository Structure

```text
House-Price-Analysis/
│
├── House-Price-Dashboard/
│   ├── House Price Dashboard.twb      ← Tableau workbook
│   ├── house-price-dataset.xlsx       ← Excel data source for Tableau
│   ├── Dashboard Preview.png          ← Static screenshot of the dashboard
│   └── README.md                      ← Dashboard-specific documentation
│
├── House-Price-Prediction/
│   ├── house-price-prediction.ipynb   ← Jupyter notebook (full pipeline)
│   ├── house-price-dataset.csv        ← CSV data source for Python
│   ├── house-price-prediction.pdf     ← Pre-rendered notebook export
│   └── README.md                      ← Notebook-specific documentation
│
└── README.md                          ← You are here
```

---

## Dataset Summary

The dataset is included in **two formats** (CSV for Python, XLSX for Tableau) and contains the same underlying data.

| Property | Value |
|----------|-------|
| **Rows** | 14,619 |
| **Columns** | 23 |
| **Target Variable** | `Price` (range: 78,000 – 7,700,000) |
| **Date Range** | 2016-05-01 to 2016-12-30 (stored as Excel serial numbers) |
| **Notable Quirk** | Latitude column is spelled `Lattitude` in the source |

<details>
<summary><strong>Full Column List (click to expand)</strong></summary>

| # | Column | Description |
|---|--------|-------------|
| 1 | `id` | Unique property identifier |
| 2 | `Date` | Sale date (Excel serial number) |
| 3 | `number of bedrooms` | Bedroom count |
| 4 | `number of bathrooms` | Bathroom count |
| 5 | `living area` | Interior living area (sq. ft.) |
| 6 | `lot area` | Total lot area (sq. ft.) |
| 7 | `number of floors` | Number of floors |
| 8 | `waterfront present` | Binary flag — waterfront property |
| 9 | `number of views` | Number of property viewings |
| 10 | `condition of the house` | Condition rating |
| 11 | `grade of the house` | Construction & design grade |
| 12 | `Area of the house(excluding basement)` | Above-ground area (sq. ft.) |
| 13 | `Area of the basement` | Basement area (sq. ft.) |
| 14 | `Built Year` | Year originally built |
| 15 | `Renovation Year` | Year last renovated (0 = never) |
| 16 | `Postal Code` | Postal / ZIP code |
| 17 | `Lattitude` | Latitude coordinate |
| 18 | `Longitude` | Longitude coordinate |
| 19 | `living_area_renov` | Living area after renovation |
| 20 | `lot_area_renov` | Lot area after renovation |
| 21 | `Number of schools nearby` | Count of nearby schools |
| 22 | `Distance from the airport` | Distance to nearest airport |
| 23 | `Price` | **Target** — sale price |

</details>

---

## Dashboard Preview

Below is a static screenshot of the Tableau dashboard. Open the `.twb` file for the full interactive experience.

![Dashboard Preview](./House-Price-Dashboard/Dashboard%20Preview.png)

---

## Baseline Model Results

The notebook trains a **Linear Regression** model (scikit-learn) after standardising all features with `StandardScaler`.

```
                    ┌──────────────────────┐
                    │   14,619 Records     │
                    │     23 Columns       │
                    └──────────┬───────────┘
                               │
                               │ Drop 7 columns
                               ▼
                    ┌──────────────────────┐
                    │      16 Columns      │
                    │  15 Features + Price │
                    └──────────┬───────────┘
                               │
                               │ 70/30 split
                 ┌─────────────┴─────────────┐
                 │                           │
                 ▼                           ▼
      ┌─────────────────────┐     ┌─────────────────────┐
      │      Train Set      │     │     Test Set        │
      │    ~10,233 rows     │     │    ~4,386 rows      │
      └──────────┬──────────┘     └──────────┬──────────┘
                 │                           │
                 │ StandardScaler            │ StandardScaler
                 ▼                           ▼
      ┌─────────────────────┐     ┌─────────────────────┐
      │    Scaled Train     │     │    Scaled Test      │
      └──────────┬──────────┘     └──────────┬──────────┘
                 │                           │
                 └────────────┬──────────────┘
                              │
                              ▼
                   ┌────────────────────────┐
                   │ LinearRegression.fit() │
                   └──────────┬─────────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │   Predict on Test    │
                   └──────────┬───────────┘
                              │
                              ▼
                   ┌──────────────────────┐
                   │      Evaluation      │
                   └──────────┬───────────┘
                              │
              ┌───────────────┴───────────────┐
              │                               │
              ▼                               ▼
   ┌────────────────────┐        ┌─────────────────────┐
   │       MSE          │        │    R² Score         │
   │  45,193,596,846    │        │  0.6002 ≈ 60%       │
   └────────────────────┘        └─────────────────────┘
```

| Metric | Value |
|--------|-------|
| **Mean Squared Error (MSE)** | 45,193,596,846.39 |
| **R² Score** | 0.6002 (~60.02%) |
| **Train / Test Split** | 70% / 30% |
| **Scaler** | `StandardScaler` |
| **Features Used** | 15 (after dropping 7 non-predictive columns) |

---

## Future Improvements

| Category | Enhancement | Expected Impact |
|----------|-------------|-----------------|
| **Models** | Random Forest, Gradient Boosting, XGBoost | Capture complex non-linear relationships |
| **Features** | House age, price per sq. ft., interaction terms | Add domain knowledge to predictions |
| **Target** | Log-transform `Price` | Reduce right-skew in distribution |
| **Validation** | K-fold cross-validation + hyperparameter tuning | More robust performance estimates |
| **Data** | Neighbourhood socioeconomic features | Incorporate location-based insights |

---

## Contributing

Contributions are welcome! Here's how you can help:

1. **Fork the repository**
2. **Create a feature branch:** `git checkout -b feature/AmazingFeature`
3. **Commit your changes:** `git commit -m 'Add some AmazingFeature'`
4. **Push to the branch:** `git push origin feature/AmazingFeature`
5. **Open a Pull Request**

---

## Contact

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/ch-ayushman-patro) [![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Ch-Ayushman-Patro)

*For questions, suggestions, or collaboration opportunities, feel free to reach out!*
