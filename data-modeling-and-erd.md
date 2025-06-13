# Data Modeling and ER Diagrams (ERDs)

This topic covers how to design conceptual data models using ERDs (Entity Relationship Diagrams). It includes how to define entities, relationships, attributes, and their roles in database structure.

---

## 1. What is Data Modeling?

**Data modeling** is the process of visually representing the structure of a database at a high level before implementation.

- Conceptual: ER diagrams (entities, attributes, relationships)
- Logical: Relational model (tables, keys, constraints)
- Physical: Actual database schema and storage

---

## 2. Entity Relationship Diagram (ERD)

An **ERD** is a visual representation of entities and the relationships between them.

### Elements:
- **Entity**: An object (e.g. Student, Course)
- **Attribute**: A property of the entity (e.g. studentName)
- **Relationship**: A link between entities (e.g. Enrolls)

---

## 3. Attribute Types

| Type            | Description                                         | Notation        |
|-----------------|-----------------------------------------------------|-----------------|
| Simple          | Cannot be divided further (e.g. age)                | Regular name    |
| Composite       | Can be divided into subparts (e.g. full name)       | Uses parentheses ( ) |
| Multivalued     | Can have more than one value (e.g. phone numbers)   | Uses { }        |
| Derived         | Calculated from other attributes (e.g. age from DOB)| Uses [ ]        |

---

## 4. Cardinality and Modality

These define the **quantity** and **necessity** of relationships between entities.

- **Cardinality**: Maximum number of relationships (1:1, 1:M, M:N)
- **Modality**: Minimum number (0 = optional, 1 = mandatory)

### Visual Guide:

| Symbol      | Meaning              |
|-------------|----------------------|
| Circle      | Optional (0)         |
| Line        | Mandatory (1)        |
| Crow’s foot | Many (N)             |

Examples:

- 1:1 → A person has one passport
- 1:M → A customer can place many orders
- M:N → A student can enroll in many courses; a course has many students

---

## 5. Strong vs Weak Entities

| Type         | Description                                                           |
|--------------|-----------------------------------------------------------------------|
| **Strong**   | Exists independently, has its own primary key                         |
| **Weak**     | Depends on a strong entity, uses its key in combination as identifier |

**Weak entities** are connected to strong entities using **identifying relationships**.

> Example:  
> - Album (strong)  
> - Track (weak — must include AlbumID in its key)

---

## 6. Associative Entities

Used to **represent M:N relationships with attributes**.

> Example:
> - Employee completes many courses
> - A course has many employees enrolled
> - Certificate entity contains additional info (e.g. completion date)

This entity has:
- A **composite key** made from both primary keys (EmployeeID, CourseID)
- Possibly a surrogate key (CertificateID)

---

## 7. Relationship Degrees

| Degree    | Description                            | Example                        |
|-----------|----------------------------------------|--------------------------------|
| Unary     | Relationship within the same entity    | Employee supervises Employee   |
| Binary    | Between two entities                   | Student enrolls in Course      |
| Ternary   | Between three entities                 | Doctor treats Patient with Treatment |

---

## 8. Logical Design from ERD

Once the conceptual ERD is ready, it can be **transformed into a relational model**:

Steps:
1. Convert each entity to a table
2. Copy primary keys and attributes
3. Create foreign keys for relationships
4. Apply naming conventions
5. Ensure constraints and keys match relationships

---

## Summary

- ERDs help organize entities and define their relationships visually.
- Understanding attribute types, entity strength, and relationship degrees is key to modeling.
- Logical models are built on well-structured conceptual designs.
