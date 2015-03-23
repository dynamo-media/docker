FROM ubuntu:14.04

RUN apt-get update && apt-get install -y ca-certificates curl libxml2 --no-install-recommends

RUN apt-get install -y php5-fpm php5-cli php5-curl php5-gd php5-mcrypt php5-memcache php5-mysql php5-intl

RUN apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*

ENV USER www-data
ENV GROUP www-data
ENV LISTEN 127.0.0.1:9000

COPY php-fpm.conf /etc/php5/fpm/
COPY run-php5-fpm /run-php5-fpm

RUN mkdir -p /data /home/www/cs_config_files
VOLUME ["/data", "/home/www/cs_config_files"]

CMD ["/run-php5-fpm"]