FROM maven:3.9.1-eclipse-temurin-20 AS build
WORKDIR /demo
COPY pom.xml pom.xml
COPY src src
RUN ls && mvn clean install package -DskipTests=true

FROM eclipse-temurin:20-jdk-alpine
COPY --from=build /demo/target/demo-0.0.1-SNAPSHOT.jar demo.jar
EXPOSE 8080
ENTRYPOINT ["java", "-jar", "demo.jar"]
