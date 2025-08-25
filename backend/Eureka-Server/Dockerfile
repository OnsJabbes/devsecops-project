# Use official OpenJDK 17 image
FROM eclipse-temurin:17-jdk-alpine

# Set working directory inside container
WORKDIR /app

# Copy Maven project files
COPY pom.xml .
COPY src ./src

# Build the application
RUN ./mvnw clean package -DskipTests

# Expose Eureka port
EXPOSE 8761

# Run the jar
CMD ["java", "-jar", "target/Eureka-Server-0.0.1-SNAPSHOT.jar"]
