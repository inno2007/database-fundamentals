# Advanced SQL: Aggregates, GROUP BY, HAVING, and Subqueries

This section builds on SQL basics and introduces tools to summarize and analyze data across groups, along with nested queries and more advanced filtering.

---

## 1. Aggregate Functions

Aggregate functions summarize multiple values into a single result.

| Function | Description              |
|----------|--------------------------|
| `SUM()`  | Total of a column        |
| `AVG()`  | Average value            |
| `MIN()`  | Smallest value           |
| `MAX()`  | Largest value            |
| `COUNT()`| Number of rows/values    |

### Example

```sql
SELECT AVG(Salary) AS avg_salary
FROM Employee;
```

---

## 2. GROUP BY Clause

Used to group rows that share a common value so that aggregate functions can be applied to each group.

### Syntax

```sql
SELECT column, AGG_FUNC(column2)
FROM table
GROUP BY column;
```

### Example

```sql
SELECT branch_id, COUNT(*) AS num_customers
FROM customers
GROUP BY branch_id;
```

---

## 3. HAVING Clause

Filters groups created by `GROUP BY`. It works like `WHERE`, but is applied **after grouping**.

### Example

```sql
SELECT branch_id, AVG(salary) AS avg_salary
FROM employees
GROUP BY branch_id
HAVING AVG(salary) > 60000;
```

---

## 4. Using Aliases

Aliases rename columns or tables for clarity.

```sql
SELECT s.name AS student_name, e.grade AS final_grade
FROM students AS s
JOIN exams AS e ON s.id = e.student_id;
```

---

## 5. Subqueries (Nested Queries)

A **subquery** is a query inside another query. It can be used:

- In a `WHERE` clause
- In a `FROM` clause
- In `SELECT` for comparison

### Example: Using WHERE

```sql
SELECT name
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

This returns employees earning above average.

---

### Example: In FROM Clause (Derived Table)

```sql
SELECT dept, avg_sal
FROM (
    SELECT department AS dept, AVG(salary) AS avg_sal
    FROM employees
    GROUP BY department
) AS dept_summary
WHERE avg_sal > 50000;
```

---

### 6. IN, ANY, and ALL in Subqueries

```sql
-- Use IN
SELECT name
FROM students
WHERE id IN (
    SELECT student_id
    FROM enrollments
    WHERE course_id = 1001
);
```

---

## 7. EXISTS vs. IN

- `EXISTS`: Returns true if the subquery returns at least one row.
- Often faster than `IN` for large datasets.

```sql
SELECT name
FROM customers c
WHERE EXISTS (
    SELECT 1 FROM orders o WHERE o.customer_id = c.customer_id
);
```

---

## Summary

| Feature     | Use Case                                   |
|-------------|--------------------------------------------|
| `GROUP BY`  | Organize results into groups               |
| `HAVING`    | Filter results **after** grouping          |
| `SUBQUERIES`| Use query results within other queries     |
| `ALIAS`     | Rename columns or tables for readability   |
