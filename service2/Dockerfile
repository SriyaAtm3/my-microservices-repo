# Step 1: Build the application
FROM maven:3.8.1-openjdk-11-slim AS builder

WORKDIR /app

COPY pom.xml ./
RUN mvn dependency:go-offline

COPY src ./src

RUN mvn clean package -DskipTests

# Step 2: Run the application in a smaller runtime image
FROM openjdk:11-jre-slim

WORKDIR /app

COPY --from=builder /app/target/service2-1.0-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
