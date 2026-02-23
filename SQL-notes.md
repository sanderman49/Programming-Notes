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


