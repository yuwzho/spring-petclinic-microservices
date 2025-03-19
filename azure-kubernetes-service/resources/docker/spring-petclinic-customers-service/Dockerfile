FROM openjdk:17-jdk-slim
WORKDIR /app

COPY customers-service-3.4.1.jar customers-service.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "customers-service.jar"]
