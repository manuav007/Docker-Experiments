# Microservices Orchestration with Minikube & Kubernetes

This project demonstrates a basic microservices architecture using Minikube and Kubernetes. It includes an API Gateway and a Backend Service, showcasing how to containerize applications and deploy them in a Kubernetes cluster.

## Prerequisites
Before you begin, ensure you have the following installed:

- **Minikube** - For running a local Kubernetes cluster
- **kubectl** - For interacting with the Kubernetes cluster
- **Docker** - For building container images
- **VS Code** (Optional) - For writing and managing code files

## Project Structure
```
.
├── README.md
├── backend/
│   ├── Dockerfile
│   ├── backend.py
│   └── requirements.txt
├── api-gateway/
│   ├── Dockerfile
│   ├── api_gateway.py
│   └── requirements.txt
└── kubernetes/
    ├── backend-service.yaml
    └── api-gateway.yaml
```

## Step-by-Step Guide

### 1. Start Minikube
Open a terminal (PowerShell or Command Prompt as Administrator) and run:
```bash
minikube start
```

### 2. Set Up Docker Environment
Configure Docker to use Minikube’s Docker daemon:
```bash
eval $(minikube -p minikube docker-env)
```

### 3. Build and Deploy Services

#### 3.1 Backend Service
Navigate to the backend directory:
```bash
cd backend
```
Build the Docker image:
```bash
docker build -t backend-service .
```
Deploy the backend service to Kubernetes:
```bash
kubectl apply -f ../kubernetes/backend-service.yaml
```

#### 3.2 API Gateway
Navigate to the api-gateway directory:
```bash
cd ../api-gateway
```
Build the Docker image:
```bash
docker build -t api-gateway .
```
Deploy the API Gateway to Kubernetes:
```bash
kubectl apply -f ../kubernetes/api-gateway.yaml
```

### 4. Verify Deployment
Check the status of your deployments:
```bash
kubectl get deployments
kubectl get services
```

### 5. Access the Application
To access the API Gateway service, run:
```bash
minikube service api-gateway
```
This will open your browser to the API Gateway endpoint, displaying a response from the backend service.

### 6. Monitoring and Debugging

- View logs of the API Gateway:
```bash
kubectl logs deployment/api-gateway
```
- View logs of the Backend Service:
```bash
kubectl logs deployment/backend-service
```
- Get detailed information about pods:
```bash
kubectl describe pods
```

### 7. Clean Up
When you're done, clean up the resources:
```bash
kubectl delete -f kubernetes/api-gateway.yaml
kubectl delete -f kubernetes/backend-service.yaml
```
Stop Minikube:
```bash
minikube stop
```

## Architecture Overview

### Components

- **API Gateway**
  - Acts as the entry point for all client requests
  - Routes requests to the backend service
  - Port: 8080

- **Backend Service**
  - Handles business logic
  - Returns responses
  - Port: 5000

### Communication Flow
```
Client → API Gateway (8080)
API Gateway → Backend Service (5000)
Backend Service → API Gateway
API Gateway → Client
```

## Troubleshooting

### Common Issues and Solutions:

- **Images not found**
  - Ensure you are using Minikube’s Docker daemon.
  - Verify image names in Kubernetes manifests.

- **Services not accessible**
  - Check if pods are running: `kubectl get pods`
  - Verify service types and ports.
  - Check logs for errors.

- **Minikube issues**
  - Restart Minikube: `minikube stop && minikube start`
  - Reset cluster: `minikube delete && minikube start`

## Uploading to GitHub
To upload this project to GitHub, follow these steps:
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/manuav007/microservices-minikube.git
git push -u origin main
```

## Additional Resources
- [Minikube Documentation](https://minikube.sigs.k8s.io/docs/)
- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Docker Documentation](https://docs.docker.com/)
