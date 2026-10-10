# Customer Shopping Behavior Analysis

An analysis of customer shopping patterns using Python, SQL database integration, and an interactive Power BI dashboard. The project explores purchase amounts, product categories, age groups, subscriptions, and customer review ratings.

## Project Objectives

- Prepare customer shopping data for analysis.
- Explore purchasing patterns across customer segments and product categories.
- Summarize customer behavior through an interactive dashboard.
- Demonstrate data preparation in Python and database integration using SQLAlchemy.

## Tools and Technologies

- **Python and pandas:** data inspection, cleaning, and feature engineering.
- **Jupyter Notebook:** documented data preparation workflow.
- **SQLAlchemy:** loading prepared data into a relational database.
- **PostgreSQL:** database connection and data loading in the notebook.
- **MySQL and SQL Server:** alternative connection examples included in the notebook.
- **Power BI:** dashboard visuals, measures, and interactive filters.

## Dataset

The original dataset contains **3,900 records and 18 columns**, with one unique customer ID per record. It includes customer demographics, purchased items, purchase amounts, locations, review ratings, subscription status, shipping types, discounts, previous purchases, payment methods, and purchase frequency.

The original CSV contains **37 missing review ratings**.

## Python Data Preparation

The notebook performs the following steps:

1. Loads `customer_shopping_behavior.csv` using pandas.
2. Inspects sample records, data types, summary statistics, and missing values.
3. Fills missing review ratings using the median rating within each product category.
4. Converts column names to lowercase with underscores and renames the purchase amount column.
5. Creates four age groups using age quartiles: Young Adult, Adult, Middle-aged, and Senior.
6. Maps purchase frequency labels to a numeric `purchase_frequency_days` feature.
7. Checks whether discount and promo-code indicators match, then removes the redundant promo-code column.
8. Loads the prepared DataFrame into a database table named `customer`.

The database examples use `if_exists="replace"`, so running an export cell replaces an existing `customer` table in the configured database. Run only the database section you intend to use.

## Power BI Dashboard

The dashboard includes:

- **KPI cards:** number of customers, average purchase amount, and average review rating.
- **Subscription breakdown:** customers by subscription status.
- **Category comparisons:** purchase amounts and customer counts by product category.
- **Age-group comparisons:** purchase amounts and customer counts by age group.
- **Interactive filters:** subscription status, gender, category, and shipping type.

The dashboard uses `powerbi_customer_shopping_clean.csv`, which contains **3,900 records and 26 columns**. Additional fields include age groups, rating groups, purchase bands, sort-order columns, and subscriber, discount, and promo flags.

**Preparation distinction:** the supplied Power BI CSV uses age bands such as `18-24`, `25-34`, and `65+`, while the notebook uses age quartiles. The notebook does not contain the export steps that recreate the supplied Power BI CSV; these are separate prepared representations of the data.

## Selected Findings

These figures were calculated from the supplied CSV files before applying dashboard filters:

| Metric | Result |
| --- | ---: |
| Unique customers | 3,900 |
| Total recorded purchase amount | $233,081 |
| Average purchase amount | $59.76 |
| Average review rating in the Power BI CSV | 3.75 / 5 |

### Purchase Amount by Category

| Category | Total Purchase Amount |
| --- | ---: |
| Clothing | $104,264 |
| Accessories | $74,200 |
| Footwear | $36,093 |
| Outerwear | $18,524 |

Clothing accounts for the largest recorded purchase amount, followed by Accessories. These totals summarize the provided purchase records and do not include the monetary value of customers' previous purchases.

## Repository Files

Keep the notebook and its input CSV in the same directory for the existing relative file path to work.

| File | Purpose |
| --- | --- |
| `README.md` | Project overview and usage instructions |
| `Customer_Shopping_Behavior_Analysis.ipynb` | Python preparation and database integration notebook |
| `customer_shopping_behavior.csv` | Original input dataset |
| `powerbi_customer_shopping_clean.csv` | Prepared dataset used by the dashboard |
| `customer_behavior_dashboard.pbix` | Power BI report and data model |

The supplied `customer_behavior.csv` is a query-output file rather than the complete input dataset and is not required for this workflow.

## How to Use

### Run the Python Notebook

1. Download or clone the repository.
2. Install the core dependencies:

   ```bash
   pip install pandas jupyter sqlalchemy
   ```

3. Launch Jupyter:

   ```bash
   jupyter notebook
   ```

4. Open `Customer_Shopping_Behavior_Analysis.ipynb` and run the data preparation cells in order.
5. For database export, configure your local database connection and install the appropriate driver: `psycopg2-binary` for PostgreSQL, `pymysql` for MySQL, or `pyodbc` for SQL Server. SQL Server also requires a compatible Microsoft ODBC driver.

Keep real database passwords outside the committed notebook, for example in environment variables. Replace any existing credentials before publishing the notebook.

### View the Power BI Dashboard

1. Download `customer_behavior_dashboard.pbix` and `powerbi_customer_shopping_clean.csv`.
2. Open the `.pbix` file in Power BI Desktop.
3. If refresh fails because the original local CSV path is unavailable, update the source path in Power Query to the downloaded CSV and apply the changes.
4. Use the dashboard filters to explore customer segments.

The `.pbix` file is intended to be opened in Power BI Desktop. A dashboard screenshot can also be added to the repository so visitors can preview the report on GitHub.

## Scope

This project focuses on descriptive analysis and data preparation. The supplied notebook does not implement a machine learning prediction model or a complete SQL analysis script.

## Dataset Attribution

The original dataset source link was not included in the supplied project files. Add the original source and its applicable usage terms when available.

## Author

**Md Shakib Mostafa**
