FROM openjdk:17-jdk-slim
WORKDIR /app

COPY vets-service-3.4.1.jar vets-service.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "vets-service.jar"]
