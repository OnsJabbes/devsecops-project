# Use official OpenJDK 17 image
FROM openjdk:17-jdk-alpine

# Set working directory
WORKDIR /app

# Copy the built jar (placeholder)
COPY target/User-Service-0.0.1-SNAPSHOT.jar app.jar

# Expose the service port
EXPOSE 8089

# Run the jar
ENTRYPOINT ["java", "-jar", "app.jar"]
