# ACID Properties, Transactions & Indexing

This is one of the highest-priority DBMS topics for interviews.

---

# 1. What is a Transaction?

A transaction is a sequence of database operations performed as a single unit of work.

### Example: Bank Transfer

Suppose you transfer ₹1000 from Account A to Account B.

Steps:

```text
1. Deduct ₹1000 from Account A
2. Add ₹1000 to Account B
```

Both operations together form one transaction.

---

## Problem Without Transactions

Suppose:

```text
Step 1 completed
Server crashed
Step 2 not completed
```

Result:

```text
Account A lost ₹1000
Account B didn't receive ₹1000
```

Money disappeared.

This is why transactions are needed.

---

# Transaction States

## Active

Transaction is running.

```text
Transfer started
```

---

## Partially Committed

Operations completed but not permanently saved.

---

## Committed

Changes permanently saved.

```text
Transfer successful
```

---

## Failed

Something went wrong.

```text
Server crash
Power failure
```

---

## Aborted

Transaction rolled back.

Database returns to previous state.

---

# ACID Properties

ACID ensures database reliability.

### A → Atomicity

### C → Consistency

### I → Isolation

### D → Durability

---

# 1. Atomicity

## Meaning

Either all operations happen or none happen.

### Example

Bank Transfer

```text
Deduct ₹1000
Add ₹1000
```

Both must happen.

Not:

```text
Deduct completed
Add failed
```

---

### Real-Life Example

Online ticket booking.

Either:

```text
Seat booked
Payment deducted
```

OR

```text
Nothing happens
```

No partial work.

---

### Easy Memory Trick

```text
ALL or NOTHING
```

---

# 2. Consistency

## Meaning

Database must remain valid before and after transaction.

---

### Example

Before Transfer

```text
A = 5000
B = 3000

Total = 8000
```

After Transfer

```text
A = 4000
B = 4000

Total = 8000
```

Consistency maintained.

---

### Easy Memory Trick

```text
Rules must never break
```

---

# 3. Isolation

## Meaning

Multiple transactions should not interfere with each other.

---

### Example

Two users withdraw money simultaneously.

Without isolation:

```text
User A reads balance = 1000
User B reads balance = 1000
```

Both withdraw.

Incorrect result.

Isolation prevents this.

---

### Easy Memory Trick

```text
Transactions work independently
```

---

# 4. Durability

## Meaning

Once committed, data remains saved permanently.

---

### Example

You transfer money.

Transaction committed.

Immediately:

```text
Power failure
```

Still:

```text
Money transfer remains saved.
```

---

### Easy Memory Trick

```text
Committed = Permanent
```

---

# Complete ACID Example

Imagine ATM withdrawal.

### Atomicity

Either money deducted and cash dispensed, or neither.

---

### Consistency

Balance remains correct.

---

### Isolation

Two withdrawals don't interfere.

---

### Durability

After successful withdrawal, record remains saved.

---

# ACID Summary Table

| Property    | Meaning                  |
| ----------- | ------------------------ |
| Atomicity   | All or Nothing           |
| Consistency | Valid State              |
| Isolation   | Independent Transactions |
| Durability  | Permanent Storage        |

---

# What is COMMIT?

Makes changes permanent.

Example:

```sql
UPDATE Employee
SET Salary = 60000
WHERE ID = 1;

COMMIT;
```

Now changes are permanently saved.

---

# What is ROLLBACK?

Undo changes.

Example:

```sql
UPDATE Employee
SET Salary = 60000
WHERE ID = 1;

ROLLBACK;
```

Salary returns to previous value.

---

# What is an Index?

An index improves search speed.

Think of it like a book index.

---

## Without Index

Suppose table has:

```text
10 lakh records
```

Searching StudentID = 999999

Database may check rows one by one.

Slow.

---

## With Index

Database directly jumps to the required record.

Fast.

---

### Real-Life Example

Book Index

Instead of reading entire book:

```text
DBMS → Page 50
```

Directly jump.

---

# Why Use Index?

Benefits:

* Faster SELECT queries
* Faster searching
* Faster sorting

---

# Drawback of Index

Indexes consume extra storage.

Insert and Update operations may become slightly slower.

---

# Clustered Index

Physically sorts table data.

Example:

```text
1
2
3
4
5
```

Stored in sorted order.

Only one clustered index per table.

---

# Non-Clustered Index

Separate structure pointing to data.

Table remains unchanged.

Multiple non-clustered indexes possible.

---

# Clustered vs Non-Clustered Index

| Clustered           | Non-Clustered           |
| ------------------- | ----------------------- |
| Sorts actual data   | Separate structure      |
| One per table       | Multiple possible       |
| Faster range search | Faster specific lookups |

---

# Most Asked Interview Questions

### Easy

1. What is a transaction?
2. What is COMMIT?
3. What is ROLLBACK?
4. What is an Index?
5. Why use Indexing?

---

### Medium

6. What are ACID properties?
7. Explain Atomicity.
8. Explain Consistency.
9. Explain Isolation.
10. Explain Durability.

---

### Hard

11. Clustered vs Non-Clustered Index?
12. Why is Isolation important?
13. What happens if Atomicity is violated?
14. Why does Index improve performance?
15. Drawbacks of Indexing?

---

# End of Day 8 Target

You should be able to explain:

✅ Transaction

✅ Transaction States

✅ ACID Properties

✅ COMMIT

✅ ROLLBACK

✅ Index

✅ Clustered Index

✅ Non-Clustered Index

# Day 8 – Interview Questions & Answers (In Depth)

---

# Easy Questions

## 1. What is a Transaction?

### Answer

A transaction is a group of one or more database operations that are executed as a single unit of work.

A transaction must either:

* Complete fully, or
* Fail completely

There should never be a partial execution.

---

### Example: Bank Transfer

Suppose you transfer ₹1000 from Account A to Account B.

Steps:

```text
Step 1: Deduct ₹1000 from Account A
Step 2: Add ₹1000 to Account B
```

Both steps together form one transaction.

---

### Problem

Suppose:

```text
Step 1 completed
Server crashed
Step 2 not completed
```

Result:

```text
A lost ₹1000
B did not receive ₹1000
```

Money disappears.

To prevent this, DBMS treats both operations as a single transaction.

---

### Interview Answer

> A transaction is a sequence of database operations performed as a single logical unit of work. It must either complete entirely or not execute at all.

---

# 2. What is COMMIT?

### Answer

COMMIT permanently saves all changes made during a transaction.

---

### Example

```sql
UPDATE Employee
SET Salary = 60000
WHERE ID = 1;

COMMIT;
```

After COMMIT:

```text
Changes become permanent.
```

Even if:

```text
Power failure occurs
```

Data remains saved.

---

### Real-Life Example

Online payment success.

Once payment succeeds:

```text
Transaction committed.
```

Cannot be automatically undone.

---

### Interview Answer

> COMMIT permanently saves all changes made during a transaction to the database.

---

# 3. What is ROLLBACK?

### Answer

ROLLBACK undoes all changes made during the current transaction.

---

### Example

Before:

| ID | Salary |
| -- | ------ |
| 1  | 50000  |

Execute:

```sql
UPDATE Employee
SET Salary = 70000
WHERE ID = 1;

ROLLBACK;
```

After rollback:

| ID | Salary |
| -- | ------ |
| 1  | 50000  |

---

### Real-Life Example

ATM transaction fails.

Money deduction is rolled back.

Original balance is restored.

---

### Interview Answer

> ROLLBACK cancels a transaction and restores the database to its previous consistent state.

---

# 4. What is an Index?

### Answer

An index is a special data structure used to speed up data retrieval operations.

It works similarly to a book index.

---

### Without Index

Suppose:

```text
1,000,000 records
```

Searching:

```text
StudentID = 999999
```

Database checks row by row.

Very slow.

---

### With Index

Database directly jumps to the record.

Much faster.

---

### Real-Life Example

Book Index

Without index:

Read all pages.

With index:

Go directly to page number.

---

### Interview Answer

> An index is a database object that improves query performance by allowing faster data retrieval.

---

# 5. Why Use Indexing?

### Answer

Indexing is used to improve query performance.

---

### Benefits

#### Faster Searching

```sql
SELECT *
FROM Student
WHERE StudentID = 101;
```

---

#### Faster Sorting

```sql
ORDER BY Salary
```

---

#### Faster Filtering

```sql
WHERE Department='ISE'
```

---

### Interview Answer

> Indexing is used to reduce data lookup time and improve the performance of SELECT queries.

---

# Medium Questions

---

# 6. What are ACID Properties?

### Answer

ACID properties ensure reliable and accurate database transactions.

ACID stands for:

```text
A → Atomicity
C → Consistency
I → Isolation
D → Durability
```

These properties guarantee data correctness even during failures.

---

### Interview Answer

> ACID properties are a set of rules that ensure reliable and consistent transaction processing in a database.

---

# 7. Explain Atomicity

### Answer

Atomicity means:

```text
All operations execute
OR
No operation executes
```

No partial execution is allowed.

---

### Example

Transfer ₹1000:

```text
Deduct ₹1000
Add ₹1000
```

If second step fails:

```text
First step also undone.
```

---

### Easy Memory Trick

```text
ALL OR NOTHING
```

---

### Interview Answer

> Atomicity ensures that a transaction is treated as a single unit, where either all operations succeed or all fail.

---

# 8. Explain Consistency

### Answer

Consistency ensures the database remains valid before and after a transaction.

---

### Example

Before Transfer:

```text
A = 5000
B = 3000

Total = 8000
```

After Transfer:

```text
A = 4000
B = 4000

Total = 8000
```

Total remains correct.

---

### Easy Memory Trick

```text
Rules must never break
```

---

### Interview Answer

> Consistency ensures that every transaction takes the database from one valid state to another valid state.

---

# 9. Explain Isolation

### Answer

Isolation ensures multiple transactions execute independently without affecting each other.

---

### Example

Balance:

```text
1000
```

User A reads:

```text
1000
```

User B reads:

```text
1000
```

Both withdraw ₹800 simultaneously.

Without isolation:

```text
Incorrect balance occurs.
```

---

### Isolation prevents:

* Dirty Reads
* Lost Updates
* Data Corruption

---

### Interview Answer

> Isolation ensures that concurrent transactions do not interfere with one another.

---

# 10. Explain Durability

### Answer

Durability guarantees that committed data remains permanently stored.

---

### Example

Money transfer successful.

Immediately:

```text
Power Failure
```

Still:

```text
Transfer remains saved.
```

---

### Easy Memory Trick

```text
COMMITTED = PERMANENT
```

---

### Interview Answer

> Durability ensures that once a transaction is committed, its changes remain permanent even after system failures.

---

# Hard Questions

---

# 11. Clustered vs Non-Clustered Index

| Clustered Index              | Non-Clustered Index    |
| ---------------------------- | ---------------------- |
| Physically sorts data        | Separate structure     |
| Data stored in indexed order | Data stored separately |
| One per table                | Multiple possible      |
| Faster range queries         | Faster exact lookups   |

---

### Example

Clustered:

```text
1
2
3
4
5
```

Stored in sorted order.

Non-Clustered:

```text
Index → Pointer → Data
```

---

### Interview Answer

> A clustered index determines the physical order of data, whereas a non-clustered index stores pointers to the actual data.

---

# 12. Why is Isolation Important?

### Answer

Without isolation:

Multiple users may modify the same data simultaneously.

Result:

* Wrong balances
* Lost updates
* Inconsistent data

---

### Example

Two users booking the last train seat.

Without isolation:

```text
Seat booked twice.
```

---

### Interview Answer

> Isolation prevents concurrent transactions from interfering with each other and ensures data accuracy.

---

# 13. What Happens if Atomicity is Violated?

### Answer

Partial transactions may occur.

---

### Example

Transfer:

```text
Deduct ₹1000 from A
```

Success.

```text
Add ₹1000 to B
```

Fails.

Result:

```text
Money lost.
```

Database becomes inconsistent.

---

### Interview Answer

> If atomicity is violated, a transaction may complete partially, leading to inconsistent and incorrect data.

---

# 14. Why Does Index Improve Performance?

### Answer

Without index:

Database performs:

```text
Full Table Scan
```

Checks every row.

Complexity:

```text
O(n)
```

---

With index:

Database directly locates required records.

Much fewer operations needed.

---

### Example

Searching:

```text
StudentID = 999999
```

Without index:

```text
Check thousands of rows.
```

With index:

```text
Jump directly to record.
```

---

### Interview Answer

> Indexing improves performance by reducing the number of rows the database must scan to find data.

---

# 15. Drawbacks of Indexing

### Answer

Indexes are beneficial but not free.

---

### 1. Extra Storage

Indexes require additional memory.

---

### 2. Slower INSERT

When inserting:

```text
Data inserted
Index updated
```

Extra work.

---

### 3. Slower UPDATE

Updating indexed columns requires index maintenance.

---

### 4. Slower DELETE

Index entries must also be removed.

---

### Interview Answer

> While indexes improve query speed, they increase storage requirements and can slow down insert, update, and delete operations.

---

# Top 5 Questions Most Frequently Asked

### 1. What are ACID Properties?

Atomicity, Consistency, Isolation, Durability.

---

### 2. Explain Atomicity with a Bank Example.

All operations succeed or all fail.

---

### 3. What is an Index?

A structure that improves data retrieval speed.

---

### 4. Clustered vs Non-Clustered Index?

Clustered sorts data physically; non-clustered uses pointers.

---

### 5. Why is Isolation Important?

It prevents conflicts when multiple transactions access the same data simultaneously.

These five questions alone cover a large portion of DBMS transaction and indexing questions asked in fresher interviews.
