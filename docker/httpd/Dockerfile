FROM docker.io/amazonlinux:latest

RUN yum -y update && yum -y install \
  httpd24 \
  mod24_ssl \
  which \
  vim \
  && yum clean all

COPY ./etc/httpd/conf/httpd.conf /etc/httpd/conf/httpd.conf
COPY ./etc/httpd/conf.d/tamakiii.com.conf /etc/httpd/conf.d/tamakiii.com.conf

ENTRYPOINT httpd -D FOREGROUND
