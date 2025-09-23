# Normalization in Database

**Definition:**  
Normalization is the process of organizing data in a database to reduce redundancy (duplicate data) and improve data integrity.

## 🎯 Goal
- Avoid storing the same data multiple times  
- Ensure data consistency  
- Make updates, inserts, and deletes efficient  

## ⚙️ How it works
Data is divided into multiple related tables, connected with **foreign keys**.

### Example (Unnormalized)
| StudentID | Name  | Course   | Instructor |
|-----------|-------|----------|------------|
| 1         | Alex  | Math     | Dr. Smith  |
| 2         | Priya | Math     | Dr. Smith  |
| 3         | John  | Physics  | Dr. Brown  |

👉 Issue: "Math" and "Dr. Smith" repeat.

### After Normalization
**Students Table**
| StudentID | Name  | CourseID |
|-----------|-------|----------|
| 1         | Alex  | 101      |
| 2         | Priya | 101      |
| 3         | John  | 102      |

**Courses Table**
| CourseID | Course   | Instructor |
|----------|----------|------------|
| 101      | Math     | Dr. Smith  |
| 102      | Physics  | Dr. Brown  |

✅ No redundancy for courses/instructors.

---

# Denormalization in Database

**Definition:**  
Denormalization is the process of combining normalized tables back into fewer tables to improve **read performance**.

## 🎯 Goal
- Faster query execution  
- Reduce joins in frequently used queries  
- Optimize for **read-heavy systems** (analytics, dashboards, reporting)  

## ⚙️ How it works
Denormalization adds redundancy **intentionally** to reduce costly `JOIN` operations.

### Example
From the normalized example above, combine back into one table:

| StudentID | Name  | Course   | Instructor |
|-----------|-------|----------|------------|
| 1         | Alex  | Math     | Dr. Smith  |
| 2         | Priya | Math     | Dr. Smith  |
| 3         | John  | Physics  | Dr. Brown  |

✅ Querying is faster (no join needed)  
❌ But redundant data returns  

---

# 🔹 Key Differences

| Feature             | Normalization 🟢                   | Denormalization 🔴             |
|---------------------|------------------------------------|--------------------------------|
| **Purpose**         | Reduce redundancy, ensure consistency | Improve query performance      |
| **Data Redundancy** | Minimal (almost none)              | Present (allowed)              |
| **Storage Need**    | Less                               | More                           |
| **Query Speed**     | Slower (requires joins)            | Faster (fewer joins)           |
| **Best for**        | Transactional DBs (OLTP)           | Analytics, reporting (OLAP)    |

---

# 🔹 Normalization in Detail

👉 Normalization = Breaking data into multiple related tables to reduce redundancy and improve data integrity.  
It’s done in **stages called Normal Forms (NF).**

---

## 1NF (First Normal Form)

**Rule:**
- No repeating groups or arrays  
- Each column must hold atomic values  

**Not 1NF:**
| StudentID | Name  | Courses             |
|-----------|-------|---------------------|
| 1         | Alex  | Math, Physics       |
| 2         | Priya | Chemistry, Biology  |

❌ Courses are stored as a list.

**Fixed (1NF):**
| StudentID | Name  | Course     |
|-----------|-------|------------|
| 1         | Alex  | Math       |
| 1         | Alex  | Physics    |
| 2         | Priya | Chemistry  |
| 2         | Priya | Biology    |

✅ Each field has atomic values.

---

## 2NF (Second Normal Form)

**Rule:**
- Must be in 1NF  
- Remove **partial dependency** (non-key attributes must depend on the whole primary key, not part of it)  

**Not 2NF (Composite key = StudentID, CourseID):**
| StudentID | CourseID | StudentName | CourseName |
|-----------|----------|-------------|------------|
| 1         | 101      | Alex        | Math       |
| 2         | 102      | Priya       | Physics    |

❌ StudentName depends only on StudentID (not full key).  

**Fixed (2NF):**

**Students**
| StudentID | StudentName |
|-----------|-------------|
| 1         | Alex        |
| 2         | Priya       |

**Courses**
| CourseID | CourseName |
|----------|------------|
| 101      | Math       |
| 102      | Physics    |

**Enrollments**
| StudentID | CourseID |
|-----------|----------|
| 1         | 101      |
| 2         | 102      |

✅ Dependencies are correct.

---

## 3NF (Third Normal Form)

**Rule:**
- Must be in 2NF  
- Remove **transitive dependency** (non-key attributes should depend only on the primary key, not other non-key attributes).  

**Not 3NF:**
| StudentID | StudentName | Department | DeptHead   |
|-----------|-------------|------------|------------|
| 1         | Alex        | CS         | Dr. Smith  |
| 2         | Priya       | Math       | Dr. Brown  |

❌ DeptHead depends on Department (not StudentID).

**Fixed (3NF):**

**Students**
| StudentID | StudentName | Department |
|-----------|-------------|------------|
| 1         | Alex        | CS         |
| 2         | Priya       | Math       |

**Departments**
| Department | DeptHead   |
|------------|------------|
| CS         | Dr. Smith  |
| Math       | Dr. Brown  |

✅ No transitive dependency.

---

## BCNF (Boyce–Codd Normal Form)

**Definition:**  
- Stricter version of 3NF  
- Ensures **no anomalies where non-primary attributes determine keys**  
- Every determinant must be a **super key**

**Example:**
| Student | Course  | Instructor |
|---------|---------|------------|
| Alex    | Math    | Dr. Smith  |
| Priya   | Math    | Dr. Smith  |
| Alex    | Physics | Dr. Brown  |

**Issue:**  
- `Instructor → Course`  
- In 3NF, this passes, but in BCNF, Instructor is **not a super key** → violation.  

**BCNF Fix (Decompose):**

**Instructors**
| Instructor | Course  |
|------------|---------|
| Dr. Smith  | Math    |
| Dr. Brown  | Physics |

**Enrollments**
| Student | Instructor |
|---------|------------|
| Alex    | Dr. Smith  |
| Priya   | Dr. Smith  |
| Alex    | Dr. Brown  |

✅ No BCNF violation.

---

# 🔹 Denormalization in Detail

👉 Denormalization = Merging tables to reduce joins and improve read performance.  
Redundancy is **added intentionally**.

### Example: E-commerce

**Normalized**

**Customers**
| CustomerID | Name  |
|------------|-------|
| 1          | Alex  |
| 2          | Priya |

**Orders**
| OrderID | CustomerID | ProductID | Qty |
|---------|------------|-----------|-----|
| 101     | 1          | P1        | 2   |
| 102     | 2          | P2        | 1   |

**Products**
| ProductID | ProductName | Price  |
|-----------|-------------|--------|
| P1        | Laptop      | 60000  |
| P2        | Phone       | 20000  |

👉 To get order details → multiple joins required.

---

**Denormalized**
| OrderID | CustomerName | ProductName | Price | Qty |
|---------|--------------|-------------|-------|-----|
| 101     | Alex         | Laptop      | 60000 | 2   |
| 102     | Priya        | Phone       | 20000 | 1   |

✅ Faster reporting (no joins)  
❌ Redundant data (if Laptop price changes → multiple rows to update)  

---

# ✅ Summary

- **Normalization** → Efficiency, consistency, fewer errors, but slower reads.  
- **Denormalization** → Faster reads, fewer joins, but more storage + risk of inconsistency.  
