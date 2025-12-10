# Build environment
FROM maven:3.9.9-eclipse-temurin-21 AS builder

# Set working directory
WORKDIR /app

# Copy project files
COPY ./demo .

# Build the application
RUN mvn package -DskipTests=true

# Run the application
#CMD ["java","-jar","/app/target/demo-0.0.1-SNAPSHOT.jar"]

# Runtime environment
FROM amazoncorretto:21-alpine3.21 AS production

WORKDIR /app
COPY --from=builder /app/target/demo-0.0.1-SNAPSHOT.jar .

CMD ["java","-jar","/app/demo-0.0.1-SNAPSHOT.jar"]