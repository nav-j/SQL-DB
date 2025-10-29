# SQL Task – Working with Dates in MySQL

---

## 🎯 Objective
Learn how to work with **dates and times** in MySQL using built-in functions such as `CURDATE()`, `NOW()`, `DATE_ADD()`, `DATEDIFF()`, `YEAR()`, and more.

---

## 📋 Table: Employees

| EmpID | EmpName     | Department | JoinDate   | BirthDate  |
|-------:|--------------|-------------|-------------|-------------|
| 1 | Ravi Kumar   | IT       | 2022-05-10 | 1995-06-15 |
| 2 | Neha Sharma  | HR       | 2021-08-20 | 1990-11-25 |
| 3 | Amit Verma   | Finance  | 2023-01-05 | 1988-04-09 |
| 4 | Priya Singh  | IT       | 2024-02-28 | 1996-12-30 |
| 5 | Suresh Mehta | HR       | 2020-07-12 | 1985-02-18 |

---

## Task 1 – Display Current Date and Time

```sql
SELECT CURDATE() AS CurrentDate, NOW() AS CurrentDateTime;
````

**🟢 Sample Output:**

| CurrentDate | CurrentDateTime     |
| ----------- | ------------------- |
| 2025-10-06  | 2025-10-06 10:45:00 |

---

## Task 2 – Find Employees Who Joined After 2022

```sql
SELECT EmpName, Department, JoinDate
FROM Employees
WHERE JoinDate > '2022-12-31';
```

**🟢 Sample Output:**

| EmpName     | Department | JoinDate   |
| ----------- | ---------- | ---------- |
| Amit Verma  | Finance    | 2023-01-05 |
| Priya Singh | IT         | 2024-02-28 |

---

## Task 3 – Calculate Number of Days Since Joining

```sql
SELECT EmpName, DATEDIFF(CURDATE(), JoinDate) AS DaysSinceJoining
FROM Employees;
```

**🟢 Sample Output:**

| EmpName      | DaysSinceJoining |
| ------------ | ---------------: |
| Ravi Kumar   |              877 |
| Neha Sharma  |             1503 |
| Amit Verma   |              640 |
| Priya Singh  |              586 |
| Suresh Mehta |             1908 |

---

## Task 4 – Extract Year, Month, and Day from JoinDate

```sql
SELECT EmpName,
       YEAR(JoinDate) AS JoinYear,
       MONTH(JoinDate) AS JoinMonth,
       DAY(JoinDate) AS JoinDay
FROM Employees;
```

**🟢 Sample Output:**

| EmpName      | JoinYear | JoinMonth | JoinDay |
| ------------ | -------: | --------: | ------: |
| Ravi Kumar   |     2022 |         5 |      10 |
| Neha Sharma  |     2021 |         8 |      20 |
| Amit Verma   |     2023 |         1 |       5 |
| Priya Singh  |     2024 |         2 |      28 |
| Suresh Mehta |     2020 |         7 |      12 |

---

## Task 5 – Add 6 Months to Join Date

```sql
SELECT EmpName, JoinDate,
       DATE_ADD(JoinDate, INTERVAL 6 MONTH) AS SixMonthsAfterJoin
FROM Employees;
```

**🟢 Sample Output:**

| EmpName      | JoinDate   | SixMonthsAfterJoin |
| ------------ | ---------- | ------------------ |
| Ravi Kumar   | 2022-05-10 | 2022-11-10         |
| Neha Sharma  | 2021-08-20 | 2022-02-20         |
| Amit Verma   | 2023-01-05 | 2023-07-05         |
| Priya Singh  | 2024-02-28 | 2024-08-28         |
| Suresh Mehta | 2020-07-12 | 2021-01-12         |

---

## Task 6 – Find Employees Whose Birthday Falls in December

```sql
SELECT EmpName, BirthDate
FROM Employees
WHERE MONTH(BirthDate) = 12;
```

**🟢 Sample Output:**

| EmpName     | BirthDate  |
| ----------- | ---------- |
| Priya Singh | 1996-12-30 |

---

## Task 7 – Calculate Employee Age

```sql
SELECT EmpName,
       TIMESTAMPDIFF(YEAR, BirthDate, CURDATE()) AS Age
FROM Employees;
```

**🟢 Sample Output:**

| EmpName      | Age |
| ------------ | --: |
| Ravi Kumar   |  30 |
| Neha Sharma  |  34 |
| Amit Verma   |  37 |
| Priya Singh  |  28 |
| Suresh Mehta |  40 |

---

## Task 8 – Employees Who Joined Within the Last 2 Years

```sql
SELECT EmpName, JoinDate
FROM Employees
WHERE JoinDate >= DATE_SUB(CURDATE(), INTERVAL 2 YEAR);
```

**🟢 Sample Output:**

| EmpName     | JoinDate   |
| ----------- | ---------- |
| Priya Singh | 2024-02-28 |
| Amit Verma  | 2023-01-05 |

---

## Task 9 – Display Employees’ Next Work Anniversary (After 1 Year)

```sql
SELECT EmpName, JoinDate,
       DATE_ADD(JoinDate, INTERVAL 1 YEAR) AS NextAnniversary
FROM Employees;
```

**🟢 Sample Output:**

| EmpName      | JoinDate   | NextAnniversary |
| ------------ | ---------- | --------------- |
| Ravi Kumar   | 2022-05-10 | 2023-05-10      |
| Neha Sharma  | 2021-08-20 | 2022-08-20      |
| Amit Verma   | 2023-01-05 | 2024-01-05      |
| Priya Singh  | 2024-02-28 | 2025-02-28      |
| Suresh Mehta | 2020-07-12 | 2021-07-12      |

---

## Bonus Challenge

1. Find employees who joined **before 2022** and are **older than 35 years**.
2. Show how many **months** each employee has been in the company using `TIMESTAMPDIFF(MONTH, JoinDate, CURDATE())`.
3. Display employees whose birthday is **this month** using `MONTH(BirthDate) = MONTH(CURDATE())`.

---

## ✅ Concepts Practiced

| Function                     | Description                | Example                                     |
| ---------------------------- | -------------------------- | ------------------------------------------- |
| `CURDATE()`                  | Current date               | `CURDATE()`                                 |
| `NOW()`                      | Current date and time      | `NOW()`                                     |
| `DATE_ADD()`                 | Add interval to date       | `DATE_ADD(JoinDate, INTERVAL 6 MONTH)`      |
| `DATE_SUB()`                 | Subtract interval          | `DATE_SUB(CURDATE(), INTERVAL 1 YEAR)`      |
| `DATEDIFF()`                 | Difference in days         | `DATEDIFF(CURDATE(), JoinDate)`             |
| `TIMESTAMPDIFF()`            | Difference in years/months | `TIMESTAMPDIFF(YEAR, BirthDate, CURDATE())` |
| `YEAR()`, `MONTH()`, `DAY()` | Extract date parts         | `YEAR(JoinDate)`                            |

---
