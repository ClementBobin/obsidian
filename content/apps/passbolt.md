# 🔐 Passbolt

> [!info]  
> **Passbolt** is a free and open-source password manager designed for team collaboration.  
> It's secure, flexible, and ready for automation. Trusted by thousands of organizations, including Fortune 500 companies, newspapers, and governments.

🌐 **Project Homepage**: [Passbolt Homepage](https://passbolt.com/)

---

## 🔍 Overview

- **Type**: Password Manager
    
- **Use Case**: Collaborative password management with strong encryption.
    
- **Key Features**:
    
    - Self-hosted solution
        
    - Role-based access control
        
    - Two-factor authentication (2FA)
        
    - Encryption keys stored locally
        

---

## 🛠️ Features

- 🔑 Secure password management for teams
    
- 🔄 Backup and restore options
    
- ⚙️ Easy to deploy using Docker
    
- 📜 Supports public/private key encryption
    
- 🛡️ Role-based access control (RBAC) for user permissions
    

---

## 🏃 Getting Started

### 🧑‍💻 Create Admin User

Run the following command to create an admin user for Passbolt:

```sh
docker-compose exec passbolt su -m -c "/usr/share/php/passbolt/bin/cake \
                                passbolt register_user \
                                -u <your_email> \
                                -f <first_name> \
                                -l <last_name>\
                                -r admin" -s /bin/sh www-data
```

🌍 **Explore More**: Learn more about user registration in the [Passbolt Docs](https://help.passbolt.com/).

---

## 🔧 Customization and Configuration

### 🗂️ Backup Database

To back up the database, replace `database-container` with your actual database container name and specify the backup location:

```sh
docker exec -i database-container bash -c \
  'mysqldump -u${MYSQL_USER} -p${MYSQL_PASSWORD} ${MYSQL_DATABASE}' \
  > /path/to/backup.sql
```

🌍 **Explore More**: For advanced backup strategies, check the [Passbolt Backup Guide](https://help.passbolt.com/).

### 🗝️ Backup Server Keys

To back up the server's private and public keys, run:

```sh
docker cp passbolt-container:/etc/passbolt/gpg/serverkey_private.asc \
    /path/to/backup/serverkey_private.asc
docker cp passbolt-container:/etc/passbolt/gpg/serverkey.asc \
    /path/to/backup/serverkey.asc
```

> [!warning]  
> Always keep your private keys backed up securely!

---

### 🖼️ Backup Avatars

To back up user avatars:

```sh
docker exec -i passbolt-container \
    tar cvfzp - -C /usr/share/php/passbolt/ webroot/img/avatar \
    > passbolt-avatars.tar.gz
```

---

## 🔄 Related

- **[[Docker]]** — Platform used for deploying Passbolt.
    
- **[[MySQL]]** — Database used by Passbolt for storage.
    

---

## 🌍 Explore More

- 🌐 [Passbolt Documentation](https://help.passbolt.com/)
    
- 🌐 [Passbolt GitHub Repository](https://github.com/passbolt/passbolt)
    

---

## 📚 Tags

- #Passbolt
    
- #PasswordManager
    
- #Docker
    
- #Security
    
- #Backup
    
- #Encryption
    
- #Collaboration
    

---

Let me know if you need to expand on any specific sections like **security configurations**, **role management**, or **integration with other tools**!