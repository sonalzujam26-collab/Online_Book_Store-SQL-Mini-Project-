# 📚 Online Book Store — SQL Mini Project

A PostgreSQL-based SQL mini project designed to analyze an **Online Book Store** database using relational database concepts, SQL queries, joins, filtering, aggregation, grouping, and data analysis.

The project contains information about **books, customers, and orders** and demonstrates how SQL can be used to retrieve meaningful insights from transactional data.

\---

## 📌 Project Overview

The **Online Book Store SQL Mini Project** consists of three interconnected tables:

* **Books** — Contains information about books, authors, genres, prices, publication years, and available stock.
* **Customers** — Contains customer details including name, email, phone number, city, and country.
* **Orders** — Contains transaction information linking customers with the books they ordered.

The project uses PostgreSQL and includes SQL queries ranging from basic data retrieval to more advanced analytical queries involving `JOIN`, `GROUP BY`, `HAVING`, aggregate functions, sorting, and filtering.

\---

## 🎯 Objectives

The main objectives of this project are to:

* Design a relational database for an online book store.
* Import CSV datasets into PostgreSQL tables.
* Retrieve and filter data using SQL.
* Perform calculations using aggregate functions.
* Analyze book sales by genre and author.
* Identify frequently ordered books.
* Analyze customer purchasing behavior.
* Identify high-value customers.
* Practice SQL joins and relational database concepts.
* Generate useful business insights from transactional data.

\---

## 🛠️ Technologies Used

|Technology|Purpose|
|-|-|
|**PostgreSQL**|Relational database management system|
|**SQL**|Database creation, querying, and analysis|
|**CSV**|Dataset storage and data import|
|**Git \& GitHub**|Version control and project hosting|

\---

## 🗂️ Project Structure

```text
Online-Book-Store-SQL/
│
├── README.md
│
├── SQL/
│   └── Online\\\_Book\\\_Store\\\_MiniProject.sql
│
├── Data/
    ├── Books.csv
    ├── Customers.csv
    └── Orders.csv


🗄️ Database Schema

The database consists of three main tables:

```text
┌──────────────────────┐
│       Customers      │
├──────────────────────┤
│ Customer\\\_ID (PK)    │
│ Name                 │
│ Email                │
│ Phone                │
│ City                 │
│ Country              │
└──────────┬───────────┘
           │
           │ Customer\\\_ID
           │
           ▼
┌──────────────────────┐
│        Orders        │
├──────────────────────┤
│ Order\\\_ID (PK)       │
│ Customer\\\_ID (FK)    │
│ Book\\\_ID (FK)        │
│ Order\\\_Date          │
│ Quantity             │
│ Total\\\_Amount        │
└──────────┬───────────┘
           │
           │ Book\\\_ID
           │
           ▼
┌──────────────────────┐
│         Books        │
├──────────────────────┤
│ Book\\\_ID (PK)        │
│ Title                │
│ Author               │
│ Genre                │
│ Published\\\_Year      │
│ Price                │
│ Stock                │
└──────────────────────┘
```

\---

# 📖 Tables

## 1\. Books

The `Books` table stores information about books available in the store.

|Column|Data Type|Description|
|-|-|-|
|`Book\\\_ID`|SERIAL|Primary key|
|`Title`|VARCHAR(100)|Book title|
|`Author`|VARCHAR(100)|Book author|
|`Genre`|VARCHAR(50)|Book genre|
|`Published\\\_Year`|INT|Year of publication|
|`Price`|NUMERIC(10,2)|Book price|
|`Stock`|INT|Available stock|

## 2\. Customers

The `Customers` table stores customer information.

|Column|Data Type|Description|
|-|-|-|
|`Customer\\\_ID`|SERIAL|Primary key|
|`Name`|VARCHAR(100)|Customer name|
|`Email`|VARCHAR(100)|Customer email|
|`Phone`|VARCHAR(15)|Customer phone|
|`City`|VARCHAR(50)|Customer city|
|`Country`|VARCHAR(150)|Customer country|

## 3\. Orders

The `Orders` table stores book purchase transactions.

|Column|Data Type|Description|
|-|-|-|
|`Order\\\_ID`|SERIAL|Primary key|
|`Customer\\\_ID`|INT|Foreign key referencing Customers|
|`Book\\\_ID`|INT|Foreign key referencing Books|
|`Order\\\_Date`|DATE|Date of order|
|`Quantity`|INT|Number of books ordered|
|`Total\\\_Amount`|NUMERIC(10,2)|Total order amount|

The `Orders` table connects customers and books through foreign keys.

\---

# 📊 Dataset

The project uses three CSV datasets:

### `Books.csv`

Contains book-level information such as:

* Book ID
* Title
* Author
* Genre
* Published Year
* Price
* Stock

### `Customers.csv`

Contains:

* Customer ID
* Name
* Email
* Phone
* City
* Country

### `Orders.csv`

Contains:

* Order ID
* Customer ID
* Book ID
* Order Date
* Quantity
* Total Amount

\---

# 🚀 Getting Started

## Prerequisites

Before running the project, install:

* PostgreSQL
* pgAdmin 4 (optional)
* Git (optional, for cloning the repository)

\---

## 1\. Clone the Repository

```bash
git clone https://github.com/your-username/Online-Book-Store-SQL.git
```

Navigate to the project directory:

```bash
cd Online-Book-Store-SQL
```

\---

## 2\. Create a PostgreSQL Database

Open PostgreSQL or pgAdmin and create a database:

```sql
CREATE DATABASE online\\\_book\\\_store;
```

Connect to the newly created database.

\---

## 3\. Create the Tables

Run the table creation queries from:

```text
SQL/Online\\\_Book\\\_Store\\\_MiniProject.sql
```

The project creates the `Books`, `Customers`, and `Orders` tables.

\---

# 📥 Importing the CSV Data

The SQL file contains `COPY` commands for importing the three CSV files.

The original SQL contains a local Windows file path, so you should **replace that path with the location of the CSV files on your own computer**.

Example:

```sql
COPY Books(Book\\\_ID, Title, Author, Genre, Published\\\_Year, Price, Stock)
FROM 'your\\\_path/Books.csv'
CSV HEADER;
```

```sql
COPY Customers(Customer\\\_ID, Name, Email, Phone, City, Country)
FROM 'your\\\_path/Customers.csv'
CSV HEADER;
```

```sql
COPY Orders(Order\\\_ID, Customer\\\_ID, Book\\\_ID, Order\\\_Date, Quantity, Total\\\_Amount)
FROM 'your\\\_path/Orders.csv'
CSV HEADER;
```

Alternatively, the CSV files can be imported through **pgAdmin's Import/Export Data** feature.

\---

# 🔎 SQL Analysis

The project contains two levels of SQL questions.

## 🟢 Basic SQL Questions

### 1\. Retrieve all books in the Fiction genre

```sql
SELECT \\\*
FROM Books
WHERE Genre = 'Fiction';
```

### 2\. Find books published after 1950

```sql
SELECT \\\*
FROM Books
WHERE Published\\\_Year > 1950;
```

### 3\. List customers from Canada

```sql
SELECT \\\*
FROM Customers
WHERE Country = 'Canada';
```

### 4\. Show orders placed in November 2023

```sql
SELECT \\\*
FROM Orders
WHERE Order\\\_Date BETWEEN '2023-11-01' AND '2023-11-30';
```

### 5\. Calculate total available book stock

```sql
SELECT SUM(Stock) AS Total\\\_Stock
FROM Books;
```

### 6\. Find the most expensive book

```sql
SELECT \\\*
FROM Books
ORDER BY Price DESC
LIMIT 1;
```

### 7\. Find orders containing more than one book

```sql
SELECT \\\*
FROM Orders
WHERE Quantity > 1;
```

### 8\. Find orders exceeding $20

```sql
SELECT \\\*
FROM Orders
WHERE Total\\\_Amount > 20;
```

### 9\. List all available genres

```sql
SELECT DISTINCT Genre
FROM Books;
```

### 10\. Find the book with the lowest stock

```sql
SELECT \\\*
FROM Books
ORDER BY Stock
LIMIT 1;
```

### 11\. Calculate total revenue

```sql
SELECT SUM(Total\\\_Amount) AS Revenue
FROM Orders;
```

\---

# 🔵 Advanced SQL Analysis

## 1\. Total books sold by genre

```sql
SELECT
    b.Genre,
    SUM(o.Quantity) AS Total\\\_Books\\\_Sold
FROM Orders o
JOIN Books b
    ON o.Book\\\_ID = b.Book\\\_ID
GROUP BY b.Genre;
```

## 2\. Average price of Fantasy books

```sql
SELECT AVG(Price) AS Average\\\_Price
FROM Books
WHERE Genre = 'Fantasy';
```

## 3\. Customers who placed at least two orders

```sql
SELECT
    o.Customer\\\_ID,
    c.Name,
    COUNT(o.Order\\\_ID) AS Order\\\_Count
FROM Orders o
JOIN Customers c
    ON o.Customer\\\_ID = c.Customer\\\_ID
GROUP BY o.Customer\\\_ID, c.Name
HAVING COUNT(o.Order\\\_ID) >= 2;
```

## 4\. Most frequently ordered book

```sql
SELECT
    o.Book\\\_ID,
    b.Title,
    COUNT(o.Order\\\_ID) AS Order\\\_Count
FROM Orders o
JOIN Books b
    ON o.Book\\\_ID = b.Book\\\_ID
GROUP BY o.Book\\\_ID, b.Title
ORDER BY Order\\\_Count DESC
LIMIT 1;
```

## 5\. Top 3 most expensive Fantasy books

```sql
SELECT \\\*
FROM Books
WHERE Genre = 'Fantasy'
ORDER BY Price DESC
LIMIT 3;
```

## 6\. Total books sold by each author

```sql
SELECT
    b.Author,
    SUM(o.Quantity) AS Total\\\_Books\\\_Sold
FROM Orders o
JOIN Books b
    ON o.Book\\\_ID = b.Book\\\_ID
GROUP BY b.Author;
```

## 7\. Cities of customers who spent more than $30

```sql
SELECT DISTINCT
    c.City,
    o.Total\\\_Amount
FROM Orders o
JOIN Customers c
    ON o.Customer\\\_ID = c.Customer\\\_ID
WHERE o.Total\\\_Amount > 30;
```

## 8\. Customer who spent the most

```sql
SELECT
    c.Customer\\\_ID,
    c.Name,
    SUM(o.Total\\\_Amount) AS Total\\\_Spent
FROM Orders o
JOIN Customers c
    ON o.Customer\\\_ID = c.Customer\\\_ID
GROUP BY c.Customer\\\_ID, c.Name
ORDER BY Total\\\_Spent DESC
LIMIT 1;
```

\---

# 🧠 SQL Concepts Demonstrated

### Database Design

* Relational database structure
* Primary keys
* Foreign keys
* Table relationships

### Data Retrieval

* `SELECT`
* `WHERE`
* `DISTINCT`
* `BETWEEN`

### Sorting \& Limiting

* `ORDER BY`
* `LIMIT`

### Aggregate Functions

* `SUM()`
* `AVG()`
* `COUNT()`

### Data Grouping

* `GROUP BY`
* `HAVING`

### Table Relationships

* `JOIN`

### Data Import

* CSV data loading
* PostgreSQL `COPY`

\---

# 📈 Dataset Summary

Based on the supplied datasets:

|Metric|Value|
|-|-:|
|Books records|500|
|Customer records|500|
|Order records|500|
|Total quantity ordered|2,697|
|Total order revenue|$75,628.66|
|Earliest order date|December 9, 2022|
|Latest order date|December 7, 2024|

These figures describe the supplied dataset and are not intended to represent a real-world online bookstore.

\---

# 💡 Business Questions Answered

The project demonstrates how SQL can answer questions such as:

* Which books belong to the Fiction genre?
* Which books were published after 1950?
* Which customers are from Canada?
* What orders were placed during November 2023?
* How much stock is currently recorded?
* What is the most expensive book?
* Which orders contain multiple books?
* Which orders exceed a specific spending threshold?
* What genres are available?
* Which book has the lowest stock?
* What is the total revenue?
* How many books were sold by genre?
* What is the average Fantasy book price?
* Which customers placed multiple orders?
* Which book was ordered most frequently?
* What are the three most expensive Fantasy books?
* How many books were sold by each author?
* Which customer locations had orders above $30?
* Which customer spent the most?

\---

# 📂 Files Included

|File|Description|
|-|-|
|`Books.csv`|Book catalog dataset|
|`Customers.csv`|Customer dataset|
|`Orders.csv`|Order transaction dataset|
|`Online\\\_Book\\\_Store\\\_MiniProject.sql`|Database creation, data import, and SQL analysis queries|
|`README.md`|Project documentation|

\---

# 🧪 How to Use the Project

1. Clone the repository.
2. Create a PostgreSQL database.
3. Open `Online\\\_Book\\\_Store\\\_MiniProject.sql`.
4. Create the three tables.
5. Import the CSV datasets.
6. Execute the basic SQL queries.
7. Execute the advanced SQL queries.
8. Explore and modify the queries to perform additional analysis.

\---

# 🔮 Possible Future Enhancements

The current project focuses on SQL-based analysis. It could be extended with:

* SQL views for frequently used analysis.
* Stored procedures and functions.
* More detailed sales analysis.
* Monthly and yearly revenue analysis.
* Customer segmentation.
* Genre performance analysis.
* Inventory-level analysis.
* Power BI or Tableau visualization.
* A Python-based data analysis layer.
* An interactive dashboard.

These are potential extensions and are **not part of the current project implementation**.

\---

# 👨‍💻 Author

**Sonal Satish Zujam**

BE CSEAI | Data \& Technology Enthusiast

### Skills Demonstrated

`SQL` • `PostgreSQL` • `Database Design` • `Data Analysis` • `Joins` • `Aggregation` • `Data Import`

\---

# ⭐ Project Highlights

* Relational PostgreSQL database
* 3 interconnected tables
* CSV-based datasets
* Basic and advanced SQL queries
* Practical use of aggregate functions
* SQL joins and grouping
* Customer and sales analysis
* Inventory-related analysis
* GitHub-ready project structure

\---

## 📜 License

This project is created for **educational and portfolio purposes**.

