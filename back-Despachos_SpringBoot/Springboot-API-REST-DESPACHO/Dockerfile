# Etapa 1: Compilación (Build)
FROM maven:3.9.4-eclipse-temurin-17 AS builder
WORKDIR /app
COPY pom.xml .
# Descargamos las dependencias primero para aprovechar la caché de Docker
RUN mvn dependency:go-offline
COPY src ./src
# Compilamos saltando los tests para mayor velocidad
RUN mvn clean package -DskipTests

# Etapa 2: Ejecución (Run)
FROM eclipse-temurin:17-jre-alpine
WORKDIR /app
# Copiamos solo el ejecutable de la etapa anterior
COPY --from=builder /app/target/*.jar app.jar

# Configuración de seguridad: Usuario no-root
RUN addgroup -S springgroup && adduser -S springuser -G springgroup
RUN chown springuser:springgroup app.jar
USER springuser

# Exponemos el puerto de Spring Boot
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "app.jar"]