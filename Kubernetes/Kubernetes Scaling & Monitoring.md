# 📈 Kubernetes Scaling & Monitoring (DevOps)

[[Kubernetes Volumes & Storage]] ← Previous | Next → [[CD & DevOps]]

> [!info] Purpose
Scaling and monitoring in Kubernetes ensure that apps are **reliable, performant, and observable** in production.

---

## 🔹 Scaling in Kubernetes
- **Manual Scaling** → set replicas manually  
- **Horizontal Pod Autoscaler (HPA)** → scale based on CPU/Memory usage  
- **Vertical Pod Autoscaler (VPA)** → adjust pod resource requests/limits  
- **Cluster Autoscaler** → adds/removes worker nodes

---

## 🔹 Manual Scaling
```bash
# Scale to 5 replicas
kubectl scale deployment nginx-deployment --replicas=5

# Verify
kubectl get deployment nginx-deployment
```

## 🔹 Horizontal Pod Autoscaler (HPA)

```bash
kubectl autoscale deployment nginx-deployment \
  --cpu-percent=70 --min=2 --max=10

# Check autoscaler
kubectl get hpa
```

HPA YAML
```yaml
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: nginx-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: nginx-deployment
  minReplicas: 2
  maxReplicas: 10
  metrics:
    - type: Resource
      resource:
        name: cpu
        target:
          type: Utilization
          averageUtilization: 70
```

## 🔹 Monitoring in Kubernetes

### Key Tools:

- **kubectl top** → quick CPU/memory usage
    
- **Metrics Server** → provides metrics API
    
- **Prometheus** → monitoring & alerting
    
- **Grafana** → visualization dashboards
    
- **ELK / EFK Stack** → centralized logging


## 🔹 Metrics Server

Install
```bash
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/latest/download/components.yaml
```

Check
```bash
kubectl top nodes
kubectl top pods
```

## 🔹 Logging

```bash
# Logs from single pod
kubectl logs nginx-pod

# Logs from all pods in deployment
kubectl logs deployment/nginx-deployment
```

Use **EFK (Elasticsearch + Fluentd + Kibana)** or **Loki + Grafana** for centralized logs.

## 🔹 Monitoring with Prometheus & Grafana

- Deploy **Prometheus Operator** or Helm chart
    
- Scrape metrics from Kubernetes components and apps
    
- Use **Grafana dashboards** to visualize cluster health

```bash
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm install monitoring prometheus-community/kube-prometheus-stack
```

## 🔹 Python + Monitoring

**List pod metrics (via Metrics API):**

```python
from kubernetes import client, config

config.load_kube_config()
api = client.CustomObjectsApi()

metrics = api.list_cluster_custom_object(
    group="metrics.k8s.io",
    version="v1beta1",
    plural="pods"
)

for pod in metrics["items"]:
    name = pod["metadata"]["name"]
    ns = pod["metadata"]["namespace"]
    usage = pod["containers"][0]["usage"]
    print(f"{ns}/{name} - CPU: {usage['cpu']} - MEM: {usage['memory']}")
```

---

## 🔹 Best Practices

- Always define **resource requests/limits** for pods
    
- Use **HPA** for workload spikes
    
- Combine **HPA + Cluster Autoscaler** for full elasticity
    
- Centralize logs (EFK/Loki) for troubleshooting
    
- Set up **alerts** (Prometheus Alertmanager) for failures
    
- Use **Grafana dashboards** for visualization


[!tip]  
Scaling = **resilience & performance**  
Monitoring = **visibility & control**  
Together, they keep Kubernetes clusters **healthy in production**.