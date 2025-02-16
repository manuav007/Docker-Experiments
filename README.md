# Titanic Survival Predictor - Dockerized Streamlit App

This project demonstrates how to build and run a containerized Streamlit app for Titanic survival prediction using Docker Desktop.

## Prerequisites
Ensure you have the following installed on your system:
- [Docker Desktop](https://www.docker.com/products/docker-desktop/)
- [Git](https://git-scm.com/downloads)
- [VS Code](https://code.visualstudio.com/)
- Basic understanding of command-line interface (CLI)

## Steps to Perform the Experiment

### 1. Clone the Repository
```sh
git clone https://github.com/manuav007/Docker-Experiments.git
cd Docker-Experiments/titanic_survival
```

### 2. Create a Virtual Environment (Optional)
```sh
python -m venv venv
source venv/bin/activate  # On macOS/Linux
venv\Scripts\activate     # On Windows
```

### 3. Install Dependencies
```sh
pip install -r requirements.txt
```

### 4. Run the Streamlit App Locally (Optional)
```sh
streamlit run app.py
```

### 5. Create a Dockerfile
Ensure your **Dockerfile** is properly configured:
```dockerfile
# Use an official Python runtime as base image
FROM python:3.9

# Set the working directory
WORKDIR /app

# Copy the local files into the container
COPY . /app

# Install dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Expose the Streamlit port
EXPOSE 8501

# Command to run the app
CMD ["streamlit", "run", "app.py", "--server.port=8501", "--server.address=0.0.0.0"]
```

### 6. Build the Docker Image
```sh
docker build -t titanic_survival .
```

### 7. Run the Docker Container
```sh
docker run -p 8501:8501 titanic_survival
```

### 8. Access the Streamlit App
Open your browser and go to:
```
http://localhost:8501
```

### 9. Push the Image to Docker Hub
```sh
docker tag titanic_survival manuav007/titanic_survival:v1

docker login

docker push manuav007/titanic_survival:v1
```

### 10. Stop and Remove the Container (If Needed)
```sh
docker ps  # Check running containers
docker stop <container_id>
docker rm <container_id>
```

### 11. Pull and Run the Image from Docker Hub
```sh
docker pull manuav007/titanic_survival:v1
docker run -p 8501:8501 manuav007/titanic_survival:v1
```

## Conclusion
You have successfully built and deployed a containerized Streamlit app for Titanic survival prediction using Docker! 🚀

---
For any issues, feel free to open an issue in the repository or contact me. 😊
