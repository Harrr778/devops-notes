# 🏗️ Kubernetes Pods & Deployments (DevOps)

[[Kubernetes Basics]] ← Previous | Next → [[Kubernetes Services & Networking]]

> [!info] Purpose
Pods and Deployments are **core building blocks** of Kubernetes.  
They define how containers run, scale, and update in a cluster.

---

## 🔹 Pods
- Smallest deployable unit in Kubernetes  
- Can contain **one or more containers**  
- Share **networking and storage**  
- Ephemeral (short-lived) → managed via **Deployments**  

---

### Example: Pod YAML
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: nginx-pod
  labels:
    app: nginx
spec:
  containers:
    - name: nginx
      image: nginx:latest
      ports:
        - containerPort: 80
```

Apply and check

```bash
kubectl apply -f nginx-pod.yaml
kubectl get pods
kubectl describe pod nginx-pod
kubectl logs nginx-pod
```

---

## 🔹 Deployments

- Higher-level object that manages Pods
    
- Supports **scaling**, **rolling updates**, and **self-healing**
    
- Ensures **desired state = actual state**

Example: Deployment YAML
```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
        - name: nginx
          image: nginx:1.25
          ports:
            - containerPort: 80
```

Commands
```bash
kubectl apply -f nginx-deployment.yaml
kubectl get deployments
kubectl get pods
```

## 🔹 Scaling

```bash
# Scale to 5 replicas
kubectl scale deployment nginx-deployment --replicas=5

# Autoscale (HPA)
kubectl autoscale deployment nginx-deployment --cpu-percent=80 --min=2 --max=10
```

## 🔹 Updating a Deployment

```bash
# Update image
kubectl set image deployment/nginx-deployment nginx=nginx:1.26

# Rollout status
kubectl rollout status deployment/nginx-deployment

# Rollback
kubectl rollout undo deployment/nginx-deployment
```

## 🔹 Delete Pods & Deployments

```bash
kubectl delete pod nginx-pod
kubectl delete deployment nginx-deployment
```

## 🔹 Python + Kubernetes

```python
from kubernetes import client, config

config.load_kube_config()
apps_v1 = client.AppsV1Api()

# Create Deployment (simplified)
deployment = client.V1Deployment(
    metadata=client.V1ObjectMeta(name="nginx-deployment"),
    spec=client.V1DeploymentSpec(
        replicas=2,
        selector={"matchLabels": {"app": "nginx"}},
        template=client.V1PodTemplateSpec(
            metadata=client.V1ObjectMeta(labels={"app": "nginx"}),
            spec=client.V1PodSpec(
                containers=[client.V1Container(
                    name="nginx",
                    image="nginx:latest",
                    ports=[client.V1ContainerPort(container_port=80)]
                )]
            )
        )
    )
)

apps_v1.create_namespaced_deployment(namespace="default", body=deployment)
```

## 🔹 Best Practices

- Use **Deployments**, not raw Pods
    
- Always set **replicas ≥ 2** for production
    
- Use **labels and selectors** for organization
    
- Define **resource requests & limits**
    
- Monitor rollouts and use `kubectl rollout undo` when needed
    

---

> [!tip]  
> Pods are **single units** but short-lived.  
> Deployments ensure **scalability, availability, and updates** in DevOps workflows.