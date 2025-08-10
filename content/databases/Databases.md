# 🗄️ **Introduction to Databases**

> [!info]  
> A **database** is a structured collection of data that enables efficient storage, retrieval, and management. They are foundational to modern computing and are used by virtually every application today.

---

## 🧠 **Key Concepts**

### 1. 🧾 **Data**

> Databases can store structured, semi-structured, and unstructured data — such as text, numbers, images, and more — organized into tables, documents, or key-value pairs.

### 2. 🧰 **DBMS (Database Management System)**

> [!example]  
> A DBMS is software for managing a database. It provides tools for data manipulation, security, and structure.  
> **Examples**: `MySQL`, [[databases/postgres|PostgreSQL]], `Oracle`, [[databases/MongoDB|MongoDB]]

### 3. 📝 **SQL (Structured Query Language)**

> SQL is the standard language for querying and managing **relational databases**. It supports operations like:
> 
> - `SELECT`, `INSERT`, `UPDATE`, `DELETE`
>     
> - Defining schemas and constraints
>     

---

## 🧱 **Types of Databases**

> [!abstract]+  
> There are various types of databases, each with distinct architectures and use cases:

### 1. 🧮 **Relational Databases (RDBMS)**

- **Structure**: Table-based
    
- **Schema**: Fixed
    
- **Use Cases**: Banking, ERP, e-commerce
    
- **Examples**: MySQL, [[databases/postgres|PostgreSQL]], Oracle, SQL Server
    

---

### 2. 🌐 **NoSQL Databases**

- **Structure**: Flexible — includes document, key-value, column-family, and graph
    
- **Schema**: Dynamic
    
- **Use Cases**: Web apps, IoT, real-time analytics
    
- **Examples**: [[databases/MongoDB|MongoDB]] (document), Redis (key-value), Cassandra (column-family), Neo4j (graph)
    

---

### 3. 🚀 **NewSQL Databases**

- **Goal**: Marry SQL and horizontal scalability
    
- **Use Cases**: Globally distributed apps with strong consistency
    
- **Examples**: Google Spanner, CockroachDB
    

---

### 4. ⚡ **In-Memory Databases**

- **Storage**: RAM
    
- **Use Cases**: Real-time apps, caching, gaming
    
- **Examples**: Redis, Memcached
    

---

### 5. 📄 **Document Stores**

- **Structure**: JSON or BSON documents
    
- **Use Cases**: CMS, catalogs, schema-evolving apps
    
- **Examples**: [[databases/MongoDB|MongoDB]], CouchDB
    

---

### 6. 🧱 **Column-Family Stores**

- **Structure**: Columns grouped into families
    
- **Use Cases**: Sensor/time-series data, logging
    
- **Examples**: Apache Cassandra, HBase
    

---

### 7. 🔗 **Graph Databases**

- **Structure**: Nodes + Edges
    
- **Use Cases**: Social networks, fraud detection, recommendations
    
- **Examples**: Neo4j, Amazon Neptune
    

---

### 8. 🧭 **Vector Databases**

- **Purpose**: Store and search high-dimensional vectors
    
- **Use Cases**: AI, recommendation systems, similarity search
    
- **Examples**: Faiss, Milvus
    

---

## 🔑 **Importance of Databases**

> [!note] Why are databases critical?

1. 📦 **Storage** – Centralized data storage
    
2. 🔍 **Retrieval** – Efficient querying and indexing
    
3. 🔐 **Integrity** – Enforce data rules and ACID compliance
    
4. 📈 **Scalability** – Handle growth in size and users
    
5. 🛡️ **Security** – Control access and safeguard data
    
6. 📊 **[[databases/Metabase|Analysis]]** – Power business intelligence
    
7. 🧩 **App Support** – Backend for nearly all apps
    

---

## 🧩 **Database Design**

> [!tip] Good design = efficient + accurate  
> Design includes:

- Defining entities and relationships
    
- Normalization to reduce redundancy
    
- Constraints for data integrity (e.g., primary keys, foreign keys)
    

---

## ✅ **Conclusion**

Databases are the core of modern systems. From websites to analytics platforms and AI apps, choosing the **right type of database** is key to performance, scalability, and maintainability. Understanding their structure and use cases empowers better technical decisions.

---

## 📚 **Related**

- [[databases/postgres]]
    
- [[databases/MongoDB]]
    
- [[databases/Metabase]]
    
- [CAP Theorem](https://en.wikipedia.org/wiki/CAP_theorem)
    

---

## 🌍 **Explore More**

- [DB-Engines Ranking](https://db-engines.com/en/ranking)
    
- [SQL vs NoSQL Explained](https://www.mongodb.com/nosql-explained/nosql-vs-sql)
    
- [ACID vs BASE](https://www.ibm.com/topics/acid)
    

---

## 🏷️ **Tags 📚**

#databases #sql #nosql #newsql #graphdatabases #vectordatabases #dbms #dataarchitecture #dataengineering
