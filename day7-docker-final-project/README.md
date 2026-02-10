# Docker Day 7 – Multi-Container Application (Flask + Nginx)

## Project Overview
This project demonstrates a real-world Docker setup using a multi-container architecture.
A Flask backend runs as one container, and Nginx runs as another container acting as a reverse proxy.
Both services are managed using Docker Compose.

---

## Project Structure


day7-docker-final-project
├── backend
│ ├── Dockerfile
│ └── app.py
├── frontend
│ └── nginx.conf
├── docker-compose.yml
└── README.md


---

## Technologies Used
- Docker
- Docker Compose
- Python (Flask)
- Nginx
- AWS EC2 (Ubuntu)

---

## Application Flow


Browser → Nginx (Port 80) → Flask Backend (Port 5000)


- Nginx is exposed to the browser on port 80
- Flask runs internally on port 5000
- Backend port is not exposed publicly for security

---

## How to Run the Project

1. Navigate to the project directory
```bash
cd day7-docker-final-project


Start the application

docker compose up -d


Access in browser

http://<EC2-PUBLIC-IP>

Ports Used
Service	Port	Access
Nginx	80	Public
Flask	5000	Internal
Key Learnings

Multi-container Docker architecture

Nginx as a reverse proxy

Docker internal networking

Docker Compose orchestration

Security best practices (expose only required ports)






