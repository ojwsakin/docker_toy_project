FROM centos:7

RUN yum -y install httpd php
WORKDIR /var/www/html

ADD index.html .
ADD httpd.conf /etc/httpd/conf

EXPOSE 80

CMD ["/usr/sbin/httpd", "-D", "FOREGROUND"]

