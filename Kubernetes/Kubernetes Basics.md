# ☸️ Kubernetes Basics (DevOps)

[[Docker Compose & Multi-Container Apps]] ← Previous | Next → [[Kubernetes Pods & Deployments]]

> [!info] Purpose
Kubernetes (K8s) is a **container orchestration system**.  
It automates **deployment, scaling, networking, and management** of containers in production environments.

---

## 🔹 History of Kubernetes
- 2003 → Google created **Borg**, an internal cluster manager  
- 2014 → Google open-sourced **Kubernetes**  
- 2015 → Kubernetes 1.0 released under **CNCF**  
- Today → De-facto standard for container orchestration  

---

## 🔹 Why Kubernetes?
- Automates deployment & scaling  
- Provides self-healing (restarts failed pods)  
- Handles service discovery & networking  
- Manages storage and secrets  
- Production-grade orchestration for DevOps  

---

## 🔹 Kubernetes Architecture
| Component     | Role |
|---------------|------|
| **Master Node** | Controls cluster |
| - API Server   | Entry point for kubectl & clients |
| - Scheduler    | Assigns pods to nodes |
| - Controller Manager | Ensures desired state |
| - etcd         | Key-value store for cluster state |
| **Worker Node** | Runs workloads (Pods) |
| - Kubelet      | Communicates with master |
| - Kube Proxy   | Networking |
| - Container Runtime | Runs containers (Docker, containerd) |

---

## 🔹 Key Concepts
- **Cluster** → group of nodes (master + workers)  
- **Node** → machine (VM or physical) in the cluster  
- **Pod** → smallest deployable unit (one or more containers)  
- **Deployment** → manages pods (scaling, updates)  
- **Service** → exposes pods over network  
- **Namespace** → logical isolation inside cluster  

---

## 🔹 First Commands
```bash
# View cluster nodes
kubectl get nodes

# View all pods
kubectl get pods -A

# Create a pod
kubectl run nginx --image=nginx --restart=Never

# View pod logs
kubectl logs nginx

# Delete pod
kubectl delete pod nginx
```

## 🔹 Minikube for Local Kubernetes

- Install Kubernetes locally for practice

```bash
minikube start
kubectl get nodes
```

Access dashboard

```bash
minikube dashboard
```

## 🔹 Python + Kubernetes

Install Python client

```bash
pip install kubernetes
```

List pods

```python
from kubernetes import client, config

config.load_kube_config()
v1 = client.CoreV1Api()
for pod in v1.list_pod_for_all_namespaces().items:
    print(f"{pod.metadata.namespace} - {pod.metadata.name}")
```

---

## 🔹 Best Practices

- Use **namespaces** for separation (dev, staging, prod)
    
- Always define **resource limits** (CPU & memory)
    
- Use **deployments**, not standalone pods
    
- Monitor logs & metrics with Prometheus/Grafana
    
- Store configs in **ConfigMaps** and secrets in **Secrets**

> [!tip]  
> Kubernetes is the backbone of **modern DevOps**.  
> Learn it step by step:

1. Pods → 2. Deployments → 3. Services → 4. Storage → 5. Scaling & Monitoring