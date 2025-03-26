Best practices to enhance SQL query performance and database efficiency.

## 1. Use Indexes Effectively

- Create indexes on columns used in WHERE, JOIN, and ORDER BY.

```sql
CREATE INDEX idx_employee_salary ON employees(salary);
```

- Avoid indexing low-cardinality columns (e.g., boolean fields).

## 2. Avoid SELECT *

- Fetch only required columns for better performance.
```sql
SELECT id, name FROM employees;
```

## 3. Optimize Joins

- Use INNER JOIN when you only need matching rows.

- Ensure joined columns are indexed.

## 4. Use EXISTS Instead of IN

- EXISTS is faster for subqueries returning large datasets.
```sql
SELECT *
FROM employees e
WHERE EXISTS (
    SELECT 1 FROM departments d WHERE d.id = e.department_id
);
```

## 5. Avoid DISTINCT for Duplicate Removal

- Prefer GROUP BY if you also need aggregation.
```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```

## 6. Analyze Query Execution Plan

- Use EXPLAIN to understand and optimize query performance.
```sql
EXPLAIN SELECT * FROM employees WHERE id = 1001;
```

## 

EXPLAIN SELECT * FROM employees WHERE id = 1001;

7. Partition Large Tables

- Partitioning helps with query performance on massive datasets.
```sql
CREATE TABLE orders (
    id INT,
    customer_id INT,
    order_date DATE
)
PARTITION BY RANGE (order_date);
7. Partition Large Tables

Partitioning helps with query performance on massive datasets.
