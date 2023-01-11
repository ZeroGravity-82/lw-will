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
COPY --from=ghcr.io/symfony-cli/symfony-cli:5.4.21 /usr/local/bin/symfony /usr/local/bin/symfony

WORKDIR /app

# PHP configuration
COPY ./docker/php-cli/conf.d /usr/local/etc/php/conf.d

# Clean the APT cache
RUN apt-get clean && rm -rf /var/lib/apt/lists
