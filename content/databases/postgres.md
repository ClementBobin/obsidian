# 🐘 PostgreSQL Cheat Sheet

> [!info] PostgreSQL is a powerful open-source relational database known for reliability, feature robustness, and performance. This sheet covers essential commands and configuration tips to get started and work efficiently.

---

## ⚙️ Overview

PostgreSQL, or Postgres, supports advanced data types, powerful functions, and ACID compliance. It’s ideal for transactional applications, BI tools, and scalable web services.

---

## 🚀 Features

- ACID-compliant transactions
    
- JSONB and XML support
    
- Materialized views and triggers
    
- Full-text search
    
- Custom functions and stored procedures
    
- Extensions like PostGIS, TimescaleDB
    

---

## 🧰 Getting Started

### 🛠️ Installation (Ubuntu 20.04)

```bash
sudo apt update
sudo apt install -y postgresql postgresql-contrib postgresql-client
sudo systemctl status postgresql.service
```

### ☁️ Install on Kubernetes via Zalando Operator

> [!example]  
> Useful for production-grade PostgreSQL in Kubernetes environments.

Resources:

- [Zalando Operator Guide](https://thedatabaseme.de/2022/03/13/keep-the-elefants-in-line-deploy-zalando-operator-on-your-kubernetes-cluster/)
    
- [Backups with WAL-G](https://thedatabaseme.de/2022/03/26/backup-to-s3-configure-zalando-postgres-operator-backup-with-wal-g/)
    
- [Restores with WAL-G](https://thedatabaseme.de/2022/05/03/restore-and-clone-from-s3-configure-zalando-postgres-operator-restore-with-wal-g/)
    

---

## 🔐 Initial Access & Configuration

### Connect to PostgreSQL

```bash
sudo -u postgres psql
```

### Set Password

```sql
\password
-- or
ALTER USER postgres WITH PASSWORD 'SuperSecret';
```

### 🔄 Enable Password Auth (pg_hba.conf)

Edit:

```bash
sudo vi /etc/postgresql/12/main/pg_hba.conf
```

Change:

```
local   all             postgres                                peer
```

to:

```
local   all             postgres                                md5
```

Restart:

```bash
sudo systemctl restart postgresql
```

---

## 👥 User & Database Management

### Create User

```sql
CREATE USER myuser WITH ENCRYPTED PASSWORD 'SuperSecret';
```

### Create Database

```sql
CREATE DATABASE dbname OWNER myuser;
```

### Change Owner of Existing DB

```sql
ALTER DATABASE dbname OWNER TO myuser;
```

---

## 💾 Backup & Restore

### 🧳 `pg_dump`

SQL file:

```bash
pg_dump -h host -U user -d dbname --create -Z 9 -f /tmp/db.sql.gz
```

Custom format:

```bash
pg_dump -h host -U user -d dbname -F c -f /tmp/db.dmp
```

Restore SQL:

```bash
psql -d newdb -f db.sql
```

### 📦 `pg_dumpall`

Full instance backup:

```bash
pg_dumpall -h host -U postgres > database.out
```

Restore:

```bash
psql -h host -U postgres -f database.out
```

### 🛠️ `pg_restore`

Restore from custom format:

```bash
pg_restore -h host -U user -d postgres --create -F c /tmp/db.dmp -v
```

---

## Related

- [PostgreSQL Official Docs](https://www.postgresql.org/docs/)
    
- [pgAdmin](https://www.pgadmin.org/)
    
- [Zalando Postgres Operator GitHub](https://github.com/zalando/postgres-operator)
    

---

## Explore More 🌍

- [Postgres Best Practices](https://www.crunchydata.com/blog/postgresql-best-practices)
    
- [Tuning Guide](https://wiki.postgresql.org/wiki/Tuning_Your_PostgreSQL_Server)
    
- [Learn with SQLBolt](https://sqlbolt.com/)
    

---

## Tags 📚

#postgresql #database  #sql #kubernetes

---