# 🚀 Chat App Deployment Using Kubernetes

This project is a production-style deployment of a **three-tier chat application** using **Kubernetes**.

---

## 📦 Components

- **Frontend**: React (Dockerized)
- **Backend**: Node.js + Express (Dockerized)
- **Database**: MongoDB (Official image)

---

## ⚙️ Tools Used

- Kubernetes
- Docker
- kubectl
- MongoDB

---

## 🧠 Architecture Summary

| Component  | Kubernetes Object | Replicas | Service Type |
|------------|-------------------|----------|---------------|
| Frontend   | Deployment        | 3        | NodePort      |
| Backend    | Deployment        | 3        | ClusterIP     |
| MongoDB    | StatefulSet       | 1        | ClusterIP     |

---

## 📋 Prerequisites

- Kubernetes cluster (e.g. Minikube, Kind, or Cloud K8s)
- `kubectl` configured and pointing to the cluster

---

1. git clone https://github.com/atharva-kulkarni123/ChatApp-Deployment-K8s.git

2. Deploy MongoDB
--> kubectl apply -f database/mongodb.yaml

3. Deploy Backend
--> kubectl apply -f backend/k8s-backend.yaml

4. Deploy Frontend
--> kubectl apply -f frontend/k8s-frontend.yaml  # Exposed on port 5173
🌐 Accessing the Frontend (Port Forward)
Since NodePort may not work on WSL2 or certain setups, use port-forwarding instead:
1. kubectl port-forward service/frontend-service 5173:5173
2. http://localhost:5173

💾 MongoDB Setup & Inspection
1. kubectl exec -it mongodb-0 -- mongosh -u <username> -p <password>
2. show dbs
3. use test (or the name of the table that you have set)
4. show collections
5. db.users.find().pretty()
6. db.messages.find().pretty()
