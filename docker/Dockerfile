FROM maven:3.8.1-openjdk-17-slim

WORKDIR /build

# Build dependency offline to streamline build
COPY pom.xml .
#COPY settings.xml .
#RUN mvn dependency:go-offline

COPY src src
RUN mvn package -Dmaven.test.skip=true

FROM openjdk:11-jdk
COPY --from=0 /build/target/camel-example-spring-boot-xml-3.14.1-SNAPSHOT.jar /app/target/camel-example-spring-boot-xml-3.14.1-SNAPSHOT.jar

EXPOSE 8081
ENTRYPOINT [ "java", "-jar", "/app/target/camel-example-spring-boot-xml-3.14.1-SNAPSHOT.jar", "--server.port=8081" ]
