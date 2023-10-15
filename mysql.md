# Databases

## SQL injection

SQL injection is a type of cyber attack where malicious actors insert malicious SQL code into an application's input field, which is then executed by the database. This can result in unauthorized access, data theft, or data corruption. Some ways to protect against SQL injection:

* `Use prepared statements`: Prepared statements are a type of parameterized query that can prevent SQL injection attacks. The parameter values are sent separately from the SQL query, which makes it difficult for attackers to modify the SQL statement. These ensure that user input is treated as data, not executable code.
* `Use input validation`: Validate user input on both the client and server side. Input validation can prevent users from entering characters that can be used for SQL injection attacks.
* `Sanitize user input`: Use data sanitization techniques to remove special characters that could be used for SQL injection attacks. This can include removing single quotes, double quotes, and semicolons.
* `Limit database permissions`: Limit the permissions of the user accounts that access the database. This can help prevent attackers from executing malicious SQL statements if they do manage to gain access to the database.

## SQL

### SQL data types

| Data Type     | Description                                             | Example            |
| ------------- | ------------------------------------------------------- | ------------------- |
| CHAR(n)       | Fixed-length character string                          | CHAR(10)           |
| VARCHAR(n)    | Variable-length character string                       | VARCHAR(255)       |
| TEXT          | Variable-length character string (large max length)    | TEXT               |
| INT           | 32-bit signed integer                                  | INT               |
| BIGINT        | 64-bit signed integer                                  | BIGINT            |
| DECIMAL(p, s) | Fixed-point decimal number with precision and scale   | DECIMAL(10, 2)     |
| FLOAT(p)      | Floating-point number with precision                   | FLOAT(10)          |
| DATE          | Date without time information                          | DATE               |
| TIME          | Time without date information                          | TIME               |
| DATETIME      | Date and time combined                                 | DATETIME           |
| TIMESTAMP     | Timestamp with date and time                           | TIMESTAMP           |
| BOOLEAN       | Synonym for TINYINT (can store 0 for false, 1 for true) | BOOLEAN           |
| BLOB          | Binary Large Object (for binary data)                  | BLOB               |
| ENUM          | A column with predefined set of values                | ENUM('Val1', 'Val2') |

### Group By

Groups the result set by one or more columns. It is used in combination with aggregate functions like `COUNT`, `SUM`, `AVG`, `MIN`, and `MAX` to perform calculations on the grouped data.

```sql
-- given
+--------------+-------------+----------+
| CustomerName | OrderDate   | Amount   |
+--------------+-------------+----------+
| Alice        | 2023-10-01  | 100.00   |
| Bob          | 2023-10-02  | 75.00    |
| Alice        | 2023-10-03  | 50.00    |
| Carol        | 2023-10-01  | 200.00   |
| Bob          | 2023-10-02  | 90.00    |
+--------------+-------------+----------+

SELECT CustomerName, SUM(Amount) AS TotalAmount
FROM Orders
GROUP BY CustomerName;

-- result
+--------------+--------------+
| CustomerName | TotalAmount  |
+--------------+--------------+
| Alice        | 150.00       |
| Bob          | 165.00       |
| Carol        | 200.00       |
+--------------+--------------+
```

### Joins

#### Inner Join

Returns only the matching rows from both tables
Non-matching rows from either table are excluded

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### Left Join (Same as Left Outer Join)
Returns all rows from the left table and the matching rows from the right table. Non-matching rows from the right table are excluded

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### Right Join (Same as Right Outer Join)

Returns all rows from the right table and the matching rows from the left table. Non-matching rows from the left table are excluded

 ```sql
 SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
RIGHT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

#### Full Join (Same as Full Outer Join)

Returns all rows from both tables, matching or non-matching
Where no match exists, `NULL` values are returned for missing columns

```sql
SELECT Customers.CustomerName, Orders.OrderID
FROM Customers
FULL JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
```

## Mysql

* autocommit by default is `on`. use `set autocommit = off` to turn it off.