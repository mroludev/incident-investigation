FROM maven:3.8.4-jdk-11 AS build
COPY src /app/src
COPY pom.xml /app
RUN mvn -f /app/pom.xml clean package

FROM openjdk:11-jre-slim
COPY --from=build /app/target/incident-service.jar /app/incident-service.jar
ENTRYPOINT ["java","-jar","/app/incident-service.jar"]