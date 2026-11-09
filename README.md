SQL Basic Query Theory and Fundamentals
 📌 Project Overview

Welcome to my SQL Fundamentals project!

This repository demonstrates my understanding of **Structured Query Language (SQL)** and its application in managing, retrieving, filtering, and analysing data stored in relational databases.

The project focuses on basic SQL query theory, essential SQL commands, database manipulation, and practical query examples. It serves as a foundation for developing database management and data analysis skills.

 🎯 Project Objectives

- Understand the fundamentals of relational databases.
- Learn how to retrieve data using SQL queries.
- Apply filtering and sorting techniques.
- Perform calculations and aggregations on datasets.
- Understand how to combine data from multiple tables.
- Manipulate and manage database records.
- Develop practical SQL skills for data analytics.

🗄️ 1. Introduction to SQL

SQL stands for **Structured Query Language**. It is a programming language used to communicate with relational database management systems (RDBMS).

SQL allows users to:
- Create and manage databases.
- Retrieve information from tables.
- Insert new records.
- Update existing records.
- Delete records.
- Analyse data using aggregate functions.

What is a Relational Database?

A relational database stores information in structured tables consisting of rows and columns.

| Term | Description |
|---|---|
| Database | An organised collection of data. |
| Table | A structure that stores related information. |
| Row | A single record in a table. |
| Column | A specific attribute or field. |
| Primary Key | A unique identifier for each record. |
| Foreign Key | A field that links one table to another. |

🔍 2. Basic SQL Queries

SELECT Statement

The SELECT statement retrieves data from a database table.

```sql
SELECT *
FROM Customers;
```

To retrieve specific columns:

```sql
SELECT CustomerName, City
FROM Customers;
```

DISTINCT Statement

DISTINCT removes duplicate values from query results.

```sql
SELECT DISTINCT Country
FROM Customers;
```

WHERE Clause

The WHERE clause filters records based on specified conditions.

```sql
SELECT *
FROM Customers
WHERE Country = 'South Africa';
```

ORDER BY Clause

ORDER BY sorts query results in ascending or descending order.

```sql
SELECT *
FROM Customers
ORDER BY CustomerName ASC;
```

Descending order:

```sql
SELECT *
FROM Customers
ORDER BY CustomerName DESC;
```

LIMIT Clause

LIMIT restricts the number of records returned.

```sql
SELECT *
FROM Customers
LIMIT 5;
```

*Note: SQL Server uses TOP instead of LIMIT, while other database systems have their own syntax variations.*

⚙️ 3. SQL Operators

SQL operators help filter and compare data.

| Operator | Description |
|---|---|
| = | Equal to |
| <> | Not equal to |
| > | Greater than |
| < | Less than |
| >= | Greater than or equal to |
| <= | Less than or equal to |
| AND | Both conditions must be true |
| OR | At least one condition must be true |
| NOT | Reverses a condition |
| BETWEEN | Checks a range of values |
| IN | Matches values in a specified list |
| LIKE | Searches for a specified pattern |

Practical Examples

**AND Operator**

```sql
SELECT *
FROM Employees
WHERE Department = 'Finance'
AND Salary > 10000;
```

**OR Operator**

```sql
SELECT *
FROM Customers
WHERE City = 'Durban'
OR City = 'Johannesburg';
```

**BETWEEN Operator**

```sql
SELECT *
FROM Products
WHERE Price BETWEEN 100 AND 500;
```

**IN Operator**

```sql
SELECT *
FROM Customers
WHERE Country IN ('South Africa', 'India', 'USA');
```

**LIKE Operator**

```sql
SELECT *
FROM Customers
WHERE CustomerName LIKE 'A%';
```

📊 4. Aggregate Functions

Aggregate functions perform calculations on multiple records and return a single result.

| Function | Description |
|---|---|
| COUNT() | Counts records or non-NULL values. |
| SUM() | Calculates the total. |
| AVG() | Calculates the average. |
| MIN() | Returns the minimum value. |
| MAX() | Returns the maximum value. |

Practical Examples

```sql
-- Count total employees
SELECT COUNT(*)
FROM Employees;

-- Calculate total sales
SELECT SUM(SalesAmount)
FROM Sales;

-- Calculate average salary
SELECT AVG(Salary)
FROM Employees;

-- Find the highest salary
SELECT MAX(Salary)
FROM Employees;

-- Find the lowest salary
SELECT MIN(Salary)
FROM Employees;
```

📈 5. GROUP BY and HAVING

 GROUP BY

GROUP BY groups records with matching values and is commonly used with aggregate functions.

```sql
SELECT Department, COUNT(*) AS EmployeeCount
FROM Employees
GROUP BY Department;
```

HAVING

HAVING filters grouped results based on aggregate conditions.

```sql
SELECT Department, AVG(Salary) AS AverageSalary
FROM Employees
GROUP BY Department
HAVING AVG(Salary) > 15000;
```

**Difference between WHERE and HAVING:**

- WHERE filters individual records before grouping.
- HAVING filters grouped results after aggregation.

🔗 6. SQL JOINS

SQL JOIN statements combine records from two or more tables using related columns.

| Join Type | Description |
|---|---|
| INNER JOIN | Returns matching records from both tables. |
| LEFT JOIN | Returns all records from the left table and matching records from the right table. |
| RIGHT JOIN | Returns all records from the right table and matching records from the left table. |
| FULL OUTER JOIN | Returns matching and non-matching records from both tables. |
| CROSS JOIN | Returns every possible combination of records from both tables. |

INNER JOIN Example

```sql
SELECT Customers.CustomerName,
       Orders.OrderDate
FROM Customers
INNER JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

LEFT JOIN Example

```sql
SELECT Customers.CustomerName,
       Orders.OrderID
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID = Orders.CustomerID;
```

🛠️ 7. Data Manipulation Language (DML)

DML commands are used to manipulate data stored in database tables.

INSERT

Adds new records to a table.

```sql
INSERT INTO Customers (CustomerID, CustomerName, City)
VALUES (1, 'John Smith', 'Durban');
```

UPDATE

Modifies existing records.

```sql
UPDATE Customers
SET City = 'Johannesburg'
WHERE CustomerID = 1;
```

DELETE

Removes records from a table.

```sql
DELETE FROM Customers
WHERE CustomerID = 1;
```

🏗️ 8. Data Definition Language (DDL)

DDL commands define and modify database structures.

| Command | Description |
|---|---|
| CREATE | Creates a database or table. |
| ALTER | Modifies an existing table. |
| DROP | Deletes a database object. |
| TRUNCATE | Removes all records from a table. |

CREATE TABLE

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    EmployeeName VARCHAR(100),
    Department VARCHAR(50),
    Salary DECIMAL(10,2)
);
```

ALTER TABLE

```sql
ALTER TABLE Employees
ADD Email VARCHAR(100);
```

DROP TABLE

```sql
DROP TABLE Employees;
```

🔄 9. SQL Subqueries

A subquery is a query nested inside another SQL query.

Example: Find employees earning more than the average salary.

```sql
SELECT EmployeeName, Salary
FROM Employees
WHERE Salary > (
    SELECT AVG(Salary)
    FROM Employees
);
```

Subqueries are useful when a query depends on the results of another query.

🧩 10. SQL CASE Statement

The CASE statement introduces conditional logic into SQL queries.

```sql
SELECT EmployeeName,
       Salary,
       CASE
           WHEN Salary >= 30000 THEN 'High Salary'
           WHEN Salary >= 15000 THEN 'Medium Salary'
           ELSE 'Low Salary'
       END AS SalaryCategory
FROM Employees;
```

📝 11. SQL NULL Values

NULL represents missing or unknown data.

To identify NULL values:

```sql
SELECT *
FROM Customers
WHERE City IS NULL;
```

To identify non-NULL values:

```sql
SELECT *
FROM Customers
WHERE City IS NOT NULL;
```

COALESCE can replace NULL values with an alternative value:

```sql
SELECT CustomerName,
       COALESCE(City, 'Unknown') AS City
FROM Customers;
```

📚 12. SQL Query Execution Order

Although SQL queries are written in a particular order, the database logically processes their clauses in a different order.

The general logical execution order is:

1. FROM – Identifies the source tables.
2. JOIN – Combines related tables.
3. ON – Defines join conditions.
4. WHERE – Filters individual records.
5. GROUP BY – Groups records.
6. HAVING – Filters grouped records.
7. SELECT – Selects the output columns.
8. DISTINCT – Removes duplicates.
9. ORDER BY – Sorts the results.
10. LIMIT / OFFSET – Restricts or skips returned records.

💡 13. Skills Demonstrated

Through this project, I demonstrate the following technical skills:

- SQL Fundamentals
- Data Retrieval
- Data Filtering
- Data Sorting
- Aggregate Functions
- Data Grouping
- Database Joins
- Subqueries
- Conditional Statements
- Data Manipulation
- Database Structure Management
- Basic Data Analysis

🧰 14. Tools and Technologies

- **SQL:** Structured Query Language.
- **MySQL:** Relational database management system.
- **Microsoft SQL Server:** Database management and querying.
- **PostgreSQL:** Open-source relational database system.
- **GitHub:** Project documentation and version control.

*Note: SQL syntax can differ slightly between database management systems.*

🚀 15. Future Improvements

Future developments of this project may include:

- Advanced SQL queries.
- Common Table Expressions (CTEs).
- Window Functions.
- Stored Procedures.
- Views and Indexes.
- Query Optimisation.
- Real-world SQL data analysis projects.

👨‍💻 Author

**SQL Fundamentals – GitHub Portfolio**

This repository represents my learning journey in SQL and database management, with a focus on developing practical querying skills for data analytics and business intelligence.

---

⭐ If you find this repository useful, feel free to explore the SQL examples and follow my progress in data analytics.xercises
