# Docker Day 4 – Volumes & Data Persistence 🐳💾

## 📌 Why This Topic Matters
By default, Docker containers are **ephemeral**.  
If a container stops or is removed, the data inside it is **lost**.

Docker **Volumes** solve this problem by providing **persistent storage**.

---

## 🎯 What I Learned

### 1️⃣ Why Containers Lose Data
- Containers are temporary and replaceable
- Container filesystem is destroyed when the container is deleted

**Interview line:**  
> Container storage is ephemeral by default.

---

### 2️⃣ What is a Docker Volume?
- A **Docker-managed persistent storage**
- Exists **outside the container lifecycle**
- Data remains even after container deletion

**Interview line:**  
> Docker volumes provide persistent storage for containers.

---

### 3️⃣ Volume vs Bind Mount (Fresher Level)

| Feature | Docker Volume | Bind Mount |
|------|------|------|
| Managed by Docker | ✅ Yes | ❌ No |
| Host path required | ❌ No | ✅ Yes |
| Production usage | ✅ Yes | ⚠️ Rare |
| Portable | ✅ Yes | ❌ No |
| Safe | ✅ Yes | ❌ Risky |

**Golden rule:**  
👉 Production → Volumes  
👉 Local development → Bind Mounts

---

### 4️⃣ Real-World Usage of Volumes
- Databases (MySQL, PostgreSQL)
- Logs
- Application uploads
- Jenkins home directory

---

## 🛠 Practical Hands-on (Commands Used)

### 🔹 Step 1: Create Docker Volume
```bash
docker volume create mydata
docker volume ls


🔹 Step 2: Attach Volume to Container
docker run -it --name vol-test -v mydata:/data ubuntu


Inside container:

cd /data
echo "Docker Day 4" > file.txt
cat file.txt
exit

🔹 Step 3: Remove Container
docker rm vol-test


⚠️ Volume is not deleted

🔹 Step 4: Reattach Same Volume to New Container
docker run -it --name vol-test2 -v mydata:/data ubuntu


Inside container:

cd /data
cat file.txt


✅ Data is still present → Persistence proved

Interview line:

Volumes persist data even after container deletion.


🧠 Key Interview Takeaways

✔ Containers are ephemeral
✔ Volumes provide persistent storage
✔ Volumes are Docker-managed
✔ Used mainly for databases and logs

✅ Day 4 Status

✔ Understood ephemeral storage
✔ Created and used Docker volume
✔ Proved data persistence
✔ Learned real-world usage
