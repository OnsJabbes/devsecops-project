# --- Stage 1: Build JAR ---
FROM maven:3.9.2-eclipse-temurin-17-slim AS builder
WORKDIR /app
COPY pom.xml .
RUN mvn dependency:go-offline -B
COPY src ./src

# Build with UTF-8
RUN mvn clean package -DskipTests -Dproject.build.sourceEncoding=UTF-8

# --- Stage 2: Run JAR ---
FROM eclipse-temurin:17-jdk-focal
WORKDIR /app
COPY --from=builder /app/target/Formation-Service-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 9094
ENTRYPOINT ["java", "-jar", "app.jar"]
