FROM openjdk:11 AS BUILD_IMMAGE
RUN apt update && apt install maven -y
RUN git clone  https://github.com/bethakiran95/vprofile-project.git
RUN cd vprofile-project && git checkout containers && mvn install


FROM tomcat:9-jre11
LABEL "Project"="vprofile"
LABEL "Author"="Kiran"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=BUILD_IMMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh", "run"]