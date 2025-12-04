# Use JDK for building
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app

# Copy project files
COPY pom.xml .
COPY src ./src

# Build jar
RUN mvn clean package -DskipTests

# Runtime image
FROM eclipse-temurin:17-jdk
WORKDIR /app

# Copy jar from builder
COPY --from=build /app/target/sample-app-1.0.0.jar app.jar

# Default command
CMD ["java", "-jar", "app.jar"]
