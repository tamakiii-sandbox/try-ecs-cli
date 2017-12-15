FROM centos:7

RUN yum -y update && yum -y install epel-release
RUN rpm -Uvh http://rpms.famillecollet.com/enterprise/remi-release-7.rpm

RUN yum -y install \
  libyaml \
  which \
  vim \
  less \
  git

RUN yum -y install --enablerepo=remi-php71 \
  php \
  php-fpm \
  php-opcache \
  php-bcmath \
  php-gd \
  php-mbstring \
  php-mcrypt \
  php-mysqlnd \
  php-pecl-apcu \
  php-pecl-memcached \
  php-pecl-xdebug

RUN yum clean all && rm -rf /var/cache/yum

RUN groupadd -g 500 contentsuser && usermod -G contentsuser apache
RUN mkdir -p /var/log/app_preserve/zucks.co.jp
RUN chgrp -R contentsuser /var/log/app_preserve && chmod g+rw -R /var/log/app_preserve

COPY ./etc/php.ini /etc/php.ini
COPY ./etc/php-fpm.d/www.conf /etc/php-fpm.d/www.conf

ENTRYPOINT php-fpm --nodaemonize
