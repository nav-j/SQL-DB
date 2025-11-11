# **Final SQL Task – School Management Database (Without Solutions)**

## **Objective:**

Build and query a small **School Management System** database using MySQL.
This exercise will help you practice **database creation, constraints, joins, subqueries, aggregate functions, and conditions**.

---

## **Step 1: Create Database**

Write a query to create a database named **SchoolDB**.

---

## **Step 2: Use Database**

Write a query to select and use the **SchoolDB** database.

---

## **Step 3: Create Tables**

### **a) Students Table**

Create a table named **Students** with the following columns:

* `StudentID` → INT, Primary Key, Auto Increment
* `Name` → VARCHAR(50), Not Null
* `Age` → INT, with a check constraint that Age must be greater than 5
* `City` → VARCHAR(30), default value ‘Delhi’
* `ClassID` → INT

---

### **b) Classes Table**

Create a table named **Classes** with the following columns:

* `ClassID` → INT, Primary Key
* `ClassName` → VARCHAR(50), Not Null
* `TeacherID` → INT

---

### **c) Teachers Table**

Create a table named **Teachers** with the following columns:

* `TeacherID` → INT, Primary Key, Auto Increment
* `Name` → VARCHAR(50), Not Null
* `Subject` → VARCHAR(50)
* `Salary` → DECIMAL(10,2)

---

## **Step 4: Insert Data**

Insert sample data into all three tables:

* At least **4 teachers** with different subjects and salaries
* At least **4 classes**, each linked to a teacher
* At least **6 students** enrolled in different classes

Ensure:

* Some students belong to the same class
* Include students from at least **three different cities**

---

## **Step 5: Perform SQL Queries**

Perform the following tasks using appropriate SQL queries.

---

### **1️⃣ Display All Students with Their Class and Teacher Names**

Display all students’ names along with their class names and the respective teacher names.

---

### **2️⃣ Find Students from Delhi**

Show all students whose city is **‘Delhi’**.

---

### **3️⃣ Find Average Teacher Salary**

Display the **average salary** of all teachers.

---

### **4️⃣ Display Highest and Lowest Teacher Salary**

Show the **maximum** and **minimum** salaries from the Teachers table.

---

### **5️⃣ Categorize Teachers by Salary Using CASE**

Display each teacher’s name and a new column `SalaryCategory`:

* “Highly Paid” if salary ≥ 58000
* “Moderately Paid” if salary between 52000 and 57999
* “Low Paid” otherwise

---

### **6️⃣ Display Classes Having More Than 1 Student**

Show class names that have **more than one student** enrolled.

---

### **7️⃣ Subquery: Teachers with Salary Greater Than Average**

Find and display teachers whose salary is **greater than the average salary** of all teachers.

---

### **8️⃣ Delete a Student Younger Than 13**

Write a query to delete any student whose **age is less than 13**.

---

### **9️⃣ Drop Table Example**

Write a query to drop the **Students** table if it already exists.

---

## **Concepts You Should Apply**

✅ CREATE DATABASE / TABLE
✅ PRIMARY KEY, CHECK, DEFAULT constraints
✅ INSERT, DELETE, SELECT
✅ JOIN (INNER JOIN)
✅ WHERE, GROUP BY, HAVING
✅ SUBQUERY
✅ CASE statement
✅ AGGREGATE functions (AVG, MAX, MIN, COUNT)
✅ DROP TABLE

---
