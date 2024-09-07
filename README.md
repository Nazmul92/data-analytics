# Sales Data Insight Project
### This project demonstrates how to analyze sales data using MySQL and Power BI. Through a series of SQL queries, it provides insights into customer and market performance, helping the business make data-driven decisions.
## Tools Used

- **MySQL**: For data storage and querying.
- **Power BI**: For data visualization and creating interactive dashboards.
- **GitHub**: To host and share this project.

## Features

- Distinct Customer Names Query
- Top Customer Analysis
- Top 5 Markets Analysis

## SQL query
### 1. Distinct Customer Names
#### This query retrieves a list of distinct customer names from the database:

```bash
SELECT DISTINCT customer_name 
FROM sales.customers 
INNER JOIN sales.transactions 
ON sales.customers.customer_code = sales.transactions.customer_code;
```
### 2. Top Customer by Total Purchases
#### This query identifies the top customer based on the number of products purchased:
```bash
SELECT 
    customer_name,
    COUNT(sales.transactions.product_code) AS product_count
FROM 
    sales.customers
INNER JOIN 
    sales.transactions 
    ON sales.customers.customer_code = sales.transactions.customer_code
GROUP BY 
    customer_name
ORDER BY 
    product_count DESC
LIMIT 1;

```
### 3. Top Customer in 2020
#### This query identifies the top customer based on the number of purchases made in the year 2020:
```bash
SELECT 
    customer_name,
    COUNT(product_code) AS product_count
FROM 
    sales.customers 
INNER JOIN 
    sales.transactions  
    ON sales.customers.customer_code = sales.transactions.customer_code
INNER JOIN 
    sales.date
    ON sales.date.cy_date = sales.transactions.order_date
WHERE 
    year = 2020
GROUP BY 
    customer_name
ORDER BY 
    product_count DESC
LIMIT 1;

```
### 4. Top 5 Customers with the Least Purchases in 2020
###$ This query identifies the 5 customers who made the fewest purchases in the year 2020:
```bash
SELECT 
    customer_name,
    COUNT(product_code) AS product_count
FROM 
    sales.customers 
INNER JOIN 
    sales.transactions  
    ON sales.customers.customer_code = sales.transactions.customer_code
INNER JOIN 
    sales.date
    ON sales.date.cy_date = sales.transactions.order_date
WHERE 
    year = 2020
GROUP BY 
    customer_name
ORDER BY 
    product_count ASC
LIMIT 5;


```
### 5. Top 5 Markets by Sales Volume
#### This query identifies the top 5 markets based on the number of products sold:
```bash
SELECT 
    markets_name,
    COUNT(product_code) AS product_count
FROM 
    sales.markets
INNER JOIN
    sales.transactions
ON
    sales.markets.markets_code = sales.transactions.market_code
GROUP BY
    markets_name
ORDER BY
    product_count DESC
LIMIT 5;


```
## ETL and data visualization in Power BI
