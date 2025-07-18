# 📚 BookStack Docker Setup

This repository contains a complete Docker-based setup for running [BookStack](https://www.bookstackapp.com/), a simple, self-hosted wiki platform. It includes a MySQL database, environment configuration, and instructions for backup and restore.

---

## 🚀 Quick Start

### 1. Clone the Repository

```bash
git clone https://github.com/ltsali8220/Bookstacks-docker.git
cd Bookstacks-docker
```

### 2. Start the Containers

```bash
docker-compose up -d
```

BookStack will be available at:  
👉 [http://localhost:8080](http://localhost:8080)

---

## 🔐 Default Login

- **Email:** `admin@admin.com`  
- **Password:** `password`

You can change these credentials after logging in.

---

## ⚙️ Project Structure

```
Bookstacks-docker/
├── docker-compose.yml       # Docker services definition
├── .env                     # (Optional) Environment variables
├── README.md                # This file
└── db_backup.sql            # (Optional) MySQL backup file
```

---

## 💾 Backup & Restore

### 🔄 Backup the Database

To create a backup of your BookStack MySQL database:

```bash
docker exec -t bookstack_db mysqldump -u root -p bookstack > db_backup.sql
```

- Replace `bookstack_db` with your MySQL container name if different.
- Enter the MySQL root password when prompted (default: `root`).

### ♻️ Restore the Database

To restore from a backup:

1. Copy the backup file into the container:
   ```bash
   docker cp db_backup.sql bookstack_db:/db_backup.sql
   ```

2. Run the restore command:
   ```bash
   docker exec -i bookstack_db mysql -u root -p bookstack < /db_backup.sql
   ```

---

## 🧹 Clean Up

To stop and remove all containers:

```bash
docker-compose down
```

To remove volumes (**Warning:** this deletes all data):

```bash
docker-compose down -v
```

---

## 🛠️ Customization

You can modify the `docker-compose.yml` to:

- Change ports
- Use a different database
- Add volumes for persistent storage
- Set environment variables like `APP_KEY`, `DB_PASSWORD`, etc.

---

## 📦 Requirements

- [Docker](https://www.docker.com/products/docker-desktop)
- [Docker Compose](https://docs.docker.com/compose/) (usually included with Docker Desktop)

---

## 📘 Resources

- [BookStack Documentation](https://www.bookstackapp.com/docs/)
- [Docker Hub: solidnerd/bookstack](https://hub.docker.com/r/solidnerd/bookstack)

---

## 🧑‍🔧 Maintainer

**Salivan Veerasekaran**  
[GitHub](https://github.com/ltsali8220)

---

Would you like me to generate a `.gitignore` file next to keep your repo clean and secure?
