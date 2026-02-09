# ---------- 1️⃣ BUILD STAGE ----------
FROM eclipse-temurin:21-jdk AS build

WORKDIR /app

# Копирај сè што му треба на Maven
COPY . .

# Изгради го jar-от (без тестови за CI)
RUN mvn clean package -DskipTests

# ---------- 2️⃣ RUNTIME STAGE ----------
FROM eclipse-temurin:21-jdk

WORKDIR /app

# Копирај го jar-от од build stage
COPY --from=build /app/target/emt-2025-0.0.1-SNAPSHOT.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]
