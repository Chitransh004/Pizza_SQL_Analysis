# 🍕 Pizza Sales Data Analysis with SQL

This project analyzes sales data from a fictional pizza delivery company using **SQL**. The goal is to derive business insights such as order trends, revenue performance, top-selling items, and more.

---

## 📊 Objectives

- Explore total orders and revenue
- Identify top-performing pizzas
- Analyze sales by size, category, and time
- Use window functions for advanced analytics

---

## 📁 Dataset Overview

The dataset includes the following tables:

- **orders**: order_id, date, time
- **order_details**: order_details_id, order_id, pizza_id, quantity
- **pizzas**: pizza_id, pizza_type_id, size, price
- **pizza_types**: pizza_type_id, name, category, ingredients

---

## 🔍 SQL Queries

### ✅ Basic Queries
- Total number of orders
- Total revenue generated
- Highest-priced pizza
- Most common pizza size
- Top 5 most ordered pizza types

### ⚙️ Intermediate Queries
- Total quantity per pizza category
- Orders by hour of the day
- Category-wise distribution of pizzas
- Average pizzas ordered per day
- Top 3 pizza types by revenue

### 🧠 Advanced Queries
- Revenue % contribution by category
- Cumulative revenue over time
- Top 3 pizzas by revenue within each category

---

## 🧪 Sample Query: Top 3 Pizza Types by Revenue

```sql
SELECT 
    pizza_types.name,
    SUM(orders_details.quantity * pizzas.price) AS revenue
FROM pizza_types
JOIN pizzas ON pizza_types.pizza_type_id = pizzas.pizza_type_id
JOIN orders_details ON orders_details.pizza_id = pizzas.pizza_id
GROUP BY pizza_types.name
ORDER BY revenue DESC
LIMIT 3;
