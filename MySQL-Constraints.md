# 🐬 SQL Task – MySQL Constraints

---

## 🎯 Objective
Learn how to use **SQL constraints** to control data rules and maintain data integrity.

---

## 🔹 What are Constraints?

Constraints are rules applied to table columns to **restrict invalid data entry**.  
Common MySQL constraints include:

| Constraint | Description |
|-------------|--------------|
| `PRIMARY KEY` | Uniquely identifies each record |
| `FOREIGN KEY` | Links data between two tables |
| `UNIQUE` | Ensures all values are unique |
| `NOT NULL` | Prevents NULL (empty) values |
| `CHECK` | Ensures data meets specific conditions |
| `DEFAULT` | Assigns a default value when no value is provided |

---

## 🧱 Table 1: Departments

### **Task 1 – Create Table with PRIMARY KEY and UNIQUE**

```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY,
    DeptName VARCHAR(50) UNIQUE
);
````

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.03 sec)
```

✅ Here:

* `DeptID` uniquely identifies each department.
* `DeptName` must be unique.

---

## 🧱 Table 2: Employees

### **Task 2 – Create Table with Multiple Constraints**

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    Name VARCHAR(50) NOT NULL,
    Email VARCHAR(100) UNIQUE,
    Salary DECIMAL(10,2) CHECK (Salary >= 30000),
    DepartmentID INT,
    City VARCHAR(50) DEFAULT 'Delhi',
    FOREIGN KEY (DepartmentID) REFERENCES Departments(DeptID)
);
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.05 sec)
```

✅ Here’s what each constraint does:

| Constraint    | Column       | Description                |
| ------------- | ------------ | -------------------------- |
| `PRIMARY KEY` | EmpID        | Unique identifier          |
| `NOT NULL`    | Name         | Must have a value          |
| `UNIQUE`      | Email        | Prevents duplicate emails  |
| `CHECK`       | Salary       | Must be ≥ 30,000           |
| `DEFAULT`     | City         | Auto-fills with 'Delhi'    |
| `FOREIGN KEY` | DepartmentID | Links to Departments table |

---

### **Task 3 – Insert Valid Data**

```sql
INSERT INTO Departments VALUES (1, 'HR'), (2, 'IT'), (3, 'Finance');

INSERT INTO Employees (EmpID, Name, Email, Salary, DepartmentID)
VALUES
(101, 'Ramesh', 'ramesh@gmail.com', 40000, 1),
(102, 'Priya', 'priya@gmail.com', 55000, 2),
(103, 'Anil', 'anil@gmail.com', 30000, 3);
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.04 sec)
```

---

### **Task 4 – Violate Constraints (Try and Observe)**

#### ❌ Attempt to insert a duplicate Email:

```sql
INSERT INTO Employees (EmpID, Name, Email, Salary, DepartmentID)
VALUES (104, 'Neha', 'ramesh@gmail.com', 45000, 2);
```

**🔴 Output:**

```
ERROR 1062 (23000): Duplicate entry 'ramesh@gmail.com' for key 'Email'
```

---

#### ❌ Attempt to insert a NULL Name:

```sql
INSERT INTO Employees (EmpID, Name, Email, Salary, DepartmentID)
VALUES (105, NULL, 'neha@gmail.com', 45000, 2);
```

**🔴 Output:**

```
ERROR 1048 (23000): Column 'Name' cannot be null
```

---

#### ❌ Attempt to insert Salary below 30,000:

```sql
INSERT INTO Employees (EmpID, Name, Email, Salary, DepartmentID)
VALUES (106, 'Karan', 'karan@gmail.com', 25000, 1);
```

**🔴 Output:**

```
ERROR 3819 (HY000): Check constraint 'Employees_chk_1' is violated
```

---

### **Task 5 – Use DEFAULT Value**

Insert data without specifying `City` — the default ‘Delhi’ will be used.

```sql
INSERT INTO Employees (EmpID, Name, Email, Salary, DepartmentID)
VALUES (107, 'Suresh', 'suresh@gmail.com', 38000, 1);
```

**🟢 Sample Output:**

```
Query OK, 1 row affected (0.02 sec)
```

**Result:**

| EmpID | Name   | Email                                       | Salary   | DepartmentID | City  |
| ----- | ------ | ------------------------------------------- | -------- | ------------ | ----- |
| 101   | Ramesh | [ramesh@gmail.com](mailto:ramesh@gmail.com) | 40000.00 | 1            | Delhi |
| 102   | Priya  | [priya@gmail.com](mailto:priya@gmail.com)   | 55000.00 | 2            | Delhi |
| 103   | Anil   | [anil@gmail.com](mailto:anil@gmail.com)     | 30000.00 | 3            | Delhi |
| 107   | Suresh | [suresh@gmail.com](mailto:suresh@gmail.com) | 38000.00 | 1            | Delhi |

---

### **Task 6 – Drop a Constraint (Optional)**

Drop the `CHECK` constraint from the `Employees` table.

```sql
ALTER TABLE Employees
DROP CHECK Employees_chk_1;
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
```

---

## ✅ Concepts Practiced

| Constraint    | Description                | Example                            |
| ------------- | -------------------------- | ---------------------------------- |
| `PRIMARY KEY` | Unique record identifier   | EmpID                              |
| `FOREIGN KEY` | Reference to another table | DepartmentID → Departments(DeptID) |
| `UNIQUE`      | No duplicate values        | Email                              |
| `NOT NULL`    | Value cannot be empty      | Name                               |
| `CHECK`       | Must meet condition        | Salary >= 30000                    |
| `DEFAULT`     | Automatic default value    | City = 'Delhi'                     |

---

📘 **Practice Goal:**
This task will help you clearly understand **how each constraint works**, what **violations cause errors**, and how to ensure **data integrity** in your SQL database.

---

💡 **Challenge:**
Try creating a new table `Projects` with constraints:

* `ProjectID` (Primary Key)
* `ProjectName` (NOT NULL, UNIQUE)
* `Budget` (CHECK > 50000)
* `DeptID` (Foreign Key references Departments)

```
