# SQL Task – FOREIGN KEY Constraint

---

## Objective
Learn how to use the **FOREIGN KEY constraint** in MySQL to establish relationships between two tables.

---

## 🔹 What is a FOREIGN KEY?

- A **FOREIGN KEY** is used to link two tables.  
- It ensures **referential integrity** — meaning the foreign key value in one table must exist in the referenced table.  
- The table containing the foreign key is called the **child table**.  
- The table being referenced is the **parent table**.

---

## Task 1 – Create Parent Table (`Departments`)

```sql
CREATE TABLE Departments (
    DeptID INT PRIMARY KEY AUTO_INCREMENT,
    DeptName VARCHAR(50) NOT NULL
);
````

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.02 sec)
```

---

## Task 2 – Insert Data into Departments

```sql
INSERT INTO Departments (DeptName)
VALUES ('HR'), ('Finance'), ('IT');
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.03 sec)
```

**Result:**

| DeptID | DeptName |
| -----: | -------- |
|      1 | HR       |
|      2 | Finance  |
|      3 | IT       |

---

## Task 3 – Create Child Table (`Employees`) with FOREIGN KEY

Now create the **Employees** table that references the `Departments` table using a foreign key.

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY AUTO_INCREMENT,
    EmpName VARCHAR(50) NOT NULL,
    Salary DECIMAL(10,2),
    DeptID INT,
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID)
);
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
```

✅ The `DeptID` in `Employees` must exist in the `Departments` table.

---

## Task 4 – Insert Valid Data into Employees

```sql
INSERT INTO Employees (EmpName, Salary, DeptID)
VALUES
('Ravi Kumar', 50000, 1),
('Priya Sharma', 60000, 2),
('Amit Singh', 70000, 3);
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.02 sec)
```

**Result:**

| EmpID | EmpName      |   Salary | DeptID |
| ----: | ------------ | -------: | -----: |
|     1 | Ravi Kumar   | 50000.00 |      1 |
|     2 | Priya Sharma | 60000.00 |      2 |
|     3 | Amit Singh   | 70000.00 |      3 |

---

## Task 5 – Try Inserting Invalid DeptID

```sql
INSERT INTO Employees (EmpName, Salary, DeptID)
VALUES ('Neha Verma', 45000, 10);
```

**🔴 Sample Output:**

```
ERROR 1452 (23000): Cannot add or update a child row:
a foreign key constraint fails (`test`.`Employees`, CONSTRAINT `Employees_ibfk_1` FOREIGN KEY (`DeptID`) REFERENCES `Departments` (`DeptID`))
```

✅ MySQL prevents inserting a record with a department ID that doesn’t exist in the `Departments` table.

---

## Task 6 – Delete a Department (and See Constraint in Action)

Try deleting a department that is being used by an employee.

```sql
DELETE FROM Departments WHERE DeptID = 1;
```

**🔴 Sample Output:**

```
ERROR 1451 (23000): Cannot delete or update a parent row:
a foreign key constraint fails (`test`.`Employees`, CONSTRAINT `Employees_ibfk_1` FOREIGN KEY (`DeptID`) REFERENCES `Departments` (`DeptID`))
```

✅ MySQL prevents deleting a department that has employees assigned.

---

## Task 7 – Use ON DELETE CASCADE

To automatically delete employees when their department is deleted, modify the foreign key with **ON DELETE CASCADE**.

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY AUTO_INCREMENT,
    EmpName VARCHAR(50),
    Salary DECIMAL(10,2),
    DeptID INT,
    FOREIGN KEY (DeptID) REFERENCES Departments(DeptID) ON DELETE CASCADE
);
```

Now, deleting a department will also delete all related employees automatically.

---

## ✅ Concepts Practiced

| Concept           | Description                        | Example                |
| ----------------- | ---------------------------------- | ---------------------- |
| FOREIGN KEY       | Links two tables                   | `FOREIGN KEY (DeptID)` |
| Parent Table      | The table referenced by FK         | `Departments`          |
| Child Table       | The table containing FK            | `Employees`            |
| ON DELETE CASCADE | Deletes related rows automatically | `ON DELETE CASCADE`    |

---

## Bonus Challenge

Create two more tables:

* `Projects(ProjectID, ProjectName, DeptID)`
* `Departments(DeptID, DeptName)`

Then, define a **foreign key** in `Projects` referencing `Departments`, and try inserting invalid department IDs to test constraint behavior.
