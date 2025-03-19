# Use an official OpenJDK runtime as base image
FROM openjdk:17-jdk-slim

# Set the working directory inside the container
WORKDIR /app

# Copy the built JAR file from the target directory to the container
COPY . /app

# Command to run the application
CMD ["java", "-jar", "app.jar"]

