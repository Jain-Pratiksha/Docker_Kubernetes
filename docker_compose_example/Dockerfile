## 🏗️ Dockerfile (for Spring Boot App)

# Use OpenJDK 21 image - since using java 21, different supporting images can also be used
FROM openjdk:21-jdk-slim

# First stage: clean and build the JAR file using Maven, for mvn command you need to have maven installed
# RUN mvn clean package -DskipTests

#Set working directory inside the container
WORKDIR /usr/src/app

# Copy the jar file from the host to the container
# target/name_of_jar_file.jar work_director_name
COPY target/shows_watchlist-0.0.1-SNAPSHOT.jar /usr/src/app

# Expose the port on which the application will run (basically the port that we use with base url for apis to trigger)
EXPOSE 8080

# Set the command to run the application
# This command will be executed when the container starts
# java -jar name_of_jar_file.jar
# Using ENTRYPOINT over CMD helps you restricting overwriting of commands.
ENTRYPOINT ["java", "-jar", "shows_watchlist-0.0.1-SNAPSHOT.jar"]

# Steps to build and run the Docker container (will be doing with docker compose so no need of running the below separately):
# 1. Build image
# docker build -t image_name_you_want_to_give .
# 2. Run container, maps container port:local port (port used in project)
# docker run -p 8080:8080 image_name_that_you_gave_during_build
