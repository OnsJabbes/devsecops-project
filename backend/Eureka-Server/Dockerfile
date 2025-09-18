# Use official OpenJDK 17 image
FROM eclipse-temurin:17-jdk-alpine

# Set working directory inside container
WORKDIR /app

# Copy Maven project files
COPY pom.xml .
COPY src ./src


# RUN ./mvnw clean package -DskipTests


ARG MAVEN_CMD=mvn
RUN $MAVEN_CMD clean package -DskipTests && \
    mv target/*.jar app.jar

# Expose Eureka port
EXPOSE 8761

# Run the jar
CMD ["java", "-jar", "target/Eureka-Server-0.0.1-SNAPSHOT.jar"]
