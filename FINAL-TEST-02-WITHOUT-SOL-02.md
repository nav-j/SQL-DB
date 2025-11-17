# **Final SQL Task – School Management Database**

## **Objective:**

Build and query a small **School Management System** database using MySQL.

## **Step 1: Create Database SchoolDB**

## **Step 2: Use Database SchoolDB**

## **Step 3: Create Tables**

### **Students Table**

| **Column Name** | **Data Type** | **Constraints / Description**                    |
| --------------- | ------------- | ------------------------------------------------ |
| **StudentID**   | INT           | Primary Key, Auto Increment                      |
| **Name**        | VARCHAR(50)   | NOT NULL                                         |
| **Age**         | INT           | CHECK (Age > 5)                                  |
| **City**        | VARCHAR(30)   | DEFAULT 'Delhi'                                  |
| **ClassID**     | INT           | Can store class reference (foreign key if added) |

### **Classes Table**

| **Column Name** | **Data Type** | **Constraints / Description** |
| --------------- | ------------- | ----------------------------- |
| **ClassID**     | INT           | Primary Key                   |
| **ClassName**   | VARCHAR(50)   | NOT NULL                      |
| **TeacherID**   | INT           | Stores linked teacher’s ID    |

### **Teachers Table**

| **Column Name** | **Data Type** | **Constraints / Description**       |
| --------------- | ------------- | ----------------------------------- |
| **TeacherID**   | INT           | Primary Key, Auto Increment         |
| **Name**        | VARCHAR(50)   | NOT NULL                            |
| **Subject**     | VARCHAR(50)   | Can be NULL (optional subject name) |
| **Salary**      | DECIMAL(10,2) | Stores salary with 2 decimal places |

## **Step 4: Insert Data**

### **Teachers Table**

| **TeacherID** | **Name**    | **Subject** | **Salary (₹)** |
| ------------: | ----------- | ----------- | -------------: |
|             1 | Amit Sharma | Maths       |       55000.00 |
|             2 | Pooja Singh | Science     |       60000.00 |
|             3 | Raj Mehta   | English     |       50000.00 |
|             4 | Neha Kapoor | History     |       58000.00 |

### **Classes Table**

| **ClassID** | **ClassName** | **TeacherID** |
| ----------: | ------------- | ------------: |
|           1 | 10th Grade    |             1 |
|           2 | 9th Grade     |             2 |
|           3 | 8th Grade     |             3 |
|           4 | 7th Grade     |             4 |

### **Students Table**

| **StudentID** | **Name** | **Age** | **City**  | **ClassID** |
| ------------: | -------- | ------: | --------- | ----------: |
|             1 | Ravi     |      15 | Delhi     |           1 |
|             2 | Anjali   |      14 | Mumbai    |           2 |
|             3 | Suresh   |      13 | Pune      |           3 |
|             4 | Meena    |      12 | Delhi     |           4 |
|             5 | Karan    |      16 | Chennai   |           1 |
|             6 | Neha     |      14 | Bangalore |           2 |



##  **Step 5: Perform SQL Queries**

### **1️ Display All Students with Their Class and Teacher Names**

 **Output:**

| StudentName | ClassName  | TeacherName |
| ----------- | ---------- | ----------- |
| Ravi        | 10th Grade | Amit Sharma |
| Karan       | 10th Grade | Amit Sharma |
| Anjali      | 9th Grade  | Pooja Singh |
| Neha        | 9th Grade  | Pooja Singh |
| Suresh      | 8th Grade  | Raj Mehta   |
| Meena       | 7th Grade  | Neha Kapoor |

---

### **2️ Find Students from Delhi**

 **Output:**

| StudentID | Name  | Age | City  | ClassID |
| --------- | ----- | --- | ----- | ------- |
| 1         | Ravi  | 15  | Delhi | 1       |
| 4         | Meena | 12  | Delhi | 4       |

---

### **3️ Find Average Teacher Salary**

**Output:**

| AvgTeacherSalary |
| ---------------- |
| 55750.00         |

---

### **4️ Display Highest and Lowest Teacher Salary**

 **Output:**

| HighestSalary | LowestSalary |
| ------------- | ------------ |
| 60000.00      | 50000.00     |

---

### **5️ Use CASE Statement to Categorize Teachers by Salary**

 **Output:**

| Name        | SalaryCategory  |
| ----------- | --------------- |
| Amit Sharma | Moderately Paid |
| Pooja Singh | Highly Paid     |
| Raj Mehta   | Low Paid        |
| Neha Kapoor | Highly Paid     |

---

### **6️ Display Classes Having More Than 1 Student**

 **Output:**

| ClassName  | TotalStudents |
| ---------- | ------------- |
| 10th Grade | 2             |
| 9th Grade  | 2             |

---

### **7️ Subquery: Find Teachers with Salary Greater Than Average Salary**

 **Output:**

| Name        | Salary   |
| ----------- | -------- |
| Pooja Singh | 60000.00 |
| Neha Kapoor | 58000.00 |

---

### **8️ Delete a Student Who is Younger Than 13**

### **9️ Drop Table Example**

## **Concepts Covered**

* ✅ CREATE DATABASE / TABLE
* ✅ PRIMARY KEY, CHECK, DEFAULT constraints
* ✅ INSERT, DELETE, SELECT
* ✅ JOIN (INNER JOIN)
* ✅ WHERE, GROUP BY, HAVING
* ✅ SUBQUERY
* ✅ CASE statement
* ✅ AGGREGATE functions (AVG, MAX, MIN, COUNT)
* ✅ DROP TABLE

---
