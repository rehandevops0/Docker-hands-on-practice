# 🐳 Docker Hands-On Practice (Day 1 to Day 7)

This repository documents my **7-day Docker learning journey**, starting from Docker basics to building a **real-world multi-container application** using Docker Compose.  
All learning is **hands-on**, practiced on **AWS EC2 (Ubuntu)**.

---

## 🗓️ Day 1 – Docker Basics

### Concepts Learned
- What is Docker and why it is used
- Image vs Container
- Why containers are lightweight
- Docker architecture (Client, Daemon, Image, Container)

### Commands Practiced
```bash
docker --version
docker pull nginx
docker images
docker run nginx
docker run -p 8080:80 nginx
docker ps
docker ps -a

🗓️ Day 2 – Container Lifecycle & Logs
Concepts Learned

    Container lifecycle (run, stop, start, delete)

    Logs and exec

    Foreground vs detached mode

    Why -f is used while removing containers

Commands Practiced

docker run -d nginx
docker stop <container_id>
docker start <container_id>
docker rm <container_id>
docker rm -f <container_id>
docker logs <container_id>
docker exec -it <container_id> /bin/bash

🗓️ Day 3 – Docker Images & Dockerfile
Concepts Learned

    What is a Dockerfile

    Image build process

    RUN vs CMD

    Why containers are immutable

Dockerfile Example

FROM python:3.9-slim
WORKDIR /app
COPY app.py .
RUN pip install flask
CMD ["python", "app.py"]

Commands Practiced

docker build -t flask-app .
docker run -p 5000:5000 flask-app
docker image prune

🗓️ Day 4 – Docker Volumes & Bind Mounts
Concepts Learned

    Data persistence

    Volume vs Bind Mount

    Why containers should not store data internally

Commands Practiced

docker volume create myvolume
docker volume ls
docker run -v myvolume:/data nginx
docker run -v $(pwd):/app nginx

🗓️ Day 5 – Docker Networking
Concepts Learned

    Default bridge network

    Custom bridge network

    Container-to-container communication

    Using service names instead of IPs

Commands Practiced

docker network ls
docker network create mynetwork
docker run --network mynetwork nginx
docker inspect <container_id>
curl http://<container_name>:80

🗓️ Day 6 – Docker Compose
Concepts Learned

    Why Docker Compose is used

    docker-compose.yml structure

    Services, networks, ports

    Single command to manage multi-containers

Commands Practiced

docker compose version
docker compose up
docker compose up -d
docker compose ps
docker compose down

🗓️ Day 7 – Final Real-World Docker Project
Project: Flask Backend + Nginx Frontend
Project Structure

day7-docker-final-project
├── backend
│   ├── Dockerfile
│   └── app.py
├── frontend
│   └── nginx.conf
├── docker-compose.yml
└── README.md

Architecture Flow

Browser → Nginx (Port 80) → Flask Backend (Port 5000)

Key Learnings

    Multi-container architecture

    Nginx as reverse proxy

    Docker internal networking

    Security best practice (only expose required ports)

Run Final Project

docker compose up -d

Access in browser:

http://<EC2-PUBLIC-IP>

🔓 Ports Summary
Service	Port	Access
Nginx	80	Public
Flask	5000	Internal

🎯 

    “I practiced Docker for 7 days starting from basics to building a real-world multi-container application using Docker Compose. I used Flask as backend, Nginx as reverse proxy, and followed security best practices by exposing only required ports.”
