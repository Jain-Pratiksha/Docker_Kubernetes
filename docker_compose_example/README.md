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

https://github.com/Jain-Pratiksha/Docker_Kubernetes/blob/49c0451009912bc4125e6075c9adb31fbe0ff3cc/docker_compose_example/Dockerfile

## 📜 docker-compose.yml

https://github.com/Jain-Pratiksha/Docker_Kubernetes/blob/12011235ac90abb41c30a18ccbc573a8ffa5c5eb/docker_compose_example/docker-compose.yml

On IDE, clean install the project.
On terminal, be on the root path of project and run the below command (make sure you have you Dockerfile and docker-compose.yml there:

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

In Docker Desktop:
Under Containers you'll see the below, it means there are two services created, springboot project and mongodb, which are interacting with eachother.

<img width="760" height="92" alt="image" src="https://github.com/user-attachments/assets/f76d068b-ea65-4e9d-9880-50008e214b4a" />

You can see the logs, the request made.
<img width="940" height="462" alt="image" src="https://github.com/user-attachments/assets/f4cd06ea-09e6-436d-8d07-6d34db04ab49" />

Happy Learning and Sharing!
