# -----------------------------
# Build stage
# -----------------------------
FROM eclipse-temurin:21-jdk-alpine AS builder
WORKDIR /app
COPY . .
RUN ./mvnw clean package -DskipTests

# -----------------------------
# Runtime stage
# -----------------------------
FROM eclipse-temurin:21-jre-alpine
WORKDIR /app
COPY --from=builder /app/target/*.war app.war
EXPOSE 8081
ENTRYPOINT ["java","-jar","/app/app.war"]
