# # Usa una imagen de Maven para construir la aplicación
# FROM maven:3.8.5-openjdk-17-slim AS build

# # Establece el directorio de trabajo
# WORKDIR /app

# # Copia los archivos de la aplicación al contenedor
# COPY . .

# # Configuración de variables de entorno para la base de datos
# ENV SPRING_DATASOURCE_URL=jdbc:mysql://mysql:3306/demo
# ENV SPRING_DATASOURCE_USERNAME=root
# ENV SPRING_DATASOURCE_PASSWORD=root

# # Construye el proyecto
# RUN mvn clean package -Dmaven.test.skip=true

# # Usa una imagen de Java para el runtime
# FROM openjdk:17-jdk-alpine

# # Establece el directorio de trabajo
# WORKDIR /app

# ARG JAR_FILE=target/*.jar
# # Copia el archivo JAR de tu aplicación al contenedor desde la etapa de construcción
# COPY --from=build /app/target/springboot-mysql-docker.jar app.jar

# # # Expone el puerto en el que tu aplicación se ejecutará
# # EXPOSE 8080

# # Comando para ejecutar tu aplicación
# ENTRYPOINT ["java", "-jar", "app.jar"]


# FROM openjdk:8-jdk-alpine
# ARG JAR_FILE=target/*.jar
# COPY ${JAR_FILE} app.jar
# ENTRYPOINT ["java","-jar","/app.jar"]




FROM eclipse-temurin:17-jdk-focal

WORKDIR /app

COPY .mvn/ .mvn
COPY mvnw pom.xml ./

# Add execute permission to mvnw
RUN chmod +x mvnw

# Download dependencies
RUN ./mvnw dependency:go-offline

EXPOSE 8080

COPY src ./src

CMD ["./mvnw", "spring-boot:run"]
