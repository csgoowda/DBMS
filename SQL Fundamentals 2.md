# SQL Fundamentals (Most Important for Interviews)

Before learning SQL, remember:

**SQL = Structured Query Language**

SQL is used to communicate with a database.

Think of DBMS as a library and SQL as the language you use to ask the librarian for books.

---

# Sample Table Used Throughout Day 6

## Employee Table

| EmpID | Name    | Department | Salary |
| ----- | ------- | ---------- | ------ |
| 1     | Chethan | ISE        | 50000  |
| 2     | Rahul   | CSE        | 45000  |
| 3     | Anu     | ISE        | 60000  |
| 4     | Priya   | ECE        | 55000  |

We will use this table for all examples.

---

# SQL Categories

SQL commands are mainly divided into:

### DDL (Data Definition Language)

Used to create and modify structure.

Commands:

* CREATE
* ALTER
* DROP
* TRUNCATE

---

### DML (Data Manipulation Language)

Used to manipulate data.

Commands:

* INSERT
* UPDATE
* DELETE

---

### DQL (Data Query Language)

Used to retrieve data.

Command:

* SELECT

---

### DCL (Data Control Language)

Used for permissions.

Commands:

* GRANT
* REVOKE

---

### TCL (Transaction Control Language)

Used for transaction management.

Commands:

* COMMIT
* ROLLBACK

---

# 1. SELECT

Used to retrieve data from a table.

### Syntax

```sql
SELECT * FROM Employee;
```

### Output

| EmpID | Name    | Department | Salary |
| ----- | ------- | ---------- | ------ |
| 1     | Chethan | ISE        | 50000  |
| 2     | Rahul   | CSE        | 45000  |
| 3     | Anu     | ISE        | 60000  |
| 4     | Priya   | ECE        | 55000  |

---

## Select Specific Columns

```sql
SELECT Name, Salary
FROM Employee;
```

Output:

| Name    | Salary |
| ------- | ------ |
| Chethan | 50000  |
| Rahul   | 45000  |

---

# 2. WHERE Clause

Used to filter records.

### Example

```sql
SELECT *
FROM Employee
WHERE Department = 'ISE';
```

Output:

| EmpID | Name    | Department | Salary |
| ----- | ------- | ---------- | ------ |
| 1     | Chethan | ISE        | 50000  |
| 3     | Anu     | ISE        | 60000  |

---

## Multiple Conditions

```sql
SELECT *
FROM Employee
WHERE Salary > 50000;
```

---

# Operators Used with WHERE

## AND

```sql
SELECT *
FROM Employee
WHERE Department='ISE'
AND Salary > 50000;
```

---

## OR

```sql
SELECT *
FROM Employee
WHERE Department='ISE'
OR Department='CSE';
```

---

## NOT

```sql
SELECT *
FROM Employee
WHERE NOT Department='ISE';
```

---

# 3. ORDER BY

Used to sort records.

---

## Ascending Order

```sql
SELECT *
FROM Employee
ORDER BY Salary ASC;
```

Lowest salary first.

---

## Descending Order

```sql
SELECT *
FROM Employee
ORDER BY Salary DESC;
```

Highest salary first.

---

# 4. INSERT

Used to add new records.

### Example

```sql
INSERT INTO Employee
VALUES(5,'Kiran','ME',40000);
```

New row inserted.

---

# 5. UPDATE

Used to modify existing records.

### Example

```sql
UPDATE Employee
SET Salary = 70000
WHERE EmpID = 1;
```

Updates Chethan's salary.

---

# Why WHERE is Important?

Without WHERE:

```sql
UPDATE Employee
SET Salary = 70000;
```

Every employee salary becomes 70000.

This is a common interview warning question.

---

# 6. DELETE

Used to remove records.

### Example

```sql
DELETE FROM Employee
WHERE EmpID = 5;
```

Deletes one record.

---

# DELETE vs TRUNCATE vs DROP

## DELETE

Removes selected rows.

```sql
DELETE FROM Employee
WHERE EmpID=1;
```

Table remains.

---

## TRUNCATE

Removes all rows.

```sql
TRUNCATE TABLE Employee;
```

Table remains.

---

## DROP

Deletes entire table.

```sql
DROP TABLE Employee;
```

Table structure also removed.

---

# 7. Aggregate Functions

Used for calculations.

---

## COUNT()

Counts records.

```sql
SELECT COUNT(*)
FROM Employee;
```

Output:

```text
4
```

---

## SUM()

Total salary.

```sql
SELECT SUM(Salary)
FROM Employee;
```

Output:

```text
210000
```

---

## AVG()

Average salary.

```sql
SELECT AVG(Salary)
FROM Employee;
```

---

## MAX()

Highest salary.

```sql
SELECT MAX(Salary)
FROM Employee;
```

Output:

```text
60000
```

---

## MIN()

Lowest salary.

```sql
SELECT MIN(Salary)
FROM Employee;
```

Output:

```text
45000
```

---

# 8. GROUP BY

Groups similar records.

### Example

```sql
SELECT Department,
COUNT(*)
FROM Employee
GROUP BY Department;
```

Output:

| Department | Count |
| ---------- | ----- |
| ISE        | 2     |
| CSE        | 1     |
| ECE        | 1     |

---

# Why GROUP BY?

Without GROUP BY:

```sql
COUNT(*)
```

gives total employees.

With GROUP BY:

```sql
COUNT(*)
```

gives department-wise employees.

---

# 9. HAVING

Filters grouped data.

### Example

```sql
SELECT Department,
COUNT(*)
FROM Employee
GROUP BY Department
HAVING COUNT(*) > 1;
```

Output:

| Department | Count |
| ---------- | ----- |
| ISE        | 2     |

---

# WHERE vs HAVING

| WHERE                          | HAVING                      |
| ------------------------------ | --------------------------- |
| Filters rows                   | Filters groups              |
| Used before GROUP BY           | Used after GROUP BY         |
| Cannot use aggregate functions | Can use aggregate functions |

---

# Execution Order of SQL Query

Interviewers sometimes ask this.

```text
FROM
WHERE
GROUP BY
HAVING
SELECT
ORDER BY
```

---

# Most Important SQL Interview Concepts

## Find Highest Salary

```sql
SELECT MAX(Salary)
FROM Employee;
```

---

## Find Lowest Salary

```sql
SELECT MIN(Salary)
FROM Employee;
```

---

## Find Average Salary

```sql
SELECT AVG(Salary)
FROM Employee;
```

---

## Count Employees

```sql
SELECT COUNT(*)
FROM Employee;
```

---

## Department-wise Employee Count

```sql
SELECT Department,
COUNT(*)
FROM Employee
GROUP BY Department;
```

---

# End of Day 6 Target

You should fully understand:

✅ SELECT

✅ WHERE

✅ ORDER BY

✅ INSERT

✅ UPDATE

✅ DELETE

✅ COUNT

✅ SUM

✅ AVG

✅ MAX

✅ MIN

✅ GROUP BY

✅ HAVING

✅ DELETE vs TRUNCATE vs DROP


