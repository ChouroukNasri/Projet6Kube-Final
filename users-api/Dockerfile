# Étape 1: Construction de l'application
FROM maven:3.8.4-openjdk-11 AS build
WORKDIR /usr/src/app

# Copier le fichier pom.xml
COPY pom.xml ./

# Copier le code source
COPY src ./src

# Construire le package
RUN mvn clean package -DskipTests

# Étape 2: Exécution de l'application
FROM openjdk:11-jre-slim
WORKDIR /usr/src/app

# Copier le JAR construit à partir de l'étape précédente
COPY --from=build /usr/src/app/target/*.jar app.jar

# Exposer le port (modifiez si nécessaire)
EXPOSE 8080

# Commande pour exécuter l'application
ENTRYPOINT ["java", "-jar", "app.jar"]

