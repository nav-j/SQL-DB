# SQL Task – DEFAULT Constraint

---

## 🎯 Objective
Learn how to use the **DEFAULT constraint** in MySQL to automatically insert default values when no value is provided for a column.

---

## 🔹 What is a DEFAULT Constraint?

- A **DEFAULT constraint** assigns a **default value** to a column when no value is specified during an `INSERT` operation.  
- It helps ensure data completeness without requiring manual input for every field.  
- Example: Automatically setting `Status = 'Active'` for new employees.

---

## Task 1 – Create Table with DEFAULT Constraints

Create an **Employees** table with:
- `City` defaulting to `'Delhi'`
- `Status` defaulting to `'Active'`
- `JoinDate` defaulting to the **current date**

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY AUTO_INCREMENT,
    EmpName VARCHAR(50) NOT NULL,
    Department VARCHAR(50),
    City VARCHAR(50) DEFAULT 'Delhi',
    Status VARCHAR(20) DEFAULT 'Active',
    JoinDate DATE DEFAULT (CURRENT_DATE)
);
````

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.03 sec)
```

---

## Task 2 – Insert Data Without Defaults (All Columns Specified)

```sql
INSERT INTO Employees (EmpName, Department, City, Status, JoinDate)
VALUES ('Ravi Kumar', 'IT', 'Mumbai', 'On Leave', '2025-09-20');
```

**🟢 Sample Output:**

```
Query OK, 1 row affected (0.01 sec)
```

**Result:**

| EmpID | EmpName    | Department | City   | Status   | JoinDate   |
| ----: | ---------- | ---------- | ------ | -------- | ---------- |
|     1 | Ravi Kumar | IT         | Mumbai | On Leave | 2025-09-20 |

---

## Task 3 – Insert Data Using Defaults (Some Columns Missing)

```sql
INSERT INTO Employees (EmpName, Department)
VALUES ('Neha Sharma', 'HR');
```

**🟢 Sample Output:**

```
Query OK, 1 row affected (0.01 sec)
```

**Result:**

| EmpID | EmpName     | Department | City  | Status | JoinDate   |
| ----: | ----------- | ---------- | ----- | ------ | ---------- |
|     2 | Neha Sharma | HR         | Delhi | Active | 2025-10-06 |

✅ The `City`, `Status`, and `JoinDate` columns used their **default values**.

---

## Task 4 – Insert Data Overriding Default Values

```sql
INSERT INTO Employees (EmpName, Department, City, Status)
VALUES ('Amit Verma', 'Finance', 'Pune', 'Inactive');
```

**🟢 Sample Output:**

```
Query OK, 1 row affected (0.01 sec)
```

**Result:**

| EmpID | EmpName    | Department | City | Status   | JoinDate   |
| ----: | ---------- | ---------- | ---- | -------- | ---------- |
|     3 | Amit Verma | Finance    | Pune | Inactive | 2025-10-06 |

---

## Task 5 – View All Records

```sql
SELECT * FROM Employees;
```

**🟢 Sample Output:**

| EmpID | EmpName     | Department | City   | Status   | JoinDate   |
| ----: | ----------- | ---------- | ------ | -------- | ---------- |
|     1 | Ravi Kumar  | IT         | Mumbai | On Leave | 2025-09-20 |
|     2 | Neha Sharma | HR         | Delhi  | Active   | 2025-10-06 |
|     3 | Amit Verma  | Finance    | Pune   | Inactive | 2025-10-06 |

---

## Task 6 – Add a DEFAULT Constraint After Table Creation

If the table already exists, you can **add a default value** using `ALTER TABLE`.

```sql
ALTER TABLE Employees
ALTER City SET DEFAULT 'Chennai';
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.02 sec)
```

✅ Now, any new employee added without specifying `City` will have `'Chennai'` as the default.

---

## ✅ Concepts Practiced

| Concept            | Description            | Example                            |
| ------------------ | ---------------------- | ---------------------------------- |
| DEFAULT Constraint | Assigns default values | `City VARCHAR(50) DEFAULT 'Delhi'` |
| CURRENT_DATE       | Inserts today’s date   | `DEFAULT (CURRENT_DATE)`           |
| ALTER TABLE        | Change default value   | `ALTER City SET DEFAULT 'Chennai'` |

---

## Bonus Challenge

Create a `Products` table with:

* `Category` default `'General'`
* `Stock` default `10`
* `CreatedDate` default to current date

Then:

1. Insert records with and without default values.
2. Observe how MySQL automatically fills in missing data.

---
