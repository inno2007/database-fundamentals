# SQL Joins and Table Relationships

This section explains how to combine data from multiple tables using SQL JOINs. You'll learn how INNER JOINs, OUTER JOINs, and self-joins are used to represent entity relationships in queries.

---

## 1. What is a Join?

A **JOIN** allows you to retrieve data from two or more related tables based on a condition — typically using **primary key–foreign key relationships**.

### Common Join Types:

| Join Type     | Description                                              |
|---------------|----------------------------------------------------------|
| **INNER JOIN**| Returns only rows where there is a match in both tables. |
| **LEFT JOIN** | Returns all rows from the left table, and matched rows from the right. |
| **RIGHT JOIN**| Returns all rows from the right table, and matched rows from the left. |
| **FULL JOIN** | Returns all rows from both tables (only in some DBMSs).  |
| **SELF JOIN** | A table is joined with itself.                          |

---

## 2. INNER JOIN

Returns only rows where the join condition is true.

### Example:

```sql
SELECT s.student_name, e.course_name
FROM students s
INNER JOIN enrollments e ON s.student_id = e.student_id;
```

---

## 3. Aliases for Simplicity

Using aliases helps shorten query syntax:

```sql
SELECT s.name, e.course
FROM students AS s
JOIN enrollments AS e ON s.student_id = e.student_id;
```

You can also use implicit joins:

```sql
SELECT s.name, e.course
FROM students s, enrollments e
WHERE s.student_id = e.student_id;
```

But **explicit JOIN** is preferred for clarity.

---

## 4. Joining More Than Two Tables

You can join three or more tables as long as each join condition is valid:

```sql
SELECT o.order_id, c.customer_name, p.product_name
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id
JOIN products p ON o.product_id = p.product_id;
```

---

## 5. LEFT and RIGHT JOIN

### LEFT JOIN

Returns all rows from the left table and matched rows from the right table.

```sql
SELECT s.name, e.course_id
FROM students s
LEFT JOIN enrollments e ON s.student_id = e.student_id;
```

If a student isn’t enrolled in any course, their name still appears with NULLs.

### RIGHT JOIN

Same as LEFT JOIN but reversed.

---

## 6. SELF JOIN

Used when a table references itself — such as in hierarchical structures.

### Example: Employee supervises other employees

```sql
SELECT e1.name AS employee, e2.name AS supervisor
FROM employees e1
JOIN employees e2 ON e1.supervisor_id = e2.employee_id;
```

---

## 7. Join Performance Tips

- Index foreign keys for faster joins.
- Always specify join conditions.
- Avoid unnecessary cross joins unless intentional.

---

## Summary

| Join Type     | Use Case                                      |
|---------------|-----------------------------------------------|
| INNER JOIN    | Combine matching rows                         |
| LEFT JOIN     | Include all from left, even if no match       |
| RIGHT JOIN    | Include all from right, even if no match      |
| SELF JOIN     | Compare rows within the same table            |
