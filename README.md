# Online Retail Sales Analysis — SQL Project

## 1. Project Overview

This project analyzes an online retail transaction dataset using **SQL, DuckDB, and Python in Google Colab**.

The goal is to explore sales patterns, identify top-performing countries and products, compare monthly sales values, and investigate data-quality issues that may affect business decisions.

## 2. Business Questions

This project investigates the following questions:

- What is the calculated transaction value across the dataset?
- How do sales values change from month to month?
- Which countries have the highest positive-item sales value?
- Which products rank highest by calculated sales value?
- How many customer records have missing CustomerID values?
- Are there unusual quantities, prices, or cancellation records that require investigation?

## 3. Dataset Information

| Property | Details |
|---|---|
| Dataset | Online Retail |
| Source file | `Online Retail.xlsx` |
| Rows | 541,909 |
| Columns | 8 |
| Period | December 2010 – December 2011 |
| Database engine | DuckDB |
| Environment | Google Colab |
| Query language | SQL |

### Dataset Columns

- `InvoiceNo` — Invoice identifier
- `StockCode` — Product or item code
- `Description` — Item description
- `Quantity` — Quantity purchased or recorded
- `InvoiceDate` — Transaction date and time
- `UnitPrice` — Price per unit
- `CustomerID` — Customer identifier
- `Country` — Customer's country

## 4. Tools and SQL Skills

**Tools used**
- SQL
- DuckDB
- Python
- Google Colab
- Pandas

**SQL concepts demonstrated**
- SELECT, WHERE, ORDER BY, LIMIT and DISTINCT
- Aggregate functions: COUNT, SUM, AVG, MIN and MAX
- GROUP BY and HAVING
- CASE WHEN and COALESCE
- INNER JOIN and LEFT JOIN concepts
- Common Table Expressions (CTEs)
- Subqueries
- Date-based analysis
- Window functions, including ranking and LAG
- Data-quality checks and business KPI calculations

## 5. Key Findings

### Dataset overview

- Total transaction rows: **541,909**
- Distinct identified customers: **4,372**
- Rows missing CustomerID: **135,080 (approximately 24.93%)**

### Calculated transaction values

- All-row calculated net value: **9,747,747.93**
- Positive-item calculated value: **10,666,684.54**

These figures use different filters and should not be treated as interchangeable.

### Monthly trend

November 2011 had an all-row calculated net value of **1,461,756.25**, the highest among the monthly values reviewed.

December 2011 had a calculated value of **433,668.01**, but the available dataset ends on December 9, 2011. Therefore, December is a partial month and should not be compared directly with complete months.

### Leading countries

Under the positive-item filters, the United Kingdom had the highest calculated value at **9,025,222.08**, followed by the Netherlands and EIRE.

### Leading products

The REGENCY CAKESTAND 3 TIER product had a calculated positive-item value of **174,484.74**.

The PAPER CRAFT, LITTLE BIRDIE item ranked highly, but its result includes a single transaction row with a quantity of 80,995. This record should be validated before using the ranking for business decisions.

## 6. Data-Quality Checks

The analysis identified records that warrant further investigation:

- Missing CustomerID values
- Negative quantities
- Zero and negative unit prices
- Invoice numbers beginning with `C`
- Unusually large quantities
- Incomplete December 2011 coverage

These are **validation flags, not automatic proof of errors**. Returns, cancellations, free items, or legitimate bulk purchases may explain some records.

## 7. Metric Definitions

### All-row calculated net value

Calculated as:

`SUM(Quantity * UnitPrice)`

This includes all rows, including negative quantities and zero-value records.

### Positive-item calculated value

Calculated using these filters:

- InvoiceNo does not start with `C`
- Quantity > 0
- UnitPrice > 0

This is a filtered positive-item measure, **not verified accounting revenue or net revenue**.

Product ranking also excludes the stock codes `DOT`, `M`, and `POST` under the project's analysis rules.

## 8. How to Run the Project

The analysis was developed in Google Colab using DuckDB.

1. Open Google Colab.
2. Upload `Online Retail.xlsx`.
3. Install or import the required libraries, including DuckDB and Pandas.
4. Create a DuckDB connection.
5. Load the Excel data into a table named `online_retail`.
6. Run the SQL analysis code in the project script or notebook.
7. Review the result tables and validate the key figures.

**Important:** The current SQL project script assumes that the `con` connection and `online_retail` table already exist. The dataset and setup steps must be available before running the analysis.

## 9. Recommendations

Based on the analysis:

1. Define consistent rules for cancellations, returns, free items, and service codes.
2. Validate unusually large transaction quantities.
3. Mark December 2011 as a partial month in reports.
4. Disclose missing CustomerID values when presenting customer metrics.
5. Build a dashboard showing monthly trends, country rankings, product rankings, and data-quality indicators.

## 10. Limitations

- The project is exploratory analysis, not an audited financial report.
- The positive-item value is not verified accounting revenue.
- Missing customer identifiers limit customer-level analysis.
- Unusual transaction records require business-context validation.
- December 2011 has incomplete date coverage.
- Product descriptions may contain inconsistent formatting.

## 11. Future Improvements

- Create charts for monthly trends and country/product rankings.
- Build a Power BI dashboard using validated metrics.
- Add a reproducible notebook with setup instructions.
- Publish the SQL code, report, and visualizations in a GitHub repository.

## Conclusion

This project demonstrates a practical SQL workflow for exploring retail transactions, calculating business metrics, comparing countries and products, analyzing monthly trends, and identifying data-quality risks.

The next step is to pair this analysis with clear visualizations and a Power BI dashboard to create a more complete Data Analyst portfolio project.
# Retail-Sales-Analysis-
