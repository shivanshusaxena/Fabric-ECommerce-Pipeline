---

## What It Does

- Ingests raw E-Commerce CSV data into Fabric Lakehouse Bronze layer
- Cleans data using PySpark — null removal, deduplication, date conversion, column renaming
- Joins Orders and Order Details tables
- Aggregates business metrics by State — total profit, total orders, average order value
- Saves each layer as Delta tables for ACID compliance and time travel
- Gold layer ready for Power BI reporting via Direct Lake mode

---

## Tech Stack

- Microsoft Fabric
- Lakehouse (OneLake)
- PySpark (Fabric Notebook)
- Delta Lake
- Power BI (Direct Lake)

---

## Medallion Architecture

| Layer | Description | Format |
|---|---|---|
| Bronze | Raw CSV files as-is | CSV in Files folder |
| Silver | Cleaned and standardized data | Delta Table |
| Gold | Business aggregations | Delta Table |

---

## Key Transformations

- `dropna()` — removed null rows
- `dropDuplicates()` — removed duplicate records
- `to_date()` — converted date strings to date type
- `withColumnRenamed()` — standardized column names
- `join()` — joined Orders with Order Details on Order ID
- `groupBy().agg()` — aggregated profit, orders, avg value by state
- `round()` — rounded metrics to 2 decimal places

---

## Business Insights from Gold Layer

- Maharashtra — highest orders (290) and profit (6176)
- Madhya Pradesh — 340 orders, profit 5551
- Tamil Nadu, Punjab, Bihar — negative profit (loss making states)
- Uttar Pradesh — strong performer with 3237 profit

---

## Author

**Shivanshu Saxena**
Data Engineer | Azure Databricks • PySpark • Microsoft Fabric • Power BI | PL-300 Certified
[GitHub](https://github.com/shivanshusaxena)