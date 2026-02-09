# 🐳 Docker Day 6 – Docker Compose

## 📌 Objective
Learn how to use **Docker Compose** to run and manage **multi-container applications** using a single YAML configuration file.

---

## 🧠 Why Docker Compose?
Running multiple containers using `docker run` commands is hard to manage and not scalable.

Docker Compose allows:
- One-command startup & shutdown
- Built-in networking
- Service-to-service communication
- Clean and repeatable deployments

---

## 📦 What is Docker Compose?
Docker Compose is a tool used to define and run **multi-container Docker applications** using a `docker-compose.yml` file.

---

## 📁 Project Structure

day6-docker-compose/
├── docker-compose.yml
├── README.md


---

## 🧾 docker-compose.yml
```yaml
version: "3.8"

services:
  frontend:
    image: nginx
    ports:
      - "8080:80"
    depends_on:
      - backend

  backend:
    image: nginx


▶️ Run the Application
docker compose up -d


Verify:

docker ps

🔄 Test Container Communication
docker compose exec frontend curl http://backend


✔ Docker Compose creates a default network
✔ Services communicate using service names

⛔ Stop and Remove Containers
docker compose down

🧠 Key Learnings

Docker Compose simplifies multi-container management

YAML files are declarative, not procedural

Services act as containers

Networking is automatic in Docker Compose

🎯 Interview Explanation

Docker Compose is used to define and run multi-container applications using a single YAML file. It simplifies container orchestration, networking, and lifecycle management.

