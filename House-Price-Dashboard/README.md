# 📊 House Price Dashboard - Tableau

An interactive **Tableau dashboard** for exploring the housing dataset through visual analytics. The workbook surfaces key property metrics (average bedrooms, bathrooms, living area, lot area) alongside charts that reveal price distributions, grade breakdowns, and feature relationships - all without writing a single line of code.

---

## 📌 Table of Contents

- [Contents of This Folder](#contents-of-this-folder)
- [Dashboard Architecture](#dashboard-architecture)
- [How to Open](#how-to-open)
- [What the Dashboard Shows](#what-the-dashboard-shows)
- [Data Source](#data-source)
- [Dashboard Preview](#dashboard-preview)
- [Troubleshooting](#troubleshooting)

---

## 📂 Contents of This Folder

| File | Description |
|------|-------------|
| `House Price Dashboard.twb` | Tableau workbook containing all sheets, dashboards, and layout |
| `house-price-dataset.xlsx` | Excel data source consumed by the workbook |
| `Dashboard Preview.png` | Static screenshot of the completed dashboard |

---

## 🏗 Dashboard Architecture

```
Data Flow:

┌─────────────────────────────────────────────────┐
│  Data Source: house-price-dataset.xlsx         │
│  (14,619 rows × 23 columns)                    │
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│  Processing Engine: Tableau Data Engine        │
└──────────────────────┬──────────────────────────┘
                       │
                       ▼
┌─────────────────────────────────────────────────┐
│  Dashboard Layout Components:                   │
│  • KPI Cards                                    │
│  • Price Histogram                              │
│  • Grade Pie Chart                              │
│  • Bedrooms vs Bathrooms                        │
│  • Floor-Count Breakdown                        │
└─────────────────────────────────────────────────┘
```

> **Note:** A `.twb` file stores workbook metadata (sheet definitions, calculated fields, layout) but **not** the data itself. The `.xlsx` file must remain alongside the workbook for it to load properly.

---

## 🚀 How to Open

### Prerequisites

- **Tableau Desktop** (any recent version) **or** **Tableau Public** (free)

### Steps

1. Open `House Price Dashboard.twb` in Tableau.
2. If Tableau prompts you to locate the data source, navigate to this folder and select `house-price-dataset.xlsx`.
3. The dashboard should render immediately with all visualisations populated.

---

## 🔍 What the Dashboard Shows

The dashboard is organised into several complementary views:

### KPI Summary Cards

| Metric | Description |
|--------|-------------|
| **Avg Bedrooms** | Mean number of bedrooms across all 14,619 properties |
| **Avg Bathrooms** | Mean number of bathrooms |
| **Avg Living Area** | Mean interior living area (sq. ft.) |
| **Avg Lot Area** | Mean total lot area (sq. ft.) |

### Visualisation Panels

| Panel | Chart Type | Insight |
|-------|------------|---------|
| **Price Distribution** | Histogram | Shows the frequency spread of property prices - reveals right-skew typical of real estate data |
| **Grade Breakdown** | Pie Chart | Proportional split of properties by construction and design grade |
| **Bedrooms vs Bathrooms** | Cross-tab / Bar | How bedroom and bathroom counts co-vary across the dataset |
| **Floor-Count Analysis** | Bar Chart | Distribution of properties by number of floors and its relationship to price |

---

## 🗃 Data Source

| Property | Value |
|----------|-------|
| **File** | `house-price-dataset.xlsx` |
| **Format** | Microsoft Excel (`.xlsx`) |
| **Rows** | 14,619 |
| **Columns** | 23 |
| **Date Range** | 2016-05-01 to 2016-12-30 |
| **Target Variable** | `Price` (78,000 - 7,700,000) |

The same data is also available as a CSV in the sibling `House-Price-Prediction/` folder for use with Python.

---

## 🖼 Dashboard Preview

![Dashboard Preview](./Dashboard%20Preview.png)

---

## 🛠 Troubleshooting

| Issue | Solution |
|-------|----------|
| **"Missing data source" error** | Go to **Data > Edit Data Source** and re-point the Excel connection to `house-price-dataset.xlsx` in this folder |
| **Blank / empty dashboard** | Ensure `house-price-dataset.xlsx` is in the **same directory** as the `.twb` file |
| **Tableau version mismatch** | Save-as from Tableau Desktop to downgrade the workbook, or update your Tableau installation |
| **Cannot open `.twb` file** | Install [Tableau Public](https://public.tableau.com/) (free) - it can open `.twb` workbooks |

---

Back to the main project overview: [../README.md](../README.md)