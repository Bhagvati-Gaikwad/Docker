# Docker
# Docker Basics Lab 🚀

This repository documents a **beginner-friendly Docker lab** performed using **Docker Playground (Play with Docker)**. The goal is to understand containers, images, isolation, networking, and cleanup — with **no prior Docker knowledge required**.

---

## 📌 Prerequisites

* A web browser
* Docker Playground account: [https://labs.play-with-docker.com/](https://labs.play-with-docker.com/)
* Basic terminal usage (copy & paste commands)

> 💡 No local installation required. Docker is preinstalled in the playground.

---

## 🧪 Lab Objectives

* Run your first Docker container
* Understand container isolation (PID & networking)
* Use verified images from Docker Hub
* Run multiple containers on the same host
* Expose container ports
* Stop and remove containers safely

---

## 🔹 Part 1: Run Your First Container (Ubuntu + top)

### Step 1: Start a container

```bash
docker container run -t ubuntu top
```

**What this does:**

* Pulls the Ubuntu image (if not present)
* Starts a container
* Runs the `top` command
* Shows process isolation (only one process visible)

---

## 🔹 Part 2: Access the Running Container

### Step 1: Open a second terminal

In Docker Playground, click **Add New Instance**.

### Step 2: List running containers

```bash
docker container ls
```

### Step 3: Exec into the container

```bash
docker container exec -it <container_id> bash
```

### Step 4: View processes inside container

```bash
ps -ef
```

Only container processes will be visible.

Exit the container:

```bash
exit
```
<img width="2880" height="1531" alt="image" src="https://github.com/user-attachments/assets/e3253dbf-2968-44e9-83ec-4757357a016f" />
---

## 🔹 Part 3: Run an NGINX Web Server

```bash
docker container run --detach --publish 8080:80 --name nginx nginx
```


### Access NGINX

* Click **OPEN PORT** in Docker Playground
* Enter **8080**
* You should see **Welcome to nginx!**

---

## 🔹 Part 4: Run a MongoDB Container

```bash
docker container run --detach --publish 8081:27017 --name mongo mongo:3.4
```

### Access MongoDB

* Click **OPEN PORT**
* Enter **8081**

> ⚠️ MongoDB is not a web app — seeing a warning message is normal.

---

## 🔹 Part 5: Verify Running Containers

```bash
docker container ls
```

Expected containers:

| Name  | Image     | Ports        |
| ----- | --------- | ------------ |
| nginx | nginx     | 8080 → 80    |
| mongo | mongo:3.4 | 8081 → 27017 |

---

<img width="2880" height="1704" alt="image" src="https://github.com/user-attachments/assets/ce671c8f-4dd6-4e42-b7a8-f5ff53808715" />
<img width="2880" height="328" alt="image" src="https://github.com/user-attachments/assets/60efe36d-07ea-4dcd-a2dd-7feaf9c135c2" />
<img width="2880" height="610" alt="image" src="https://github.com/user-attachments/assets/8098edd8-ca3a-4fa3-977e-b0c7a45d39b5" />

## 🔹 Part 6: Stop and Remove Containers

### Stop containers

```bash
docker container stop nginx mongo
```

### Remove stopped containers & cleanup

```bash
docker system prune
```

Type `y` when prompted.

---

## 🧹 Verification

```bash
docker container ls -a
```

There should be **no running containers**.
<img width="2880" height="1065" alt="image" src="https://github.com/user-attachments/assets/37ee2d1a-077e-44f7-a33d-144652715a29" />
---

## 🧠 Key Concepts Learned

* Containers are isolated processes
* Containers share the host kernel
* Docker Hub provides verified images
* Port mapping enables external access
* Multiple containers can safely run together

---

## 📚 Useful Commands Cheat Sheet

```bash
docker container ls
docker container stop <name>
docker container exec -it <id> bash
docker system prune
```

---

## ✅ Lab Complete!

You’ve successfully completed a hands-on Docker basics lab 🎉

Next steps:

* Build your own Docker image
* Learn Dockerfile basics
* Explore volumes & networking

Happy Dockering 🐳
