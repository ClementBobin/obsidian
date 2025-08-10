# 🗂️ SQLite Cheat Sheet

> [!info] SQLite is a self-contained, file-based relational database engine. It doesn’t require a server to run and is often used in embedded applications, prototyping, or lightweight desktop/mobile apps.

---

## ⚙️ Overview

SQLite stores data in a single cross-platform disk file. It's **zero-configuration**, **serverless**, and supports **SQL transactions**. While it loosely follows PostgreSQL syntax, SQLite is more permissive—particularly around types.

---

## 🚀 Features

- Serverless architecture
    
- Lightweight (~500KB binary)
    
- Atomic commit and rollback
    
- Cross-platform compatible database files
    
- No installation or configuration required
    
- Embeddable in applications (C/C++/Python/etc.)
    

---

## 🧰 Getting Started

### 🏁 Launch SQLite

```bash
sqlite3 my_database.db
```

> [!tip] This command creates the `my_database.db` file if it doesn’t exist and opens the SQLite prompt.

---

## 📚 Common Commands

|Command|Description|
|---|---|
|`.help`|List all SQLite dot-commands|
|`.databases`|Show attached databases|
|`.tables`|List all tables in the current db|
|`.schema`|Show CREATE statements for tables|
|`.headers on`|Enable column headers in output|
|`.mode column`|Format output in aligned columns|
|`.quit`|Exit the SQLite shell|
|`.backup`|Backup current database to file|

> [!example] Run `.backup backup_file.db` in the shell to save a copy.

---

## 🛠️ Basic SQL Commands

### Create Table

```sql
CREATE TABLE users (
  id INTEGER PRIMARY KEY,
  name TEXT,
  email TEXT
);
```

### Insert Data

```sql
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');
```

### Select Data

```sql
SELECT * FROM users;
```

### Update Data

```sql
UPDATE users SET name = 'Bob' WHERE id = 1;
```

### Delete Data

```sql
DELETE FROM users WHERE id = 1;
```

---

## ⚠️ Notes on Type System

> [!warning] SQLite uses **dynamic typing**. You can insert a string into an `INTEGER` column without error.

---

## Related

- [SQLite Documentation](https://sqlite.org/docs.html)
    
- [PostgreSQL Cheat Sheet](https://chatgpt.com/c/databases/postgres.md)
    
- [DB Browser for SQLite](https://sqlitebrowser.org/)
    

---

## Explore More 🌍

- [SQLite CLI Documentation](https://sqlite.org/cli.html)
    
- [SQLite SQL Language Reference](https://sqlite.org/lang.html)
    
- [SQLite With Python](https://docs.python.org/3/library/sqlite3.html)
    

---

## Tags 📚

#sqlite #database  #sql 