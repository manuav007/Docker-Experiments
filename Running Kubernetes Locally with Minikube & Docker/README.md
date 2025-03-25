# Local Kubernetes Deployment with Minikube and Docker

This guide walks you through setting up a local Kubernetes cluster using **Minikube** with **Docker** as the driver. Minikube provides an easy way to experiment with Kubernetes without requiring cloud infrastructure.

---

## ✅ Prerequisites
Before starting, ensure you have the necessary tools installed:

1. **Docker Desktop** 🐋  
   - Download and install [Docker Desktop](https://www.docker.com/products/docker-desktop/).
   - Ensure that **WSL 2 backend** is enabled (recommended). ⚙️
   - If using Windows Pro/Enterprise, enable **Hyper-V**. 🔧

2. **Minikube** 📦  
   - Install using Chocolatey (Windows):
     ```bash
     choco install minikube
     ```
   - Or download from [Minikube’s official website](https://minikube.sigs.k8s.io/docs/start/).

3. **kubectl (Kubernetes CLI)**  
   - Install using Chocolatey:
     ```bash
     choco install kubernetes-cli
     ```
   - Verify installation:
     ```bash
     kubectl version --client
     ```

---

## ✅ Step 1: Start Minikube with Docker Driver 🐳
Ensure **Docker Desktop** is running before proceeding.

1. Start Minikube:
   ```bash
   minikube start --driver=docker
   ```

2. Check the Minikube status:
   ```bash
   minikube status
   ```

---

## ✅ Step 2: Deploy an Application 🚀
Deploy a simple **nginx** web server inside your Minikube cluster.

1. **Create an Nginx Deployment**:
   ```bash
   kubectl create deployment nginx --image=nginx
   ```

2. **Expose the Deployment**:
   ```bash
   kubectl expose deployment nginx --type=NodePort --port=80
   ```

3. **Get the Service URL**:
   ```bash
   minikube service nginx --url
   ```
   Open the provided URL in your browser to see the running **nginx** web server. 🌐

---

## ✅ Step 3: Manage Kubernetes Cluster

1. **Check Running Pods 📋**:
   ```bash
   kubectl get pods
   ```

2. **Scale the Deployment 📏**:
   ```bash
   kubectl scale deployment nginx --replicas=3
   ```
   Check running pods again:
   ```bash
   kubectl get pods
   ```

3. **Delete the Deployment 🧹**:
   ```bash
   kubectl delete service nginx
   kubectl delete deployment nginx
   ```

---

## ✅ Step 4: Stop and Delete Minikube 🗑️

1. **Stop Minikube**:
   ```bash
   minikube stop
   ```

2. **Delete the Cluster**:
   ```bash
   minikube delete
   ```
   This removes all Kubernetes resources and stops the local cluster.

---

## 🎯 Conclusion
By using **Minikube with Docker**, you can run a Kubernetes cluster locally without requiring additional virtualization. This setup allows you to experiment with Kubernetes, deploy applications, and manage containerized services efficiently. 🚀😊

---
