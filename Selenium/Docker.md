# 🐳 Docker Beginner Practice Guide

---

## 🧱 STEP 0 — Check Docker Is Installed

Open terminal and run:

    docker --version

- If it prints a version → Docker is installed.
- If not → Install Docker Desktop first.

---

## 🟢 STEP 1 — Run Your First Container (No Code)

Run:

    docker run hello-world

### What Happens?

Docker will:

- Download the image
- Create a container
- Run it
- Print a message
- Stop the container

You just created and ran your first container 🎉

### Check Images

    docker images

You should see:

    hello-world

That is an image.

### Check Containers

    docker ps -a

You will see a stopped container.

---

## 🟢 STEP 2 — Run a Real Linux Machine Inside Docker

Run:

    docker run -it ubuntu bash

Now you are inside a Linux container.

Try:

    ls
    pwd

You are inside a mini OS.

Exit:

    exit

Container stops.

---

## 🟢 STEP 3 — Create Your Own Image

### 1️⃣ Create Folder

    mkdir docker-practice
    cd docker-practice

### 2️⃣ Create app.py

Create a file named `app.py` and add:

```python
print("Docker is easy 🚀")
```

## 3️⃣ Create Dockerfile

Create a file named `Dockerfile` (no extension).

Add the following:

```dockerfile
FROM python:3.10
WORKDIR /app
COPY app.py .
CMD ["python", "app.py"]
```

## 🟢 STEP 4 — Build Your Image

Inside the folder run:

```bash
docker build -t myapp .
```

### 🔍 Check Images

Run:

```bash
docker images
```

## 🟢 STEP 5 — Run Container From Your Image

```bash
docker run myapp
```
Output:

Docker is easy 🚀

That is your container running.

## 🧠 What Just Happened?

- Dockerfile → Blueprint  
- docker build → Creates image  
- docker run → Creates container  

Image = Template  
Container = Running instance


## 🟢 STEP 6 — See Containers

### Running containers:

```bash
docker ps
```
All containers (including stopped):

```python
docker ps -a
```

## 🟢 STEP 7 — Remove Container

### Find container ID:

```bash
docker ps -a
```
Then:
```python
docker rm <container_id>
```
### 🟢 STEP 8 — Remove Image
```python
docker rmi myapp
```
