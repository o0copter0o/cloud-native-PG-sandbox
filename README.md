# PostgreSQL 

This repository is for learning PostgreSQL.
Testing a PostgreSQL cluster on your local machine by deploying CloudNativePG on a local Kubernetes cluster using Minikube.

---

## 📁 Project Structure
```
kong-helm-sandbox/
  └── values-kong-oss-manager-local.yaml
```

---

## 🧩 What is CloudNativePG?
CloudNativePG (CNPG) is an open-source operator designed to manage PostgreSQL workloads on any supported Kubernetes cluster.

Ref : https://cloudnative-pg.io/documentation/1.27/quickstart/

---
## 🚀 Setup Guide
### **1️⃣ Install CloudNativePG**
Install the operator manifest
```bash
kubectl apply --server-side -f https://raw.githubusercontent.com/cloudnative-pg/cloudnative-pg/release-1.27/releases/cnpg-1.27.1.yaml
```
Verify that with
```bash
kubectl rollout status deployment -n cnpg-system cnpg-controller-manager
```

### **2️⃣ Deploy a PostgreSQL cluster**
Create namespace
```bash
kubectl create namespace cnpg-cluster
```

Create file cluster-example.yaml
```bash
kubectl apply -f cluster-example.yaml
```

### **3️⃣ Verify pg**
```bash
kubectl exec -it cluster-example-1 -- psql -U postgres
```