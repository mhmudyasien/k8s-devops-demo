# k8s-devops-demo
> A DevOps-focused Kubernetes manifest bundle demonstrating secure, declarative, and maintainable deployment patterns—ideal for local development (Minikube) and CI/CD pipelines.

This project is **not about the application**—it’s about **how** you deploy it on Kubernetes.

---

## ✨ DevOps & Kubernetes Best Practices Demonstrated

### 🔐 Security by Design
- **Secrets management**: Sensitive credentials (e.g., DB username/password) stored in `Secret` and injected via `secretKeyRef`.
- **No hardcoded values**: Configuration decoupled using `ConfigMap`.
- **Least privilege**: No `root` containers or excessive permissions (base images follow upstream defaults securely).

### 📁 Declarative & Maintainable Structure
- Separate manifests per resource type (`Deployment`, `Service`, `ConfigMap`, `Secret`) → easy GitOps compatibility.
- Clear labeling and selector conventions for service discovery.
- Explicit API versions (`apps/v1`, `v1`) for stability.

### 🖥️ Local Development Ready (Minikube)
- All manifests tested on **Minikube** (Ubuntu/Linux).
- `LoadBalancer` service with `nodePort: 30000` for easy access during local testing.
- No cloud-specific dependencies—pure upstream Kubernetes.

### 🚀 CI/CD & Production-Ready Signals
- Idempotent manifests: Safe to apply repeatedly (`kubectl apply -f .`).
- Externalized config → environment promotion without manifest changes.
- Foundation for adding:  
  - Resource requests/limits  
  - Liveness/readiness probes  
  - NetworkPolicies  
  - RBAC (service accounts)  
  - Helm or Kustomize abstraction

---

## 🚀 Quick Start (Minikube)

```bash
# Start Minikube
minikube start

# Apply all manifests
kubectl apply -f .

# Access Mongo Express
minikube service mongo-express-service --url
# Or open in browser (Minikube on Linux):
minikube service mongo-express-service
