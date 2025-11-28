To do:
* A **simple Python FastAPI backend**
* A **Dockerfile**
* A **Helm chart (Deployment, Service, Ingress)**
* Clear steps to run it on Minikube

Everything beginner-friendly.

---

# ✅ **1. Python backend (FastAPI)**

In app, Build & push your image:

```bash
docker build -t fastapi-helm:latest .
```

If using Minikube:

```bash
eval $(minikube docker-env)
docker build -t fastapi-helm:latest .
```

(Minikube will use the local image, no pushing needed.)

---

# ✅ **2. Helm chart structure**

Create this folder structure:

```
fastapi-helm-chart/
  Chart.yaml
  values.yaml
  templates/
      deployment.yaml
      service.yaml
      ingress.yaml
```

---

# ✅ **3. Enable Minikube Ingress**

If not enabled:

```bash
minikube addons enable ingress
```

Wait for the controller:

```bash
kubectl get pods -n ingress-nginx
```

---

# ✅ **4. Install Helm chart**

```bash
helm install fastapi-demo ./fastapi-helm-chart
```

Check resources:

```bash
kubectl get all
kubectl get ingress
```

---

# ✅ **5. Add host entry on your machine**

Get Minikube IP:

```bash
minikube ip
```

Edit `/etc/hosts` (or Windows hosts file):

```
192.168.xx.xx   fastapi.local
```

---

# ✅ **6. Test in browser**

Open:

```
http://fastapi.local
```

You should see:

```json
{"message":"Hello from FastAPI via Ingress + Helm!"}
```

🎉 **You now have Python + Helm + Ingress working on Minikube.**
