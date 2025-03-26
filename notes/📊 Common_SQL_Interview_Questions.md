A curated collection of frequently asked SQL problems and their solution patterns.

## 1. Find the Second Highest Salary
```sql
SELECT MAX(salary) AS second_highest_salary
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

## 2. Find Duplicate Records
```sql
SELECT column_name, COUNT(*)
FROM table_name
GROUP BY column_name
HAVING COUNT(*) > 1;
```

## 3. Nth Highest Salary
```sql
WITH SalaryRank AS (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rank
    FROM employees
)
SELECT salary FROM SalaryRank
WHERE rank = 3;
```

## 4. Consecutive Records
```sql
SELECT id, score
FROM (
    SELECT id, score,
           LEAD(score) OVER (ORDER BY id) AS next_score,
           LAG(score) OVER (ORDER BY id) AS prev_score
    FROM scores
) t
WHERE score = next_score AND score = prev_score;
```

## 5. Median of a Column
```sql
WITH Median AS (
    SELECT value, ROW_NUMBER() OVER (ORDER BY value) AS rn,
                  COUNT(*) OVER () AS total
    FROM dataset
)
SELECT value
FROM Median
WHERE rn IN ((total + 1) / 2, (total + 2) / 2);
