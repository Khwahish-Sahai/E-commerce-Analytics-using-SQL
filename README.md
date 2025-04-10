# 📊 Task 3 – SQL for Data Analysis

## 🎯 Objective
The goal of this task was to perform SQL-based analysis on an E-commerce dataset using MySQL Workbench. The dataset was structured across multiple related tables, and the analysis was conducted using joins, groupings, aggregate functions, and ordering techniques.

---

## 🧰 Tools & Technologies
- **Database:** MySQL Workbench
- **Data Preparation:** Excel (converted to CSV files)
- **Languages:** SQL (Structured Query Language)

---

## 📦 Dataset Overview
The database (`ecommerce_db`) includes the following 5 tables:

| Table Name     | Description                                  |
|----------------|----------------------------------------------|
| `Customers`    | Customer details (ID, name, email, country)  |
| `Orders`       | Orders placed with date and total amount     |
| `OrderDetails` | Items within each order (product & quantity) |
| `Products`     | List of products sold                        |
| `Categories`   | Product categories (Apparel, Footwear, etc.) |

---

## 🔍 SQL Queries & Insights

### 1. 🧾 Total Amount Spent by Each Customer
Shows which customers have spent the most overall.
```sql

SELECT 
    c.name AS customer_name,
    SUM(o.total_amount) AS total_spent
FROM Orders o
JOIN Customers c ON o.customer_id = c.customer_id
GROUP BY c.name
ORDER BY total_spent DESC;
📄 Output: orders_by_customer.csv
2. 📦 Most Popular Products (by Quantity Sold)
Identifies products that have been sold the most.
SELECT 
    p.name AS product_name,
    SUM(od.quantity) AS total_sold
FROM OrderDetails od
JOIN Products p ON od.product_id = p.product_id
GROUP BY p.name
ORDER BY total_sold DESC;
📄 Output: products_by_quantity.csv

3. 💰 Revenue by Product
Finds which products generated the highest total revenue.
SELECT 
    p.name AS product_name,
    SUM(od.quantity * od.price) AS total_revenue
FROM OrderDetails od
JOIN Products p ON od.product_id = p.product_id
GROUP BY p.name
ORDER BY total_revenue DESC;
📄 Output: products_by_revenue.csv
```


