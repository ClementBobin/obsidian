# 🍃 **MongoDB Cheat Sheet**

> [!info] **MongoDB** is a flexible, scalable **NoSQL document database** used widely in modern application development. It stores data in **JSON-like documents**, making it ideal for unstructured or semi-structured data.

---

## ⚙️ Installation

### 🪟 Windows

1. Download MongoDB from the [official website](https://www.mongodb.com/try/download/community).
    
2. Run the installer and follow the setup wizard.
    

---

### 🍏 macOS

Install via Homebrew:

```bash
brew tap mongodb/brew
brew install mongodb-community
```

---

### 🐧 Linux

#### Ubuntu / Debian

```bash
sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv 9DA31620334BD75D9DCB49F368818C72E52529D4

echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list

sudo apt-get update
sudo apt-get install -y mongodb-org
```

#### Red Hat / CentOS

1. Create a repo file:
    

```bash
sudo vi /etc/yum.repos.d/mongodb-org-5.0.repo
```

2. Add:
    

```ini
[mongodb-org-5.0]
name=MongoDB Repository
baseurl=https://repo.mongodb.org/yum/redhat/$releasever/mongodb-org/5.0/x86_64/
gpgcheck=1
enabled=1
gpgkey=https://www.mongodb.org/static/pgp/server-5.0.asc
```

3. Then:
    

```bash
sudo yum install -y mongodb-org
```

---

## 🔄 Starting the MongoDB Service

### Windows

```bash
mongod --install
net start MongoDB
```

---

### macOS / Linux

```bash
sudo systemctl start mongod
```

---

## 🧪 Access MongoDB Shell

```bash
mongo
```

---

## 💻 Basic MongoDB Commands

> [!tip]  
> Use these commands within the `mongo` shell unless otherwise specified.

### 📋 Show Databases

```js
show dbs
```

---

### 🧭 Switch/Create Database

```js
use your_database_name
```

---

### 🗃️ Create a Collection

```js
db.createCollection("your_collection_name")
```

---

### 🧾 Insert Document

```js
db.your_collection_name.insertOne({ key1: "value1", key2: "value2" })
```

---

### 🔍 Find Documents

```js
db.your_collection_name.find()
```

---

### 🔎 Find with Filter

```js
db.your_collection_name.find({ key: "value" })
```

---

### 🛠️ Update One Document

```js
db.your_collection_name.updateOne(
  { key: "value" },
  { $set: { new_key: "new_value" } }
)
```

---

### 🛠️ Update Multiple Documents

```js
db.your_collection_name.updateMany(
  { key: "value" },
  { $set: { new_key: "new_value" } }
)
```

---

### ❌ Delete One Document

```js
db.your_collection_name.deleteOne({ key: "value" })
```

---

### ❌ Delete Multiple Documents

```js
db.your_collection_name.deleteMany({ key: "value" })
```

---

## 🧠 Notes

> [!note] You can connect programmatically using drivers for:
> 
> - [[NodeJS]]
>     
> - [[Python]]
>     
> - [[PHP]]
>     
> - [[Go]]
>     
> 
> Check out: [MongoDB Drivers](https://www.mongodb.com/docs/drivers/)

---

## 📚 Related

- [[databases]]
    
- [[MariaDB Sheet]]
    
- [[Metabase: Open Source Business Intelligence and Analytics]]
    
- [[Php.md]]
    

---

## 🌍 Explore More

- [MongoDB Documentation](https://www.mongodb.com/docs/)
    
- [MongoDB University (Free Courses)](https://university.mongodb.com/)
    
- [MongoDB Compass GUI](https://www.mongodb.com/products/compass)
    

---

## 🏷️ Tags 📚

#mongodb #nosql #database #mongo