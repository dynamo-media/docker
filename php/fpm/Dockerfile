FROM ubuntu:14.04

COPY php-fpm.conf /etc/php5/fpm/
COPY run-php5-fpm /run-php5-fpm

RUN apt-get update && apt-get install -y ca-certificates curl libxml2 --no-install-recommends && \ 
    apt-get install -y php5-fpm php5-cli php5-curl php5-gd php5-mcrypt php5-memcache php5-mysql php5-intl && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && chmod a+x /run-php5-fpm

ENV USER www-data
ENV GROUP www-data
ENV LISTEN 0.0.0.0:9000

CMD ["/run-php5-fpm"]
