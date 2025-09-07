# 🌐 Docker Networking (DevOps)

[[Docker Practice]] ← Previous | Next → [[Docker Volumes & Storage]]

> [!info] Purpose
Docker networking allows containers to **communicate with each other and the outside world**.  
DevOps engineers must understand bridge, host, overlay networks, and port mapping.

---

## 🔹 Network Types
| Type      | Description | Example Use |
|-----------|-------------|-------------|
| Bridge    | Default isolated network for containers | Small apps, local testing |
| Host      | Shares host network stack | High-performance apps |
| Overlay   | Connects containers across multiple hosts | Swarm, multi-node clusters |
| Macvlan   | Assigns MAC address to container | Direct access to LAN |

---

## 🔹 Bridge Network
- Default network for containers  
- Containers communicate via **container name / IP**  
```bash
# List networks
docker network ls

# Inspect bridge
docker network inspect bridge

# Run container on bridge
docker run -d --name web --network bridge nginx
docker run -d --name app --network bridge myapp
```

Ping between containers

```bash
docker exec -it web ping app
```

## ## 🔹 Host Network

- Container shares **host's network stack**
    
- Useful for low-latency apps

```bash 
docker run --rm --network host myapp
```

## ## 🔹 Overlay Network

- Used in **Docker Swarm / multi-host setups**
    
- Connects containers across hosts

```bash 
# Create overlay network
docker network create -d overlay my_overlay

# Deploy service to overlay network
docker service create --name web --network my_overlay nginx
```

## ## 🔹 Port Mapping

- Map container ports to host ports

```bash
# Map host 8080 → container 80
docker run -d -p 8080:80 nginx

# Multiple ports
docker run -d -p 5000:5000 -p 5001:5001 myapz
```

## 🔹 Connecting Existing Containers

```bash
# Connect container to network
docker network connect mynet container_name

# Disconnect container
docker network disconnect mynet container_name
```

## 🔹 Inspecting Network

```bash 
# Inspect container IP
docker inspect -f '{{ .NetworkSettings.IPAddress }}' container_name

# Show network connections
docker network inspect mynet
```


## 🔹 Python + Docker Networking

**List networks:**

```python
import docker

client = docker.from_env()
for net in client.networks.list():
    print(net.name, net.id)

```


Connect container to network via Python:

```python
network = client.networks.get("mynet")
container = client.containers.get("myapp")
network.connect(container)
```

> [!tip]  
> Docker networking is key for **multi-container apps**:

- Use **bridge** for simple apps
    
- Use **overlay** for Swarm or multi-host setups
    
- Always map ports correctly for external access
    
- Combine CLI + Python SDK for automation