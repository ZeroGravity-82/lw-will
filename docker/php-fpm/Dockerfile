FROM php:8.2-fpm

RUN apt-get update \
    # extension required for MySQL
    && docker-php-ext-install pdo_mysql \
    # extensions recommended for ramsey/uuid
    && apt-get install -y libgmp-dev && docker-php-ext-install bcmath gmp

# Clear APT cache
RUN apt-get clean && rm -rf /var/lib/apt/lists

# Create non-root user for container
ARG HOST_USER_UID
ARG HOST_USER_GID
ENV HOST_USER_UID=${HOST_USER_UID}
ENV HOST_USER_GID=${HOST_USER_GID}
RUN addgroup --system --gid ${HOST_USER_GID} nonroot
RUN adduser --system --shell /bin/sh --uid ${HOST_USER_UID} --gid ${HOST_USER_GID} --disabled-password nonroot
RUN sed -i "s/user = www-data/user = nonroot/g" /usr/local/etc/php-fpm.d/www.conf
RUN sed -i "s/group = www-data/group = nonroot/g" /usr/local/etc/php-fpm.d/www.conf

WORKDIR /app
