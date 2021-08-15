FROM maven:3.3.9-jdk-8 as maven_builder
#RUN mkdir /code
WORKDIR /code
COPY pom.xml .
COPY src ./src
RUN mvn clean package

FROM  openjdk:8-jdk-alpine
#FROM fabric8/java-alpine-openjdk8-jdk
#RUN mkdir /code
WORKDIR /app
#EXPOSE 8080
COPY --from=maven_builder /code/target/spring-boot-web.jar .
ENTRYPOINT [ "java", "-jar", "spring-boot-web.jar" ]
