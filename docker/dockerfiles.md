# Dockerfile

## Example: Minimal

```
FROM ubuntu:latest
# docker build -t "sea/timecheck" .
ENTRYPOINT ["date"]
```

## Example: Spring Boot

```
FROM openjdk:8-jdk-alpine
RUN addgroup -S spring && adduser -S spring -G spring
USER spring:spring
ARG JAR_FILE=target/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
