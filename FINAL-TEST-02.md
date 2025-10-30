# **Final SQL Task – School Management Database**

## **Objective:**

Build and query a small **School Management System** database using MySQL.
This task will include **database creation, constraints, joins, subqueries, aggregate functions, and conditions** — all in one!

---

## **Step 1: Create Database**

```sql
CREATE DATABASE SchoolDB;
```

 **Output:**

```
Query OK, 1 row affected (0.01 sec)
```

---

## **Step 2: Use Database**

```sql
USE SchoolDB;
```

 **Output:**

```
Database changed
```

---

## **Step 3: Create Tables**

### **Students Table**

```sql
CREATE TABLE Students (
    StudentID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(50) NOT NULL,
    Age INT CHECK (Age > 5),
    City VARCHAR(30) DEFAULT 'Delhi',
    ClassID INT
);
```

### **Classes Table**

```sql
CREATE TABLE Classes (
    ClassID INT PRIMARY KEY,
    ClassName VARCHAR(50) NOT NULL,
    TeacherID INT
);
```

### **Teachers Table**

```sql
CREATE TABLE Teachers (
    TeacherID INT PRIMARY KEY AUTO_INCREMENT,
    Name VARCHAR(50) NOT NULL,
    Subject VARCHAR(50),
    Salary DECIMAL(10,2)
);
```

**Output:**

```
Query OK, 0 rows affected (0.03 sec)
```

---

## **Step 4: Insert Data**

```sql
INSERT INTO Teachers (Name, Subject, Salary)
VALUES
('Amit Sharma', 'Maths', 55000),
('Pooja Singh', 'Science', 60000),
('Raj Mehta', 'English', 50000),
('Neha Kapoor', 'History', 58000);

INSERT INTO Classes (ClassID, ClassName, TeacherID)
VALUES
(1, '10th Grade', 1),
(2, '9th Grade', 2),
(3, '8th Grade', 3),
(4, '7th Grade', 4);

INSERT INTO Students (Name, Age, City, ClassID)
VALUES
('Ravi', 15, 'Delhi', 1),
('Anjali', 14, 'Mumbai', 2),
('Suresh', 13, 'Pune', 3),
('Meena', 12, 'Delhi', 4),
('Karan', 16, 'Chennai', 1),
('Neha', 14, 'Bangalore', 2);
```

 **Output:**

```
Query OK, 6 rows affected (0.01 sec)
```

---

##  **Step 5: Perform SQL Queries**

---

### **1️ Display All Students with Their Class and Teacher Names**

```sql
SELECT s.Name AS StudentName, c.ClassName, t.Name AS TeacherName
FROM Students s
JOIN Classes c ON s.ClassID = c.ClassID
JOIN Teachers t ON c.TeacherID = t.TeacherID;
```

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

```sql
SELECT * FROM Students
WHERE City = 'Delhi';
```

 **Output:**

| StudentID | Name  | Age | City  | ClassID |
| --------- | ----- | --- | ----- | ------- |
| 1         | Ravi  | 15  | Delhi | 1       |
| 4         | Meena | 12  | Delhi | 4       |

---

### **3️ Find Average Teacher Salary**

```sql
SELECT AVG(Salary) AS AvgTeacherSalary FROM Teachers;
```

**Output:**

| AvgTeacherSalary |
| ---------------- |
| 55750.00         |

---

### **4️ Display Highest and Lowest Teacher Salary**

```sql
SELECT MAX(Salary) AS HighestSalary, MIN(Salary) AS LowestSalary
FROM Teachers;
```

 **Output:**

| HighestSalary | LowestSalary |
| ------------- | ------------ |
| 60000.00      | 50000.00     |

---

### **5️ Use CASE Statement to Categorize Teachers by Salary**

```sql
SELECT Name,
CASE 
    WHEN Salary >= 58000 THEN 'Highly Paid'
    WHEN Salary BETWEEN 52000 AND 57999 THEN 'Moderately Paid'
    ELSE 'Low Paid'
END AS SalaryCategory
FROM Teachers;
```
 **Output:**

| Name        | SalaryCategory  |
| ----------- | --------------- |
| Amit Sharma | Moderately Paid |
| Pooja Singh | Highly Paid     |
| Raj Mehta   | Low Paid        |
| Neha Kapoor | Highly Paid     |

---

### **6️ Display Classes Having More Than 1 Student**

```sql
SELECT c.ClassName, COUNT(s.StudentID) AS TotalStudents
FROM Students s
JOIN Classes c ON s.ClassID = c.ClassID
GROUP BY c.ClassName
HAVING COUNT(s.StudentID) > 1;
```

 **Output:**

| ClassName  | TotalStudents |
| ---------- | ------------- |
| 10th Grade | 2             |
| 9th Grade  | 2             |

---

### **7️ Subquery: Find Teachers with Salary Greater Than Average Salary**

```sql
SELECT Name, Salary
FROM Teachers
WHERE Salary > (SELECT AVG(Salary) FROM Teachers);
```

 **Output:**

| Name        | Salary   |
| ----------- | -------- |
| Pooja Singh | 60000.00 |
| Neha Kapoor | 58000.00 |

---

### **8️ Delete a Student Who is Younger Than 13**

```sql
DELETE FROM Students
WHERE Age < 13;
```

 **Output:**

```
Query OK, 1 row affected (0.00 sec)
```

---

### **9️ Drop Table Example**

```sql
DROP TABLE IF EXISTS Students;
```

 **Output:**

```
Query OK, 0 rows affected (0.01 sec)
```

---

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
