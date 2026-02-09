# ---------- 1️⃣ BUILD STAGE ----------
FROM maven:3.9.6-eclipse-temurin-21 AS build

WORKDIR /app

# Копирај pom.xml прво (за кеш)
COPY pom.xml .
RUN mvn dependency:go-offline

# Копирај го кодот
COPY src ./src

# Изгради JAR (без тестови)
RUN mvn clean package -DskipTests


# ---------- 2️⃣ RUNTIME STAGE ----------
FROM eclipse-temurin:21-jdk

WORKDIR /app

COPY --from=build /app/target/emt-2025-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java","-jar","app.jar"]
