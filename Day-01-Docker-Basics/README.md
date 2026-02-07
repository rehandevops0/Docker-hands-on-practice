# 🐳 Docker Day 1 — Zero → Strong Foundation

> **Repository:** Docker-Hands-on-Practices
> **Path:** Day-01-Docker-Basics/README.md

**Environment:** AWS EC2 + MobaXterm
**Goal:** Understand why Docker exists and run your first real container

---

## 📌 What This Day Covers

### 🔹 Theory

* Why Docker was created (real DevOps pain)
* Docker vs Virtual Machine (very common interview question)
* Docker architecture (CLI, Daemon, Image, Container)
* How Docker works internally (Namespaces & Cgroups)
* Real‑world usage of Docker in companies

### 🔹 Practical (Hands‑On)

* Create AWS EC2 instance
* Connect using MobaXterm
* Install Docker
* Run first container (hello‑world)
* Run nginx container
* Verify from browser
* Understand what happened internally

---

## 📘 PART 1 — THEORY

### 1️⃣ Why Docker Was Created (Real Problem)

**Before Docker:**

* App works on developer laptop ❌
* Fails on test/production ❌
* Dependency mismatch
* OS / library conflicts

**Docker Solution:**

* Package application + dependencies + OS libraries
* Run the same container everywhere

🎤 **Interview Line:**

> Docker eliminates environment inconsistency by containerizing applications.

---

### 2️⃣ Docker vs Virtual Machine

| Feature     | Docker             | Virtual Machine |
| ----------- | ------------------ | --------------- |
| Boot Time   | Seconds            | Minutes         |
| Size        | MBs                | GBs             |
| OS          | Shares host kernel | Full OS         |
| Performance | Near‑native        | Slower          |
| Use Case    | Microservices      | Heavy isolation |

🎤 **Interview Line:**

> Docker containers share the host OS kernel, unlike virtual machines which run a full operating system.

---

### 3️⃣ Docker Architecture

```
User → Docker CLI → Docker Daemon → Container
```

* **Docker CLI:** `docker` commands
* **Docker Daemon:** Manages images & containers
* **Image:** Read‑only template
* **Container:** Running instance of image

🎤 **Interview Line:**

> Docker follows a client‑server architecture where the Docker CLI communicates with the Docker Daemon.

---

### 4️⃣ How Docker Works Internally (Basic)

* Uses Linux Kernel
* Uses **Namespaces** → process isolation
* Uses **Cgroups** → CPU & memory control

⚠️ As a fresher, knowing the names is enough.

---

### 5️⃣ Real‑World Usage of Docker

* CI/CD pipelines
* Microservices
* Local development
* Kubernetes pods

---

## 🛠 PART 2 — PRACTICAL

### 🔹 STEP 1: Create AWS EC2 Instance

* **AMI:** Ubuntu / Amazon Linux 2
* **Instance Type:** t2.micro
* **Security Group:**

  * SSH → 22 → My IP
  * Custom TCP → 8080 → Anywhere (for nginx)

---

### 🔹 STEP 2: Connect Using MobaXterm

* Open MobaXterm
* Start SSH session
* Login user:

```
ubuntu   (for Ubuntu AMI)
ec2-user (for Amazon Linux)
```

---

### 🔹 STEP 3A: Update System

```
sudo apt update -y
sudo apt upgrade -y
```

---

### 🔹 STEP 3B: Install Docker

```
sudo apt install docker.io -y
```

Start & enable Docker:

```
sudo systemctl start docker
sudo systemctl enable docker
```

---

### 🔹 STEP 3C: Give User Docker Access

```
sudo usermod -aG docker ubuntu
exit
```

⚠️ Close MobaXterm and reconnect after this step.

---

### 🔹 STEP 3D: Verify Docker Installation

```
docker --version
docker info
```

✔ Docker installed successfully if version details appear.

---

### 🔹 STEP 4: Run First Container

```
docker run hello-world
```

✔ Docker pulls image and prints success message.

---

### 🔹 STEP 5: Run Nginx Container

```
docker pull nginx
docker run -d -p 8080:80 nginx
```

Verify running container:

```
docker ps
```

Open browser:

```
http://<EC2-PUBLIC-IP>:8080
```

---

## 📸 Screenshots (Attached)

* Docker version output
* `docker ps` output
* Nginx default page in browser

*(Screenshots added in repository for proof of hands‑on practice)*

---

## 🎯 Key Takeaways

* Docker solves environment inconsistency
* Containers are lightweight compared to VMs
* Docker is essential for DevOps & Kubernetes
* Successfully deployed nginx using Docker on AWS EC2

---

## important commands whcih i ahve learn on day 1 

* Command 1: docker pull nginx
🔹 What this command does (Simple)

Downloads the nginx image from DockerHub to your local machine.


Command 2: docker run -d -p 8080:80 nginx

⚠️ This is the MOST IMPORTANT command for interviews.

🔹 What this command does (Simple)

Creates and starts a container from the nginx image and exposes it to the outside world.

🔹 Break it word by word (THIS IS GOLD)
docker run -d -p 8080:80 nginx

🔸 docker run

Creates a container

Starts it immediately

If image not present:
👉 Docker automatically pulls it

🔸 -d (Detached mode)

Runs container in background

Terminal is free

🎤 Interview:

“Detached mode is used in production so containers run in background.”

🔸 -p 8080:80 (Port mapping)

This means:

HOST:CONTAINER


8080 → your EC2 instance

80 → nginx inside container

So:

Browser → EC2:8080 → Container:80


Command 3: docker ps
🔹 What this command does (Simple)

Shows currently running containers.

docker ps -a 

shows all conatiners including the stop ones 
