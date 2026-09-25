# 🛒 E-COMMERCE CUSTOMER ANALYSIS — SQL PROJECT

A beginner-friendly **MySQL E-Commerce Customer Analysis Project** created to practice real-world SQL concepts such as filtering, aggregation, `GROUP BY`, `HAVING`, `JOIN`, subqueries, window functions, CTEs, and views.

---

## 📋 TABLE OF CONTENTS

* [📖 Project Overview](#-project-overview)
* [🎯 Project Objectives](#-project-objectives)
* [🛠️ Technologies Used](#️-technologies-used)
* [🗄️ Database Structure](#️-database-structure)
* [📊 Table Structure](#-table-structure)
* [🔗 Table Relationships](#-table-relationships)
* [📦 Dataset Summary](#-dataset-summary)
* [🧠 SQL Concepts Covered](#-sql-concepts-covered)
* [💻 Complete SQL Project](#-complete-sql-project)
* [🔎 Analysis Queries](#-analysis-queries)
* [📈 Key Analysis](#-key-analysis)
* [🚀 How to Run](#-how-to-run)
* [📂 Project Structure](#-project-structure)
* [📚 Learning Outcomes](#-learning-outcomes)
* [👨‍💻 Author](#-author)

---

# 📖 PROJECT OVERVIEW

The **E-Commerce Customer Analysis** project is a MySQL-based data analysis project that analyzes customers, products, and orders.

The project contains three main tables:

* 👤 `customers`
* 🛍️ `products`
* 🧾 `orders`

The database is designed to simulate a small e-commerce business and answer common business questions using SQL.

---

# 🎯 PROJECT OBJECTIVES

The main objectives of this project are:

* Find customers based on location.
* Calculate total orders and total sales.
* Analyze customer spending.
* Find high-value customers.
* Analyze product categories.
* Find customers with multiple orders.
* Calculate average order value.
* Find products above average price.
* Rank customers based on spending.
* Find the highest-value order for each customer.
* Calculate running sales.
* Find best-selling products.
* Create reusable SQL views.


---


# 🗄️ DATABASE STRUCTURE

## Database Name

```sql
ecommerce_customer_analysis
```

## Database Schema

```text
ecommerce_customer_analysis
│
├── customers
│   ├── customer_id
│   ├── customer_name
│   ├── city
│   ├── state
│   └── signup_date
│
├── products
│   ├── product_id
│   ├── product_name
│   ├── category
│   └── price
│
└── orders
    ├── order_id
    ├── customer_id
    ├── product_id
    ├── order_date
    ├── quantity
    └── total_amount
```

---

# 📊 TABLE STRUCTURE

## 1. 👤 CUSTOMERS TABLE

Stores customer information.

| Column          | Data Type    | Key | Description                |
| --------------- | ------------ | --- | -------------------------- |
| `customer_id`   | INT          | PK  | Unique customer ID         |
| `customer_name` | VARCHAR(100) |     | Customer name              |
| `city`          | VARCHAR(50)  |     | Customer city              |
| `state`         | VARCHAR(50)  |     | Customer state             |
| `signup_date`   | DATE         |     | Customer registration date |

### Primary Key

```text
customer_id
```

---

## 2. 🛍️ PRODUCTS TABLE

Stores product information.

| Column         | Data Type     | Key | Description       |
| -------------- | ------------- | --- | ----------------- |
| `product_id`   | INT           | PK  | Unique product ID |
| `product_name` | VARCHAR(100)  |     | Product name      |
| `category`     | VARCHAR(50)   |     | Product category  |
| `price`        | DECIMAL(10,2) |     | Product price     |

### Primary Key

```text
product_id
```

---

## 3. 🧾 ORDERS TABLE

Stores customer purchase transactions.

| Column         | Data Type     | Key | Description        |
| -------------- | ------------- | --- | ------------------ |
| `order_id`     | INT           | PK  | Unique order ID    |
| `customer_id`  | INT           | FK  | Customer reference |
| `product_id`   | INT           | FK  | Product reference  |
| `order_date`   | DATE          |     | Order date         |
| `quantity`     | INT           |     | Quantity purchased |
| `total_amount` | DECIMAL(10,2) |     | Total order amount |

### Primary Key

```text
order_id
```

### Foreign Keys

```text
customer_id → customers.customer_id

product_id → products.product_id
```


# 📦 DATASET SUMMARY

| Table     | Records |
| --------- | ------: |
| Customers |      15 |
| Products  |      15 |
| Orders    |      50 |

## Product Categories

The dataset contains:

* 💻 Electronics
* 👕 Fashion
* 🪑 Furniture
* 🎒 Accessories

## Customer Locations

Customers are located across:

* Haryana
* Chandigarh
* Delhi
* Rajasthan
* Uttar Pradesh
* Punjab

---

# 🧠 SQL CONCEPTS COVERED

```text
SELECT
WHERE
COUNT()
SUM()
AVG()
GROUP BY
HAVING
ORDER BY
INNER JOIN
LEFT JOIN
Subqueries
RANK()
ROW_NUMBER()
SUM() OVER()
PARTITION BY
CTE
WITH
CREATE VIEW
COALESCE()
LIMIT
PRIMARY KEY
FOREIGN KEY
```

---

# 💻 COMPLETE SQL PROJECT

## 1️⃣ CREATE DATABASE

```sql
CREATE DATABASE ecommerce_customer_analysis;

USE ecommerce_customer_analysis;
```

---

## 2️⃣ CREATE CUSTOMERS TABLE

```sql
CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    customer_name VARCHAR(100),
    city VARCHAR(50),
    state VARCHAR(50),
    signup_date DATE
);
```

---

## 3️⃣ CREATE PRODUCTS TABLE

```sql
CREATE TABLE products (
    product_id INT PRIMARY KEY,
    product_name VARCHAR(100),
    category VARCHAR(50),
    price DECIMAL(10,2)
);
```

---

## 4️⃣ CREATE ORDERS TABLE

```sql
CREATE TABLE orders (
    order_id INT PRIMARY KEY,
    customer_id INT,
    product_id INT,
    order_date DATE,
    quantity INT,
    total_amount DECIMAL(10,2),

    FOREIGN KEY (customer_id)
        REFERENCES customers(customer_id),

    FOREIGN KEY (product_id)
        REFERENCES products(product_id)
);
```

---

# 👤 INSERT CUSTOMERS DATA

```sql
INSERT INTO customers
(customer_id, customer_name, city, state, signup_date)
VALUES
(1, 'tarun', 'yamunanagar', 'haryana', '2025-01-10'),
(2, 'rahul', 'chandigarh', 'chandigarh', '2025-01-15'),
(3, 'priya', 'delhi', 'delhi', '2025-01-20'),
(4, 'aman', 'jaipur', 'rajasthan', '2025-02-05'),
(5, 'neha', 'ambala', 'haryana', '2025-02-10'),
(6, 'rohit', 'panipat', 'haryana', '2025-02-18'),
(7, 'sneha', 'noida', 'uttar pradesh', '2025-03-01'),
(8, 'vikas', 'ludhiana', 'punjab', '2025-03-08'),
(9, 'anjali', 'delhi', 'delhi', '2025-03-15'),
(10, 'deepak', 'karnal', 'haryana', '2025-03-22'),
(11, 'pooja', 'amritsar', 'punjab', '2025-04-01'),
(12, 'karan', 'gurgaon', 'haryana', '2025-04-10'),
(13, 'simran', 'chandigarh', 'chandigarh', '2025-04-18'),
(14, 'arjun', 'hisar', 'haryana', '2025-05-02'),
(15, 'meena', 'rohtak', 'haryana', '2025-05-12');
```

---

# 🛍️ INSERT PRODUCTS DATA

```sql
INSERT INTO products
(product_id, product_name, category, price)
VALUES
(101, 'laptop', 'electronics', 55000),
(102, 'smartphone', 'electronics', 30000),
(103, 'headphones', 'electronics', 2500),
(104, 'keyboard', 'electronics', 1500),
(105, 'mouse', 'electronics', 800),
(106, 'monitor', 'electronics', 12000),
(107, 'running shoes', 'fashion', 3500),
(108, 't-shirt', 'fashion', 1000),
(109, 'jeans', 'fashion', 2200),
(110, 'backpack', 'fashion', 1800),
(111, 'office chair', 'furniture', 8500),
(112, 'study table', 'furniture', 7000),
(113, 'water bottle', 'accessories', 600),
(114, 'smart watch', 'accessories', 4500),
(115, 'wallet', 'accessories', 1200);
```

---

# 🧾 INSERT ORDERS DATA

```sql
INSERT INTO orders
(order_id, customer_id, product_id, order_date, quantity, total_amount)
VALUES
(1001, 1, 101, '2025-05-01', 1, 55000),
(1002, 2, 102, '2025-05-02', 1, 30000),
(1003, 3, 107, '2025-05-03', 2, 7000),
(1004, 4, 108, '2025-05-04', 3, 3000),
(1005, 5, 103, '2025-05-05', 1, 2500),

(1006, 1, 104, '2025-05-07', 2, 3000),
(1007, 6, 106, '2025-05-08', 1, 12000),
(1008, 7, 109, '2025-05-09', 2, 4400),
(1009, 8, 111, '2025-05-10', 1, 8500),
(1010, 9, 113, '2025-05-11', 3, 1800),

(1011, 10, 102, '2025-05-12', 1, 30000),
(1012, 11, 114, '2025-05-13', 1, 4500),
(1013, 12, 112, '2025-05-14', 1, 7000),
(1014, 13, 110, '2025-05-15', 2, 3600),
(1015, 14, 115, '2025-05-16', 2, 2400),

(1016, 15, 107, '2025-05-17', 1, 3500),
(1017, 1, 102, '2025-05-18', 1, 30000),
(1018, 2, 106, '2025-05-19', 1, 12000),
(1019, 3, 101, '2025-05-20', 1, 55000),
(1020, 4, 103, '2025-05-21', 2, 5000),

(1021, 5, 109, '2025-05-22', 1, 2200),
(1022, 6, 108, '2025-05-23', 2, 2000),
(1023, 7, 111, '2025-05-24', 1, 8500),
(1024, 8, 114, '2025-05-25', 1, 4500),
(1025, 9, 105, '2025-05-26', 3, 2400),

(1026, 10, 101, '2025-05-27', 1, 55000),
(1027, 11, 107, '2025-05-28', 2, 7000),
(1028, 12, 103, '2025-05-29', 1, 2500),
(1029, 13, 102, '2025-05-30', 1, 30000),
(1030, 14, 106, '2025-05-31', 1, 12000),

(1031, 15, 110, '2025-06-01', 1, 1800),
(1032, 1, 111, '2025-06-02', 1, 8500),
(1033, 2, 108, '2025-06-03', 2, 2000),
(1034, 3, 114, '2025-06-04', 1, 4500),
(1035, 4, 105, '2025-06-05', 4, 3200),

(1036, 5, 112, '2025-06-06', 1, 7000),
(1037, 6, 101, '2025-06-07', 1, 55000),
(1038, 7, 103, '2025-06-08', 2, 5000),
(1039, 8, 109, '2025-06-09', 1, 2200),
(1040, 9, 102, '2025-06-10', 1, 30000),

(1041, 10, 107, '2025-06-11', 1, 3500),
(1042, 11, 111, '2025-06-12', 1, 8500),
(1043, 12, 106, '2025-06-13', 1, 12000),
(1044, 13, 115, '2025-06-14', 2, 2400),
(1045, 14, 108, '2025-06-15', 3, 3000),

(1046, 15, 113, '2025-06-16', 4, 2400),
(1047, 1, 107, '2025-06-17', 1, 3500),
(1048, 2, 101, '2025-06-18', 1, 55000),
(1049, 3, 106, '2025-06-19', 1, 12000),
(1050, 5, 102, '2025-06-20', 1, 30000);
```

---

# 🔎 ANALYSIS QUERIES

## 1. View All Customers

```sql
SELECT *
FROM customers;
```

## 2. View All Products

```sql
SELECT *
FROM products;
```

## 3. View All Orders

```sql
SELECT *
FROM orders;
```

---

# 🟢 DATA FILTERING

## Find all customers who are from Haryana.

```sql
SELECT *
FROM customers
WHERE state = 'haryana';
```

### Concept

```text
WHERE
```

---

##  Find all orders where the total order amount is greater than ₹20,000.

```sql
SELECT *
FROM orders
WHERE total_amount > 20000;
```

---

# 🟡 AGGREGATE FUNCTIONS

##  Find the total number of orders and total sales generated by the company.

```sql
SELECT
    COUNT(*) AS total_orders,
    SUM(total_amount) AS total_sales
FROM orders;
```

### Functions

```text
COUNT()
SUM()
```

---

## Average Order Value

```sql
SELECT
    AVG(total_amount) AS average_order_value
FROM orders;
```

---

# 🟠 GROUP BY & HAVING

##   Find the total sales generated by each customer and display the results in descending order of sales.

```sql
SELECT
    customer_id,
    SUM(total_amount) AS total_sales
FROM orders
GROUP BY customer_id
ORDER BY total_sales DESC;
```

---

##   Find customers whose total spending is greater than ₹50,000.

```sql
SELECT
    customer_id,
    SUM(total_amount) AS total_spending
FROM orders
GROUP BY customer_id
HAVING SUM(total_amount) > 50000;
```

---

##  Find the total sales generated by each product category.

```sql
SELECT
    p.category,
    SUM(o.total_amount) AS total_sales
FROM orders o
JOIN products p
    ON o.product_id = p.product_id
GROUP BY p.category
ORDER BY total_sales DESC;
```

---

# 🔵 JOINS

##   Display the customer name, product name, product category, order date, and order amount for every order.

```sql
SELECT
    c.customer_name,
    p.product_name,
    p.category,
    o.order_date,
    o.total_amount
FROM orders o
JOIN customers c
    ON o.customer_id = c.customer_id
JOIN products p
    ON o.product_id = p.product_id;
```

---

## Find customers who have placed more than 3 orders.

```sql
SELECT
    c.customer_id,
    c.customer_name,
    COUNT(o.order_id) AS total_orders
FROM customers c
JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY
    c.customer_id,
    c.customer_name
HAVING COUNT(o.order_id) > 3;
```

---

# 🟣 SUBQUERIES

##  Find all products whose price is greater than the average price of all products.

```sql
SELECT *
FROM products
WHERE price > (
    SELECT AVG(price)
    FROM products
);
```

---

##  Find customers whose total spending is greater than the average spending of all customers

```sql
SELECT
    customer_id,
    SUM(total_amount) AS total_spending
FROM orders
GROUP BY customer_id
HAVING SUM(total_amount) > (
    SELECT AVG(customer_total)
    FROM (
        SELECT
            customer_id,
            SUM(total_amount) AS customer_total
        FROM orders
        GROUP BY customer_id
    ) AS t
);
```

---

# 🪟 WINDOW FUNCTIONS

## . Rank all customers based on their total spending, with the highest spender getting Rank 1.
```sql
SELECT
    customer_id,
    total_spending,
    RANK() OVER (
        ORDER BY total_spending DESC
    ) AS customer_rank
FROM (
    SELECT
        customer_id,
        SUM(total_amount) AS total_spending
    FROM orders
    GROUP BY customer_id
) AS customer_sales;
```

---

##  Find the highest-value order placed by each customer.

```sql
WITH ranked_orders AS (
    SELECT
        customer_id,
        order_id,
        total_amount,
        ROW_NUMBER() OVER (
            PARTITION BY customer_id
            ORDER BY total_amount DESC
        ) AS rn
    FROM orders
)
SELECT
    customer_id,
    order_id,
    total_amount
FROM ranked_orders
WHERE rn = 1;
```

### Concepts

```text
ROW_NUMBER()
PARTITION BY
ORDER BY
```

---

##   Calculate the running total of sales based on the order date.

```sql
SELECT
    order_date,
    total_amount,
    SUM(total_amount) OVER (
        ORDER BY order_date
    ) AS running_sales
FROM orders
ORDER BY order_date;
```

---

# 🔄 CTE

##  Using a CTE, find customers whose total spending is greater than the average customer spending.

```sql
WITH customer_sales AS (
    SELECT
        customer_id,
        SUM(total_amount) AS total_spending
    FROM orders
    GROUP BY customer_id
)
SELECT
    customer_id,
    total_spending
FROM customer_sales
WHERE total_spending > (
    SELECT AVG(total_spending)
    FROM customer_sales
);
```

---

##  Using a CTE, find the best-selling product based on total quantity sold.
```sql
WITH product_sales AS (
    SELECT
        product_id,
        SUM(quantity) AS total_quantity
    FROM orders
    GROUP BY product_id
)
SELECT
    p.product_id,
    p.product_name,
    p.category,
    ps.total_quantity
FROM product_sales ps
JOIN products p
    ON ps.product_id = p.product_id
ORDER BY ps.total_quantity DESC
LIMIT 1;
```

---

# 👁️ VIEWS

##  Create a view that shows each customer's name, city, state, total number of orders, and total spending.

```sql
CREATE VIEW customer_sales_view AS
SELECT
    c.customer_id,
    c.customer_name,
    c.city,
    c.state,
    COUNT(o.order_id) AS total_orders,
    COALESCE(SUM(o.total_amount), 0) AS total_spending
FROM customers c
LEFT JOIN orders o
    ON c.customer_id = o.customer_id
GROUP BY
    c.customer_id,
    c.customer_name,
    c.city,
    c.state;
```

---

##  View

```sql
SELECT *
FROM customer_sales_view;
```

---

## Using the customer sales view, find the top 5 customers based on total spending.


```sql
SELECT
    customer_name,
    city,
    total_orders,
    total_spending
FROM customer_sales_view
ORDER BY total_spending DESC
LIMIT 5;
```

---

##  Find the top 3 products based on total revenue generated.

```sql
SELECT
    p.product_id,
    p.product_name,
    p.category,
    SUM(o.total_amount) AS total_revenue
FROM products p
JOIN orders o
    ON p.product_id = o.product_id
GROUP BY
    p.product_id,
    p.product_name,
    p.category
ORDER BY total_revenue DESC
LIMIT 3;
```

---

# # 💡 PROJECT INSIGHTS

* 💰 **High-Value Orders:** Several orders are above ₹20,000.
* 👤 **Repeat Customers:** Some customers placed more than 3 orders.
* 🛍️ **Product Performance:** Electronics products generate significant sales.
* 📊 **Customer Spending:** A few customers contribute higher total spending.
