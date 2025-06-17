FROM maven:maven:3.9.9-eclipse-temurin-21-jammy AS build_image

RUN git clone https://github.com/Rushi247/Ultimate-CICD.git
WORKDIR /Ultimate-CICD/vprofile-project
RUN mvn clean install

FROM tomcat:10-jdk21

RUN rm -rf /usr/local/tomcat/webapps/*

COPY --from=build_image /Ultimate-CICD/vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]
