# Docker Logging Application

## Overview
This project demonstrates a simple Python application that logs messages continuously. The application is containerized using Docker and uses a Docker volume to persist log data.

## Project Structure
```
📂 docker-logging-app
├── 📄 Dockerfile       # Docker configuration
├── 📄 app.py          # Python logging script
└── 📄 README.md       # Project documentation
```

## Prerequisites
Ensure you have the following installed:
- **Docker Desktop** ([Download here](https://www.docker.com/get-started/))
- **Git** (for pushing the project to GitHub)

## Installation & Setup
### 1️⃣ Clone the Repository
```sh
git clone https://github.com/manuav007/docker-logging-app.git
cd docker-logging-app
```

### 2️⃣ Build the Docker Image
```sh
docker build -t manu-log-app .
```

### 3️⃣ Run the Container with a Volume
```sh
docker run -d -v manu-app-data:/data manu-log-app
```

### 4️⃣ Verify Logs
#### View running containers:
```sh
docker ps
```
#### Check container logs:
```sh
docker logs <container-id>
```
#### Enter the container and check log file:
```sh
docker exec -it <container-id> sh
cd /data
cat app.log
```

### 5️⃣ Stop and Clean Up
```sh
docker stop <container-id>
docker rm <container-id>
docker rmi manu-log-app
docker volume rm manu-app-data
```

## Pushing to GitHub
### 1️⃣ Initialize Git
```sh
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/manuav007/docker-logging-app.git
git push -u origin main
```

## Expected Output
The log file (`app.log`) inside the container will contain entries like:
```
App is running at Mon Mar 31 12:00:00 2025
App is running at Mon Mar 31 12:00:05 2025
App is running at Mon Mar 31 12:00:10 2025
```

## Conclusion
This experiment demonstrates how to:
✅ Containerize a Python application with Docker.  
✅ Use **Docker volumes** for persistent data storage.  
✅ Inspect logs inside a running Docker container.  
✅ Push the project to **GitHub**.  

🚀 Happy Coding!

