FROM php:7.1
RUN apt-get update \
    && apt-get install -y unzip zlib1g-dev libicu-dev \
    && docker-php-ext-install pdo pdo_mysql zip intl \
    && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
    && yes '' | pecl install -f apcu \
    && pecl clear-cache \
    && echo "extension=apcu.so" > /usr/local/etc/php/conf.d/apcu.ini

# Install Node
ENV NPM_CONFIG_LOGLEVEL notice
ENV NODE_VERSION 8.9.1

RUN curl -SLO "https://nodejs.org/dist/v$NODE_VERSION/node-v$NODE_VERSION-linux-x64.tar.xz" \
  && tar -xJf "node-v$NODE_VERSION-linux-x64.tar.xz" -C /usr/local --strip-components=1 \
  && rm "node-v$NODE_VERSION-linux-x64.tar.xz" \
  && ln -s /usr/local/bin/node /usr/local/bin/nodejs
