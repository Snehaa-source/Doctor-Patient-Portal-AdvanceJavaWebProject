FROM maven:3.9-eclipse-temurin-17 AS build
WORKDIR /build
COPY . .
RUN mvn -B -DskipTests clean package

FROM tomcat:9.0-jre17
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=build /build/target/Doctor-Patient-Portal.war /usr/local/tomcat/webapps/ROOT.war
EXPOSE 8080
CMD ["catalina.sh", "run"]
