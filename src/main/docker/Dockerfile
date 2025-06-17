# Build stage
FROM maven:3.9.6-eclipse-temurin-21 AS build

WORKDIR /app

# Copy pom.xml and download dependencies
COPY pom.xml ./
RUN mvn dependency:go-offline -B

# Copy source code
COPY src ./src

# Build the application
RUN mvn clean package -DskipTests -Pprod

# Runtime stage
FROM eclipse-temurin:21-jre-alpine

# Install curl for healthcheck
RUN apk add --no-cache curl

# Create app user
RUN addgroup -g 1001 -S app && \
    adduser -u 1001 -S app -G app

WORKDIR /app

# Copy the built application
COPY --from=build /app/target/*.jar app.jar

# Copy entrypoint script
COPY src/main/docker/jib/entrypoint.sh /entrypoint.sh
RUN chmod +x /entrypoint.sh

# Set ownership to app user
RUN chown -R app:app /app

USER app

EXPOSE 8080

ENTRYPOINT ["/entrypoint.sh"] 