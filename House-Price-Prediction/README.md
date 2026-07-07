# House Price Prediction

A machine learning project that predicts residential property prices using **Linear Regression**. The entire pipeline — from data loading and cleaning to model training and evaluation — is implemented in a Jupyter Notebook using Python and scikit-learn.

---

## Table of Contents

- [Goal](#-goal)
- [Dataset Overview & Features](#-dataset-overview--features)
- [Data Preprocessing Steps](#-data-preprocessing-steps)
- [Model Used](#-model-used)
- [Evaluation Metrics](#-evaluation-metrics)
- [Results & Performance Summary](#-results--performance-summary)
- [How to Run the Notebook](#-how-to-run-the-notebook)
- [Requirements & Libraries](#-requirements--libraries)
- [PDF Report](#-pdf-report)

---

## Goal

The objective of this project is to build a regression model that can **predict the sale price of a house** based on its physical and locational attributes. By training on historical property data, the model learns the relationship between features (like area, rooms, and condition) and the final price.

---

## Dataset Overview & Features

The dataset (`house-price-dataset.csv`) contains **14,619 property records** with **23 columns**.

| Feature                                   | Type    | Description                                           |
| ----------------------------------------- | ------- | ----------------------------------------------------- |
| `id`                                      | Integer | Unique property identifier                            |
| `Date`                                    | Integer | Transaction date (encoded)                            |
| `number of bedrooms`                      | Integer | Total bedrooms                                        |
| `number of bathrooms`                     | Float   | Total bathrooms                                       |
| `living area`                             | Integer | Living area in sq. ft.                                |
| `lot area`                                | Integer | Lot area in sq. ft.                                   |
| `number of floors`                        | Float   | Number of floors                                      |
| `waterfront present`                      | Integer | Waterfront indicator (0 or 1)                         |
| `number of views`                         | Integer | Number of property viewings                           |
| `condition of the house`                  | Integer | Overall condition (1–5)                               |
| `grade of the house`                      | Integer | Construction quality grade                            |
| `Area of the house (excluding basement)`  | Integer | Above-ground area in sq. ft.                          |
| `Area of the basement`                    | Integer | Basement area in sq. ft.                              |
| `Built Year`                              | Integer | Year built                                            |
| `Renovation Year`                         | Integer | Year renovated (0 = never)                            |
| `Postal Code`                             | Integer | Location postal code                                  |
| `Latitude`                                | Float   | Geographic latitude                                   |
| `Longitude`                               | Float   | Geographic longitude                                  |
| `living_area_renov`                       | Integer | Living area after renovation                          |
| `lot_area_renov`                          | Integer | Lot area after renovation                             |
| `Number of schools nearby`                | Integer | Count of nearby schools                               |
| `Distance from the airport`               | Integer | Distance to the nearest airport                       |
| `Price`                                   | Integer | **Target variable** — Sale price                      |

---

## Data Preprocessing Steps

The notebook follows a structured preprocessing pipeline:

1. **Data Loading** — Read the CSV file into a Pandas DataFrame.
2. **Column Inspection** — Review all 23 columns and their data types using `.info()` and `.columns`.
3. **Dropping Irrelevant Columns** — The following columns are removed as they don't contribute directly to price prediction:
   - `id`, `Date`, `Built Year`, `Renovation Year`, `Postal Code`, `Latitude`, `Longitude`
4. **Missing Value Check** — Verified that the dataset has **zero null values** across all remaining 16 features.
5. **Unique Value Exploration** — Examined the range and distribution of values in each feature.
6. **Exploratory Data Analysis (EDA)** — Generated visualizations (scatter plots, histograms, heatmaps) to understand feature distributions and correlations.
7. **Feature Scaling** — Applied `StandardScaler` to normalize the feature values for better model performance.
8. **Train-Test Split** — Split the data into training (~70%) and testing (~30%) sets using `train_test_split`.

---

## Model Used

### Linear Regression (scikit-learn)

Linear Regression models the relationship between features and the target variable (Price) as a weighted linear combination:

```
Price = β₀ + β₁·x₁ + β₂·x₂ + ... + βₙ·xₙ
```

The model was trained using `sklearn.linear_model.LinearRegression` and fitted on the training set.

---

## Evaluation Metrics

The model was evaluated using two standard regression metrics:

| Metric                     | Description                                                                                                       |
| -------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| **Mean Squared Error (MSE)** | Measures the average of the squares of the errors between predicted and actual values. Lower is better.          |
| **R² Score**                 | Indicates the proportion of variance in the target variable explained by the model. Ranges from 0 to 1 (higher is better). |

---

## 📈 Results & Performance Summary

| Metric                      | Value                   |
| --------------------------- | ----------------------- |
| **Mean Squared Error (MSE)** | ~45,193,596,846         |
| **R² Score**                 | **0.6002** (~60%)       |

### Interpretation

- The model explains approximately **60%** of the variance in house prices.
- The relatively high MSE is expected given the wide range of property prices (from ~$146,000 to over $1,900,000).
- A KDE (Kernel Density Estimation) plot comparing actual, testing, and predicted price distributions shows that the model captures the general pricing trend but has difficulty with extreme values.

### Possible Improvements

- Use more advanced models (e.g., Random Forest, Gradient Boosting, XGBoost)
- Perform feature engineering (e.g., price per sq. ft., age of property)
- Apply log-transformation to the target variable to handle skewness
- Include or re-engineer the dropped location-based features

---

## 🚀 How to Run the Notebook

### 1. Clone the Repository

```bash
git clone https://github.com/Ch-Ayushman-Patro/House-Price-Analysis.git
cd House-Price-Analysis/House-Price-Prediction
```

### 2. Install Dependencies

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```

### 3. Launch Jupyter Notebook

```bash
jupyter notebook
```

### 4. Open and Run

- In your browser, click on **`house-price-prediction.ipynb`**.
- Run all cells from top to bottom using **Cell → Run All** or press `Shift + Enter` cell by cell.
- The notebook will load the dataset, preprocess it, train the model, and display the results including evaluation metrics and plots.

---

## Requirements & Libraries

| Library          | Version (used) | Purpose                        |
| ---------------- | -------------- | ------------------------------ |
| `numpy`          | —              | Numerical operations           |
| `pandas`         | —              | Data manipulation              |
| `matplotlib`     | 3.7.3          | Data visualization             |
| `seaborn`        | —              | Statistical plots              |
| `scikit-learn`   | —              | ML model, metrics, preprocessing |
| `jupyter`        | —              | Notebook environment           |

Install all at once:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn jupyter
```
