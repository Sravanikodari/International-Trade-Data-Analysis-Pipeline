**International Trade Data Pipeline**

This repository contains a complete data engineering and analytics pipeline that processes raw international trade data (2017–2025) into structured tables, analytical outputs, and interactive Power BI dashboards.

The project includes data cleaning, feature extraction, SQL-based transformations, anomaly detection, and business intelligence reporting.
**
Repository Structure**
project/
│
├── data/
│   ├── raw/                                 # Original Excel input files
│   └── processed/
│       ├── cleaned_data.csv                 # Cleaned and enriched dataset
│       └── category_summary_for_dashboard.csv
│
├── sql/
│   ├── 01_macro_trends_yoy.sql
│   ├── 02_category_hierarchy.sql
│   ├── 03_supplier_analysis.sql
│   ├── 04_unit_economics.sql
│   └── 05_duty_anomalies.sql
│
├── notebook/
│   └── trade_analysis_pipelines.ipynb                  # Jupyter notebook for full pipeline
│
└── README.md

**Project Objectives**

Clean and preprocess raw trade shipment data.

Extract structured information from semi-structured goods descriptions.

Standardize units of measurement and create derived metrics.

Build analytical datasets for trends, category hierarchy, suppliers, and unit economics.

Implement SQL scripts for high-level analysis.

Design an interactive Power BI dashboard showcasing insights.

Data Cleaning and Feature Engineering

The core cleaning and transformation logic is implemented in:

notebook/trade_analysis_pipelines.ipynb

Key processing steps include:

Cleaning and normalizing column names.

Parsing GOODS DESCRIPTION to extract:

Model name

Model number

Capacity specification

Embedded quantities and units

Engineering new fields such as:

unit_price_inr, total_value_inr

orig_unit_price (foreign currency price)

landed_cost_per_unit

year, month

category and subcategory classification

Handling missing values and inconsistent units.

Creating a final cleaned dataset for analysis.

Outputs produced:

data/processed/cleaned_data.csv

data/processed/category_summary_for_dashboard.csv

**SQL Analytical Scripts**

All SQL logic is organized under sql/.
Each script corresponds to a major analysis component.

01_macro_trends_yoy.sql

Computes:

Total imports per year

Duty paid per year

Year-over-year growth metrics

Inputs for trend line charts and heatmaps

02_category_hierarchy.sql

Generates:

Category to Sub-category to Model hierarchy

Roll-ups used in treemap and sunburst visualizations

03_supplier_analysis.sql

Analyzes supplier-level patterns:

Top suppliers by import value

Supplier activity status (active in 2025 vs churned)

04_unit_economics.sql

Analyzes cost structure:

Relationship between capacity specification and landed cost per unit

Average foreign unit price and cost behaviour

05_duty_anomalies.sql

Implements anomaly detection:

Calculates duty percentage

Applies statistical deviation thresholds

Flags abnormal duty entries

Power BI Dashboard

Two datasets are imported:

cleaned_data.csv

category_summary_for_dashboard.csv

Key dashboard components:

Macro Trends

Line chart: Total Imports vs Duty Paid (2017–2025)

Year-over-year growth heatmap via matrix visual

Category Drilldown

Treemap or Sunburst from Category → Sub-category → Model

Highlights product-level distribution

Unit Economics

Scatter plot correlating capacity or specification with landed cost per unit

Used to understand product cost efficiency

Tools and Technologies Used

Python (pandas, numpy, regex)

Jupyter Notebook

SQLite for SQL transformations

Power BI Desktop


