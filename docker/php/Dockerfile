FROM docker.io/amazonlinux:latest

RUN yum -y update && yum -y install epel-release
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-6.rpm

RUN yum -y install \
  libyaml \
  which \
  vim \
  && yum clean all

RUN yum -y install \
  php71 \
  php71-fpm \
  php71-opcache \
  php71-bcmath \
  php71-gd \
  php71-mbstring \
  php71-mcrypt \
  php71-mysqlnd \
  php71-pecl-apcu \
  php71-pecl-memcached \
  php71-pecl-xdebug \
  && yum clean all

RUN yum -y install --disablerepo=amzn-main --enablerepo=remi-php71 \
  php-pecl-yaml \
  && yum clean all

RUN ln -s /usr/lib64/php/modules/yaml.so /usr/lib64/php/7.1/modules/yaml.so

RUN mkdir -p /var/log/app_preserve/zucks.co.jp
RUN groupadd -g 500 contentsuser && usermod -G contentsuser apache
RUN chgrp -R contentsuser /var/log/app_preserve && chmod g+rw -R /var/log/app_preserve

COPY ./etc/php-7.1.ini /etc/php-7.1.ini
COPY ./etc/php-fpm.d/www.conf /etc/php-fpm.d/www.conf

ENTRYPOINT php-fpm --nodaemonize
