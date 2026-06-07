# Normalization & Functional Dependency (Most Asked DBMS Topic)

Today we learn **why normalization is needed**, not just definitions.

Interviewers love asking:

* What is normalization?
* Why normalization?
* Explain 1NF, 2NF, 3NF.
* What is Functional Dependency?
* What are anomalies?

---

# Before Normalization

Imagine a college stores data like this:

| StudentID | StudentName | Course1 | Course2 | Course3 |
| --------- | ----------- | ------- | ------- | ------- |
| 101       | Chethan     | DBMS    | OOP     | CN      |
| 102       | Rahul       | DBMS    | NULL    | NULL    |

Problems:

### Data Redundancy

Student details may repeat many times.

### Wasted Space

Many NULL values.

### Difficult Updates

If Chethan changes his name, we may need to update multiple places.

---

# What is Normalization?

Normalization is the process of organizing data into multiple tables to:

* Reduce redundancy
* Remove anomalies
* Improve consistency
* Improve integrity

### Interview Answer

> Normalization is the process of organizing data to minimize redundancy and dependency.

---

# Why Do We Need Normalization?

Without normalization:

### 1. Update Anomaly

Suppose:

| StudentID | StudentName | Dept |
| --------- | ----------- | ---- |
| 101       | Chethan     | ISE  |
| 102       | Chethan     | ISE  |

If Chethan's department changes,

we must update multiple rows.

If we forget one row → inconsistency.

---

### 2. Insert Anomaly

Suppose a new department exists but no students yet.

We cannot insert department information.

---

### 3. Delete Anomaly

If the last student leaves ISE,

deleting the student record may also remove department information.

---

# Functional Dependency (FD)

Before learning NFs, understand FD.

---

# What is Functional Dependency?

If one attribute determines another attribute, it is called Functional Dependency.

Notation:

```text
A → B
```

Meaning:

If we know A,
we can determine B.

---

# Example

| StudentID | Name    |
| --------- | ------- |
| 101       | Chethan |
| 102       | Rahul   |

Here:

```text
StudentID → Name
```

Because StudentID uniquely identifies Name.

---

# Another Example

| USN        | Name    | Branch |
| ---------- | ------- | ------ |
| 4SU22IS001 | Chethan | ISE    |

Then:

```text
USN → Name
USN → Branch
```

---

# Types of Functional Dependency

---

# 1. Full Functional Dependency

Attribute depends on the entire primary key.

Example:

| StudentID | CourseID | Marks |
| --------- | -------- | ----- |
| 1         | DBMS     | 90    |

Primary Key:

```text
(StudentID, CourseID)
```

Marks depend on both columns.

```text
(StudentID, CourseID) → Marks
```

This is Full Dependency.

---

# 2. Partial Dependency

Attribute depends on only part of a composite key.

Example:

| StudentID | CourseID | StudentName |
| --------- | -------- | ----------- |
| 1         | DBMS     | Chethan     |

StudentName depends only on StudentID.

```text
StudentID → StudentName
```

Not on CourseID.

This is Partial Dependency.

---

# 3. Transitive Dependency

A depends on B,
B depends on C.

Then:

```text
A → C
```

indirectly.

Example:

| StudentID | DeptID | DeptName |
| --------- | ------ | -------- |
| 101       | 1      | ISE      |

Dependencies:

```text
StudentID → DeptID
DeptID → DeptName
```

Therefore:

```text
StudentID → DeptName
```

This is Transitive Dependency.

---

# First Normal Form (1NF)

Rule:

### No repeating groups

### No multi-valued attributes

---

## Not 1NF

| StudentID | Subjects    |
| --------- | ----------- |
| 101       | DBMS,OOP,CN |

Multiple values in one column.

---

## Convert to 1NF

| StudentID | Subject |
| --------- | ------- |
| 101       | DBMS    |
| 101       | OOP     |
| 101       | CN      |

Now each cell contains a single value.

---

### Easy Memory Trick

**1NF = One Cell → One Value**

---

# Second Normal Form (2NF)

Rule:

### Must be in 1NF

### Remove Partial Dependency

---

## Example

| StudentID | CourseID | StudentName |
| --------- | -------- | ----------- |
| 1         | DBMS     | Chethan     |

Primary Key:

```text
(StudentID, CourseID)
```

But:

```text
StudentID → StudentName
```

Partial dependency exists.

---

## Solution

### Student Table

| StudentID | StudentName |
| --------- | ----------- |
| 1         | Chethan     |

---

### Enrollment Table

| StudentID | CourseID |
| --------- | -------- |
| 1         | DBMS     |

Now Partial Dependency removed.

---

### Easy Memory Trick

**2NF = Remove Partial Dependency**

---

# Third Normal Form (3NF)

Rule:

### Must be in 2NF

### Remove Transitive Dependency

---

## Example

| StudentID | DeptID | DeptName |
| --------- | ------ | -------- |
| 101       | 1      | ISE      |

Dependencies:

```text
StudentID → DeptID
DeptID → DeptName
```

Transitive Dependency exists.

---

## Solution

### Student Table

| StudentID | DeptID |
| --------- | ------ |
| 101       | 1      |

---

### Department Table

| DeptID | DeptName |
| ------ | -------- |
| 1      | ISE      |

Transitive dependency removed.

---

### Easy Memory Trick

**3NF = Remove Transitive Dependency**

---

# BCNF (Boyce-Codd Normal Form)

BCNF is stronger than 3NF.

Rule:

Every determinant must be a candidate key.

For interviews:

Usually understanding up to 3NF is enough.

---

# Normal Forms Summary

| Normal Form | Purpose                      |
| ----------- | ---------------------------- |
| 1NF         | Remove repeating groups      |
| 2NF         | Remove partial dependency    |
| 3NF         | Remove transitive dependency |
| BCNF        | Stronger version of 3NF      |

---

# Complete Example

### Original Table

| StudentID | StudentName | DeptID | DeptName |
| --------- | ----------- | ------ | -------- |
| 101       | Chethan     | 1      | ISE      |

Problems:

* Repetition
* Partial dependency
* Transitive dependency

---

### After 3NF

Student Table

| StudentID | StudentName | DeptID |
| --------- | ----------- | ------ |
| 101       | Chethan     | 1      |

Department Table

| DeptID | DeptName |
| ------ | -------- |
| 1      | ISE      |

Much cleaner.

---

# Interviewer's Favorite Questions

### Must Know

1. What is normalization?
2. Why normalization?
3. What are anomalies?
4. What is Functional Dependency?
5. What is 1NF?
6. What is 2NF?
7. What is 3NF?
8. Difference between 2NF and 3NF?
9. What is Partial Dependency?
10. What is Transitive Dependency?

---

# Easy Memory Tricks

### 1NF

One Cell = One Value

---

### 2NF

Remove Partial Dependency

---

### 3NF

Remove Transitive Dependency

---

### Functional Dependency

```text
A → B
```

Knowing A determines B.

---

# End of Day 7 Target

You should clearly understand:

✅ Why normalization is needed

✅ Data redundancy

✅ Update, Insert, Delete anomalies

✅ Functional Dependency

✅ Partial Dependency

✅ Transitive Dependency

✅ 1NF

✅ 2NF

✅ 3NF


