# DB Management
## Create Database
```sql
create database my_db;
```
## Use Database
`PSQL` shorthand:
```psql
\c my_database
```

Otherwise:
```sql
use my_database
```

## Create Table
```sql
create table table_name (
    column_name data_type constraint,
    id serial,
    name varchar(255),
    ... etc
);
```

# Insert
You can insert by optionally specifying the column names to insert into:
```sql
INSERT INTO dogs (name, age)
VALUES ('Gino', 3);
```
or (this will create an error cause of the `id` column):
```sql
INSERT INTO dogs
VALUES ('Gino', 3);
```
## Multiple records
```sql
INSERT INTO dogs (name, age)
VALUES
  ('Gino', 3),
  ('Nora', 2);
```

# PostgreSQL Types
## Numeric
- `Integer` - 32-bit signed.
- `Smallint`
- `Bigint`
- `Serial` - Un-nullable `integer` with auto-increment.
- `Float`
- `Decimal`

## Time
- `Timestamp` - Both date and time. Also:
    - `Timestamp with time zone` - Stores the timezone too.
- `Date`
- `Time`

## Character/String
- `Char`
- `Varchar(max_length)` - String with max length.
- `Text` - String of any length.

## Unicode
- `Ntext`
- `Nvarchar`

## Other
- `Binary`
- `Boolean`
- `XML`
- `Table`
- And more...

# SQL Statements
- `SELECT` - extracts data from a database
- `UPDATE` - updates data in a database
- `DELETE` - deletes data from a database
- `INSERT INTO` - inserts new data into a database
- `CREATE DATABASE` - creates a new database
- `ALTER DATABASE` - modifies a database
- `CREATE TABLE` - creates a new table
- `ALTER TABLE` - modifies a table
- `DROP TABLE` - deletes a table
- `CREATE INDEX` - creates an index (search key)
- `DROP INDEX` - deletes an index

# Select
```sql
SELECT column1, column2, ...
FROM table_name;
```

## Wildcard
```sql
SELECT *
FROM table_name;
```

# Select Distinct
returns only unique values
```sql
SELECT DISTINCT column1, column2, ...
FROM table_name;
```

# Where
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition;
```
Example:
```sql
SELECT * FROM Customers
WHERE Country='Mexico';
```
When searching for numbers don't put them in quotes.

## Operators
| Operator | Description                                                                 |
|----------|-----------------------------------------------------------------------------|
| =        | Equal                                                                       |
| >        | Greater than                                                                |
| <        | Less than                                                                   |
| >=       | Greater than or equal                                                       |
| <=       | Less than or equal                                                          |
| <>       | Not equal. Note: In some versions of SQL this operator may be written as != |
| BETWEEN  | Between a certain range                                                     |
| LIKE     | Search for a pattern                                                        |
| IN       | To specify multiple possible values for a column                            |


# Order By
```sql
SELECT column1, column2, ...
FROM table_name
ORDER BY column1, column2, ... ASC|DESC;
```

Specifying several operators will allow for an secondary column to sort by.
You can also insert `ASC`|`DESC` after each column name to use different sorts on different columns.

# And
Used on the `WHERE` operator
```sql
SELECT column1, column2, ...
FROM table_name
WHERE condition1 AND condition2 AND condition3 ...;
```

# Joins
## Inner Join
Includes rows which match the join condition on both tables.
```sql
SELECT *
FROM products
INNER JOIN sales
  ON products.product_id = sales.product_id;
```
## Full outer join
Gets all rows from both tables (combines the data where it matches, has null in columns with no match)
```sql
SELECT *
FROM products
FULL OUTER JOIN sales
  ON products.product_id = sales.product_id;
```

## Left outer join
Gets all values on the left table and the matching information from the right table (otherwise the values for the right table are fulled with null).
```sql
SELECT *
FROM products
LEFT JOIN sales
  ON products.product_id = sales.product_id;
```

## Right outer join
Gets all values on the right table and the matching information from the left table (otherwise the values for the left table are fulled with null).
```sql
SELECT *
FROM products
RIGHT JOIN sales
  ON products.product_id = sales.product_id;
```

## Self join
Joins two copies of the same table

## Cross join
Joins every row of the first table with every row of the second table.

# Constraints
## Primary Key
```sql
CREATE TABLE students (
  student_id SERIAL PRIMARY KEY,
  name VARCHAR(100)
);
```

## Composite Primary Key
```sql
CREATE TABLE table_name (
  column1 data_type column_constraint,
  column2 data_type column_constraint,
  column3 data_type column_constraint,
  ...
  PRIMARY KEY (column1, column2)
);
```
## Foreign Key
```sql
CREATE TABLE customers (
  customer_id SERIAL PRIMARY KEY,
  first_name VARCHAR(100) NOT NULL,
  ...
);

CREATE TABLE orders (
  order_id SERIAL PRIMARY KEY,
  customer_id INTEGER,
  ...
  FOREIGN KEY (customer_id) REFERENCES customers(customer_id)
);
```

# Subqueries
A nested query, usually denoted with `()` syntax, although this syntax is not fixed:
```sql
SELECT column_name
FROM table_name
WHERE column_name expression operator 
   (SELECT column_name FROM table_name WHERE ...);
```

Can be used with `join`, `from`, `update`, `delete`, `where`, etc.

There are different types of subqueries:
## Single-row
Returns one value:
```sql
SELECT * FROM Employees
WHERE Salary = (SELECT MAX(Salary) FROM Employees);
```

## Mutli-row
Returns multiple values:
```sql
SELECT * FROM Employees
WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE Location = 'New York');
```

## Correlated
Depends on the outer query for its values
```sql
SELECT e.Name, e.Salary:
FROM Employees e
WHERE e.Salary > (SELECT AVG(Salary) 
                  FROM Employees 
                  WHERE DepartmentID = e.DepartmentID);
```
