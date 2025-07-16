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

