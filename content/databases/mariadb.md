# 🛢️ **MariaDB Sheet**

> [!info]  
> **MariaDB** is a robust, open-source relational database system. It’s a community-driven fork of MySQL, known for performance, reliability, and compatibility with existing MySQL setups.

---

## 🚀 **Introduction**

MariaDB is used for storing, retrieving, and managing data efficiently. It’s a popular choice for web development, enterprise apps, and embedded systems.

---

## 🧰 **Installation**

### 🪟 Windows

1. Download the installer from [mariadb.org](https://mariadb.org/download/).
    
2. Run and follow the on-screen steps.
    

### 🍎 macOS (Homebrew)

```bash
brew install mariadb
```

### 🐧 Ubuntu (20.04 LTS+)

```bash
sudo apt update
sudo apt install mariadb-server
sudo mysql_secure_installation
```

### 🎩 RHEL / CentOS

```bash
sudo yum install mariadb-server
```

---

## 🔗 **Connecting to MariaDB**

```bash
mysql -u your_username -p
```

You'll be prompted for your password.

---

## 🌍 **Remote Access**

> [!warning]  
> **Be cautious when opening DB ports publicly.** Secure with firewalls and IP allowlists.

Edit `/etc/mysql/mariadb.conf.d/50-server.cnf`:

```ini
bind-address = 0.0.0.0
```

---

## 🧑‍💻 **Connect via Code**

> [!example] PHP See → [[Php.md]]

You can also connect using:

- Node.js: `mysql2` or `sequelize`
    
- Python: `mysql-connector-python` or `SQLAlchemy`
    
- Java: JDBC drivers
    

---

## 👑 **Create Administrative User**

```sql
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO 'newuser'@'localhost';
FLUSH PRIVILEGES;
```

---

## 🏗️ **Database Operations**

### ➕ Create Database

```sql
CREATE DATABASE your_database_name;
```

### 📁 Select Database

```sql
USE your_database_name;
```

---

## 🧱 **Table Operations**

### 📄 Create Table

```sql
CREATE TABLE your_table_name (
  column1 datatype1 constraints,
  column2 datatype2 constraints
);
```

### ➕ Insert Data

```sql
INSERT INTO your_table_name (column1, column2) VALUES (value1, value2);
```

### 🔍 Query Data

```sql
SELECT column1, column2 FROM your_table_name WHERE condition;
```

### ✏️ Update Data

```sql
UPDATE your_table_name SET column1 = new_value1 WHERE condition;
```

### ❌ Delete Data

```sql
DELETE FROM your_table_name WHERE condition;
```

---

## 🧠 **Tips and Best Practices**

> [!tip]
> 
> - Always use `WHERE` in `UPDATE`/`DELETE` to avoid affecting all rows.
>     
> - Backup databases regularly using `mysqldump`.
>     
> - Secure remote access with SSL and user-based permissions.
>     

---

## 📘 **Conclusion**

MariaDB offers an approachable, powerful platform for managing structured data. Whether you're building web apps, running internal tools, or learning SQL, it’s an excellent RDBMS to master.

> [!quote] _"MariaDB is MySQL’s wiser sibling — open, community-led, and scalable for the real world."_

Explore more features in the [official docs](https://mariadb.org/documentation/).

---

## 📚 **Related**

- [[Php.md]]
    
- [[databases/postgres]]
    
- [[databases]]
    
- [[databases/Metabase]]
    

---

## 🌍 **Explore More**

- [MariaDB vs MySQL Comparison](https://mariadb.com/kb/en/mariadb-vs-mysql-compatibility/)
    
- [MariaDB Client Commands](https://mariadb.com/kb/en/mysql-command-line-client/)
    
- [Secure Remote Access Guide](https://mariadb.com/kb/en/configuring-mariadb-for-remote-client-access/)
    

---

## 🏷️ **Tags 📚**

#mariadb #mysql #sql #databases #devops #linux #webdev #php