FROM tomcat:8-jdk15-openjdk-slim

WORKDIR /usr/local/tomcat/webapps

RUN rm -rf /usr/local/tomcat/webapps/ROOT/*

EXPOSE 8080

ENTRYPOINT /usr/local/tomcat/bin/catalina.sh run
