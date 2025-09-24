# 🛒 E-commerce Store Database Management System

## 📌 Overview
This project implements a complete relational database system for an E-commerce Store using **MySQL**. It models core business operations including customer management, product cataloging, inventory tracking, order processing, and payment recording.

---

## 🧱 Schema Design

### 🔗 Relationships
- **Customers → Orders**: One-to-Many
- **Orders → Payments**: One-to-One
- **Orders ↔ Products**: Many-to-Many (via `OrderItems`)
- **Categories → Products**: One-to-Many
- **Products → Inventory**: One-to-One

### 📋 Tables
| Table         | Description                              |
|---------------|------------------------------------------|
| `Customers`   | Stores customer details                  |
| `Categories`  | Defines product categories               |
| `Products`    | Product catalog with pricing             |
| `Inventory`   | Tracks stock levels per product          |
| `Orders`      | Records customer orders                  |
| `OrderItems`  | Line items for each order                |
| `Payments`    | Payment details for orders               |

---

## 🧪 Sample Data

Includes realistic entries for:
- Categories: Electronics, Books, Clothing
- Products: Smartphone, Laptop, Novel, T-Shirt
- Customers: Ann Katui, Ayub Samuel
- Orders and OrderItems with quantities and prices
- Inventory levels and payment records

---

## 🧠 Key SQL Queries

### 1. 🧾 Orders with Customer Names and Total Amount
```sql
SELECT 
    o.order_id,
    c.name AS customer_name,
    SUM(oi.quantity * oi.price) AS total_amount
FROM Orders o
JOIN Customers c ON o.customer_id = c.customer_id
JOIN OrderItems oi ON o.order_id = oi.order_id
GROUP BY o.order_id, c.name;

2.  Product List with Category and Stock
SELECT 
    p.name AS product_name,
    c.name AS category,
    i.stock_quantity
FROM Products p
JOIN Categories c ON p.category_id = c.category_id
JOIN Inventory i ON p.product_id = i.product_id;

3.  Payments with Order Status
SELECT 
    pay.payment_id,
    pay.amount,
    pay.method,
    o.status
FROM Payments pay
JOIN Orders o ON pay.order_id = o.order_id;

FILE STRUCTURE
Database_Management_System/
├── ecommerce_store.sql       # Full schema and sample data
├── README.md                 # Project documentation

How to Use
Import ecommerce_store.sql into your MySQL environment.

Run the queries to explore relationships and data.

 Author
Built by Michael Muracia under PLP learnig project #instructor Zabron— passionate about clean schema design, relational integrity, and real-world business logic.
