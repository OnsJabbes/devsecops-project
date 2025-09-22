# --- Stage 1: Build JAR ---
FROM maven:3.9.2-openjdk-17 AS builder

WORKDIR /app

# Copy pom.xml and download dependencies first (for caching)
COPY pom.xml .
RUN mvn dependency:go-offline -B

# Copy source code
COPY src ./src

# Build the JAR with UTF-8 encoding
RUN mvn clean package -DskipTests -Dproject.build.sourceEncoding=UTF-8

# --- Stage 2: Run JAR ---
FROM openjdk:17-jdk

WORKDIR /app

# Copy the JAR from the builder stage
COPY --from=builder /app/target/Formation-Service-0.0.1-SNAPSHOT.jar app.jar

# Expose port
EXPOSE 9094

# Run the application
ENTRYPOINT ["java", "-jar", "app.jar"]
