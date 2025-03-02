# Stage 1: Build the application using Java 8
FROM maven:3.8.6-openjdk-8 AS build
WORKDIR /app
COPY . .
RUN mvn clean package -DskipTests

# Stage 2: Run the application with Java 8
FROM openjdk:8-jdk-alpine
WORKDIR /app
COPY --from=build /app/target/springboot2-jpa-crud-example-0.0.1-SNAPSHOT.jar app.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]