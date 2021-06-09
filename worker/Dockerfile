FROM maven:3.5-jdk-8-alpine as builder
WORKDIR /app
COPY . .
RUN mvn dependency:resolve

RUN mvn package

FROM openjdk:8-jre-alpine
WORKDIR /app
COPY --from=builder /app/target/worker-jar-with-dependencies.jar /app
CMD ["java", "-jar", "worker-jar-with-dependencies.jar"]