# 💾 Kubernetes Volumes & Storage (DevOps)

[[Kubernetes Services & Networking]] ← Previous | Next → [[Kubernetes Scaling & Monitoring]]

> [!info] Purpose
Kubernetes provides **persistent storage** for containers using Volumes, Persistent Volumes (PV), and Persistent Volume Claims (PVC).  
Also manages **configuration and secrets** via ConfigMaps and Secrets.

---

## 🔹 Why Storage?
- Containers are **ephemeral** (data lost on restart)  
- Volumes ensure **persistent data**  
- Required for databases, logs, and user files in DevOps  

---

## 🔹 Volume Types
| Type              | Description | Use Case |
|-------------------|-------------|----------|
| **emptyDir**      | Temporary storage, deleted when Pod dies | Caching |
| **hostPath**      | Uses host filesystem path | Debugging, testing |
| **ConfigMap**     | Stores configuration | App configs |
| **Secret**        | Stores sensitive data | Passwords, tokens |
| **PersistentVolume (PV)** | Cluster-level storage resource | Databases |
| **PersistentVolumeClaim (PVC)** | Request for PV by Pod | Dynamic storage |

---

## 🔹 emptyDir Example
```yaml
apiVersion: v1
kind: Pod
metadata:
  name: cache-pod
spec:
  containers:
    - name: app
      image: busybox
      command: ["sleep", "3600"]
      volumeMounts:
        - mountPath: /cache
          name: cache-vol
  volumes:
    - name: cache-vol
      emptyDir: {}
```


## 🔹 ConfigMap Example

```bash
apiVersion: v1
kind: ConfigMap
metadata:
  name: app-config
data:
  APP_ENV: "production"
  APP_DEBUG: "false"
```

Use in Pod
```bash
envFrom:
  - configMapRef:
      name: app-config
```

## 🔹 Secret Example

```bash
apiVersion: v1
kind: Secret
metadata:
  name: db-secret
type: Opaque
data:
  DB_USER: YWRtaW4=      # base64(admin)
  DB_PASS: c2VjcmV0      # base64(secret)
```

Use in Pod
```bash
envFrom:
  - secretRef:
      name: db-secret
```

## 🔹 PersistentVolume (PV) Example

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: pv-volume
spec:
  capacity:
    storage: 1Gi
  accessModes:
    - ReadWriteOnce
  hostPath:
    path: "/mnt/data"
```

## 🔹 PersistentVolumeClaim (PVC) Example

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: pv-claim
spec:
  accessModes:
    - ReadWriteOnce
  resources:
    requests:
      storage: 1Gi
```

Use in Pod
```bash
volumes:
  - name: app-storage
    persistentVolumeClaim:
      claimName: pv-claim
```

## 🔹 Check Storage

```bash
kubectl get pv
kubectl get pvc
kubectl describe pvc pv-claim
```

## 🔹 Python + Kubernetes Storage

```python
from kubernetes import client, config

config.load_kube_config()
v1 = client.CoreV1Api()

# List PVCs
pvcs = v1.list_namespaced_persistent_volume_claim(namespace="default")
for pvc in pvcs.items:
    print(f"{pvc.metadata.name} - {pvc.status.phase}")
```

---

## 🔹 Best Practices

- Use **ConfigMaps** for non-sensitive configs
    
- Use **Secrets** for credentials (always base64 encode)
    
- Prefer **PVC + dynamic provisioners** in production
    
- Define **storage classes** for cloud providers
    
- Backup PV data regularly in DevOps workflows

> [!tip]

- **ConfigMaps** → configs
    
- **Secrets** → sensitive data
    
- **PV + PVC** → persistent storage  
    Together, they make Kubernetes apps **stateful and production-ready**.