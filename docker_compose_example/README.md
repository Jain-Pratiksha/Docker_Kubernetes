# 🐳 Dockerizing Spring Boot (Java 21) + MongoDB App

This guide documents how we containerized the Spring Boot 3 project **`shows_watchlist`** using **Docker** and **Docker Compose**, along with MongoDB.
Imagine you have a Spring Boot application that connects to MongoDB. To run both the application and the database seamlessly in isolated environments, you can use Docker Compose to spin up two containers — one for the Spring Boot app and another for MongoDB — with just a single command.

---

## 📦 Project Setup

### 📁 Folder Structure

project_name/

├── Dockerfile # Docker image for Spring Boot app

├── docker-compose.yml # To run app + MongoDB together


---

## 🔧 Prerequisites

- Docker Desktop installed and running
- Maven installed locally (optionally if you are using springboot project on IDE)
- MongoDB NOT running locally on port `27017` (to avoid conflicts)

---

## 🏗️ Dockerfile (for Spring Boot App)

## 📜 docker-compose.yml

On IDE clean install the project.
On terminal be on the root path of project and run the below command (make sure you have you Dockerfile and docker-compose.yml there:
```
docker-compose up --build
```

This starts:

Spring Boot app at: http://localhost:8080

MongoDB accessible via localhost:27017 or Compass

### 🧹 Clean Up
Stop and remove containers:

```
docker-compose down
# Remove volumes too (if needed):
docker-compose down -v
```

✅ Done!
Now your Spring Boot + MongoDB backend is running completely in Docker! 🎉
