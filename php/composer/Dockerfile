FROM php:5.5-cli

RUN apt-get update && DEBIAN_FRONTEND=noninteractive apt-get install -y zlib1g-dev git mercurial subversion --no-install-recommends && docker-php-ext-install zip && rm -r /var/lib/apt/lists/*
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

ENV COMPOSER_HOME /root/composer

ENTRYPOINT ["composer", "--ansi"]
