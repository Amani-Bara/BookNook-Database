# 📚 BookNook — Relational Database (MySQL/MariaDB)

**BookNook** is a relational database project for managing a bookstore.  
It was designed as part of an academic project to demonstrate **database design, normalization, and SQL implementation**.  

The system supports:
- 📖 Managing books (title, author, publisher, price, stock quantity)  
- 👥 Tracking customers and their purchase history  
- 🛒 Recording and processing online orders (with customer details and timestamps)  
- 📊 Generating insights through SQL queries (e.g., top-selling books, low inventory, order history)  

This project also includes a detailed **report** with ERD, schema design, normalization steps, and explanations of design decisions.

---


## 🗃️ Schema Overview

**Tables**
- `book` — inventory: `BookID` (PK), `Book_Title`, `Author`, `Publisher`, `Price`, `Quantity`
- `customer` — customers: `CustomerID` (PK), `Name`, `Email`, `Purchase_History`
- `online_orders` — orders: `OrderID` (PK), `CustomerID` (FK → customer), `BookID`, `Email`, `Phone_Number`, `Address`, `Date`, `Time`, `Order_History`

> Foreign key: `online_orders.CustomerID → customer.CustomerID`  
> Extendable with additional FKs (e.g., `BookID → book.BookID`) and indices depending on use.

---

## ▶️ How to Run (MySQL/MariaDB)

> Requires **MySQL**.

**MySQL CLI**
```bash
# 1) Create a new database
mysql -u root -p -e "CREATE DATABASE BookNook CHARACTER SET utf8mb4 COLLATE utf8mb4_general_ci;"

# 2) Import schema + data
mysql -u root -p BookNook < BookNook.sql
```
---

## 🧩 Design & Normalization Notes

Entities: Book, Customer, Online Order

Keys: Primary keys on each table; FK from online_orders → customer

Normalization target: 3NF (no partial/transitive dependencies; atomic attributes)

Suggested future additions:

FK online_orders.BookID → book.BookID

Tables for Suppliers, Payments, and Employees

Indexes on Email, Book_Title, and date columns for faster queries

For detailed documentation (ERD, functional dependencies, and design choices), see the report in report/Database Project Report.docx.


## 🛠️ Tech Stack

SQL (MySQL/MariaDB)

Dump created with MariaDB (UTF8MB4)
