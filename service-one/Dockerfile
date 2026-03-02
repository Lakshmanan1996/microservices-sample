# Use OpenJDK 17 base image
FROM eclipse-temurin:17-jdk-jammy

# Set working directory
WORKDIR /app

# Copy the JAR built by Maven into the container
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar

# Expose port your service listens on
EXPOSE 8081

# Run the JAR
ENTRYPOINT ["java", "-jar", "/app/app.jar"]
