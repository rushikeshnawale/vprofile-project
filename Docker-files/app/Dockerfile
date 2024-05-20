FROM openjdk:8 AS BUILD_IMAGE
RUN apt update && apt install maven -y
RUN git clone https://github.com/rushikeshnawale/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install

FROM tomcat:8-jre11
LABEL "Project"="Vprofile"
LABEL "Author"="Rushi"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]