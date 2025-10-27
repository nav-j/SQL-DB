# SQL Task – MySQL UNIQUE Constraint

---

## Objective
Learn how to apply the **UNIQUE constraint** in MySQL to ensure that no duplicate data is entered in specific columns.

---

## 🔹 What is UNIQUE Constraint?

- The `UNIQUE` constraint ensures that **all values in a column are different**.  
- You can use it on one column or multiple columns (composite unique key).  
- Unlike `PRIMARY KEY`, a table can have **multiple UNIQUE constraints**.

---

## 🧱 Task 1 – Create Table with UNIQUE Constraint

Create a table `Students` where:
- `StudentID` is the Primary Key  
- `Email` must be unique  
- `PhoneNumber` must also be unique  

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    PhoneNumber VARCHAR(15) UNIQUE
);
````

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
```

✅ **Explanation:**

* `Email` and `PhoneNumber` must be **unique**.
* Attempting to insert duplicates will raise an **error**.

---

## 🧱 Task 2 – Insert Valid Data

Insert a few student records with unique emails and phone numbers.

```sql
INSERT INTO Students (Name, Email, PhoneNumber)
VALUES
('Ravi Kumar', 'ravi@example.com', '9876543210'),
('Priya Sharma', 'priya@example.com', '9988776655'),
('Amit Singh', 'amit@example.com', '9123456789');
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.03 sec)
```

**Result:**

| StudentID | Name         | Email                                         | PhoneNumber |
| --------- | ------------ | --------------------------------------------- | ----------- |
| 1         | Ravi Kumar   | [ravi@example.com](mailto:ravi@example.com)   | 9876543210  |
| 2         | Priya Sharma | [priya@example.com](mailto:priya@example.com) | 9988776655  |
| 3         | Amit Singh   | [amit@example.com](mailto:amit@example.com)   | 9123456789  |

---

## 🧱 Task 3 – Violate the UNIQUE Constraint

Try inserting a record with a **duplicate email**.

```sql
INSERT INTO Students (Name, Email, PhoneNumber)
VALUES ('Ramesh Gupta', 'ravi@example.com', '9090909090');
```

**🔴 Sample Output:**

```
ERROR 1062 (23000): Duplicate entry 'ravi@example.com' for key 'Email'
```

✅ MySQL rejects this record because `Email` must be unique.

---

## 🧱 Task 4 – Composite UNIQUE Constraint

Let’s create another table `Enrollments` where **the same student can’t enroll in the same course twice**.
We’ll use a **composite UNIQUE constraint** on `(StudentID, CourseName)`.

```sql
CREATE TABLE Enrollments (
    EnrollID INT PRIMARY KEY AUTO_INCREMENT,
    StudentID INT,
    CourseName VARCHAR(50),
    UNIQUE (StudentID, CourseName)
);
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
```

---

### Insert Data

```sql
INSERT INTO Enrollments (StudentID, CourseName)
VALUES
(1, 'SQL Basics'),
(2, 'Python Programming'),
(1, 'Data Analysis');
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.02 sec)
```

Now, try to enroll the same student in the same course again:

```sql
INSERT INTO Enrollments (StudentID, CourseName)
VALUES (1, 'SQL Basics');
```

**🔴 Sample Output:**

```
ERROR 1062 (23000): Duplicate entry '1-SQL Basics' for key 'StudentID'
```

✅ MySQL prevents duplicate combinations of `(StudentID, CourseName)`.

---

## ✅ Concepts Practiced

| Concept            | Description                            | Example                 |
| ------------------ | -------------------------------------- | ----------------------- |
| `UNIQUE`           | Prevents duplicate entries in a column | Email                   |
| `Multiple UNIQUE`  | Can be used on more than one column    | Email, PhoneNumber      |
| `Composite UNIQUE` | Ensures unique combinations of columns | (StudentID, CourseName) |

---

## 🧠 Bonus Challenge

Create a table `Teachers` with:

* `TeacherID` (Primary Key)
* `Email` (Unique)
* `Subject` (NOT NULL)
* Try inserting two teachers with the same email and observe the error.

---
