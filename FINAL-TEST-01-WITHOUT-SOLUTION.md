# **Final SQL Task – Complete Project Practice (Without Solutions)**

## **Objective:**

Design and query a small company database using SQL concepts — including creating databases, tables, constraints, and performing advanced queries.

---

## **Step 1: Create a Database**

Write a query to create a database named **CompanyDB**.

---

## **Step 2: Use the Database**

Write a query to select and use the **CompanyDB** database.

---

## **Step 3: Create Tables**

### **a) Employees Table**

Create a table **Employees** with the following structure:

* **EmpID** → INT, Primary Key, Auto Increment
* **Name** → VARCHAR(50), Not Null, Unique
* **DepartmentID** → INT
* **Salary** → DECIMAL(10,2), with a check that salary must be greater than 0
* **City** → VARCHAR(30), default value ‘Delhi’
* **HireDate** → DATE

---

### **b) Departments Table**

Create a table **Departments** with the following structure:

* **DepartmentID** → INT, Primary Key
* **DepartmentName** → VARCHAR(50), Not Null

---

## **Step 4: Insert Data**

Insert at least **3 departments** and **5 employees** into their respective tables.
Make sure:

* Employees belong to different departments.
* Salaries vary across employees.
* Include at least one employee with a city other than Delhi.

### **Employees Table Data**

| **EmpID** | **Name** | **DepartmentID** | **Salary (₹)** | **City**  | **HireDate** |
| --------: | -------- | ---------------: | -------------: | --------- | ------------ |
|         1 | Ramesh   |                1 |       40000.00 | Delhi     | 2020-02-15   |
|         2 | Priya    |                2 |       60000.00 | Mumbai    | 2019-10-20   |
|         3 | Anil     |                3 |       55000.00 | Bangalore | 2021-01-10   |
|         4 | Neha     |                2 |       70000.00 | Delhi     | 2022-05-22   |
|         5 | Suresh   |                1 |       30000.00 | Chennai   | 2018-09-05   |


### **Departments Table Data**

| **DepartmentID** | **DepartmentName** |
| ---------------: | ------------------ |
|                1 | HR                 |
|                2 | IT                 |
|                3 | Finance            |

---

## **Step 5: SQL Queries**

Perform the following tasks using SQL queries:

---

### **1. SELECT with WHERE**

Display all employees whose salary is greater than **₹50,000**.

---

### **2. ORDER BY**

Display employee names and salaries in **descending order of salary**.

---

### **3. JOIN**

Display employee names, department names, and salaries using an **INNER JOIN** between both tables.

---

### **4. GROUP BY + HAVING**

Find the **average salary** of each department.
Show only those departments where the average salary is **greater than ₹40,000**.

---

### **5. CASE Statement**

Display each employee’s name, salary, and a new column **SalaryCategory**:

* “High Earner” if salary ≥ 60000
* “Average Earner” if salary between 40000–59999
* “Low Earner” otherwise

---

### **6. DATE Function**

Display each employee’s name along with the **year** they were hired.

---

### **7. Aggregate Functions**

Display:

* Total number of employees
* Total salary
* Average salary

---

### **8. Subquery (IN)**

Display names and salaries of employees who work in the **IT** department (use a subquery).

---

### **9. DELETE Example**

Delete employees whose salary is **less than ₹35,000**.

---

### **10. DROP TABLE**

Write a query to **drop** the **Employees** table if it exists.

---

## **Concepts You Should Apply**

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
