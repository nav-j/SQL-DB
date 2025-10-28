# SQL Task – CHECK Constraint

---

## 🎯 Objective
Learn how to use the **CHECK constraint** in MySQL to enforce data validation rules during insertion or updating of records.

---

## 🔹 What is a CHECK Constraint?

- A **CHECK constraint** ensures that all values in a column satisfy a specific condition.  
- It helps maintain data integrity and consistency within a table.  
- Example: Ensuring that salary is always greater than 0.

---

## Task 1 – Create Table with CHECK Constraint

Create an **Employees** table where:
- Salary must be **greater than or equal to 30000**  
- Age must be **between 21 and 60**

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY AUTO_INCREMENT,
    EmpName VARCHAR(50) NOT NULL,
    Age INT CHECK (Age BETWEEN 21 AND 60),
    Salary DECIMAL(10,2) CHECK (Salary >= 30000)
);
````

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.03 sec)
```

---

## Task 2 – Insert Valid Data

Insert valid employee records that meet the CHECK conditions.

```sql
INSERT INTO Employees (EmpName, Age, Salary)
VALUES
('Ravi Kumar', 25, 40000),
('Neha Sharma', 35, 60000),
('Amit Verma', 45, 80000);
```

**🟢 Sample Output:**

```
Query OK, 3 rows affected (0.02 sec)
```

**Result:**

| EmpID | EmpName     | Age |   Salary |
| ----: | ----------- | --: | -------: |
|     1 | Ravi Kumar  |  25 | 40000.00 |
|     2 | Neha Sharma |  35 | 60000.00 |
|     3 | Amit Verma  |  45 | 80000.00 |

---

## Task 3 – Insert Invalid Age (Fails CHECK)

Try inserting a record where **Age = 19**, which violates the CHECK condition.

```sql
INSERT INTO Employees (EmpName, Age, Salary)
VALUES ('Rahul Mehta', 19, 50000);
```

**🔴 Sample Output:**

```
ERROR 3819 (HY000): Check constraint 'Employees_chk_1' is violated.
```

✅ MySQL prevents inserting data that doesn’t meet the condition.

---

## Task 4 – Insert Invalid Salary (Fails CHECK)

Try inserting a record where **Salary = 25000**, below the minimum limit.

```sql
INSERT INTO Employees (EmpName, Age, Salary)
VALUES ('Priya Singh', 30, 25000);
```

**🔴 Sample Output:**

```
ERROR 3819 (HY000): Check constraint 'Employees_chk_2' is violated.
```

---

## Task 5 – Add a New CHECK Constraint After Table Creation

If the table already exists, you can add a CHECK constraint using **ALTER TABLE**.

```sql
ALTER TABLE Employees
ADD CONSTRAINT chk_name CHECK (EmpName <> '');
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.01 sec)
```

✅ This ensures the `EmpName` column is never empty.

---

## Task 6 – Verify Constraints

Use the following command to list constraints on the Employees table:

```sql
SHOW CREATE TABLE Employees;
```

**🟢 Sample Output (Partial):**

```
CREATE TABLE `Employees` (
  `EmpID` int NOT NULL AUTO_INCREMENT,
  `EmpName` varchar(50) NOT NULL,
  `Age` int CHECK ((`Age` between 21 and 60)),
  `Salary` decimal(10,2) CHECK ((`Salary` >= 30000)),
  CONSTRAINT `chk_name` CHECK ((`EmpName` <> '')),
  PRIMARY KEY (`EmpID`)
)
```

---

## ✅ Concepts Practiced

| Concept         | Description                | Example                                         |
| --------------- | -------------------------- | ----------------------------------------------- |
| CHECK           | Restricts data in a column | `CHECK (Salary >= 30000)`                       |
| ALTER TABLE     | Add constraint later       | `ALTER TABLE Employees ADD CONSTRAINT chk_name` |
| Data Validation | Ensures valid entries      | `Age BETWEEN 21 AND 60`                         |

---

## Bonus Challenge

Create a `Products` table with:

* `Price` must be greater than 100
* `Stock` must be non-negative
* `Category` must be either `'Electronics'`, `'Clothing'`, or `'Furniture'`

Try inserting valid and invalid records to test the constraints.

---
