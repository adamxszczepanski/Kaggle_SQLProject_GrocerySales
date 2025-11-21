## Executive Summary

This project explores grocery sales data using SQL to answer key business questions about product performance, customer behaviour and sales trends over time. The goal is to show how SQL can be used not only to query data, but to generate actionable insights that a store manager or analyst could use to improve revenue and operations.

The analysis focuses on questions such as:
- Which products and categories generate the highest revenue?
- How do sales evolve over time (month)?
- Who are the most valuable customers and how concentrated is revenue among them?
- Are there patterns that could inform promotions, assortment or customer targeting?

To answer these questions, I use:
- joins between fact and dimension tables,
- aggregations with `GROUP BY` and filtering with `WHERE`/`HAVING`,
- common table expressions (CTEs) to structure more complex logic,
- window functions (such as `ROW_NUMBER`, `RANK`, running totals) for ranking and advanced analytics.

Key business takeaways from the queries include, for example:
- Identification of a small group of top products and/or categories that contribute a large share of total revenue.
- Insight into seasonality and trends (e.g. specific months or periods with significantly higher sales).
- Recognition of high-value customers whose behaviour is critical for the store’s performance.
- Opportunities for targeted promotions, better inventory planning and a more data-driven product strategy.

---

## Dataset & Schema

The project is based on a tabular dataset representing transactions in a grocery retail environment. The exact structure may vary depending on how the data is loaded into the database, but the logic assumes a separation between **transaction data** and **reference (dimension) tables**.

Source of the data:  [Kaggle grocery/retail sales dataset ](https://www.kaggle.com/datasets/andrexibiza/grocery-sales-dataset/data) 

Typical tables used in the analysis:

- **Sales / Transactions table**  
  Contains one row per transaction line (e.g. per product in a receipt).  
  Example columns:
  - `transaction_id` – unique ID of the transaction/receipt,
  - `transaction_date` – date (and possibly time) of the purchase,
  - `customer_id` – identifier of the customer (if available),
  - `product_id` – identifier of the purchased product,
  - `quantity` – number of units bought,
  - `price` or `sales_amount` – unit price or total line revenue.

- **Products table**  
  Describes each product sold in the store.  
  Example columns:
  - `product_id` – primary key, links to the sales table,
  - `product_name`,
  - `category` / `subcategory`,
  - optionally: `brand`, `unit`, etc.

- **Customers table** (if available)  
  Contains information about customers.  
  Example columns:
  - `customer_id` – primary key, links to the sales table,
  - basic attributes such as `age_group`, `region`, `gender` or other segmentation fields.

Key relationships and keys:
- `Sales.product_id` → `Products.product_id` (many-to-one),
- `Sales.customer_id` → `Customers.customer_id` (many-to-one, if customer data is provided).

The SQL script joins these tables to:
- aggregate revenue and quantity at different levels (product, category, customer, time),
- compute rankings and metrics (top products, top customers, monthly trends),
- prepare intermediate result sets using CTEs for clarity and reusability.

---

The SQL code is provided in the file:

- `Kaggle_Grocery_Project.sql`

---

## Dashboard

The Power BI dashboard coming soon.
