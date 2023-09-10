ENV ARTIFACTID=joycrochet-main
ENV APP_VERSION=1.0.0

FROM maven:3.8.6-jdk-11-slim AS build
COPY . /app
WORKDIR /app
RUN mvn -f pom.xml clean package

FROM openjdk:11-jre-slim
EXPOSE 6403
COPY --from=build /app/target/${ARTIFACTID}-${APP_VERSION}.jar /app/${ARTIFACTID}-${APP_VERSION}.jar
WORKDIR /app
ENTRYPOINT ["java","-jar","${ARTIFACTID}-${APP_VERSION}.jar"]