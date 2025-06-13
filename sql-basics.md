# SQL Basics: SELECT, WHERE, ORDER BY, and Filtering

This section introduces the core SQL commands used to retrieve, filter, sort, and search data in relational databases.

---

## 1. SELECT Statement

The `SELECT` command is used to retrieve data from tables.

### Syntax
```sql
SELECT column1, column2 FROM table_name;
```

### Examples
```sql
-- Retrieve all columns from the students table
SELECT * FROM students;

-- Retrieve only student_number and student_name
SELECT student_number, student_name FROM students;
```

---

## 2. DISTINCT Clause

Removes duplicate values from the output.

```sql
SELECT DISTINCT flower FROM orders;
```

---

## 3. WHERE Clause

Used to filter rows based on a condition.

### Syntax
```sql
SELECT column1, column2 
FROM table_name 
WHERE condition;
```

### Comparison Operators

| Operator | Meaning          |
|----------|------------------|
| =        | Equal to         |
| !=       | Not equal to     |
| >, <     | Greater/Less than|
| >=, <=   | Greater/Less than or equal |

### Logical Operators

| Operator | Use                                    |
|----------|----------------------------------------|
| AND      | All conditions must be true            |
| OR       | At least one condition must be true    |
| NOT      | Negates a condition                    |

```sql
-- Students with cost > 7 and supplier is 'Floral Supplies'
SELECT flower, cost 
FROM flowers 
WHERE wholesaler = 'Floral Supplies' AND cost > 7;
```

---

## 4. Handling NULL

NULL represents unknown or missing data.

```sql
-- Get students with no home phone number
SELECT student_number, student_name 
FROM students 
WHERE HomePhoneNum IS NULL;
```

---

## 5. ORDER BY Clause

Used to sort query results.

### Syntax
```sql
SELECT column1, column2 
FROM table_name 
ORDER BY column1 [ASC|DESC];
```

### Example
```sql
-- Sort by name ascending, then student_number descending
SELECT student_name, student_number 
FROM students 
ORDER BY student_name ASC, student_number DESC;
```

You can also sort by column position:
```sql
SELECT * FROM orders ORDER BY 1;
```

---

## 6. LIKE Clause

Used for pattern matching.

| Wildcard | Meaning                     |
|----------|-----------------------------|
| %        | Zero or more characters     |
| _        | A single character          |
| [ ]      | One character from a set    |
| [-]      | Character range             |

### Examples
```sql
-- Ends with "engineer"
WHERE job LIKE '%engineer'

-- Begins with "engineer"
WHERE job LIKE 'engineer%'

-- Contains "engineer"
WHERE job LIKE '%engineer%'

-- Any 3-letter word starting with "C" and ending in "t"
WHERE word LIKE 'C_t'
```

---

## 7. IN and NOT IN Operators

Used to filter values from a list.

```sql
-- Using IN
SELECT * FROM students 
WHERE color IN ('Pink', 'Blue', 'Green');

-- Using NOT IN
SELECT * FROM students 
WHERE color NOT IN ('Pink', 'Blue', 'Green');
```

---

## 8. BETWEEN Operator

Filters values within a specified range (inclusive).

```sql
-- Salary between 50k and 100k
WHERE salary BETWEEN 50000 AND 100000;
```

---

## 9. Best Practices

- Use parentheses when combining `AND` and `OR` to avoid logic errors.
```sql
-- Correct
WHERE address LIKE '%A%' AND (Shop LIKE 'H%' OR Shop LIKE 'S%')
```

- Avoid `SELECT *` unless necessary. Always prefer selecting only required columns.

---

## Summary

| Concept     | Key Command           |
|-------------|------------------------|
| Retrieve    | SELECT                 |
| Filter      | WHERE, LIKE, IN        |
| Sort        | ORDER BY               |
| Match Range | BETWEEN                |
| Exclude     | NOT, IS NOT NULL       |
| Deduplicate | DISTINCT               |

