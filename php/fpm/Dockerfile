FROM ubuntu:14.04

ENV USER www-data
ENV GROUP www-data
ENV LISTEN 0.0.0.0:9000
ENV PM_MAX_CHILDREN 100
ENV PM_START_SERVERS 10
ENV PM_MIN_SPARE_SERVERS 5
ENV PM_MAX_SPARE_SERVERS 15
ENV PM_MAX_REQUESTS 1000

ENV OPCACHE_PRODUCTION yes

# New Relic license key
ENV NR_INSTALL_KEY aaaaaaaaaabbbbbbbbbbccccccccccdddddddddd

COPY run-php5-fpm /run-php5-fpm

RUN apt-get update && apt-get install -y ca-certificates curl libxml2 --no-install-recommends && \ 
    apt-get install -y php5-fpm php5-cli php5-curl php5-gd php5-mcrypt php5-memcache php5-mysql php5-intl php5-redis && \
    apt-get clean && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* && chmod a+x /run-php5-fpm && \
    sed -ie "s|^expose_php =.*$|expose_php = Off|g" /etc/php5/fpm/php.ini && \
    export NR_INSTALL_SILENT=true; curl -O http://download.newrelic.com/php_agent/release/newrelic-php5-4.22.0.99-linux.tar.gz && tar -xf newrelic-php5-4.22.0.99-linux.tar.gz && ./newrelic-php5-4.22.0.99-linux/newrelic-install install

COPY php-fpm.conf /etc/php5/fpm/

CMD ["/run-php5-fpm"]
