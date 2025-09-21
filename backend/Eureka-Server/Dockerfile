# Use Maven + JDK base image
FROM maven:3.9.2-eclipse-temurin-17

# Set UTF-8 environment variables
ENV LANG=en_US.UTF-8
ENV LANGUAGE=en_US:en
ENV LC_ALL=en_US.UTF-8
ENV JAVA_TOOL_OPTIONS="-Dfile.encoding=UTF-8"

# Set working directory
WORKDIR /app

# Copy pom.xml first for caching
COPY pom.xml ./

# Copy source code
COPY src ./src

# Build the application (skip tests)
RUN --mount=type=cache,target=/root/.m2 \
    mvn clean package -DskipTests

# Expose Eureka port
EXPOSE 8761

# Run the JAR built inside the container
CMD ["mvn", "spring-boot:run"]
