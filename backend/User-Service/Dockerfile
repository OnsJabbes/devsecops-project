# --- Stage 1: Build JAR ---
FROM maven:3.9.2-eclipse-temurin-17 AS builder

WORKDIR /app

# Copy pom.xml and download dependencies (caching layer)
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Copy source code
COPY src ./src

# Build the JAR (skip tests for speed, optionnel)
RUN mvn clean package -DskipTests

# --- Stage 2: Run JAR ---
FROM openjdk:17-jdk-alpine

WORKDIR /app

# Copy the JAR from builder stage
COPY --from=builder /app/target/hajerhamrouni4arctic11-0.0.1-SNAPSHOT.jar app.jar


# Expose service port
EXPOSE 8089

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
