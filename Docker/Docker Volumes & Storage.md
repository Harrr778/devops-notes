# 💾 Docker Volumes & Storage (DevOps)

[[Docker Networking]] ← Previous | Next → [[Docker Compose & Multi-Container Apps]]

> [!info] Purpose
Volumes and storage in Docker allow **persistent data storage** that survives container restarts and removals.  
Essential for DevOps when dealing with databases, logs, or user-generated data.

---

## 🔹 Volume Types
| Type      | Description | Use Case |
|-----------|-------------|----------|
| Named Volume | Managed by Docker | Databases, app data |
| Bind Mount   | Maps host directory to container | Config files, code sharing |
| tmpfs        | In-memory storage | Cache, temporary data |

---

## 🔹 Named Volumes
```bash
# Create a named volume
docker volume create mydata

# Run container with volume
docker run -d -v mydata:/data --name myapp myapp:latest

# Inspect volume
docker volume inspect mydata
```

Check files in container
```bash
Check files in container:
```

## 🔹 Bind Mounts

- Map host directory to container

```bash 
docker run -d -v /home/user/app:/app --name myapp myapp:latest

# Changes in host /home/user/app reflect in container /app
```
## 🔹 tmpfs Volumes

- Store **temporary data in memory**

```bash 
docker run -d --tmpfs /cache:rw,size=100m --name myapp myapp:latest
```
## 🔹 Backup & Restore Volumes

**Backup a volume:**

```bash 
docker run --rm -v mydata:/data -v $(pwd):/backup busybox \
    tar cvf /backup/mydata.tar /data
```

Restore a volume:

```bash 
docker run --rm -v mydata:/data -v $(pwd):/backup busybox \
    tar xvf /backup/mydata.tar -C /
```
## 🔹 Python + Docker Volumes

**Inspect volumes:**

```python
import docker

client = docker.from_env()
for vol in client.volumes.list():
    print(vol.name)

```

Attach volume to container (Python SDK):

```python
volume = client.volumes.get("mydata")
container = client.containers.run("myapp", detach=True, volumes={volume.name: {'bind': '/data', 'mode': 'rw'}})
```


## 🔹 Best Practices

- Use **named volumes** for persistent app data
    
- Use **bind mounts** for development (code sharing)
    
- Use **tmpfs** for temporary caches
    
- Always **backup important volumes** regularly
    
- Keep volume names **consistent and documented** in DevOps workflows


> [!tip]  
> Docker volumes are crucial for **databases, logs, and persistent app data**:

- Always plan volume strategy before deploying
    
- Automate backups in DevOps pipelines
    
- Combine volumes with Docker Compose for multi-container apps