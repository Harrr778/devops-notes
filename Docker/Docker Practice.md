# 🛠 Docker Practice (DevOps)

[[Docker]] ← Previous | Next → [[Docker Networking]]

> [!info] Purpose
Practice Docker commands to **build, run, monitor, and automate containers**.  
Combines Bash and Python examples for real DevOps workflows.

---

## 🔹 Run Your First Container
```bash
# Pull an image
docker pull nginx

# Run a container in detached mode
docker run -d -p 8080:80 --name webserver nginx

# Check running containers
docker ps

# Stop container
docker stop webserver

# Remove container
docker rm webserver
```

## 🔹 Build & Run Custom Image

```bash
# Build image from Dockerfile
docker build -t myapp:latest .

# Run container with port mapping
docker run -d -p 5000:5000 --name myapp myapp:latest

# Check logs
docker logs myapp

# Enter container shell
docker exec -it myapp /bin/bash
```

## 🔹 Docker Volumes (Persistent Storage)

```bash
# Create volume
docker volume create mydata

# Run container with mounted volume
docker run -d -v mydata:/data --name myapp myapp:latest

# Inspect volume
docker volume inspect mydata
```

## 🔹 Docker Networking

```bash 
# Create a custom network
docker network create mynet

# Run containers on the network
docker run -d --network mynet --name web nginx
docker run -d --network mynet --name app myapp

# Connect container to network
docker network connect mynet another_container
```

## 🔹 Docker Compose Practice

**docker-compose.yml example:**

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
docker-compose ps
docker-compose logs
docker-compose down
```

## 🔹 Monitor & Cleanup

```bash
# Show all containers (running + stopped)
docker ps -a

# Remove unused containers
docker container prune

# Remove unused images
docker image prune -a

# Remove unused volumes
docker volume prune
```

## ## 🔹 Python + Docker

**List containers with Python (docker SDK):**
```python
import docker

client = docker.from_env()
for container in client.containers.list(all=True):
    print(container.name, container.status)
```

Run a container from Python

```python
import docker

client = docker.from_env()
container = client.containers.run("nginx", detach=True, ports={'80/tcp': 8080})
print(container.id)
```

> [!tip]  
> Practice combining **Bash + Docker CLI + Python SDK** for DevOps automation:

- Automate container deployment
    
- Monitor running containers
    
- Cleanup unused resources
    
- Integrate containers in CI/CD pipelines