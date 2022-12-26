FROM centos:7

RUN mkdir -p /tomcat
WORKDIR /tomcat
RUN yum install -y java-1.8.0-openjdk &&\
    yum install -y wget &&\
    yum install -y unzip

WORKDIR /tomcat
RUN wget http://dlcdn.apache.org/tomcat/tomcat-10/v10.0.27/bin/apache-tomcat-10.0.27.zip
RUN unzip apache-tomcat-10.0.27.zip
RUN rm -rf apache-tomcat-10.0.27.zip
RUN chmod -R 777 /tomcat
WORKDIR /tomcat/apache-tomcat-10.0.27/lib
RUN wget https://repo1.maven.org/maven2/mysql/mysql-connector-java/8.0.30/mysql-connector-java-8.0.30.jar

COPY test.jsp /tomcat/apache-tomcat-10.0.27/webapps/ROOT/test.jsp
COPY dbtest.jsp /tomcat/apache-tomcat-10.0.27/webapps/ROOT/dbtest.jsp

EXPOSE 8080

CMD ["/tomcat/apache-tomcat-10.0.27/bin/catalina.sh","run"]
