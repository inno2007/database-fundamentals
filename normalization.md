# Normalization in Relational Databases

**Normalization** is a design technique that organizes data in relational databases to reduce redundancy and improve data integrity. It involves breaking down large tables into smaller, well-structured tables.

---

## 0NF (Unnormalized Form)

- The starting point of data structure.
- Data may include:
  - Multivalued attributes
  - Repeating groups
  - Derived attributes (e.g., total_price)

---

## 1NF (First Normal Form)

A relation is in **1NF** if:

- All attributes are atomic (single value per cell).
- There are no repeating groups or multivalued fields.
- Derived values are removed (e.g., `Age`, `Total`).

### Example:

| EmpID | Name   | Skills         |
|-------|--------|----------------|
| 101   | John   | Java, Python   |

🔁 After conversion to 1NF:

| EmpID | Name   | Skill   |
|-------|--------|---------|
| 101   | John   | Java    |
| 101   | John   | Python  |

---

## 2NF (Second Normal Form)

A relation is in **2NF** if:

- It is already in 1NF.
- All **non-key attributes** are fully functionally dependent on the **entire primary key**.
- No **partial dependencies** exist.

### Partial Dependency Example:

Relation: `Payment(EmpNum, Date, Rate, Hours, Pay, EName)`

FDs:
- EmpNum, Date → Pay
- EmpNum → EName  ❌ Partial Dependency

🔁 Solution:

- Employee(EmpNum, EName)
- Payment(EmpNum, Date, Rate, Hours, Pay)

---

## 3NF (Third Normal Form)

A relation is in **3NF** if:

- It is already in 2NF.
- It has **no transitive dependencies**.

### Transitive Dependency Example:

Relation: `Staff(StaffName, RoomNum, Department)`

FDs:
- StaffName → RoomNum
- RoomNum → Department  ❌ Transitive

🔁 Solution:

- Staff(StaffName, RoomNum)
- Room(RoomNum, Department)

---

## BCNF (Boyce-Codd Normal Form)

A relation is in **BCNF** if:

- It is already in 3NF.
- Every determinant is a candidate key.

### BCNF Violation Example:

Relation: `StudentSubject(StudentName, SubjectName, SubjectLecturer)`

FD:
- SubjectLecturer → SubjectName

But `SubjectLecturer` is not a candidate key → BCNF violation.

🔁 Solution:

- StudentSubject(StudentName, SubjectLecturer)
- Lecturer(SubjectLecturer, SubjectName)

---

## Insert, Update, and Delete Anomalies

| Anomaly   | Description |
|-----------|-------------|
| **Insert**  | Cannot add new data due to missing unrelated data (e.g. must add an order just to add a customer) |
| **Update**  | Must update in multiple rows to avoid inconsistency |
| **Delete**  | Deleting one row removes unintended information |

---

## Summary

Normalization ensures that:

- Data is stored once.
- Each table has a clear, focused purpose.
- Dependencies are properly managed across relations.
- Your design supports easy querying and safe updates.

Progression:

```
0NF → 1NF → 2NF → 3NF → BCNF
```

Most industry databases normalize up to **BCNF**. Higher forms (4NF, 5NF) are rare and only used for advanced modeling.

