## **Task – Using ALTER TABLE in MySQL**

###  **Objective:**

Learn how to **modify an existing table** using the `ALTER TABLE` statement — including adding, deleting, and changing columns.

---

###  **Table Used:** `Employees`

| EmpID | Name   | Department | Salary |
| ----- | ------ | ---------- | ------ |
| 1     | Ramesh | HR         | 40000  |
| 2     | Priya  | IT         | 55000  |
| 3     | Neha   | IT         | 45000  |

---

###  **Task 1 – Add a New Column**

Add a new column `City` to the `Employees` table.

```sql
ALTER TABLE Employees
ADD City VARCHAR(50);
```

** Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

**Updated Table Structure:**

| EmpID | Name   | Department | Salary | City |
| ----- | ------ | ---------- | ------ | ---- |
| 1     | Ramesh | HR         | 40000  | NULL |
| 2     | Priya  | IT         | 55000  | NULL |
| 3     | Neha   | IT         | 45000  | NULL |

---

### **Task 2 – Modify Data Type of a Column**

Change the data type of the `Salary` column from `INT` to `DECIMAL(10,2)`.

```sql
ALTER TABLE Employees
MODIFY Salary DECIMAL(10,2);
```

** Sample Output:**

```
Query OK, 0 rows affected (0.05 sec)
Records: 0  Duplicates: 0  Warnings: 0
```

**Result:**
Now `Salary` supports decimal values like `55000.50`.

---

### **Task 3 – Rename a Column**

Rename the column `Department` to `DeptName`.

```sql
ALTER TABLE Employees
CHANGE Department DeptName VARCHAR(50);
```

** Sample Output:**

```
Query OK, 0 rows affected (0.04 sec)
```

**Updated Table Structure:**

| EmpID | Name   | DeptName | Salary   | City |
| ----- | ------ | -------- | -------- | ---- |
| 1     | Ramesh | HR       | 40000.00 | NULL |
| 2     | Priya  | IT       | 55000.00 | NULL |
| 3     | Neha   | IT       | 45000.00 | NULL |

---

###  **Task 4 – Drop a Column**

Remove the `City` column from the `Employees` table.

```sql
ALTER TABLE Employees
DROP COLUMN City;
```

** Sample Output:**

```
Query OK, 0 rows affected (0.03 sec)
```

**Updated Table Structure:**

| EmpID | Name   | DeptName | Salary   |
| ----- | ------ | -------- | -------- |
| 1     | Ramesh | HR       | 40000.00 |
| 2     | Priya  | IT       | 55000.00 |
| 3     | Neha   | IT       | 45000.00 |

---

###  **Task 5 – Rename the Table**

Rename the table `Employees` to `Employee_Details`.

```sql
ALTER TABLE Employees
RENAME TO Employee_Details;
```

**Sample Output:**

```
Query OK, 0 rows affected (0.02 sec)
```

**Verification:**

```sql
SHOW TABLES;
```

**Sample Output:**

| Tables_in_test   |
| ---------------- |
| Employee_Details |

---

### ✅ **Concepts Covered**

| Command       | Description                      |
| ------------- | -------------------------------- |
| `ADD COLUMN`  | Adds a new column                |
| `MODIFY`      | Changes data type or constraints |
| `CHANGE`      | Renames a column                 |
| `DROP COLUMN` | Deletes a column                 |
| `RENAME TO`   | Renames the entire table         |
