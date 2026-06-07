# JOINs, Views, Stored Procedures & Triggers

This is the final and most practical DBMS topic.

Many interviewers ask:

> "Explain JOINs with examples."

or

> "Difference between View and Table?"

or

> "What is a Trigger?"

Let's understand them deeply.

---

# 1. Why Do We Need JOINs?

Suppose we have two tables.

## Student Table

| StudentID | Name    |
| --------- | ------- |
| 1         | Chethan |
| 2         | Rahul   |
| 3         | Anu     |

---

## Department Table

| StudentID | Department |
| --------- | ---------- |
| 1         | ISE        |
| 2         | CSE        |
| 4         | ECE        |

Notice:

```text
Student information → Table 1
Department information → Table 2
```

Now suppose we want:

```text
Chethan - ISE
Rahul - CSE
```

Information exists in different tables.

To combine them, we use JOIN.

---

# What is JOIN?

JOIN combines rows from multiple tables based on a related column.

Usually:

```text
Primary Key ↔ Foreign Key
```

relationship.

---

# Types of JOINs

1. INNER JOIN
2. LEFT JOIN
3. RIGHT JOIN
4. FULL OUTER JOIN
5. SELF JOIN (rarely asked)

---

# 1. INNER JOIN

Returns only matching records from both tables.

---

### Query

```sql
SELECT *
FROM Student S
INNER JOIN Department D
ON S.StudentID = D.StudentID;
```

---

### Output

| StudentID | Name    | Department |
| --------- | ------- | ---------- |
| 1         | Chethan | ISE        |
| 2         | Rahul   | CSE        |

---

Why not Anu?

Because:

```text
StudentID = 3
```

does not exist in Department table.

---

Why not ECE?

Because:

```text
StudentID = 4
```

does not exist in Student table.

---

### Easy Trick

```text
INNER JOIN = Common Data Only
```

---

# 2. LEFT JOIN

Returns:

```text
All rows from LEFT table
+
Matching rows from RIGHT table
```

---

### Query

```sql
SELECT *
FROM Student S
LEFT JOIN Department D
ON S.StudentID = D.StudentID;
```

---

### Output

| StudentID | Name    | Department |
| --------- | ------- | ---------- |
| 1         | Chethan | ISE        |
| 2         | Rahul   | CSE        |
| 3         | Anu     | NULL       |

---

Anu appears because:

```text
LEFT table data always appears.
```

---

### Easy Trick

```text
LEFT JOIN = Everything on Left
```

---

# 3. RIGHT JOIN

Returns:

```text
All rows from RIGHT table
+
Matching rows from LEFT table
```

---

### Output

| StudentID | Name    | Department |
| --------- | ------- | ---------- |
| 1         | Chethan | ISE        |
| 2         | Rahul   | CSE        |
| 4         | NULL    | ECE        |

---

### Easy Trick

```text
RIGHT JOIN = Everything on Right
```

---

# 4. FULL OUTER JOIN

Returns everything.

---

### Output

| StudentID | Name    | Department |
| --------- | ------- | ---------- |
| 1         | Chethan | ISE        |
| 2         | Rahul   | CSE        |
| 3         | Anu     | NULL       |
| 4         | NULL    | ECE        |

---

### Easy Trick

```text
FULL JOIN = LEFT + RIGHT
```

---

# JOIN Summary

| JOIN  | Returns                   |
| ----- | ------------------------- |
| INNER | Common records only       |
| LEFT  | All left + matching right |
| RIGHT | All right + matching left |
| FULL  | Everything                |

---

# Visual Trick

```text
Student = A
Department = B

INNER = A ∩ B

LEFT = Entire A

RIGHT = Entire B

FULL = A ∪ B
```

---

# 2. What is a View?

A View is a virtual table.

It does not store data physically.

Instead, it stores a query.

---

### Example

Employee Table

| ID | Name    | Salary |
| -- | ------- | ------ |
| 1  | Chethan | 50000  |
| 2  | Rahul   | 60000  |

---

Suppose HR should only see names.

Create View:

```sql
CREATE VIEW EmployeeView AS
SELECT Name
FROM Employee;
```

---

### Output

| Name    |
| ------- |
| Chethan |
| Rahul   |

---

### Benefits

* Security
* Simplicity
* Reusability

---

# Table vs View

| Table            | View            |
| ---------------- | --------------- |
| Stores data      | Stores query    |
| Physical         | Virtual         |
| Occupies storage | Minimal storage |

---

# 3. What is a Stored Procedure?

A stored procedure is a set of SQL statements stored inside the database.

Think of it like a function in programming.

---

### Example

```sql
CREATE PROCEDURE GetEmployees
AS
SELECT * FROM Employee;
```

Execute:

```sql
EXEC GetEmployees;
```

---

### Advantages

* Reusable
* Faster execution
* Better security

---

### Real-Life Example

Instead of writing:

```sql
SELECT * FROM Employee;
```

100 times,

Create procedure once.

Call whenever needed.

---

# Function vs Stored Procedure

| Function        | Procedure             |
| --------------- | --------------------- |
| Returns value   | May or may not return |
| Used in queries | Called separately     |
| Smaller tasks   | Larger tasks          |

---

# 4. What is a Trigger?

A trigger is a special procedure that executes automatically when an event occurs.

---

### Events

```text
INSERT
UPDATE
DELETE
```

---

# Real-Life Example

Suppose employee salary changes.

Automatically record the change.

No manual work needed.

---

### Example

```sql
CREATE TRIGGER SalaryAudit
AFTER UPDATE
ON Employee
```

Whenever salary changes:

```text
Trigger runs automatically.
```

---

# Why Use Triggers?

* Auditing
* Security
* Logging
* Automation

---

# Example Scenario

Banking System

When money is withdrawn:

```text
Update Account Table
```

Automatically:

```text
Insert record into Transaction History
```

Trigger performs this.

---

# Trigger vs Stored Procedure

| Trigger                          | Stored Procedure     |
| -------------------------------- | -------------------- |
| Automatic                        | Manual call          |
| Event-based                      | User-based           |
| Executes on INSERT/UPDATE/DELETE | Executes when called |

---

# Most Important Interview Questions

## Easy

### What is JOIN?

JOIN combines data from multiple tables.

---

### What is INNER JOIN?

Returns matching records only.

---

### What is LEFT JOIN?

Returns all left table records and matching right table records.

---

### What is a View?

A virtual table based on a query.

---

### What is a Trigger?

A procedure that automatically executes when a database event occurs.

---

## Medium

### Difference between View and Table?

| Table            | View          |
| ---------------- | ------------- |
| Stores data      | Virtual table |
| Physical storage | Query only    |

---

### Why use Stored Procedures?

* Reusability
* Performance
* Security

---

### Difference between Procedure and Trigger?

Trigger runs automatically.
Procedure is called manually.

---

## Hard

### INNER JOIN vs LEFT JOIN?

INNER:

```text
Only common records
```

LEFT:

```text
All left records + matching right records
```

---

### Why are Views useful?

Views provide:

* Security
* Simplicity
* Data abstraction

---

### When would you use a Trigger?

Use triggers for:

* Audit logs
* Automatic updates
* Data validation
* Transaction history

---

# DBMS Complete (Days 5–9)

You now know:

✅ DBMS Basics

✅ Keys

✅ Constraints

✅ SQL

✅ Normalization

✅ Functional Dependency

✅ ACID Properties

✅ Transactions

✅ Indexing

✅ JOINs

✅ Views

✅ Stored Procedures

✅ Triggers


