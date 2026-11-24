# Ice Cream Sales – Data Cleaning and Exploratory Data Analysis

## Overview

This project focuses on data cleaning and exploratory data analysis (EDA) using a synthetic sales dataset from a fictional ice cream company. Its objective is to investigate data quality issues, improve the consistency of transactional records, and analyse sales performance across products, categories and time.

The project is based on Josh Temple's [Pandas Cleanup exercise](https://github.com/joshtemple/pandas-cleanup), originally presented at the Data + Desserts talk at the Flatiron School. It extends the original exercise by investigating selected anomalies before applying cleaning operations and correcting inconsistent transaction totals rather than discarding the corresponding records.

## Technologies

- Python
- Pandas – data manipulation, cleaning and aggregation
- Matplotlib and Seaborn – data visualisation
- Regular expressions (Regex) – product category extraction
- Jupyter Notebook / Google Colab

## Dataset

The [original dataset](https://github.com/joshtemple/pandas-cleanup/blob/master/sales.csv) contains 29,922 observations and six variables. Each row represents an order line rather than an entire order. The recorded transactions span January to July 2018.

| Variable | Description |
| --- | --- |
| `order_id` | Order identifier, which may appear on multiple rows |
| `name` | Product name, including its category |
| `ordered_at` | Date and time of the order |
| `price` | Unit price in US dollars |
| `quantity` | Number of units recorded on the order line |
| `line_total` | Total monetary value of the order line |

## Methodology

### 1. Data Import and Initial Inspection

- Inspect dataset dimensions, data types and missing values.
- Create a working copy to preserve the original data.

### 2. Data Cleaning and Quality Assessment

- Rename price columns, remove currency symbols, convert prices to numeric values and convert order timestamps to datetime.
- Investigate whether unit prices uniquely identify products for missing-name imputation. Reject this general imputation strategy because several products share the same price.
- Examine negative unit prices and line totals, then convert both to absolute values under the assumption that negative signs represent recording errors.
- Inspect five sampled orders containing duplicate rows before removing 549 duplicates.
- Remove the 1,481 remaining records with missing product names.
- Identify 28 inconsistencies between recorded line totals and unit price multiplied by quantity. Recalculate the totals, assuming unit prices and quantities are correct, and verify that no arithmetic discrepancies remain.
- Review summary statistics after cleaning.

### 3. Feature Engineering

Extract product categories from the `name` column using regular expressions and store them in a new `category` column, preserving the original product names.

### 4. Exploratory Data Analysis

- Rank the ten highest-revenue products.
- Compare aggregated sales values across product categories.
- Analyse weekly sales values through time-series visualisation.

## Main Findings

- The cleaning process retains 27,892 of the original 29,922 records (approximately 93.2%). All 28 inconsistent line totals are recalculated rather than removed.
- Dark Chocolate ice cream ranks first by sales value (approximately $8,608), followed by Cookie Cone ($8,364) and Tea ($7,964).
- Ice cream is the highest-revenue category (approximately $59,267), followed by cones ($31,940) and sorbets ($27,229).
- Weekly sales values fluctuate over the observed period. The analysis is descriptive and does not establish seasonality or support forecasting conclusions.

Sales rankings are based on monetary values, not the number of units sold. Results refer to the cleaned synthetic dataset and depend on the cleaning assumptions adopted. In real transactional data, negative amounts may represent refunds or reversals, and identical rows are not necessarily erroneous duplicates. These cases would require independent validation before applying the same transformations.

## Project Structure

- `README.md` – project documentation
- `Ice_Cream_Pandas_Clean_up.ipynb` – data cleaning and exploratory analysis notebook

## How to Run

1. Download `sales.csv` from the original repository linked above.
2. Open the notebook in Google Colab or Jupyter Notebook.
3. Install Pandas, Matplotlib and Seaborn if needed (`pip install pandas matplotlib seaborn`).
4. Update the dataset path in `pd.read_csv()` to match the location of the CSV file. When running locally, remove the Google Drive mounting cell or instructions.
5. Run the notebook cells sequentially.
