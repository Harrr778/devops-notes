# 🐳 Docker (DevOps)

Next → [[Docker Practice]]

> [!info] Purpose
Docker is a **containerization platform** that allows DevOps engineers to package applications and dependencies into portable containers.  
Understanding Docker is essential for **automation, CI/CD, and cloud deployments**.

---

## 🔹 What is Docker?
- **Containers** are lightweight, isolated environments  
- Share host OS kernel but run independently  
- Advantages: portability, scalability, fast deployment  

**Components:**
- **Docker Engine** → runs containers  
- **Docker Hub** → repository for images  
- **Dockerfile** → script to build custom images  

---

## 🔹 Key Concepts
| Concept         | Description                                     |
|-----------------|------------------------------------------------|
| Image           | Read-only template for containers             |
| Container       | Running instance of an image                  |
| Volume          | Persistent storage shared with host           |
| Network         | Isolated communication between containers     |
| Dockerfile      | Instructions to build an image                |

---

## 🔹 Installing Docker
**On Linux (Debian/Ubuntu example):**
```bash
sudo apt update
sudo apt install docker.io
sudo systemctl enable --now docker
sudo usermod -aG docker $USER
```
Check installation:
```bash
docker --version
docker run hello-world
```

## 🔹 Basic Docker Commands

- List images: `docker images`
    
- List containers: `docker ps -a`
    
- Pull image: `docker pull nginx`
    
- Run container: `docker run -d -p 8080:80 nginx`
    
- Stop container: `docker stop <container_id>`
    
- Remove container: `docker rm <container_id>`
    
- Remove image: `docker rmi <image_name>`
    

---

## 🔹 Dockerfile Example

```
# Use official Python image
FROM python:3.11-slim

# Set working directory
WORKDIR /app

# Copy requirements and install
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy app code
COPY . .

# Run app
CMD ["python", "app.py"]
```

## 🔹 Building & Running

```bash
# Build image
docker build -t myapp:latest .

# Run container
docker run -d -p 5000:5000 myapp:latest

# Check logs
docker logs <container_id>
```

## 🔹 Docker Volumes

- Used for **persistent storage**

```bash
# Create volume
docker volume create mydata

# Mount volume in container
docker run -d -v mydata:/data myapp
```

## 🔹 Docker Networking

- Containers can communicate via **bridge, host, or overlay networks**

```bash
# Create custom network
docker network create mynet

# Run container on network
docker run -d --network mynet --name web nginx
docker run -d --network mynet --name app myapp
```

## 🔹 Docker Compose

- Define multi-container apps in **docker-compose.yml**

```yaml
version: "3.9"
services:
  web:
    image: nginx
    ports:
      - "8080:80"
  app:
    build: .
    volumes:
      - .:/app
    ports:
      - "5000:5000"
```

Commands:
```bash
docker-compose up -d
docker-compose down
docker-compose logs
```

## 🔹 Best Practices

- Keep images **small and clean**
    
- Use **.dockerignore** to exclude unnecessary files
    
- Use **named volumes** for persistent data
    
- Always tag images with **version numbers**
    
- Automate builds with **CI/CD pipelines**
    

---

> [!tip]  
> Docker is the backbone of modern DevOps:

- Build reproducible environments
    
- Automate deployments
    
- Scale services quickly in cloud or on-prem