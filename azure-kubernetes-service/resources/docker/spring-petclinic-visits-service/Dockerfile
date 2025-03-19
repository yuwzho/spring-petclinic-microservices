FROM openjdk:17-jdk-slim
WORKDIR /app

COPY visits-service-3.4.1.jar visits-service.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "visits-service.jar"]
