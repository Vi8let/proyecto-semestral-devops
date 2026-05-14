# ===== ETAPA 1: BUILD =====
FROM maven:3.9.6-eclipse-temurin-17 AS build
WORKDIR /app
COPY pom.xml .
COPY src ./src
RUN mvn clean package -DskipTests

# ===== ETAPA 2: RUNTIME =====
FROM eclipse-temurin:17-jre
WORKDIR /app

COPY --from=build /app/target/*.jar app.jar

RUN useradd -m springuser && \
    chown springuser:springuser app.jar

USER springuser
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]
