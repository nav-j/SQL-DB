# **Final SQL Task – Complete Project Practice**

## **Objective:**

Design and query a small company database using SQL concepts — including creating databases, tables, constraints, and performing advanced queries.

---

## **Step 1: Create a Database**

```sql
CREATE DATABASE CompanyDB;
```

 **Sample Output:**

```
Query OK, 1 row affected (0.01 sec)
```

---

## **Step 2: Use the Database**

```sql
USE CompanyDB;
```
 **Output:**

```
Database changed
```

---

## **Step 3: Create Tables**

### **Employees Table**

```sql
CREATE TABLE Employees (
    EmpID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(50) NOT NULL,
    DepartmentID INT,
    Salary DECIMAL(10,2) CHECK (Salary > 0),
    City VARCHAR(30) DEFAULT 'Delhi',
    HireDate DATE,
    UNIQUE(Name)
);
```

### **Departments Table**

```sql
CREATE TABLE Departments (
    DepartmentID INT PRIMARY KEY,
    DepartmentName VARCHAR(50) NOT NULL
);
```
 **Output:**

```
Query OK, 0 rows affected (0.02 sec)
```

---

## **Step 4: Insert Data**

```sql
INSERT INTO Departments (DepartmentID, DepartmentName)
VALUES 
(1, 'HR'),
(2, 'IT'),
(3, 'Finance');

INSERT INTO Employees (Name, DepartmentID, Salary, City, HireDate)
VALUES
('Ramesh', 1, 40000, 'Delhi', '2020-02-15'),
('Priya', 2, 60000, 'Mumbai', '2019-10-20'),
('Anil', 3, 55000, 'Bangalore', '2021-01-10'),
('Neha', 2, 70000, 'Delhi', '2022-05-22'),
('Suresh', 1, 30000, 'Chennai', '2018-09-05');
```

 **Output:**

```
Query OK, 5 rows affected (0.01 sec)
```

---

## **Step 5: Use SQL Queries**

### **1️ SELECT with WHERE**

```sql
SELECT * FROM Employees
WHERE Salary > 50000;
```

 **Output:**

| EmpID | Name  | DepartmentID | Salary   | City   | HireDate   |
| ----- | ----- | ------------ | -------- | ------ | ---------- |
| 2     | Priya | 2            | 60000.00 | Mumbai | 2019-10-20 |
| 4     | Neha  | 2            | 70000.00 | Delhi  | 2022-05-22 |

---

### **2️ ORDER BY**

```sql
SELECT Name, Salary FROM Employees
ORDER BY Salary DESC;
```

 **Output:**

| Name   | Salary   |
| ------ | -------- |
| Neha   | 70000.00 |
| Priya  | 60000.00 |
| Anil   | 55000.00 |
| Ramesh | 40000.00 |
| Suresh | 30000.00 |

---

### **3️ JOIN**

```sql
SELECT e.Name, d.DepartmentName, e.Salary
FROM Employees e
JOIN Departments d ON e.DepartmentID = d.DepartmentID;
```

 **Output:**

| Name   | DepartmentName | Salary   |
| ------ | -------------- | -------- |
| Ramesh | HR             | 40000.00 |
| Priya  | IT             | 60000.00 |
| Anil   | Finance        | 55000.00 |
| Neha   | IT             | 70000.00 |
| Suresh | HR             | 30000.00 |

---

### **4️ GROUP BY + HAVING**

```sql
SELECT DepartmentID, AVG(Salary) AS AvgSalary
FROM Employees
GROUP BY DepartmentID
HAVING AVG(Salary) > 40000;
```

**Output:**

| DepartmentID | AvgSalary |
| ------------ | --------- |
| 2            | 65000.00  |
| 3            | 55000.00  |

---

### **5️ CASE Statement**

```sql
SELECT Name, Salary,
CASE 
    WHEN Salary >= 60000 THEN 'High Earner'
    WHEN Salary BETWEEN 40000 AND 59999 THEN 'Average Earner'
    ELSE 'Low Earner'
END AS SalaryCategory
FROM Employees;
```

**Output:**

| Name   | Salary   | SalaryCategory |
| ------ | -------- | -------------- |
| Ramesh | 40000.00 | Average Earner |
| Priya  | 60000.00 | High Earner    |
| Anil   | 55000.00 | Average Earner |
| Neha   | 70000.00 | High Earner    |
| Suresh | 30000.00 | Low Earner     |

---

### **6️ DATE Function**

```sql
SELECT Name, YEAR(HireDate) AS JoiningYear
FROM Employees;
```

 **Output:**

| Name   | JoiningYear |
| ------ | ----------- |
| Ramesh | 2020        |
| Priya  | 2019        |
| Anil   | 2021        |
| Neha   | 2022        |
| Suresh | 2018        |

---

### **7️ Aggregate Functions**

```sql
SELECT COUNT(*) AS TotalEmployees,
       SUM(Salary) AS TotalSalary,
       AVG(Salary) AS AverageSalary
FROM Employees;
```
 **Output:**

| TotalEmployees | TotalSalary | AverageSalary |
| -------------- | ----------- | ------------- |
| 5              | 255000.00   | 51000.00      |

---

### **8️ Subquery (IN)**

```sql
SELECT Name, Salary 
FROM Employees
WHERE DepartmentID IN (SELECT DepartmentID FROM Departments WHERE DepartmentName = 'IT');
```

 **Output:**

| Name  | Salary   |
| ----- | -------- |
| Priya | 60000.00 |
| Neha  | 70000.00 |

---

### **9️ DELETE Example**

```sql
DELETE FROM Employees
WHERE Salary < 35000;
```

 **Output:**

```
Query OK, 1 row affected (0.00 sec)
```

---

### **10 DROP TABLE**

```sql
DROP TABLE IF EXISTS Employees;
```

 **Output:**

```
Query OK, 0 rows affected (0.01 sec)
```

---

## **Concepts Covered**

✅ CREATE DATABASE
✅ CREATE TABLE
✅ PRIMARY KEY, CHECK, DEFAULT, UNIQUE Constraints
✅ INSERT, UPDATE, DELETE
✅ SELECT, WHERE, ORDER BY, GROUP BY, HAVING
✅ JOIN, CASE, SUBQUERY
✅ AGGREGATE FUNCTIONS
✅ DATE FUNCTIONS
✅ DROP TABLE

---
