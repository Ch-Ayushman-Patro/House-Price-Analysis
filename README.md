# 🏠 House Price Analysis

A comprehensive data analytics project that combines **interactive data visualization** with **machine learning** to analyze and predict residential property prices in India. This project provides both a Tableau dashboard for visual exploration and a Python-based prediction model for price estimation.

---

## 📌 Table of Contents

- [Project Overview](#-project-overview)
- [Objectives & Business Problem](#-objectives--business-problem)
- [Project Components](#-project-components)
- [Tools & Technologies](#-tools--technologies)
- [Dataset Description](#-dataset-description)
- [Key Insights & Outcomes](#-key-insights--outcomes)
- [How to Explore the Project](#-how-to-explore-the-project)
- [Folder Structure](#-folder-structure)
- [Author](#-author)

---

## 📖 Project Overview

The real estate market is one of the most dynamic and impactful sectors of the economy. Understanding what drives house prices helps buyers, sellers, investors, and policymakers make informed decisions.

This project tackles house price analysis from two angles:

1. **Visual Analytics** — An interactive Tableau dashboard that visualizes key property features and their relationship with pricing.
2. **Predictive Modeling** — A Linear Regression model built in Python that predicts house prices based on property attributes.

---

## 🎯 Objectives & Business Problem

**Business Problem:** Accurately estimating house prices is complex, as it depends on numerous factors such as location, area, number of rooms, condition, and nearby amenities. Stakeholders need a clear, data-driven way to understand pricing patterns and estimate property values.

**Objectives:**

- Explore and visualize the key factors influencing house prices
- Identify trends, distributions, and relationships among property features
- Build a machine learning model that can predict house prices
- Present actionable insights through an interactive dashboard

---

## 🧩 Project Components

### 1. [House Price Dashboard](./House-Price-Dashboard/)

An interactive Tableau dashboard providing visual insights into the housing dataset. It includes KPI cards, bar charts, pie charts, and histograms to help users explore pricing patterns at a glance.

### 2. [House Price Prediction](./House-Price-Prediction/)

A Jupyter Notebook containing a complete machine learning pipeline — from data loading and cleaning, through exploratory data analysis, to model training and evaluation using Linear Regression.

---

## 🛠 Tools & Technologies

| Tool / Technology     | Purpose                                   |
| --------------------- | ----------------------------------------- |
| **Python 3.11**       | Programming language for data analysis    |
| **Jupyter Notebook**  | Interactive coding environment            |
| **Pandas**            | Data manipulation and analysis            |
| **NumPy**             | Numerical computations                    |
| **Matplotlib**        | Static data visualizations                |
| **Seaborn**           | Statistical data visualizations           |
| **Scikit-learn**      | Machine learning (Linear Regression)      |
| **Tableau Desktop**   | Interactive dashboard and visual analytics|
| **Microsoft Excel**   | Dataset storage (`.xlsx` for dashboard)   |

---

## 📊 Dataset Description

The dataset contains **14,619 records** of residential properties with **23 features** each.

| Feature                                 | Description                                           |
| --------------------------------------- | ----------------------------------------------------- |
| `id`                                    | Unique identifier for each property                   |
| `Date`                                  | Date of the transaction                               |
| `number of bedrooms`                    | Total number of bedrooms                              |
| `number of bathrooms`                   | Total number of bathrooms                             |
| `living area`                           | Living area in square feet                            |
| `lot area`                              | Lot area in square feet                               |
| `number of floors`                      | Number of floors in the property                      |
| `waterfront present`                    | Whether the property has a waterfront (1 = Yes, 0 = No) |
| `number of views`                       | Number of times the property was viewed               |
| `condition of the house`                | Overall condition rating (1–5)                        |
| `grade of the house`                    | Overall grade given based on construction quality     |
| `Area of the house (excluding basement)`| Above-ground living area                              |
| `Area of the basement`                  | Basement area in square feet                          |
| `Built Year`                            | Year the house was originally built                   |
| `Renovation Year`                       | Year of last renovation (0 if never renovated)        |
| `Postal Code`                           | Postal code of the property location                  |
| `Latitude`                              | Geographic latitude                                   |
| `Longitude`                             | Geographic longitude                                  |
| `living_area_renov`                     | Living area after renovation                          |
| `lot_area_renov`                        | Lot area after renovation                             |
| `Number of schools nearby`              | Count of schools in the vicinity                      |
| `Distance from the airport`             | Distance to the nearest airport                       |
| `Price`                                 | **Target variable** — Sale price of the property      |

---

## 💡 Key Insights & Outcomes

- **Living area** and **grade of the house** are among the strongest predictors of price.
- Properties with higher grades and larger living areas command significantly higher prices.
- The majority of house prices fall within a specific range, with a right-skewed distribution indicating a small number of high-value outliers.
- The **Linear Regression** model achieved an **R² score of ~0.60**, explaining approximately 60% of the variance in house prices.
- The Tableau dashboard provides at-a-glance KPIs such as average bedrooms, bathrooms, living area, and lot area alongside detailed charts.

---

## 🚀 How to Explore the Project

### Dashboard

1. Install [Tableau Desktop](https://www.tableau.com/products/desktop) or [Tableau Public](https://public.tableau.com/).
2. Open the file `House-Price-Dashboard/House Price Dashboard.twb`.
3. If prompted, point the data source to `House-Price-Dashboard/house-price-dataset.xlsx`.
4. Interact with the visualizations using filters and highlights.

### Prediction Model

1. Make sure Python 3.x is installed along with `pip`.
2. Install the required libraries:

   ```bash
   pip install numpy pandas matplotlib seaborn scikit-learn jupyter
   ```

3. Launch Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

4. Open `House-Price-Prediction/house-price-prediction.ipynb` and run all cells sequentially.
5. A PDF report of the notebook output is also available at `House-Price-Prediction/house-price-prediction.pdf`.

---

## 📁 Folder Structure

```
House-Price-Analysis/
│
├── House-Price-Dashboard/
│   ├── Dashboard Preview.png        # Screenshot of the Tableau dashboard
│   ├── House Price Dashboard.twb     # Tableau workbook file
│   ├── house-price-dataset.xlsx      # Dataset used by the dashboard
│   └── README.md                     # Dashboard-specific documentation
│
├── House-Price-Prediction/
│   ├── house-price-dataset.csv       # Dataset used for prediction
│   ├── house-price-prediction.ipynb  # Jupyter Notebook with ML pipeline
│   ├── house-price-prediction.pdf    # PDF export of the notebook
│   └── README.md                     # Prediction-specific documentation
│
└── README.md                         # This file — project overview
```

---

## ✍️ Author

**Ayushman Patro**

If you found this project helpful, feel free to ⭐ star the repository!
