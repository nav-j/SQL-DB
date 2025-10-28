# SQL Task – PRIMARY KEY Constraint

---

## Objective
Learn how to use the **PRIMARY KEY constraint** in MySQL to uniquely identify each record in a table.

---

## What is a PRIMARY KEY?

- The **PRIMARY KEY** uniquely identifies each row in a table.  
- A table can have **only one primary key**.  
- A primary key column:
  - Must contain **unique** values  
  - **Cannot be NULL**  

---

## Task 1 – Create a Table with a PRIMARY KEY

Create a table `Employees` with the following structure:

- `EmpID` – primary key  
- `EmpName` – employee name  
- `Department` – department name  
- `Salary` – numeric value  

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY,
    EmpName VARCHAR(50) NOT NULL,
    Department VARCHAR(30),
    Salary DECIMAL(10,2)
);
````

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
```

✅ **Explanation:**

* `EmpID` uniquely identifies each employee.
* It cannot contain duplicate or NULL values.

---

## Task 2 – Insert Valid Records

Insert the following data:

```sql
INSERT INTO Employees (EmpID, EmpName, Department, Salary)
VALUES
(101, 'Ravi Kumar', 'Sales', 45000.00),
(102, 'Priya Sharma', 'HR', 50000.00),
(103, 'Amit Singh', 'IT', 60000.00);
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.03 sec)
```

**Result:**

| EmpID | EmpName      | Department | Salary   |
| ----- | ------------ | ---------- | -------- |
| 101   | Ravi Kumar   | Sales      | 45000.00 |
| 102   | Priya Sharma | HR         | 50000.00 |
| 103   | Amit Singh   | IT         | 60000.00 |

---

## Task 3 – Try to Insert Duplicate PRIMARY KEY

Now, insert a record with a duplicate EmpID:

```sql
INSERT INTO Employees (EmpID, EmpName, Department, Salary)
VALUES (101, 'Ramesh Gupta', 'Finance', 48000.00);
```

**🔴 Sample Output:**

```
ERROR 1062 (23000): Duplicate entry '101' for key 'PRIMARY'
```

✅ MySQL rejects duplicate primary key values.

---

## Task 4 – Try to Insert NULL Primary Key

```sql
INSERT INTO Employees (EmpID, EmpName, Department, Salary)
VALUES (NULL, 'Neha Verma', 'Admin', 42000.00);
```

**🔴 Sample Output:**

```
ERROR 1048 (23000): Column 'EmpID' cannot be null
```

✅ Primary key cannot be NULL.

---

## Task 5 – Create Table with AUTO_INCREMENT Primary Key

Create another table `Departments` with an **auto-incremented primary key**.

```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY AUTO_INCREMENT,
    DeptName VARCHAR(50) NOT NULL
);
```

Insert data:

```sql
INSERT INTO Departments (DeptName)
VALUES ('Finance'), ('IT'), ('HR');
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.02 sec)
```

**Result:**

| DeptID | DeptName |
| -----: | -------- |
|      1 | Finance  |
|      2 | IT       |
|      3 | HR       |

✅ MySQL automatically generates unique DeptIDs.

---

## ✅ Concepts Practiced

| Concept        | Description                                | Example |
| -------------- | ------------------------------------------ | ------- |
| PRIMARY KEY    | Uniquely identifies each record            | EmpID   |
| UNIQUE         | Similar to PRIMARY KEY but allows one NULL | Email   |
| AUTO_INCREMENT | Automatically generates sequential IDs     | DeptID  |

---

## 🧠 Bonus Challenge

Create a table `Projects` with:

* `ProjectID` (Primary Key, Auto Increment)
* `ProjectName` (Unique)
* `StartDate` (Not Null)

Then insert a few records and test what happens when you try to insert a duplicate project name.

---
