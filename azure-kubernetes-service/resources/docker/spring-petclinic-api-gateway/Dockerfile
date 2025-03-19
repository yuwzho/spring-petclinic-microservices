FROM openjdk:17-jdk-slim
WORKDIR /app

COPY api-gateway-3.4.1.jar api-gateway.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "api-gateway.jar"]
