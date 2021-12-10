FROM centos:7
MAINTAINER David Martín <david@aletiasoluciones.com>

LABEL version="1.0" PHP="7.1"

RUN yum install -y --setopt=tsflags=nodocs epel-release yum-utils http://rpms.remirepo.net/enterprise/remi-release-7.rpm httpd && \
	yum-config-manager --enable remi-php71 && \
	yum install -y --setopt=tsflags=nodocs php php-common php-opcache php-mcrypt php-cli php-gd php-curl php-mysql && \
	mkdir /var/www/html/css

COPY css_content/ /var/www/html/css
COPY web_app /var/www/html/
COPY run-apache.sh /
RUN chgrp -R 0 /var/www /etc/httpd /run/httpd /var/log/httpd && \
    chmod -R g=u /var/www /etc/httpd /run/httpd /var/log/httpd && \
    sed -i 's/Listen 80/Listen 8080/' /etc/httpd/conf/httpd.conf
EXPOSE 8080

CMD /run-apache.sh
