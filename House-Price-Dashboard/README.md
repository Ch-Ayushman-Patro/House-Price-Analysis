# House Price Dashboard

An interactive Tableau dashboard that provides visual insights into residential property data in India. The dashboard helps users quickly explore pricing patterns, property distributions, and key metrics through a collection of charts and KPI cards.

---

## Table of Contents

- [Purpose](#-purpose)
- [What the Dashboard Visualizes](#-what-the-dashboard-visualizes)
- [Dataset Used](#-dataset-used)
- [Key Metrics & Visual Elements](#-key-metrics--visual-elements)
- [Insights You Can Gain](#-insights-you-can-gain)
- [Dashboard Preview](#-dashboard-preview)
- [How to Open the Dashboard](#-how-to-open-the-dashboard)

---

## Purpose

The goal of this dashboard is to provide a visual, easy-to-understand overview of the housing dataset. Instead of reading raw numbers, users can interact with charts, compare categories, and spot trends instantly. This is especially useful for:

- **Real estate analysts** examining market patterns
- **Investors** evaluating potential property segments
- **Students and learners** studying data visualization with Tableau

---

## What the Dashboard Visualizes

The dashboard presents multiple views of the housing data, organized into KPI cards and detailed charts:

| Visual Element                      | Type          | Description                                                           |
| ----------------------------------- | ------------- | --------------------------------------------------------------------- |
| **Average Bedrooms**                | KPI Card      | Displays the average number of bedrooms across all properties         |
| **Average Bathrooms**               | KPI Card      | Displays the average number of bathrooms across all properties        |
| **Average Living Area**             | KPI Card      | Shows the average living area (sq. ft.) of properties                 |
| **Average Lot Area**                | KPI Card      | Shows the average lot area (sq. ft.) of properties                    |
| **Bedrooms vs. Bathrooms**          | Bar Chart     | Compares the average number of bathrooms for each bedroom count       |
| **Total Count of Floors w.r.t Price** | Bar Chart   | Shows the distribution of properties by floor count relative to price |
| **Distribution of House Prices**    | Histogram     | Displays the frequency distribution of property prices                |
| **Pie Chart of Grade**              | Pie Chart     | Shows the proportion of properties by house grade                     |

---

## Dataset Used

The dashboard is powered by the file `house-price-dataset.xlsx`, which contains **14,619 property records** with **23 features** including:

- Property dimensions (living area, lot area, basement area)
- Room counts (bedrooms, bathrooms, floors)
- Quality indicators (condition, grade)
- Location data (latitude, longitude, postal code)
- Proximity factors (number of schools nearby, distance from airport)
- **Price** (the primary metric)

> For a full description of every column, refer to the [root README](../README.md#-dataset-description).

---

## Key Metrics & Visual Elements

### KPI Cards

At the top of the dashboard, four summary cards provide quick access to:

- **Average Bedrooms** — Understand the typical property size
- **Average Bathrooms** — Gauge the amenity level of listed properties
- **Average Living Area** — Know the mean square footage
- **Average Lot Area** — Assess the overall land size

### Charts

- **Bedrooms vs. Bathrooms** — Reveals how bathroom availability scales with the number of bedrooms.
- **Count of Floors w.r.t Price** — Highlights which floor counts are most common and how they relate to pricing.
- **Distribution of House Prices** — A histogram showing where most property prices cluster and identifying outliers.
- **Pie Chart of Grade** — Visualizes the share of each house grade category, indicating overall construction quality distribution.

---

## Insights You Can Gain

By exploring this dashboard, users can uncover:

- **What is the typical property profile** (average rooms, area, and lot size)?
- **How are house prices distributed** — is the market skewed toward luxury or budget properties?
- **Which house grades are most common**, and what does that say about construction quality in the dataset?
- **How does the number of bedrooms relate to the number of bathrooms** — do larger homes proportionally have more bathrooms?
- **Which floor counts dominate** the market, and does the number of floors correlate with a higher price?

---

## Dashboard Preview

Below is a screenshot of the Tableau dashboard:

![Dashboard Preview](./Dashboard%20Preview.png)

---

## How to Open the Dashboard

### Requirements

- [Tableau Desktop](https://www.tableau.com/products/desktop) (version 2019.4 or later) **or** [Tableau Public](https://public.tableau.com/) (free)

### Steps

1. **Download or clone** this repository to your local machine.
2. Open **Tableau Desktop** or **Tableau Public**.
3. Go to **File → Open** and navigate to the `House-Price-Dashboard/` folder.
4. Select the file **`House Price Dashboard.twb`** and click **Open**.
5. If Tableau asks you to locate the data source, browse to the `House-Price-Dashboard/` folder and select **`house-price-dataset.xlsx`**.
6. The dashboard should load with all visuals. Use the interactive filters and highlights to explore the data.

> **Note:** The `.twb` file stores only the workbook structure, not the data. Make sure the Excel file is in the same directory or update the data connection path when prompted.
