# 🤖 House Price Prediction — Linear Regression Baseline

A Jupyter Notebook that builds a **baseline Linear Regression model** to predict residential property prices from 15 housing features. The notebook walks through the complete machine learning pipeline — from raw data ingestion to model evaluation — producing an R² of **~60 %** on the held-out test set.

---

## 📌 Table of Contents

- [Contents of This Folder](#-contents-of-this-folder)
- [ML Pipeline Overview](#-ml-pipeline-overview)
- [Run Locally](#-run-locally)
- [Dataset Notes](#-dataset-notes)
- [Feature Engineering](#-feature-engineering)
- [Exploratory Data Analysis](#-exploratory-data-analysis)
- [Model Training & Evaluation](#-model-training--evaluation)
- [Results](#-results)
- [Next Steps](#-next-steps)

---

## 📂 Contents of This Folder

| File | Description |
|------|-------------|
| `house-price-prediction.ipynb` | Jupyter notebook — full pipeline (EDA → preprocessing → training → evaluation) |
| `house-price-dataset.csv` | Source dataset used by the notebook (14,619 × 23) |
| `house-price-prediction.pdf` | Pre-rendered PDF export of the executed notebook for quick viewing |

---

## 🔄 ML Pipeline Overview

```
┌─────────────────────────────────────────────────┐
│  1. Data Ingestion                              │
│  • house-price-dataset.csv                      │
│    (14,619 rows × 23 columns)                   │
└──────────────────────┬──────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────┐
│  2. Data Cleaning                               │
│  • Drop Non-Predictive Columns:                 │
│    id, Date, Built Year, Renovation Year,       │
│    Postal Code, Lattitude, Longitude            │
│  • Cast Data Types: bathrooms & floors → int    │
│  • Null Check (no missing values found)         │
└──────────────────────┬──────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────┐
│  3. Exploratory Data Analysis (EDA)             │
│  • Univariate & Bivariate Plots                 │
│    (14 visualisations)                          │
│  • Correlation Heatmap                          │
└──────────────────────┬──────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────┐
│  4. Modelling                                   │
│  • Train / Test Split (70% / 30%)               │
│  • StandardScaler (fit_transform)               │
│  • LinearRegression (.fit on train set)         │
│  • Predict on test set                          │
└──────────────────────┬──────────────────────────┘
                       ▼
┌─────────────────────────────────────────────────┐
│  5. Evaluation                                  │
│  • Mean Squared Error: 45.19 B                  │
│  • R² Score: 0.6002 ≈ 60%                       │
│  • KDE Overlay Plot (Actual vs Predicted)       │
└─────────────────────────────────────────────────┘
```

---

## 🚀 Run Locally

### Prerequisites

- **Python 3.8+**
- `pip` package manager

### Steps

```powershell
# 1 — Navigate to this folder from the repo root
cd House-Price-Prediction

# 2 — Create and activate a virtual environment
python -m venv .venv
.\.venv\Scripts\Activate.ps1          # PowerShell
# source .venv/bin/activate            # macOS / Linux

# 3 — Install dependencies
pip install numpy pandas matplotlib seaborn scikit-learn jupyter

# 4 — Launch Jupyter and open the notebook
jupyter notebook
```

Open **`house-price-prediction.ipynb`** and **Run All Cells**.

> **Tip:** If PowerShell blocks script activation, execute this first:
> ```powershell
> Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass
> ```

### Dependencies

| Package | Purpose |
|---------|---------|
| `numpy` | Numerical operations |
| `pandas` | Data manipulation & DataFrames |
| `matplotlib` | Base plotting library |
| `seaborn` | Statistical visualisations |
| `scikit-learn` | ML model, scaler, metrics, train/test split |

---

## 📊 Dataset Notes

| Property | Value |
|----------|-------|
| **Rows** | 14,619 |
| **Columns** | 23 |
| **Target Variable** | `Price` (range: 78,000 – 7,700,000) |
| **Date Range** | 2016-05-01 → 2016-12-30 (stored as Excel serial numbers 42491–42734) |
| **Latitude Spelling** | `Lattitude` (original CSV quirk) |
| **Missing Values** | None |

---

## 🧹 Feature Engineering

### Columns Dropped Before Training (7)

These columns are either identifiers, temporal, geographic, or otherwise non-predictive for a simple linear model:

| Dropped Column | Reason |
|----------------|--------|
| `id` | Unique identifier — no predictive value |
| `Date` | Encoded as serial number; not meaningful without conversion |
| `Built Year` | Temporal — better as "house age" (future improvement) |
| `Renovation Year` | Mostly 0; sparse signal |
| `Postal Code` | Categorical with high cardinality |
| `Lattitude` | Geographic coordinate — requires spatial modelling |
| `Longitude` | Geographic coordinate — requires spatial modelling |

### Features Used for Training (15)

| # | Feature | Type |
|---|---------|------|
| 1 | `number of bedrooms` | Discrete |
| 2 | `number of bathrooms` | Discrete |
| 3 | `living area` | Continuous |
| 4 | `lot area` | Continuous |
| 5 | `number of floors` | Discrete |
| 6 | `waterfront present` | Binary (0/1) |
| 7 | `number of views` | Discrete |
| 8 | `condition of the house` | Ordinal |
| 9 | `grade of the house` | Ordinal |
| 10 | `Area of the house(excluding basement)` | Continuous |
| 11 | `Area of the basement` | Continuous |
| 12 | `living_area_renov` | Continuous |
| 13 | `lot_area_renov` | Continuous |
| 14 | `Number of schools nearby` | Discrete |
| 15 | `Distance from the airport` | Continuous |

---

## 📈 Exploratory Data Analysis

The notebook generates **14 visualisations** covering both univariate and bivariate relationships, plus a full correlation heatmap:

| Plot Type | Feature(s) Explored |
|-----------|---------------------|
| Bar plot | Bedrooms vs Price |
| Line plot | Bathrooms vs Price |
| Scatter plot | Living Area vs Price |
| Scatter plot | Lot Area vs Price |
| Bar plot | Floors vs Price |
| Bar plot | Waterfront vs Price |
| Bar plot | Views vs Price |
| Bar plot | Grade vs Price |
| Line plot | Above-Ground Area vs Price |
| Scatter plot | Basement Area vs Price |
| Scatter plot | Living Area (Renov) vs Price |
| Scatter plot | Lot Area (Renov) vs Price |
| Bar plot | Schools Nearby vs Price |
| Line plot | Airport Distance vs Price |
| **Heatmap** | **Correlation matrix of all 16 columns** |

---

## 🧠 Model Training & Evaluation

```
┌─────────────────────────────────────────────────┐
│  Input: 15 Features + Price Target              │
└───────────────┬─────────────────────────────────┘
                │
       ┌────────┴────────┐
       │                 │
       ▼                 ▼
┌─────────────┐   ┌─────────────┐
│  Train Set  │   │  Test Set   │
│  70% split  │   │  30% split  │
│ ~10,233 rows│   │ ~4,386 rows │
└──────┬──────┘   └──────┬──────┘
       │                 │
       ▼                 ▼
┌─────────────┐   ┌─────────────┐
│StandardScaler│   │StandardScaler│
│fit_transform│   │  transform  │
└──────┬──────┘   └──────┬──────┘
       │                 │
       ▼                 │
┌─────────────┐          │
│   Linear    │          │
│ Regression  │          │
│   .fit()    │          │
└──────┬──────┘          │
       │                 │
       └────────┬────────┘
                ▼
         ┌─────────────┐
         │  .predict() │
         │ on test set │
         └──────┬──────┘
                ▼
         ┌─────────────┐
         │  Metrics:   │
         │  • MSE      │
         │  • R²       │
         │  • KDE Plot │
         └─────────────┘
```

| Step | Detail |
|------|--------|
| **Split** | `train_test_split(train_size=0.7)` — 70 % train, 30 % test |
| **Scaling** | `StandardScaler` applied to both train and test sets |
| **Algorithm** | `sklearn.linear_model.LinearRegression` |
| **Prediction** | `.predict()` on the scaled test features |
| **Visual Check** | KDE overlay of actual prices, test prices, and predicted prices |

---

## 📋 Results

| Metric | Value |
|--------|-------|
| **Mean Squared Error (MSE)** | 45,193,596,846.39 |
| **R² Score** | 0.6002 (~60.02 %) |

> The model captures roughly **60 %** of the variance in house prices using only linear relationships — a solid baseline for comparison with more complex models.

---

## 🔮 Next Steps

| Improvement | Expected Benefit |
|-------------|-----------------|
| **Non-linear models** (Random Forest, XGBoost) | Capture complex, non-linear feature interactions |
| **Feature engineering** (house age, price/sq. ft.) | Add domain knowledge to the feature set |
| **Log-transform `Price`** | Reduce right-skew in the target distribution |
| **Cross-validation** | More robust performance estimates |
| **Hyperparameter tuning** (GridSearch / Optuna) | Optimise model parameters systematically |
| **Spatial features** | Leverage lat/long with geospatial encoding |

---

🔗 Back to the main project overview: [../README.md](../README.md)
