FROM centos:7

RUN yum -y update && yum -y install \
  httpd \
  mod_ssl \
  which \
  vim \
  && yum clean all

COPY ./etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf
COPY ./etc/httpd/conf.d/tamakiii.com.conf /etc/httpd/conf.d/tamakiii.com.conf

ENTRYPOINT httpd -D FOREGROUND
