FROM php:7-fpm

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

RUN export NR_INSTALL_SILENT=true; export NR_VERSION="6.1.0.157"; \
    curl -O "http://download.newrelic.com/php_agent/archive/${NR_VERSION}/newrelic-php5-${NR_VERSION}-linux.tar.gz" && \
    tar -xf "newrelic-php5-${NR_VERSION}-linux.tar.gz" && ./newrelic-php5-${NR_VERSION}-linux/newrelic-install install && \
    rm -rf newrelic*

COPY php-fpm.conf /usr/local/etc/

CMD ["/run-php5-fpm"]
