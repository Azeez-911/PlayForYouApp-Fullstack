# -----------------------------
# Build stage
# -----------------------------
FROM eclipse-temurin:21-jdk-alpine AS builder

WORKDIR /app
COPY . .

# Give execute permission to mvnw
RUN chmod +x ./mvnw

# Build the Spring Boot project
RUN ./mvnw clean package -DskipTests

# -----------------------------
# Runtime stage
# -----------------------------
FROM eclipse-temurin:21-jre-alpine

WORKDIR /app

# Copy the built WAR file from builder stage
COPY --from=builder /app/target/*.war app.war

EXPOSE 8081

ENTRYPOINT ["java","-jar","/app/app.war"]
