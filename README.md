# 📦 SIT737 – 6.2C: Kubernetes Deployment of Calculator Microservice

This task demonstrates deploying a Node.js-based calculator microservice on a Kubernetes cluster. It includes containerization, service exposure via NodePort, and accessing the service using `kubectl port-forward`.

---

## 👩‍🎓 Student Details

- **Name:** Mariya Theresa Shibu  
- **Student ID:** 223992433  
- **Unit:** SIT737 – Cloud-Native Application Development  
- **Task:** 6.2C – Interacting with a Kubernetes Cluster

---

## 📁 Project Overview

- **Microservice:** Calculator App (add, subtract, multiply, divide)
- **Technology Stack:** Node.js, Express.js, Docker, Kubernetes
- **Deployment:** Kubernetes `Deployment` and `Service` using YAML
- **Container Registry:** Docker Hub  
- **Cluster Interaction:** Using `kubectl`

---

## 🛠 Prerequisites

Ensure the following tools are installed and configured:

- Docker
- Kubectl
- Kubernetes Cluster (e.g., Minikube, Docker Desktop, GKE)
- Docker Hub account

---

## 📂 Project Files

| File              | Description                          |
|-------------------|--------------------------------------|
| `app.js`          | app.js  service logic                |
| `Dockerfile`      | Docker container instructions        |
| `deployment.yaml` | Kubernetes deployment configuration  |
| `service.yaml`    | Kubernetes service configuration     |
| `package.json`    | Project dependencies                 |

---

## 🚀 Steps Performed

### ✅ 1. Docker Login

```bash
docker login

✅ 2. Build and Push Docker Image
docker build -t mariyatheresa/calculator-microservice:v2.0 .
docker push mariyatheresa/calculator-microservice:v2.0
✅ 3. Apply Kubernetes Deployment and Service
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml

✅ 4. Check Pod and Service Status
kubectl get pods
kubectl get service calculator-service

Example output:
NAME                                    READY   STATUS    RESTARTS   AGE
calculator-deployment-fc666d5cb-nzjhr   1/1     Running   0          130m

NAME                 TYPE       CLUSTER-IP       EXTERNAL-IP   PORT(S)          AGE
calculator-service   NodePort   34.118.236.101   <none>        3000:30100/TCP   129m

✅ 5. Port Forward to Access the App
kubectl port-forward service/calculator-service 30200:3000

Visit the app at: http://localhost:30200

🔍 API Endpoints (Example Usage)
Operation	Endpoint
Addition	/add?num1=5&num2=3
Subtraction	/subtract?num1=10&num2=2
Multiplication	/multiply?num1=4&num2=3
Division	/divide?num1=8&num2=2

Example:
http://localhost:30200/add?num1=5&num2=7
