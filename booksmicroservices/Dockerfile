#
# Build stage
#
FROM maven:3.8.2-openjdk-16 AS build
COPY src /home/app/src
COPY pom.xml /home/app
RUN mvn -f /home/app/pom.xml clean package

#
# Package stage
#
FROM openjdk:16-oracle
COPY --from=build /home/app/target/booksmicroservices-V1.jar /usr/local/lib/Book-Microservice.jar
EXPOSE 2000
ENTRYPOINT ["java","-jar","/usr/local/lib/Book-Microservice.jar"]