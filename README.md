# goit-rdb-hw-04

Homework 4 for the Relational Databases course: **DML, DDL and Complex SQL Expressions**.

## Dataset

This homework uses the **Olist Brazilian E-commerce Public Dataset**.

Source: Kaggle dataset `olistbr/brazilian-ecommerce`

The notebook downloads the dataset reproducibly with `kagglehub`.

## Tables Used

The homework uses six Olist source tables:

- `olist_customers_dataset.csv`
- `olist_orders_dataset.csv`
- `olist_order_items_dataset.csv`
- `olist_products_dataset.csv`
- `olist_sellers_dataset.csv`
- `olist_order_reviews_dataset.csv`

The CSV files are first loaded into raw PostgreSQL tables:

- `olist_customers_raw`
- `olist_orders_raw`
- `olist_order_items_raw`
- `olist_products_raw`
- `olist_sellers_raw`
- `olist_order_reviews_raw`

Typed tables with PostgreSQL constraints are then created and populated from the raw layer.

## Main Topics Covered

The notebook includes:

- raw and typed PostgreSQL schemas;
- primary keys, foreign keys, `CHECK`, `NOT NULL`, `UNIQUE`, identity columns and defaults;
- `INSERT ... RETURNING`;
- `INSERT ... ON CONFLICT DO UPDATE`;
- `UPDATE ... FROM`;
- `DELETE ... RETURNING`;
- customer segmentation at the `customer_unique_id` level;
- `INNER JOIN`, `LEFT JOIN`, `FULL OUTER JOIN`, `SELF JOIN` and anti-join;
- `GROUP BY`, `HAVING` and aggregate functions;
- `STRING_AGG`;
- set operations;
- CTEs and `ROW_NUMBER()` window function.

## How to Run

1. Open `hw_4.ipynb` in Google Colab.
2. Run the notebook from the beginning using **Runtime → Restart session and run all**.
3. The notebook installs the required Python packages and starts a local PostgreSQL server with `pgserver`.
4. The Olist dataset is downloaded through KaggleHub.
5. Raw tables are loaded, typed tables are created, and all SQL tasks are executed sequentially.

The notebook was validated with **Restart & Run All** and completes without traceback errors.

## Requirements

Main Python packages used:

- `pgserver`
- `psycopg2-binary`
- `sqlalchemy`
- `pandas`
- `kagglehub`

## Notes

- `customer_unique_id` is used for customer-level segmentation because one real customer may have multiple `customer_id` values.
- Review metrics are aggregated at order level before seller-level calculations to avoid multiplying review scores through item-level joins.
- The typed `olist_order_reviews` table uses a technical identity primary key instead of treating `review_id` as an unconditional unique key.
