# 📊 Data Warehouse Analytics - Exploratory Data Analysis (EDA) Portfolio

## Overview

This project demonstrates an end-to-end data warehouse analytics workflow using SQL Server and a dimensional model.  
It follows a structured approach used in professional BI and analytics teams:

**Ingest → Model → Explore → Analyze → Report**

The warehouse is built in a star schema and analyzed using common analytical SQL patterns such as ranking, time-series trends, segmentation, and part-to-whole contribution reporting.

## 🏗️ Architecture

This project follows a classic medallion-style architecture:

| Layer  | Purpose |
|--|-|
| Bronze | Raw CRM & ERP extracts (CSV files) |
| Silver | Cleaned and standardized datasets |
| Gold   | Analytics-ready star schema + reporting views |

### Gold Layer (Star Schema)

- `gold.fact_sales`
- `gold.dim_customers`
- `gold.dim_products`

## 📂 Project Structure

```
datasets/
└── csv-files/
├── bronze_*.csv
├── silver_*.csv
├── gold.dim_customers.csv
├── gold.dim_products.csv
└── gold.fact_sales.csv

scripts/
├── 00_init_database.sql
├── 01_database_exploration.sql
├── 02_dimension_exploration.sql
├── 03_date_range_exploration.sql
├── 04_measures_exploration.sql
├── 05_magnitude_analysis.sql
├── 06_ranking_analysis.sql
├── 07_change_over_time_analysis.sql
├── 08_cumulative_analysis.sql
├── 09_performance_analysis.sql
├── 10_data_segmentation.sql
├── 11_part_to_whole_analysis.sql
├── 12_report_customers.sql
└── 13_report_products.sql

```

Each script represents a distinct analytics pattern used in real-world reporting and decision support.


## ⚙️ Setup Instructions

### 1) Requirements

- Microsoft SQL Server
- SQL Server Management Studio (SSMS)
- Project CSV files located in `datasets/csv-files/`

### 2) Create Database and Load Data

Run:

```

scripts/00_init_database.sql

```

This script will:

- Drop and recreate the database `DataWarehouseAnalytics`
- Create schema `gold`
- Create star schema tables
- Bulk load CSV files into the gold tables

⚠️ WARNING: Running this script will permanently delete the existing database.

Update file paths before execution:

```sql
FROM 'C:\[YOUR PATH]\Exploratory-Data-Analysis-EDA-Portfolio\datasets\csv-files\gold.fact_sales.csv'
````


## 🔍 Exploration Phase

### 01 - Database Exploration

* Lists all tables and schemas
* Inspects table metadata using `INFORMATION_SCHEMA`

### 02 - Dimension Exploration

* Unique customer countries
* Unique product categories and subcategories

### 03 - Date Range Exploration

* First and last order dates
* Total historical coverage
* Youngest and oldest customers


## 📐 Measures & KPI Exploration

### 04 - Measures Exploration

Calculates core KPIs:

* Total sales
* Total quantity sold
* Average selling price
* Total orders
* Total products
* Total customers
* Active customers

Also generates a unified KPI report using `UNION ALL`.


## 📊 Magnitude Analysis

### 05 - Magnitude Analysis

Analyzes distribution and scale:

* Customers by country and gender
* Products by category
* Average cost per category
* Revenue by category
* Revenue by customer
* Units sold by country


## 🏆 Ranking Analysis

### 06 - Ranking Analysis

Identifies performance extremes:

* Top 5 products by revenue
* Bottom 5 products by revenue
* Top 10 customers by revenue
* Bottom 3 customers by order volume

Uses `TOP` and window ranking functions such as `RANK()`.


## 📈 Change Over Time Analysis

### 07 - Change Over Time Analysis

Tracks trends using:

* Year and month grouping
* `DATETRUNC()`
* `FORMAT()`

Measures:

* Monthly sales
* Monthly customers
* Monthly quantities


## 🔁 Cumulative Analysis

### 08 - Cumulative Analysis

Computes running metrics:

* Running total sales
* Moving average selling price

Uses window functions over time-ordered data.


## 📉 Performance Analysis

### 09 - Performance Analysis

Performs Year-over-Year evaluation:

* Compares current sales vs product average
* Compares current sales vs previous year

Uses:

* `LAG()`
* `AVG() OVER()`
* `CASE` classification logic



## 🧩 Data Segmentation

### 10 - Data Segmentation

Segments data into business-relevant groups.

Product cost segmentation:

* Below 100
* 100–500
* 500–1000
* Above 1000

Customer behavior segmentation:

* VIP
* Regular
* New



## 🥧 Part-to-Whole Analysis

### 11 - Part-to-Whole Analysis

Measures category contribution to overall sales using window totals and percentage calculations.



## 📑 Reporting Views

### 12 - Customer Report View

Creates:

```
gold.report_customers
```

Includes:

* Age and age group
* Customer segment
* Recency
* Lifespan
* Total orders, sales, quantity, products
* Average order value
* Average monthly spend



### 13 - Product Report View

Creates:

```
gold.report_products
```

Includes:

* Product segment (High / Mid / Low performer)
* Recency
* Lifespan
* Total orders, sales, quantity
* Total customers
* Average order revenue
* Average monthly revenue



## 🧠 Skills Demonstrated

* Dimensional modeling
* Star schema design
* Analytical SQL patterns
* Window functions
* Time-series analysis
* Segmentation modeling
* KPI engineering
* Reporting layer design



## 🛠️ Tech Stack

* SQL Server (T-SQL)
* SQL Server Management Studio (SSMS)
* CSV-based warehouse ingestion
* Dimensional data warehousing



## 📜 License

This project is licensed under the MIT License.
See the `LICENSE` file for details.
