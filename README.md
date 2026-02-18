# Docker Web Server Stack for CodeIgniter 4 Projects

This repository contains a simple Docker environment for running a PHP web application using:

- Apache Web Server
- PHP 8.5 (Main Application)
- MariaDB LTS (Database)
- phpMyAdmin (Database Management)

The project is designed for local development and supports multiple PHP projects inside the `www/` directory.

---

## 📁 Project Structure

```
.
├── docker-compose.yml
├── php85/
│   └── Dockerfile
├── apache/
│   └── vhost.conf
├── www/
│   └── index.php
└── README.md
```

---

## ⚙️ Services

| Service          | Description            | Port |
| ---------------- | ---------------------- | ---- |
| Apache + PHP 8.5 | Main web server        | 8080 |
| MariaDB LTS      | Database server        | 3309 |
| phpMyAdmin       | Database web interface | 8082 |

---

## 🚀 Getting Started

### 1. Clone Repository

```bash
git clone https://github.com/hafizulwanandaputra/hwp-webapp-docker-ci4.git
cd hwp-webapp-docker-ci4
```

---

### 2. Build and Run Containers

```bash
docker compose up --build -d
```

---

### 3. Access Services

- Web Server → http://localhost:8080
- phpMyAdmin → http://localhost:8082

---

## 🗄️ Database Credentials

Default root credentials:

```
Username : root
Password : root
Host     : db
Port     : 3306
```

> Inside Docker, always use `db` as the hostname — **not localhost**.

---

## 🌐 Web Root

All web files must be placed inside:

```
www/
```

Example:

```
www/index.php
```

---

## 🧩 PHP Extensions

PHP 8.5 container includes extensions required for CodeIgniter 4:

- intl
- mbstring
- mysqli
- pdo
- pdo_mysql
- gd
- zip
- bcmath
- exif

Apache `mod_rewrite` is also enabled.

---

## 🔧 Running Composer / Spark

Execute commands inside the container:

```bash
docker exec -it apache_php85 bash
composer install
php spark serve
```

Or run directly:

```bash
docker exec -it apache_php85 composer install
docker exec -it apache_php85 php spark migrate
```

---

## 🐳 Notes

- Do **not** use `localhost` for inter-container connections.
- Use Docker service names (e.g., `db`).
- Container IP addresses are dynamic and may change.

---

## 📄 License

This project is provided for development and educational purposes.

---

## ✨ Author

Created by **Hafizul Wananda Putra**
