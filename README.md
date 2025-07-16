## 📌 Create and Use Screen

Manage terminal sessions with `screen` — useful for long-running processes.

| Action                      | Command                            |
|-----------------------------|-------------------------------------|
| ✅ Create a new screen       | `screen -S mysession`              |
| 🔁 Attach (reconnect)        | `screen -r mysession`              |
| 🔍 List active screens       | `screen -ls`                       |
| 🚪 Detach from screen        | Press `Ctrl + A`, then `D`         |
| ❌ Exit from screen          | Type `exit` inside the screen      |
| 🗑️ Kill a screen (from outside) | `screen -S mysession -X quit`     |





-------------------------------------------------------------------------------------------------------------------------------------------------------




## 🚀 Docker Commands Cheat Sheet

### ✅ Create & Run Containers
| Action                        | Command                                                              |
|-------------------------------|----------------------------------------------------------------------|
| Run container (with name)     | `docker run --name mycontainer -d myimage`                           |
| Build image from Dockerfile   | `docker build -t myimage .`                                          |
| Run with port mapping         | `docker run -d -p 8080:80 --name webapp myimage`                     |
| Run with volume               | `docker run -v /host/path:/container/path -d myimage`                |
| Use docker-compose            | `docker-compose up -d`                                               |


### 🔁 Restart / Stop / Start Containers
| Action              | Command                            |
|---------------------|-------------------------------------|
| Stop container      | `docker stop mycontainer`          |
| Start container     | `docker start mycontainer`         |
| Restart container   | `docker restart mycontainer`       |


### 🗑️ Remove Cache / Volumes / Containers
| Action                         | Command                                      |
|--------------------------------|-----------------------------------------------|
| Remove all stopped containers  | `docker container prune -f`                  |
| Remove all unused volumes      | `docker volume prune -f`                     |
| Remove unused networks         | `docker network prune -f`                    |
| Remove dangling images         | `docker image prune -f`                      |
| Remove all images              | `docker rmi $(docker images -q)`            |
| Remove all containers          | `docker rm $(docker ps -aq)`                |
| Remove all volumes             | `docker volume rm $(docker volume ls -q)`   |


### 📦 Volume & Container Management
| Action                     | Command                                 |
|----------------------------|------------------------------------------|
| List volumes               | `docker volume ls`                      |
| Inspect volume             | `docker volume inspect volume_name`     |
| List containers            | `docker ps -a`                          |
| Remove specific container  | `docker rm container_name`              |
| Remove specific volume     | `docker volume rm volume_name`          |


### 🚀 Deploying with Docker Compose
| Action                        | Command                                |
|-------------------------------|----------------------------------------|
| Start services                | `docker-compose up -d`                |
| Stop services                 | `docker-compose down`                 |
| Rebuild and start fresh       | `docker-compose up --build -d`        |
| Remove everything (with volumes) | `docker-compose down -v`           |


-------------------------------------------------------------------------------------------------------------------------------------------------------


## 🌐 NGINX Commands Cheat Sheet

### ✅ Start / Stop / Reload NGINX
| Action             | Command                    |
|--------------------|----------------------------|
| Start NGINX        | `sudo systemctl start nginx`   |
| Stop NGINX         | `sudo systemctl stop nginx`    |
| Restart NGINX      | `sudo systemctl restart nginx` |
| Reload config      | `sudo systemctl reload nginx`  |
| Enable at boot     | `sudo systemctl enable nginx`  |
| Disable at boot    | `sudo systemctl disable nginx` |

---

### ⚙️ NGINX Configuration

| Action                        | Command                                      |
|-------------------------------|----------------------------------------------|
| Test NGINX config             | `sudo nginx -t`                              |
| Show config file path         | `nginx -V 2>&1 | grep -- '--conf-path'`      |
| Edit default config (Ubuntu)  | `sudo nano /etc/nginx/sites-available/default` |
| List enabled sites            | `ls /etc/nginx/sites-enabled/`              |

---

### 🔁 NGINX Logs & Status

| Action              | Command                                  |
|---------------------|-------------------------------------------|
| Check NGINX status  | `sudo systemctl status nginx`             |
| Access log          | `sudo tail -f /var/log/nginx/access.log`  |
| Error log           | `sudo tail -f /var/log/nginx/error.log`   |

---

### 🧹 Clear NGINX Cache (if used)
> Only needed if you’ve configured a proxy cache

```bash
sudo rm -rf /var/cache/nginx/*
sudo systemctl reload nginx
```


------------------------------------------------------------------------------------------------

## 🐘 PostgreSQL Commands Cheat Sheet

### ✅ Connect to PostgreSQL
| Action                          | Command                                       |
|---------------------------------|-----------------------------------------------|
| Switch to `postgres` user       | `sudo -i -u postgres`                         |
| Open PostgreSQL prompt          | `psql`                                        |
| Connect to a DB                 | `psql -d dbname -U username`                 |
| Connect with host/port         | `psql -h localhost -p 5432 -U username -d dbname` |



### 📂 Database & Table Management
| Action                        | Command                                      |
|-------------------------------|----------------------------------------------|
| List databases                | `\l` or `\list`                              |
| Create database               | `CREATE DATABASE dbname;`                   |
| Drop database                 | `DROP DATABASE dbname;`                     |
| List tables                   | `\dt`                                       |
| Describe table schema         | `\d tablename`                              |
| Create table                  | `CREATE TABLE tablename (...);`             |
| Drop table                    | `DROP TABLE tablename;`                     |



### 👤 User & Role Management
| Action                          | Command                                      |
|---------------------------------|----------------------------------------------|
| List users/roles                | `\du`                                       |
| Create user                     | `CREATE USER username WITH PASSWORD 'pass';` |
| Create superuser                | `CREATE ROLE admin WITH SUPERUSER LOGIN PASSWORD 'pass';` |
| Grant privileges                | `GRANT ALL PRIVILEGES ON DATABASE db TO user;` |
| Grant usage on schema           | `GRANT USAGE ON SCHEMA public TO user;`      |
| Grant all on tables             | `GRANT ALL ON ALL TABLES IN SCHEMA public TO user;` |



### 📋 Common SQL Queries
| Action                       | SQL Statement Example                            |
|------------------------------|--------------------------------------------------|
| Select all rows              | `SELECT * FROM table;`                          |
| Insert a row                 | `INSERT INTO table (col1, col2) VALUES ('a', 1);` |
| Update data                  | `UPDATE table SET col='value' WHERE condition;` |
| Delete data                  | `DELETE FROM table WHERE condition;`            |
| Filter rows                  | `SELECT * FROM table WHERE col='value';`        |
| Count rows                   | `SELECT COUNT(*) FROM table;`                   |
| Order rows                   | `SELECT * FROM table ORDER BY col DESC;`        |



### 🔐 Access & Permissions
| Action                         | Command                                      |
|--------------------------------|----------------------------------------------|
| Revoke all access              | `REVOKE ALL PRIVILEGES ON DATABASE db FROM user;` |
| Alter user password            | `ALTER USER username WITH PASSWORD 'newpass';` |
| Drop user                      | `DROP USER username;`                        |



### 🛠️ Maintenance & Monitoring
| Action                       | Command                                      |
|------------------------------|----------------------------------------------|
| Show active connections      | `SELECT * FROM pg_stat_activity;`           |
| Check version                | `SELECT version();` or `psql --version`     |
| Backup a database            | `pg_dump dbname > backup.sql`               |
| Restore from backup          | `psql dbname < backup.sql`                  |
| Exit psql                    | `\q`                                         |


### 🧠 Shortcuts Inside `psql`
| Shortcut       | Description                    |
|----------------|--------------------------------|
| `\q`           | Quit                            |
| `\l`           | List databases                  |
| `\c dbname`    | Connect to database             |
| `\dt`          | List tables                     |
| `\d table`     | Describe table structure        |
| `\du`          | List roles                      |
| `\!`           | Run shell command               |

## 🛠️ PostgreSQL Table & Row Operations

### 🔧 ALTER TABLE Commands

| Action                            | SQL Command Example                                      |
|-----------------------------------|-----------------------------------------------------------|
| Add new column                    | `ALTER TABLE mytable ADD COLUMN new_col TEXT;`           |
| Drop a column                     | `ALTER TABLE mytable DROP COLUMN col_to_remove;`         |
| Rename a column                   | `ALTER TABLE mytable RENAME COLUMN old TO new;`          |
| Change column data type           | `ALTER TABLE mytable ALTER COLUMN mycol TYPE INTEGER;`   |
| Set column default                | `ALTER TABLE mytable ALTER COLUMN mycol SET DEFAULT 0;`  |
| Drop column default               | `ALTER TABLE mytable ALTER COLUMN mycol DROP DEFAULT;`   |
| Rename table                      | `ALTER TABLE oldname RENAME TO newname;`                 |



### ❌ Delete & Update Rows

| Action                | SQL Command Example                                      |
|------------------------|---------------------------------------------------------|
| Delete specific row(s) | `DELETE FROM mytable WHERE id = 1;`                     |
| Delete all rows        | `DELETE FROM mytable;`                                  |
| Update row value       | `UPDATE mytable SET col1 = 'new' WHERE id = 1;`        |



### 📋 Filtering Rows (Include / Exclude using `WHERE`)

| Action                         | SQL Command Example                                      |
|--------------------------------|-----------------------------------------------------------|
| Select specific rows           | `SELECT * FROM mytable WHERE status = 'active';`         |
| Exclude specific rows          | `SELECT * FROM mytable WHERE status != 'inactive';`      |
| Include multiple values        | `SELECT * FROM mytable WHERE role IN ('admin', 'editor');` |
| Exclude multiple values        | `SELECT * FROM mytable WHERE role NOT IN ('guest', 'banned');` |
| Using `LIKE`                   | `SELECT * FROM users WHERE name LIKE 'A%';`              |



### 🔒 Constraints with ALTER TABLE

| Action                         | SQL Command Example                                      |
|--------------------------------|-----------------------------------------------------------|
| Add primary key                | `ALTER TABLE mytable ADD PRIMARY KEY (id);`              |
| Drop primary key               | `ALTER TABLE mytable DROP CONSTRAINT mytable_pkey;`      |
| Add foreign key                | `ALTER TABLE orders ADD CONSTRAINT fk_user FOREIGN KEY (user_id) REFERENCES users(id);` |
| Drop constraint                | `ALTER TABLE mytable DROP CONSTRAINT constraint_name;`   |
| Add unique constraint          | `ALTER TABLE mytable ADD CONSTRAINT unique_email UNIQUE(email);` |



### 🧪 Check Table Structure

```sql
\d mytable
```

