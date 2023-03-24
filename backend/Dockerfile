#
# Build stage
#
FROM maven:3.6.0-jdk-11-slim AS build
WORKDIR /app
COPY . /app
RUN mvn package -Dmaven.test.skip=true
#
# Package stage
#
FROM openjdk:11-jre-slim
COPY --from=build /app/target/*.jar /usr/local/lib/std.jar
EXPOSE 8080
ENTRYPOINT ["java","-jar","/usr/local/lib/std.jar"]
