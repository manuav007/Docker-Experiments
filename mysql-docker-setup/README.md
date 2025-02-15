# MySQL Docker Setup

This experiment demonstrates how to set up and run MySQL inside a Docker container. It includes creating a Dockerfile, running MySQL in a container, and integrating it with GitHub.

## Prerequisites
- Docker installed on your system
- Git installed and configured
- A GitHub repository (e.g., `https://github.com/manuav007/Docker-Experiments`)

## Step 1: Create the Project Structure
Create a directory for your experiment:
```sh
mkdir mysql-docker-setup
cd mysql-docker-setup
```

## Step 2: Create the Dockerfile
Create a `Dockerfile` with the following content:
```dockerfile
# Use the official MySQL image
FROM mysql:latest

# Set environment variables
ENV MYSQL_ROOT_PASSWORD=root
ENV MYSQL_DATABASE=manudb
ENV MYSQL_USER=manu
ENV MYSQL_PASSWORD=manu123

# Expose MySQL port
EXPOSE 3306
```

## Step 3: Create a MySQL Database Script
Create a file named `Manu_demo.sql` with the following content:
```sql
CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(100) NOT NULL UNIQUE
);
```

## Step 4: Build and Run the Docker Container
Build the Docker image:
```sh
docker build -t mysql-docker .
```
Run the MySQL container:
```sh
docker run --name mysql-container -d -p 3306:3306 mysql-docker
```

Check running containers:
```sh
docker ps
```

## Step 5: Connect to the MySQL Database
Use the following command to connect to MySQL inside the container:
```sh
docker exec -it mysql-container mysql -u manu -p
```
Enter the password: `manu123`

## Step 6: GitHub Integration
### Initialize Git Repository
```sh
git init
git remote add origin https://github.com/manuav007/Docker-Experiments.git
git branch -M main
```

### Add and Commit Files
```sh
git add .
git commit -m "Added MySQL Docker setup"
```

### Push to GitHub
If your repository already has commits, pull the latest changes first:
```sh
git pull origin main --rebase
```
Then push your changes:
```sh
git push -u origin main
```

## Step 7: Verify
- Check the running container: `docker ps`
- Access MySQL and run `SHOW DATABASES;` to confirm the database exists
- Check GitHub to confirm your files were uploaded successfully

## Conclusion
This experiment successfully sets up a MySQL database in Docker, integrates it with Git, and pushes it to GitHub for version control. 🚀
