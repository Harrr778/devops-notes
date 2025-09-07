# 🔄 Kubernetes CI/CD & DevOps

[[Kubernetes Scaling & Monitoring]] ← Previous | Next → [[DevOps Notes Home]]

> [!info] Purpose
CI/CD + Kubernetes = **automation of build, test, and deployment pipelines**.  
This ensures apps are delivered **fast, reliable, and repeatable**.

---

## 🔹 CI/CD in DevOps
- **CI (Continuous Integration):**  
  - Developers merge code frequently  
  - Automated builds & tests  
- **CD (Continuous Delivery/Deployment):**  
  - Deliver apps to production automatically  
  - Kubernetes ensures smooth rollout

---

## 🔹 Tools for CI/CD with Kubernetes
- **Jenkins** → classic automation server  
- **GitLab CI/CD** → integrated with GitLab  
- **GitHub Actions** → cloud-native CI/CD  
- **ArgoCD** → GitOps continuous delivery  
- **FluxCD** → GitOps for Kubernetes  
- **Helm** → package manager for Kubernetes apps  
- **Kustomize** → manage YAML customization

---

## 🔹 CI/CD Workflow
1. Developer pushes code → Git  
2. CI pipeline runs tests & builds Docker image  
3. Push image → Container Registry (Docker Hub, ECR, GCR)  
4. CD tool (ArgoCD, Helm, Jenkins) deploys to Kubernetes  
5. Monitor with Prometheus + Grafana  

---

## 🔹 Example: Jenkins Pipeline for Kubernetes
**Jenkinsfile:**
```groovy
pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'docker build -t myapp:${BUILD_NUMBER} .'
            }
        }
        stage('Push') {
            steps {
                sh 'docker push myrepo/myapp:${BUILD_NUMBER}'
            }
        }
        stage('Deploy') {
            steps {
                sh 'kubectl set image deployment/myapp myapp=myrepo/myapp:${BUILD_NUMBER}'
            }
        }
    }
}
```

## 🔹 Example: GitLab CI/CD with Kubernetes

**.gitlab-ci.yml**

```yaml
stages:
  - build
  - deploy

build:
  stage: build
  script:
    - docker build -t registry.gitlab.com/myuser/myapp:$CI_COMMIT_SHA .
    - docker push registry.gitlab.com/myuser/myapp:$CI_COMMIT_SHA

deploy:
  stage: deploy
  script:
    - kubectl set image deployment/myapp myapp=registry.gitlab.com/myuser/myapp:$CI_COMMIT_SHA
```

## 🔹 Helm Example

```bash
# Create Helm chart
helm create myapp

# Install chart
helm install myapp ./myapp

# Upgrade app
helm upgrade myapp ./myapp --set image.tag=v2
```


---

## 🔹 GitOps with ArgoCD

- **Declarative deployments**: cluster state = Git repo
    
- Auto-syncs Kubernetes with Git repository
    
- UI to monitor app rollouts

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

Add app
```bash
argocd app create myapp \
  --repo https://github.com/myuser/myrepo.git \
  --path k8s \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace default
```

## ## 🔹 Python + CI/CD (example with API)

**Trigger Kubernetes Deployment via Python:**

```python 
from kubernetes import client, config

config.load_kube_config()
apps = client.AppsV1Api()

apps.patch_namespaced_deployment(
    name="myapp",
    namespace="default",
    body={"spec": {"template": {"spec": {"containers": [
        {"name": "myapp", "image": "myrepo/myapp:v2"}
    ]}}}}
)
print("Deployment updated!")
```

## 🔹 Best Practices

- Store **manifests in Git** → GitOps
    
- Use **Helm** or **Kustomize** for reusable YAML
    
- Secure your **container registry** (Docker Hub, ECR, GCR)
    
- Implement **RBAC + Secrets management**
    
- Automate with **ArgoCD / FluxCD** for GitOps
    
- Add **monitoring & alerting** in pipeline

[!tip]  
Kubernetes + CI/CD = **self-healing, automated, production-ready pipelines** 🚀