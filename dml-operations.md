# SQL DML: INSERT, UPDATE, DELETE, and Restore

This section covers **Data Manipulation Language (DML)** operations in SQL — the commands used to add, change, and remove data from tables.

---

## 1. INSERT Statement

Adds new rows to a table.

### Syntax

```sql
INSERT INTO table_name (column1, column2)
VALUES (value1, value2);
```

### Example

```sql
INSERT INTO Students (StudentID, Name, Age)
VALUES (102, 'Sachio', 20);
```

If all columns are filled in order, you can omit column names:

```sql
INSERT INTO Students
VALUES (103, 'Inno', 19);
```

---

## 2. UPDATE Statement

Changes existing data in one or more rows.

### Syntax

```sql
UPDATE table_name
SET column1 = value1, column2 = value2
WHERE condition;
```

### Example

```sql
UPDATE Students
SET Age = 21
WHERE StudentID = 102;
```

**Important**: Always use a `WHERE` clause unless you want to update all rows.

---

## 3. DELETE Statement

Removes one or more rows from a table.

### Syntax

```sql
DELETE FROM table_name
WHERE condition;
```

### Example

```sql
DELETE FROM Students
WHERE StudentID = 103;
```

To delete **all rows**:

```sql
DELETE FROM Students;
```

⚠️ Be cautious — this clears the table but keeps its structure.

---

## 4. Truncate vs Delete

| Command  | Effect                                   |
|----------|------------------------------------------|
| `DELETE` | Removes selected rows (can use WHERE)    |
| `TRUNCATE` | Removes all rows, cannot be rolled back|

---

## 5. Backup and Restore Concepts

While not SQL commands, many systems support manual or automatic **backups**.

- Backups store full or partial copies of a database.
- Restore brings back the data after deletion or failure.

---

## 6. Transaction Control (if supported)

Some systems support transactions for grouped operations.

| Command     | Description                                        |
|-------------|----------------------------------------------------|
| `BEGIN`     | Starts a transaction                               |
| `COMMIT`    | Saves all changes permanently                      |
| `ROLLBACK`  | Cancels changes made since the last `BEGIN`        |

### Example:

```sql
BEGIN;

UPDATE Accounts SET balance = balance - 100 WHERE id = 1;
UPDATE Accounts SET balance = balance + 100 WHERE id = 2;

COMMIT;
```

If something goes wrong:

```sql
ROLLBACK;
```

---

## Summary

| Command | Use                             |
|---------|----------------------------------|
| `INSERT` | Add new rows to a table         |
| `UPDATE` | Modify existing row values      |
| `DELETE` | Remove specific rows            |
| `TRUNCATE` | Clear table contents entirely  |
| `COMMIT / ROLLBACK` | Apply or revert changes in transactions |
