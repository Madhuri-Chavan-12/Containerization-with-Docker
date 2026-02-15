# 📌 Docker Compose 

- Docker Compose is a tool that helps you run multiple Docker containers together using a single configuration file (docker-compose.yml).

- Instead of running multiple docker run commands, you define everything in one file and start the full app with one command.

### ✅ Why Use Docker Compose?

i. Manage multi-container apps easily (e.g., Web + DB + Redis)

ii. Simplifies container networking

iii.Easy environment configuration

iv. One command startup/shutdown

---

### 📂 Key File: docker-compose.yml

This YAML file defines:

- Services (containers)

- Images/build context

- Ports

- Volumes

- Networks

- Environment variables

---
**🛠 Basic Example**  
```
version: "3.9"

services:
  web:
    image: nginx
    ports:
      - "8080:80"
```
Run it:  
```
docker compose up
```

Now Nginx runs on:
👉 http://localhost:8080

---

### 🔥 Important Docker Compose Commands  
| Command	| Description  | 
| ----------| -------------|   
| docker compose up	| Start containers  |   
| docker compose up -d	| Start in background (detached)  |   
| docker compose down	| Stop + remove containers  |  
| docker compose ps	| List running services  |   
| docker compose logs	| View logs  |   
| docker compose build	| Build images  |   
| docker compose restart	| Restart services  |   

