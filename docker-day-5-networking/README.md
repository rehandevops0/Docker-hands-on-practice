# 🐳 Docker Day 5 – Docker Networking

## 📌 Objective
Learn how Docker containers communicate with each other using **Docker networks**, and practice **container-to-container communication** using a **custom bridge network**.

---

## 🧠 Why Docker Networking?
Docker containers are isolated by default.  
Networking allows:
- Container-to-container communication
- Service discovery using container names
- Real-world microservice architecture

---

## 🧱 Docker Network Types
- bridge (default, single host)
- host
- none
- overlay (multi-host)

👉 **Custom bridge network** is used in real-world applications.

---

## 🛠️ Hands-on Practice

### 1️⃣ List Docker Networks
```bash
docker network ls


2️⃣ Create Custom Network
docker network create my_app_network

3️⃣ Run Backend Container
docker run -d \
--name backend \
--network my_app_network \
nginx

4️⃣ Run Frontend Container
docker run -d \
--name frontend \
--network my_app_network \
nginx


Both containers are now on the same custom bridge network.

🔄 Test Communication (Using curl)
docker exec -it frontend curl http://backend


✔ Works because Docker provides internal DNS
✔ Containers communicate using names instead of IPs

❓ Why Not Ping?

Most Docker images are minimal and do not include ping.

✔ curl is preferred because:

Tests real application (HTTP)

Used in production

More practical for DevOps engineers

🔍 Inspect Network
docker network inspect my_app_network

🧹 Cleanup
docker rm -f frontend backend
docker network rm my_app_network

🧠 Key Learnings

Containers need networks to communicate

Custom bridge networks enable name-based communication

Docker provides built-in DNS

curl is better than ping in containers

🎯 Interview Line

Docker networking allows containers to communicate securely. Custom bridge networks enable container name resolution using Docker’s internal DNS, which is a best practice.

