# Zepto Inventory Analysis using SQL

**PostgreSQL | Data Cleaning | E-commerce Inventory Analytics | Pricing Analysis**

An SQL-based exploration of a Zepto-style grocery inventory dataset. The project demonstrates how to inspect and clean product records, compare prices and discounts, assess stock availability, and estimate inventory value by category.

## Project Objectives

- Explore product categories and inventory availability.
- Detect null values, duplicate product names and zero-priced records.
- Normalize stored prices from paise to rupees.
- Identify highly discounted products and expensive out-of-stock items.
- Compare pricing, category-level inventory value and product weights.

## Tools

- **PostgreSQL** for relational queries and transformations
- **SQL** for data exploration, cleaning, aggregation and business analysis
- **CSV** for the source product dataset

## Files

| File | Description |
| --- | --- |
| [`Zepto_SQL_data_analysis.sql`](Zepto_SQL_data_analysis.sql) | Table definition, data checks, cleaning steps and eight analysis queries |
| [`zepto_v2.csv`](zepto_v2.csv) | Product inventory data |
| [`LICENSE`](LICENSE) | MIT license and original copyright notice |

## Analysis Workflow

### 1. Create and explore the inventory table

The SQL script creates a `zepto` table with fields for SKU, category, product name, MRP, discount percentage, available quantity, discounted selling price, product weight, out-of-stock status and quantity.

It then checks record counts, sample rows, missing fields, distinct categories, stock status and repeated product names.

### 2. Clean pricing data

The script identifies zero-priced records, deletes rows where `mrp = 0`, and converts both `mrp` and `discountedSellingPrice` from **paise to rupees** by dividing by 100.

**Important:** Run the price-conversion UPDATE only once on an unconverted dataset. Re-running it will divide prices by 100 again. The script also deletes rows and recreates the table, so work on a copy of your data.

### 3. Answer eight business questions

| Query | Business question |
| --- | --- |
| Q1 | Which ten products offer the highest percentage discounts? |
| Q2 | Which high-MRP products are out of stock? |
| Q3 | What is the estimated inventory revenue/value by category? |
| Q4 | Which products cost more than ₹500 but offer under 10% discount? |
| Q5 | Which five categories have the highest average discount? |
| Q6 | Which products weighing at least 100 g offer the lowest price per gram? |
| Q7 | How can products be grouped into low, medium and bulk weight categories? |
| Q8 | What is the total inventory weight in each category? |

**Interpretation note:** Q3 multiplies the discounted selling price by available quantity. This is an *estimated inventory sales value*, not actual realized revenue, because the dataset does not establish completed sales.

## How to Run

1. Install **PostgreSQL** and open **pgAdmin** or another PostgreSQL SQL client.
2. Create a database for the project.
3. Open [`Zepto_SQL_data_analysis.sql`](Zepto_SQL_data_analysis.sql) and execute its `CREATE TABLE` section.
4. Import [`zepto_v2.csv`](zepto_v2.csv) into the `zepto` table using your SQL client's CSV import feature. Match the CSV columns to the table columns and verify the import settings.
5. Run the exploration queries, review any missing or invalid values, and then execute the cleaning statements.
6. Execute Q1–Q8 to explore the inventory dataset.

The script does **not** include a CSV import command, so importing the CSV is a separate required step. Review the data types and column mapping before importing.

## SQL Concepts Demonstrated

`CREATE TABLE`, `SELECT`, `DISTINCT`, `WHERE`, `GROUP BY`, `HAVING`, `ORDER BY`, `LIMIT`, `COUNT`, `SUM`, `AVG`, `ROUND`, `CASE`, `UPDATE` and `DELETE`.

## Applications

This analysis illustrates how a retail operations team could identify potential inventory gaps, compare discount strategies, estimate the value of stock on hand and evaluate product assortment by category.

These are analytical use cases, not claims of measured business impact or access to Zepto's internal operational systems.

## Attribution and License

The included [MIT License](LICENSE) credits **Amlan Mohanty (2025)** as the original copyright holder. This repository preserves that attribution. If you adapt or extend the project, describe your own changes separately and retain the license notice.
