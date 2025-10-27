## 🧩 **Task – Working with Databases**

### 🎯 **Objective:**

Learn how to create, use, and delete a database in MySQL.

---

### 🔹 **Task 1 – CREATE DATABASE**

Create a new database named **CompanyDB**.

```sql
CREATE DATABASE CompanyDB;
```

**🟢 Sample Output:**

```
Query OK, 1 row affected (0.01 sec)
```

---

### 🔹 **Task 2 – USE DATABASE**

Switch to the new database so that all future tables are created inside it.

```sql
USE CompanyDB;
```

**🟢 Sample Output:**

```
Database changed
```

---

### 🔹 **Task 3 – Verify Databases**

Display all databases available on your MySQL server.

```sql
SHOW DATABASES;
```

**🟢 Sample Output:**

| Database           |
| ------------------ |
| CompanyDB          |
| information_schema |
| mysql              |
| performance_schema |
| test               |

---

### 🔹 **Task 4 – DROP DATABASE**

Delete the **CompanyDB** database permanently.

```sql
DROP DATABASE CompanyDB;
```

**🟢 Sample Output:**

```
Query OK, 0 rows affected (0.02 sec)
```

---

### 💡 **Tip:**

Always check databases before dropping one:

```sql
SHOW DATABASES;
```
