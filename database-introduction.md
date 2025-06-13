# Introduction to Databases

This section introduces the purpose, structure, and types of databases. It also compares traditional file systems to database management systems (DBMS) and explains key concepts like data models and keys.

---

## What is a Database?

A **database** is an organized collection of data, typically stored and accessed electronically. It is designed to:

- Store large volumes of data efficiently
- Support fast access and retrieval
- Enforce data integrity and reduce redundancy

---

## DBMS (Database Management System)

A **DBMS** is software that allows users to define, manipulate, retrieve, and manage data in databases. Examples include:

- MySQL
- PostgreSQL
- SQL Server
- Oracle

### Functions of a DBMS

- Data storage and retrieval
- Transaction support
- Data security and access control
- Backup and recovery
- Data consistency and concurrency control

---

## File System vs. Database System

| Feature           | File System                       | Database System                   |
|------------------|------------------------------------|-----------------------------------|
| Data Redundancy  | High (duplicate files)             | Low (centralized data control)    |
| Integrity Checks | Manual                             | Enforced through rules/constraints|
| Access Control   | Limited                            | Role-based, query-level           |
| Data Sharing     | Difficult                          | Easily shared across apps/users   |
| Scalability      | Poor                               | High                              |

---

## Types of Databases

| Type               | Description |
|--------------------|-------------|
| **Hierarchical**   | Data stored in tree-like parent-child structure |
| **Network**        | Similar to hierarchical but allows many-to-many links |
| **Relational (RDBMS)** | Data stored in tables with rows and columns |
| **Object-Oriented**| Data stored as objects (like OOP classes) |
| **NoSQL**          | Non-relational; supports key-value, document, graph formats |

---

## Relational Database Basics

- Data is organized into **tables** (relations).
- Each table has **columns** (attributes) and **rows** (records).
- Tables are linked using **keys**.

### Primary Key

- Uniquely identifies each row in a table.
- Cannot be null.

```sql
CREATE TABLE Students (
    student_id INT PRIMARY KEY,
    name VARCHAR(100)
);
```

### Foreign Key

- References the primary key of another table to form relationships.

```sql
CREATE TABLE Enrollments (
    student_id INT,
    course_id INT,
    FOREIGN KEY (student_id) REFERENCES Students(student_id)
);
```

---

## Summary

- Databases solve many problems with traditional file-based systems.
- DBMS provides structure, consistency, and secure access.
- Relational databases use primary and foreign keys to manage structured data.
- Understanding database types and models is key to building efficient systems.

