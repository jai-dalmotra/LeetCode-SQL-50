A comprehensive cheat sheet covering essential SQL commands and concepts to quickly reference during problem-solving.

## 1. Basic SQL Commands
```sql
-- Select all columns from a table
SELECT * FROM table_name;

-- Select specific columns
SELECT column1, column2 FROM table_name;

-- Filter with WHERE
SELECT * FROM table_name WHERE column_name = 'value';

-- Sorting with ORDER BY
SELECT * FROM table_name ORDER BY column_name ASC;

-- Limiting results
SELECT * FROM table_name LIMIT 10;

```

## 2. Aggregate Functions
```
-- Common aggregates
SELECT COUNT(*) FROM table_name;
SELECT SUM(column_name) FROM table_name;
SELECT AVG(column_name) FROM table_name;
SELECT MAX(column_name) FROM table_name;
SELECT MIN(column_name) FROM table_name;

-- Grouping data
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name;

-- Filtering groups with HAVING
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING COUNT(*) > 1;
```

## 3. Joins
```
-- Inner Join (Only matching rows in both tables)
SELECT a.*, b.*
FROM tableA a
JOIN tableB b ON a.id = b.id;

-- Left Join (All rows from the left, matched rows from the right)
SELECT a.*, b.*
FROM tableA a
LEFT JOIN tableB b ON a.id = b.id;

-- Right Join (All rows from the right, matched rows from the left)
SELECT a.*, b.*
FROM tableA a
RIGHT JOIN tableB b ON a.id = b.id;

-- Full Outer Join (All rows from both tables)
SELECT a.*, b.*
FROM tableA a
FULL OUTER JOIN tableB b ON a.id = b.id;
```

## 4. Window Functions
```
-- Row Number
SELECT name, ROW_NUMBER() OVER (PARTITION BY department ORDER BY salary DESC) AS rank
FROM employees;

-- Running Total
SELECT name, SUM(salary) OVER (PARTITION BY department ORDER BY id) AS running_total
FROM employees;
```

## 5. Subqueries
```
-- Inline Subquery
SELECT name FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees);

-- Correlated Subquery
SELECT name FROM employees e
WHERE salary > (
    SELECT AVG(salary) FROM employees WHERE department_id = e.department_id
);
