# Database Constraints and Referential Integrity

This section covers database constraints that enforce rules on data. These rules ensure that the data stored is accurate, valid, and consistent. You’ll also learn how referential integrity governs relationships between tables.

---

## 1. What are Constraints?

A **constraint** is a rule applied to a column or table to ensure data integrity. It prevents invalid or inconsistent data from being entered or left in the system.

### Common Types of Constraints

| Type                  | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| **Domain Constraint** | Defines valid values for an attribute (e.g., data type, allowed range).     |
| **Entity Integrity**  | Requires that every table has a primary key, which must be unique & non-null. |
| **Referential Integrity** | Ensures that a foreign key matches a primary key in another table or is null. |

---

## 2. Entity Integrity

- Every table must have a **primary key**.
- Primary key:
  - Cannot contain NULL values
  - Must be unique
- Ensures that each record is uniquely identifiable.

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY,
    Name VARCHAR(50)
);
```

---

## 3. Foreign Keys and Referential Integrity

A **foreign key** is an attribute in one table that references the **primary key** in another.

```sql
CREATE TABLE Enrollments (
    StudentID INT,
    CourseID INT,
    FOREIGN KEY (StudentID) REFERENCES Students(StudentID)
);
```

Referential integrity ensures:
- All foreign key values in a child table must exist in the parent table.
- Or be NULL (if allowed).

---

## 4. Referential Integrity Actions

| Action     | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| **Restrict** | Prevent deletion of a parent row if a child exists. Must delete child first. |
| **Cascade**  | Deleting the parent row also deletes all child rows automatically.          |
| **Set Null** | Deleting the parent sets the child’s foreign key to NULL.                  |

### Example:

You try to delete this:

```sql
DELETE FROM Branch WHERE BranchID = 333333;
```

If:
- **RESTRICT**: You cannot delete unless all dependent rows in Customer are deleted first.
- **CASCADE**: All Customers with BranchID 333333 are deleted automatically.
- **SET NULL**: BranchID in Customer becomes NULL for those rows.

---

## 5. Adding Foreign Key Constraints

In SQL:

```sql
ALTER TABLE Orders
ADD CONSTRAINT fk_customer
FOREIGN KEY (CustomerID)
REFERENCES Customers(CustomerID);
```

In a **relational model**, the reference is added **on the child side**. A good rule:
- Use `*` to mark foreign keys.
- Then add a `REFERENCES` clause beneath the child relation.

---

## 6. Using Constraints to Define Cardinality

- The **more constrained side** is usually the “one” side.
  - Primary Key → More constrained
  - Composite Key → Less constrained
  - Foreign Key → Least constrained

→ This helps to determine which side is one-to-many or many-to-one in ERD.

---

## 7. Surrogate Keys

A **surrogate key** is a system-generated primary key used when:
- No natural key exists
- Natural key is long or volatile

Example:

```sql
CREATE TABLE Customer (
    CustomerID INT AUTO_INCREMENT PRIMARY KEY,
    TaxFileNumber VARCHAR(11)
);
```

---

## Summary

- Constraints enforce rules on data to ensure validity and consistency.
- Primary keys maintain uniqueness; foreign keys link tables.
- Referential integrity prevents orphaned rows and keeps data in sync.
- Proper constraint use supports normalization, ERD integrity, and safe data operations.

