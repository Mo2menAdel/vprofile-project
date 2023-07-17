FROM openjdk:11 As Build-Image
RUN apt update && apt install maven -y 
RUN git clone https://github.com/Mo2menAdel/vprofile-project.git
RUN cd vprofile-project && git checkout docker && mvn install 

FROM tomcat:9-jre11
LABEL "Project"="Vprofile"
LABEL "AUTHOR"="MOAMEN"
RUN rm -rf /usr/local/tomcat/webapps/*
COPY --from=Build-Image vprofile/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080 
CMD ["catalina.sh", "run"]