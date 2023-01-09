FROM php:8.2-cli

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer --version=2.5.1 --quiet
RUN apt-get update && apt-get install -y unzip \
    # extension required for MySQL
    && docker-php-ext-install pdo_mysql \
    # extensions recommended for ramsey/uuid
    && apt-get install -y libgmp-dev && docker-php-ext-install bcmath gmp \
    # extension required for XDebug
    && pecl install xdebug-3.2.0 && rm -rf /tmp/pear && docker-php-ext-enable xdebug

# Install Symfony CLI
RUN curl -1sLf 'https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh' | bash \
    && apt-get update && apt-get install -y symfony-cli

ENV WORKDIR /app/
WORKDIR ${WORKDIR}

# PHP configuration
COPY ./docker/php-cli/conf.d /usr/local/etc/php/conf.d

# Clean the APT cache
RUN apt-get clean && rm -rf /var/lib/apt/lists
