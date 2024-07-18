FROM php:8.3-fpm-bullseye as app

WORKDIR /var/www/html

# Define a build-time variables
ARG USERNAME
ARG GID
ARG UID

# Copy php necessary config
COPY ini/extra.ini /usr/local/etc/php/conf.d/extra.ini

# copy php-fpm config
COPY ./conf/www.conf /usr/local/etc/php-fpm.d/www.conf
COPY ./conf/php-fpm.conf /usr/local/etc/php-fpm.conf

## PHP extension installer image, https://github.com/mlocati/docker-php-extension-installer
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

## Install system dependencies
RUN apt update \
   && apt install -y vim curl git ca-certificates gnupg gettext-base iproute2 \
   && curl -sSfL "https://dl.cloudsmith.io/public/symfony/stable/setup.deb.sh" | bash \
   && apt install -y --no-install-recommends symfony-cli \
   && rm -rf /var/lib/apt/lists/*

# Add Symfony CLI to PATH
ENV PATH="/root/.symfony/bin:${PATH}"

RUN set -eux; \
   install-php-extensions pdo_mysql intl zip @composer

# Create a user with UID 1000 and GID 1000
RUN groupadd -g ${GID} ${USERNAME} \
   && useradd -m -r -u ${UID} -g ${USERNAME} ${USERNAME}

FROM app as app_dev

COPY ini/xdebug.ini /usr/local/etc/php/conf.d/xdebug.ini

# Install xdebug
RUN set -eux; \
	install-php-extensions xdebug

