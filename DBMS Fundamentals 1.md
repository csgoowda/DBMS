# Day 5 – DBMS Fundamentals

⚠️ DBMS is one of the most asked subjects in placements.

Today focus on:

* Database
* DBMS
* RDBMS
* Keys
* Schema
* Constraints
* ER Model

---

# 1. What is DBMS?

### Definition

DBMS (Database Management System) is software used to store, manage, and retrieve data efficiently.

### Examples

* MySQL
* PostgreSQL
* Oracle
* SQL Server

### Interview Answer

> DBMS is software that helps users create, store, retrieve, and manage data efficiently.

---

# 2. What is a Database?

### Definition

A database is an organized collection of related data.

### Example

Student Table

| ID | Name  |
| -- | ----- |
| 1  | Ram   |
| 2  | Shyam |

This table is stored inside a database.

### Interview Answer

> A database is a collection of related data organized for easy access and management.

---

# 3. What is RDBMS?

### Definition

RDBMS (Relational Database Management System) stores data in tables and maintains relationships between them.

### Example

Student Table

| StudentID | Name |
| --------- | ---- |
| 1         | Ram  |

Department Table

| StudentID | Dept |
| --------- | ---- |
| 1         | ISE  |

Relationship exists using StudentID.

### Interview Answer

> RDBMS stores data in tables and uses relationships between tables.

---

# DBMS vs RDBMS

| DBMS                     | RDBMS                    |
| ------------------------ | ------------------------ |
| Stores data              | Stores data in tables    |
| No relationship required | Relationships maintained |
| Less secure              | More secure              |
| Example: File System     | Example: MySQL           |

---

# 4. What is a Table?

### Definition

A table is a collection of rows and columns.

### Example

| ID | Name  |
| -- | ----- |
| 1  | Ram   |
| 2  | Shyam |

---

# 5. What is a Row?

### Definition

A row represents one record.

Example:

```text
1  Ram
```

One row = one student.

---

# 6. What is a Column?

### Definition

A column represents an attribute.

Example:

```text
ID
Name
```

---

# 7. What is Schema?

### Definition

Schema is the structure/design of a database.

### Example

```sql
Student(
   ID INT,
   Name VARCHAR(50)
)
```

### Interview Answer

> Schema defines the logical structure of a database.

---

# 8. What is a Constraint?

### Definition

Rules applied on table columns.

### Purpose

Maintain data integrity.

---

# Types of Constraints

## NOT NULL

Value cannot be empty.

```sql
Name VARCHAR(50) NOT NULL
```

---

## UNIQUE

No duplicate values.

```sql
Email VARCHAR(50) UNIQUE
```

---

## PRIMARY KEY

Uniquely identifies each row.

```sql
ID INT PRIMARY KEY
```

---

## FOREIGN KEY

Creates relationship between tables.

```sql
FOREIGN KEY(StudentID)
```

---

## CHECK

Validates condition.

```sql
Age INT CHECK(Age > 18)
```

---

## DEFAULT

Provides default value.

```sql
Country VARCHAR(20) DEFAULT 'India'
```

---

# 9. Keys in DBMS

Very Important Topic.

---

## Primary Key

### Definition

Uniquely identifies each record.

### Properties

* Unique
* Not NULL

Example:

| ID | Name  |
| -- | ----- |
| 1  | Ram   |
| 2  | Shyam |

ID is Primary Key.

---

## Foreign Key

### Definition

A key used to establish relationships between tables.

### Interview Answer

> A foreign key references the primary key of another table.

---

## Candidate Key

### Definition

A column that can become a primary key.

Example:

| ID | Email                                 |
| -- | ------------------------------------- |
| 1  | [abc@gmail.com](mailto:abc@gmail.com) |

Both ID and Email can uniquely identify records.

---

## Alternate Key

Candidate key not selected as primary key.

---

## Super Key

Any attribute set that uniquely identifies rows.

---

## Composite Key

Combination of multiple columns.

Example:

```text
StudentID + CourseID
```

---

# Primary Key vs Foreign Key

| Primary Key                | Foreign Key              |
| -------------------------- | ------------------------ |
| Uniquely identifies record | References another table |
| Cannot be NULL             | Can be NULL              |
| One per table              | Multiple possible        |

---

# 10. ER Model

### Definition

ER (Entity Relationship) Model is used to design databases visually.

---

## Components

### Entity

Real-world object.

Examples:

* Student
* Employee
* Course

---

### Attribute

Property of entity.

Student:

* Name
* Age
* ID

---

### Relationship

Association between entities.

Example:

```text
Student ---- Studies ---- Course
```

---

# Easy Interview Questions

### 1. What is DBMS?

### 2. What is Database?

### 3. What is RDBMS?

### 4. What is a Table?

### 5. What is a Schema?

### 6. What is a Constraint?

### 7. What is Primary Key?

### 8. What is Foreign Key?

---

# Medium Questions

### 9. DBMS vs RDBMS?

### 10. Primary Key vs Foreign Key?

### 11. Types of Constraints?

### 12. Types of Keys?

### 13. What is Candidate Key?

### 14. What is Composite Key?

---

# Hard Questions

### 15. Candidate Key vs Primary Key?

### 16. Super Key vs Candidate Key?

### 17. Why do we need Foreign Keys?

### 18. What is Data Integrity?

### 19. What is ER Model?

### 20. What are Entities and Attributes?

---

# End of Day 5 Target

You should confidently answer:

✅ What is DBMS?

✅ DBMS vs RDBMS

✅ Primary Key vs Foreign Key

✅ Candidate Key

✅ Composite Key

✅ Schema

✅ Constraints

✅ ER Model

Tomorrow (Day 6): **SQL Fundamentals**

* SELECT
* WHERE
* ORDER BY
* GROUP BY
* HAVING
* INSERT
* UPDATE
* DELETE
* Most asked SQL interview questions.
