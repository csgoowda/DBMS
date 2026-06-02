# Day 5 – DBMS Fundamentals (Complete Interview Notes)

## 1. What is Data?

Data is a collection of raw facts and figures.

### Example

```text
Chethan
22
Mysore
```

These are raw facts, so they are called data.

---

## 2. What is a Database?

A database is an organized collection of related data.

### Real-Life Example

College Database:

| USN | Name    | Branch |
| --- | ------- | ------ |
| 101 | Chethan | ISE    |
| 102 | Rahul   | CSE    |

Instead of storing student details in separate files, all data is stored together in a database.

### Why Database?

* Easy storage
* Easy retrieval
* Reduced redundancy
* Better security

---

## 3. What is DBMS?

DBMS stands for Database Management System.

It is software that helps users create, store, update, delete, and retrieve data from a database.

### Examples

* MySQL
* PostgreSQL
* Oracle
* SQL Server

### Real-World Example

When you use:

* Instagram
* WhatsApp
* College ERP

all your information is stored and managed using a DBMS.

### Functions of DBMS

1. Data Storage
2. Data Retrieval
3. Data Security
4. Data Backup
5. Data Integrity
6. Multi-user Access

---

## 4. Why Do We Need DBMS?

Before DBMS, data was stored in files.

Problems:

### Data Redundancy

Same data stored multiple times.

### Data Inconsistency

Different values in different files.

### Security Problems

Anyone could access files.

### Difficult Retrieval

Finding data was slow.

DBMS solves all these problems.

---

# File System vs DBMS

| File System         | DBMS                    |
| ------------------- | ----------------------- |
| High redundancy     | Low redundancy          |
| Less security       | High security           |
| Difficult retrieval | Easy retrieval          |
| No relationship     | Relationships supported |
| Manual management   | Automated management    |

---

## 5. What is RDBMS?

RDBMS stands for Relational Database Management System.

It stores data in the form of tables and maintains relationships between tables.

### Example

Student Table

| StudentID | Name    |
| --------- | ------- |
| 1         | Chethan |

Department Table

| StudentID | Department |
| --------- | ---------- |
| 1         | ISE        |

Relationship created using StudentID.

### Examples

* MySQL
* PostgreSQL
* Oracle

---

# DBMS vs RDBMS

| DBMS                   | RDBMS                    |
| ---------------------- | ------------------------ |
| Stores data            | Stores data in tables    |
| No relationship needed | Relationships maintained |
| Less secure            | More secure              |
| Smaller systems        | Large systems            |

---

# 6. What is a Table?

A table is a collection of rows and columns.

Example:

| ID | Name    | Age |
| -- | ------- | --- |
| 1  | Chethan | 22  |
| 2  | Rahul   | 21  |

---

## 7. What is a Row?

A row represents a single record.

Example:

| ID | Name    |
| -- | ------- |
| 1  | Chethan |

This entire line is one row.

---

## 8. What is a Column?

A column represents an attribute.

Example:

| ID | Name | Age |

ID, Name, and Age are columns.

---

## 9. What is Schema?

Schema is the blueprint or structure of a database.

### Example

```sql
Student(
   ID INT,
   Name VARCHAR(50),
   Age INT
)
```

This defines how the table should look.

### Real-Life Example

House Plan = Schema

House = Database

---

# 10. What are Constraints?

Constraints are rules applied to columns to maintain correct data.

---

## NOT NULL

Column cannot contain NULL values.

```sql
Name VARCHAR(50) NOT NULL
```

---

## UNIQUE

No duplicate values allowed.

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

Checks conditions.

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

# 11. Keys in DBMS

Keys are used to identify records and create relationships.

---

## Primary Key

### Definition

Uniquely identifies each record.

### Properties

* Unique
* Cannot be NULL

Example:

| ID | Name    |
| -- | ------- |
| 1  | Chethan |
| 2  | Rahul   |

ID is Primary Key.

---

## Foreign Key

### Definition

A column that references the Primary Key of another table.

Example:

Student Table

| StudentID | Name    |
| --------- | ------- |
| 1         | Chethan |

Department Table

| StudentID | Department |
| --------- | ---------- |
| 1         | ISE        |

StudentID is a Foreign Key.

---

## Candidate Key

Keys that can uniquely identify records.

Example:

| ID | Email                                 |
| -- | ------------------------------------- |
| 1  | [abc@gmail.com](mailto:abc@gmail.com) |

Both ID and Email can uniquely identify records.

Hence both are Candidate Keys.

---

## Alternate Key

Candidate Key not selected as Primary Key.

Example:

Primary Key = ID

Alternate Key = Email

---

## Composite Key

Combination of multiple columns.

Example:

```text
StudentID + CourseID
```

Together they uniquely identify a record.

---

## Super Key

Any set of attributes that uniquely identifies a row.

Example:

```text
ID
(ID + Name)
(ID + Name + Age)
```

All are Super Keys.

---

# Super Key vs Candidate Key

| Super Key                    | Candidate Key      |
| ---------------------------- | ------------------ |
| May contain extra attributes | Minimal attributes |
| Not optimized                | Optimized          |
| Many possible                | Few possible       |

---

# Candidate Key vs Primary Key

| Candidate Key          | Primary Key            |
| ---------------------- | ---------------------- |
| Can become Primary Key | Selected Candidate Key |
| Multiple possible      | Only one selected      |

---

# Primary Key vs Foreign Key

| Primary Key                 | Foreign Key          |
| --------------------------- | -------------------- |
| Uniquely identifies records | Creates relationship |
| Cannot be NULL              | Can be NULL          |
| One per table               | Multiple allowed     |

---

# 12. ER Model (Entity Relationship Model)

Used for database design.

Before creating tables, we draw an ER diagram.

---

## Entity

Real-world object.

Examples:

* Student
* Employee
* Course

---

## Attribute

Properties of an entity.

Student:

* Name
* Age
* USN

---

## Relationship

Connection between entities.

Example:

```text
Student ------ Studies ------ Course
```

Student and Course are connected.

---

# Data Integrity

Data Integrity means data remains:

* Accurate
* Consistent
* Reliable

### Example

If StudentID = 101 exists in Student table,

Foreign Key should not allow StudentID = 999 in another table.

This maintains integrity.

---

# Interviewer's Favorite Questions

### Must Know

1. What is DBMS?
2. Why DBMS over File System?
3. DBMS vs RDBMS?
4. What is a Schema?
5. What is a Constraint?
6. Primary Key vs Foreign Key?
7. Candidate Key vs Primary Key?
8. Super Key vs Candidate Key?
9. What is Data Integrity?
10. What is ER Model?

If you understand these concepts deeply, Day 6 (SQL) becomes much easier because SQL operates on these tables, keys, and relationships.
