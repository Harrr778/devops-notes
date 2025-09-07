# 🌐 Kubernetes Services & Networking (DevOps)

[[Kubernetes Pods & Deployments]] ← Previous | Next → [[Kubernetes Volumes & Storage]]

> [!info] Purpose
Kubernetes Services provide **network access** to Pods.  
They handle **service discovery, load balancing, and external access**.

---

## 🔹 Why Services?
- Pods have **dynamic IPs** (change on restart)  
- Services provide a **stable endpoint**  
- Enable **communication between components**  
- Allow **external traffic** to reach Pods  

---

## 🔹 Service Types
| Type         | Description | Use Case |
|--------------|-------------|----------|
| **ClusterIP** | Default, internal cluster IP | Microservices inside cluster |
| **NodePort**  | Exposes service on a node’s port | Simple external access |
| **LoadBalancer** | Uses cloud provider LB | Production apps |
| **Ingress** | HTTP/HTTPS routing via domain names | Web applications |

---

## 🔹 ClusterIP Example
```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  selector:
    app: nginx
  ports:
    - protocol: TCP
      port: 80
      targetPort: 80
```

**Usage:*

`kubectl apply -f nginx-service.yaml kubectl get svc`

## 🔹 NodePort Example

```yaml
apiVersion: v1
kind: Service
metadata:
  name: nginx-nodeport
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30080
```

**Access via:**  

`http://<NodeIP>:30080`

## 🔹 LoadBalancer Example

```bash
apiVersion: v1
kind: Service
metadata:
  name: nginx-loadbalancer
spec:
  type: LoadBalancer
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
```
☁️ Works in **cloud providers** (AWS, GCP, Azure, etc.)

## 🔹 Ingress Example

- Ingress routes traffic by **domain/paths**
    
- Requires **Ingress Controller** (e.g., NGINX Ingress)

```bash
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
spec:
  rules:
    - host: myapp.local
      http:
        paths:
          - path: /
            pathType: Prefix
            backend:
              service:
                name: nginx-service
                port:
                  number: 80
```

Access via DNS / /etc/hosts:

```lua
127.0.0.1 myapp.local
```

## 🔹 Networking Tools

```bash
kubectl exec -it nginx-pod -- curl http://nginx-service
kubectl exec -it nginx-pod -- ping nginx-service
```

## 🔹 Python + Kubernetes Services

```python
from kubernetes import client, config

config.load_kube_config()
v1 = client.CoreV1Api()

services = v1.list_service_for_all_namespaces()
for svc in services.items:
    print(f"{svc.metadata.namespace} - {svc.metadata.name} ({svc.spec.type})")
```

## 🔹 Best Practices

- Use **ClusterIP** for internal services
    
- Use **Ingress** instead of NodePort in production
    
- Secure Ingress with **TLS certificates**
    
- Label Pods consistently for reliable service selectors
    
- Monitor networking with **kubectl logs, tcpdump, or service mesh**

[!tip]  
Services = **stable networking**  
Ingress = **production-grade HTTP routing**  
Together, they power modern **microservice architectures** in DevOps.