# Ice Cream Sales – Data Cleaning and Data Analysis

## Overview

This project focuses mainly on data cleaning and briefly on data analysis, using a synthetic sales dataset from a fictional ice cream shop (sales.csv in the folder). Its objective is to investigate data quality issues, improve the consistency of transactional records, and analyse sales performance across products, categories and time.

The project is based on Josh Temple's [Pandas Cleanup exercise](https://github.com/joshtemple/pandas-cleanup). It extends the original exercise by investigating selected anomalies before applying cleaning operations and correcting inconsistent transaction totals rather than discarding the corresponding records.

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


