# SQL Date and Time Functions

SQL provides various functions and operations for working with **date and time values**. These are commonly used for filtering, formatting, and analyzing time-based data.

---

## 1. Storing Dates

Dates are usually stored using the `DATE`, `DATETIME`, or `TIMESTAMP` data types.

```sql
CREATE TABLE Events (
    event_id INT,
    event_name VARCHAR(100),
    event_date DATE
);
```

---

## 2. GETDATE() – Current Date and Time

```sql
SELECT GETDATE();
```

Returns the current system date and time (e.g., `2025-06-13 19:21:00`).

---

## 3. Extracting Year, Month, Day

You can extract parts of a date using built-in functions:

```sql
SELECT YEAR(GETDATE());  -- Returns 2025
SELECT MONTH(GETDATE()); -- Returns 6
SELECT DAY(GETDATE());   -- Returns 13
```

Apply to column values:

```sql
SELECT name
FROM employees
WHERE YEAR(join_date) = 2024;
```

---

## 4. Filtering with BETWEEN

`BETWEEN` is often used to select records within a date range.

### Example:

```sql
SELECT *
FROM orders
WHERE order_date BETWEEN '2024-01-01' AND '2024-12-31';
```

**Tip**: Always use the format `'YYYY-MM-DD'` for compatibility.

---

## 5. Date Comparison with Operators

You can also use `<`, `>`, `=` with date columns:

```sql
SELECT *
FROM events
WHERE event_date < '2023-12-31';
```

---

## 6. Formatting Dates

Formatting functions vary by SQL dialect (e.g., SQL Server, MySQL, PostgreSQL).

### SQL Server Example:

```sql
SELECT FORMAT(GETDATE(), 'yyyy-MM-dd');
```

---

## 7. Calculating Date Differences

Some systems support functions to find the difference between two dates.

### SQL Server:

```sql
SELECT DATEDIFF(DAY, '2024-01-01', GETDATE()); -- Days between
```

---

## 8. Adding/Subtracting Dates

```sql
SELECT DATEADD(DAY, 30, GETDATE());  -- 30 days from now
SELECT DATEADD(YEAR, -1, GETDATE()); -- 1 year ago
```

---

## 9. Filtering Records by Month or Year Only

```sql
SELECT *
FROM invoices
WHERE MONTH(invoice_date) = 6 AND YEAR(invoice_date) = 2025;
```

---

## Summary

| Function        | Description                                 |
|-----------------|---------------------------------------------|
| `GETDATE()`     | Current date/time                           |
| `YEAR(date)`    | Extract year from date                      |
| `BETWEEN`       | Range-based filtering                       |
| `<`, `>`, `=`   | Direct date comparison                      |
| `DATEDIFF()`    | Difference in days/months/years (SQL Server)|
| `DATEADD()`     | Add/subtract date intervals                 |

