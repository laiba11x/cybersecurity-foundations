# Database Fundamentals

## What is a Database?

A **database** is an organised collection of data that can be easily accessed, managed, manipulated and analysed.

Databases can store many types of information, including:

* Usernames and authentication data
* User profiles
* Social media posts, comments and likes
* Orders and transaction records
* Watch history
* Business information

Databases are used by organisations of all sizes to store and manage data.

---

## Types of Databases

The two main types are:

1. **Relational databases (SQL)**
2. **Non-relational databases (NoSQL)**

### Relational Databases (SQL)

Relational databases store **structured data** in tables made up of rows and columns.

For example, a `Users` table could contain:

| id | first_name | last_name | email                                           |
| -- | ---------- | --------- | ----------------------------------------------- |
| 1  | Thomas     | Anderson  | [thomas@example.com](mailto:thomas@example.com) |
| 2  | Sarah      | Smith     | [sarah@example.com](mailto:sarah@example.com)   |

Data follows a defined structure, and tables can be related to each other.

**Common use cases:**

* E-commerce
* Banking
* Financial transactions
* Systems where data needs to follow a consistent structure

### Non-Relational Databases (NoSQL)

Non-relational databases do not rely on traditional tables, rows and columns.

They can store data in formats such as:

* Documents
* Key-value pairs
* Collections

Example:

```json
{
  "name": {
    "first": "Thomas",
    "last": "Anderson"
  },
  "occupation": ["The One"]
}
```

NoSQL databases are useful when data can vary significantly in structure.

**Common use cases:**

* Social media
* Large-scale applications
* Systems handling varied or rapidly changing data

### SQL vs NoSQL

| Relational (SQL)             | Non-Relational (NoSQL)                           |
| ---------------------------- | ------------------------------------------------ |
| Structured data              | Flexible data                                    |
| Tables, rows and columns     | Documents, key-value pairs, etc.                 |
| Defined schema               | More flexible schema                             |
| Relationships between tables | Does not rely on traditional table relationships |
| Useful for consistent data   | Useful for varied data                           |

The choice depends on the requirements of the application and the type of data being stored.

---

# Tables, Rows and Columns

Relational databases organise data into **tables**.

### Table

A table stores a particular type of data.

Example:

`Books`

### Column

A **column** represents a specific attribute or type of information.

Example columns:

* `id`
* `name`
* `published_date`

Each column normally has a defined **data type**.

Common data types include:

* **String** — text and characters
* **Integer** — whole numbers
* **Float/Decimal** — numbers containing decimal places
* **Date/Time** — dates and times

### Row

A **row** represents one individual record in a table.

Example:

| id | name                       | published_date |
| -- | -------------------------- | -------------- |
| 1  | Android Security Internals | 2014-10-14     |

In this example:

* `id`, `name` and `published_date` are **columns**
* The book information is one **row/record**

---

# Primary Keys

A **primary key** uniquely identifies each record in a table.

For example:

| id | name   |
| -- | ------ |
| 1  | Book A |
| 2  | Book B |
| 3  | Book C |

The `id` can be the primary key because each book has a unique ID.

### Key points

* Uniquely identifies a record.
* A table has one primary key.
* The value should not be duplicated between records.

Think of it like a university student ID: two students might have the same name, but their student IDs uniquely identify them.

---

# Foreign Keys

A **foreign key** creates a relationship between tables.

For example, we could have:

### Authors

| id | name            |
| -- | --------------- |
| 1  | Thomas Anderson |
| 2  | Sarah Smith     |

### Books

| id | name                       | author_id |
| -- | -------------------------- | --------- |
| 1  | Android Security Internals | 1         |
| 2  | Network Security           | 2         |

Here, `author_id` in the `Books` table refers to the `id` in the `Authors` table.

Therefore:

```text
Authors.id
     ↑
     |
Books.author_id
```

This allows related information to be stored in different tables while still being connected.

### Primary Key vs Foreign Key

| Primary Key                         | Foreign Key                            |
| ----------------------------------- | -------------------------------------- |
| Uniquely identifies a record        | Links records between tables           |
| Identifies records in its own table | References a key in another table      |
| One primary key per table           | A table can have multiple foreign keys |

---

## Simple Database Structure

```text
Database
│
├── Tables
│   │
│   ├── Columns → define the type of data
│   │
│   └── Rows → individual records
│
├── Primary Keys → uniquely identify records
│
└── Foreign Keys → connect related tables
```
# SQL and Database Management

## What is a DBMS?

A **Database Management System (DBMS)** is software that provides an interface for interacting with a database.

A DBMS allows users to:

* Retrieve data
* Add data
* Update data
* Delete data
* Manage databases

Examples of DBMSs include:

* **MySQL**
* **MariaDB**
* **Oracle Database**
* **MongoDB**

---

## What is SQL?

**SQL (Structured Query Language)** is a programming language used to interact with **relational databases**.

SQL can be used to:

* Query data
* Create database structures
* Insert data
* Update data
* Delete data
* Manage data stored in relational databases

### Simple relationship

```text
User
  ↓
SQL
  ↓
DBMS
  ↓
Relational Database
```

SQL is the language used to communicate with the relational database through the DBMS.

---

## Benefits of SQL and Relational Databases

### Fast

Relational databases can efficiently process and return large amounts of structured data.

### Easy to Learn

SQL uses readable, English-like keywords, making its basic syntax relatively easy to understand.

### Reliable

Relational databases use defined structures and data types, helping maintain consistency and accuracy.

### Flexible

SQL provides many ways to query and analyse data, allowing users to retrieve specific information from large datasets.

---

## MySQL

**MySQL** is a relational database management system that uses SQL.

A MySQL database can be accessed through a command-line interface or other database management tools.

A typical MySQL command-line session starts with:

```bash
mysql -u root -p
```

The `-u` option specifies the username and `-p` prompts for the password.

Once connected, the prompt changes to:

```text
mysql>
```

This indicates that SQL commands can now be entered.

> Lab passwords and temporary credentials should not be included in public notes.

## SQL Database & Table Statements

### Database Statements

#### CREATE DATABASE

Creates a new database.

```sql
CREATE DATABASE database_name;
```

Example:

```sql
CREATE DATABASE thm_bookmarket_db;
```

#### SHOW DATABASES

Lists the databases currently available.

```sql
SHOW DATABASES;
```

#### USE

Selects a database to work with. Queries will then run against this database.

```sql
USE thm_bookmarket_db;
```

#### DROP DATABASE

Deletes a database.

```sql
DROP DATABASE database_name;
```

⚠️ This removes the database, so use it carefully.

---

## Table Statements

### CREATE TABLE

Creates a table inside the currently selected database.

```sql
CREATE TABLE table_name (
    column1 data_type,
    column2 data_type,
    column3 data_type
);
```

Example:

```sql
CREATE TABLE book_inventory (
    book_id INT AUTO_INCREMENT PRIMARY KEY,
    book_name VARCHAR(255) NOT NULL,
    publication_date DATE
);
```

### Important table options

* `INT` → stores integers/numbers.
* `VARCHAR(255)` → stores variable-length text, up to 255 characters.
* `DATE` → stores dates.
* `AUTO_INCREMENT` → automatically gives each new record the next number.
* `PRIMARY KEY` → uniquely identifies each record.
* `NOT NULL` → the column cannot be left empty.

Example:

`book_id` would automatically become `1`, `2`, `3`, etc. for new books.

### SHOW TABLES

Lists the tables in the currently selected database.

```sql
SHOW TABLES;
```

### DESCRIBE / DESC

Shows the structure of a table, including its columns, data types, keys and other properties.

```sql
DESCRIBE book_inventory;
```

or:

```sql
DESC book_inventory;
```

### ALTER TABLE

Changes the structure of an existing table.

For example, adding a page count column:

```sql
ALTER TABLE book_inventory
ADD page_count INT;
```

`ALTER TABLE` can be used to:

* Add columns
* Remove columns
* Rename columns
* Change column data types

### DROP TABLE

Deletes a table from the database.

```sql
DROP TABLE table_name;
```

⚠️ This removes the table and its data.

---

## Basic SQL Flow

A simple workflow for creating and working with a database is:

```text
CREATE DATABASE
       ↓
USE DATABASE
       ↓
CREATE TABLE
       ↓
SHOW TABLES
       ↓
DESCRIBE TABLE
       ↓
ALTER TABLE (if needed)
```
## CRUD Operations

CRUD stands for **Create, Read, Update, Delete**. These are the basic operations used to manage data in a database.

| Operation | SQL Statement | Purpose                  |
| --------- | ------------- | ------------------------ |
| Create    | `INSERT`      | Adds new records         |
| Read      | `SELECT`      | Retrieves records        |
| Update    | `UPDATE`      | Changes existing records |
| Delete    | `DELETE`      | Removes records          |

### Create — INSERT

`INSERT INTO` adds a new record to a table.

```sql
INSERT INTO books (id, name, published_date, description)
VALUES (1, "Android Security Internals", "2014-10-14", "An In-Depth Guide to Android's Security Architecture");
```

The columns are specified after the table name, followed by the values being inserted.

### Read — SELECT

`SELECT` retrieves data from a table.

To retrieve **all columns**:

```sql
SELECT * FROM books;
```

`*` means all columns.

To retrieve specific columns:

```sql
SELECT name, description FROM books;
```

### Update — UPDATE

`UPDATE` modifies existing records.

```sql
UPDATE books
SET description = "New description"
WHERE id = 1;
```

* `SET` specifies what should be changed.
* `WHERE` specifies which record should be changed.

⚠️ Be careful with `UPDATE` without a `WHERE` clause, as it can modify multiple/all records.

### Delete — DELETE

`DELETE` removes records from a table.

```sql
DELETE FROM books
WHERE id = 1;
```

The `WHERE` clause specifies which record should be deleted.

⚠️ Be careful with `DELETE` without a `WHERE` clause, as it can delete multiple/all records.

### CRUD Summary

```text
CREATE → INSERT → Add data
READ   → SELECT → Retrieve data
UPDATE → UPDATE → Modify data
DELETE → DELETE → Remove data
```
## SQL Clauses

SQL clauses help define what data a query should retrieve, filter, group or sort.

Common clauses include:

* `FROM` → specifies the table being accessed.
* `WHERE` → filters which records are used.
* `DISTINCT` → removes duplicate values.
* `GROUP BY` → groups records together.
* `ORDER BY` → sorts the results.
* `HAVING` → filters grouped results after aggregation.

### DISTINCT

`DISTINCT` returns only unique values and removes duplicates.

```sql
SELECT DISTINCT name FROM books;
```

For example, if `Ethical Hacking` appears twice, `DISTINCT` only returns it once.

### GROUP BY

`GROUP BY` groups records with the same value. It is commonly used with aggregate functions such as `COUNT()`.

```sql
SELECT name, COUNT(*)
FROM books
GROUP BY name;
```

This counts how many times each book name appears.

Example result:

```text
Ethical Hacking → 2
Android Security Internals → 1
```

### ORDER BY

`ORDER BY` sorts query results.

#### Ascending

`ASC` sorts from lowest/earliest to highest/latest.

```sql
SELECT *
FROM books
ORDER BY published_date ASC;
```

#### Descending

`DESC` sorts from highest/latest to lowest/earliest.

```sql
SELECT *
FROM books
ORDER BY published_date DESC;
```

### HAVING

`HAVING` filters the results **after grouping/aggregation**.

It is commonly used with `GROUP BY`.

```sql
SELECT name, COUNT(*)
FROM books
GROUP BY name
HAVING name LIKE '%Hack%';
```

This returns grouped book names containing `Hack`.

### WHERE vs HAVING

| Clause   | Used for                                   |
| -------- | ------------------------------------------ |
| `WHERE`  | Filters individual records before grouping |
| `HAVING` | Filters grouped results after aggregation  |

### Quick Summary

```text
DISTINCT → Remove duplicates
GROUP BY  → Group similar values
ORDER BY  → Sort results
ASC       → Ascending order
DESC      → Descending order
HAVING    → Filter grouped results
```
## SQL Operators

Operators are used in SQL to compare values, filter data and combine conditions.

These operators are used with statements such as `SELECT` and clauses such as `WHERE`.

## Logical Operators

### LIKE

`LIKE` searches for a specific pattern within a column.

```sql
SELECT *
FROM books
WHERE description LIKE "%guide%";
```

`%` is a wildcard that represents any number of characters.

This example finds books where the description contains `guide`.

### AND

`AND` combines multiple conditions. **All conditions must be true**.

```sql
SELECT *
FROM books
WHERE category = "Offensive Security"
AND name = "Bug Bounty Bootcamp";
```

### OR

`OR` combines multiple conditions where **at least one condition must be true**.

```sql
SELECT *
FROM books
WHERE name LIKE "%Android%"
OR name LIKE "%iOS%";
```

### NOT

`NOT` reverses a condition and can be used to exclude results.

```sql
SELECT *
FROM books
WHERE NOT description LIKE "%guide%";
```

This returns books whose descriptions do not contain `guide`.

### BETWEEN

`BETWEEN` checks whether a value falls within a specified range.

```sql
SELECT *
FROM books
WHERE id BETWEEN 2 AND 4;
```

This includes values from `2` through `4`.

---

## Comparison Operators

Comparison operators compare values against a condition.

| Operator | Meaning                  |
| -------- | ------------------------ |
| `=`      | Equal to                 |
| `!=`     | Not equal to             |
| `<`      | Less than                |
| `>`      | Greater than             |
| `<=`     | Less than or equal to    |
| `>=`     | Greater than or equal to |

### Equal To `=`

Finds an exact match.

```sql
SELECT *
FROM books
WHERE name = "Designing Secure Software";
```

### Not Equal To `!=`

Finds values that do not match the specified value.

```sql
SELECT *
FROM books
WHERE category != "Offensive Security";
```

### Less Than `<`

Finds values below the specified value.

```sql
SELECT *
FROM books
WHERE published_date < "2020-01-01";
```

This finds books published before 1 January 2020.

### Greater Than `>`

Finds values above the specified value.

```sql
SELECT *
FROM books
WHERE published_date > "2020-01-01";
```

This finds books published after 1 January 2020.

### Less Than or Equal To `<=`

Finds values that are less than or equal to the specified value.

```sql
SELECT *
FROM books
WHERE published_date <= "2021-11-15";
```

### Greater Than or Equal To `>=`

Finds values that are greater than or equal to the specified value.

```sql
SELECT *
FROM books
WHERE published_date >= "2021-11-02";
```

---

## Quick Summary

```text
LIKE      → Match a pattern
AND       → All conditions must be true
OR        → At least one condition must be true
NOT       → Exclude/reverse a condition
BETWEEN   → Value within a range

=         → Equal
!=        → Not equal
<         → Less than
>         → Greater than
<=        → Less than or equal
>=        → Greater than or equal
```
## SQL Functions

SQL functions perform operations on data and return a result. They can be used to manipulate strings or calculate values across multiple rows.

## String Functions

### CONCAT()

`CONCAT()` combines two or more strings into one.

```sql
SELECT CONCAT(name, " is a type of ", category, " book.") AS book_info
FROM books;
```

`AS` gives the resulting column a name, in this case `book_info`.

### GROUP_CONCAT()

`GROUP_CONCAT()` combines values from multiple rows into a single string.

```sql
SELECT category, GROUP_CONCAT(name SEPARATOR ", ") AS books
FROM books
GROUP BY category;
```

This groups books by category and combines the book names within each category.

### SUBSTRING()

`SUBSTRING()` extracts part of a string.

```sql
SELECT SUBSTRING(published_date, 1, 4) AS published_year
FROM books;
```

The `1` is the starting position and `4` is the number of characters to extract.

### LENGTH()

`LENGTH()` returns the number of characters in a string, including spaces and punctuation.

```sql
SELECT LENGTH(name) AS name_length
FROM books;
```

---

## Aggregate Functions

Aggregate functions perform calculations across multiple rows and return a single result.

### COUNT()

`COUNT()` counts the number of records.

```sql
SELECT COUNT(*) AS total_books
FROM books;
```

### SUM()

`SUM()` adds together numerical values in a column. `NULL` values are not included.

```sql
SELECT SUM(price) AS total_price
FROM books;
```

### MAX()

`MAX()` returns the highest value in a column.

```sql
SELECT MAX(published_date) AS latest_book
FROM books;
```

For dates, this returns the most recent date.

### MIN()

`MIN()` returns the lowest value in a column.

```sql
SELECT MIN(published_date) AS earliest_book
FROM books;
```

For dates, this returns the earliest date.

---

## Quick Summary

```text
CONCAT()       → Combine strings
GROUP_CONCAT() → Combine values from multiple rows
SUBSTRING()    → Extract part of a string
LENGTH()       → Count characters

COUNT() → Count rows
SUM()   → Add values
MAX()   → Find the highest/latest value
MIN()   → Find the lowest/earliest value
```
## Summary

* **Databases** store organised data that can be accessed, managed and analysed.
* **Relational databases** store structured data in tables.
* **Non-relational databases (NoSQL)** store data in other formats rather than traditional tables.
* Relational databases use **tables, rows and columns**.
* **Primary keys** uniquely identify records within a table.
* **Foreign keys** create relationships between tables.
* **SQL (Structured Query Language)** is used to interact with relational databases.
* **Database and table statements** can create and modify databases and tables.
* **CRUD operations** manage data:

  * `INSERT` → Create
  * `SELECT` → Read
  * `UPDATE` → Update
  * `DELETE` → Delete
* **Clauses** control how data is retrieved, filtered, sorted and grouped.
* **Operators** allow values to be compared and conditions to be combined.
* **Functions** can manipulate data and perform calculations.

### Key SQL Areas Covered

```text
Databases
   ↓
Tables, Rows & Columns
   ↓
SQL
   ↓
Database & Table Statements
   ↓
CRUD Operations
   ↓
Clauses
   ↓
Operators
   ↓
Functions
```
