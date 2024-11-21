# Usa l'immagine Maven con OpenJDK 17 per la fase di build
FROM maven:3.8.5-openjdk-17-slim AS build

# Imposta la directory di lavoro
WORKDIR /app

# Copia i file pom.xml e la cartella src nella directory di lavoro
COPY pom.xml /app/pom.xml
COPY src /app/src

# Esegui Maven per risolvere le dipendenze e compilare il progetto
RUN mvn clean package

# Usa l'immagine di OpenJDK 17 per eseguire l'applicazione
FROM openjdk:17-alpine

# Copia il JAR compilato dalla fase di build
COPY --from=build /app/target/user-service-0.0.1-SNAPSHOT.jar /app/user-service.jar

# Espone la porta 8080
EXPOSE 8080

# Esegui l'applicazione
ENTRYPOINT ["java", "-jar", "/app/user-service.jar"]
