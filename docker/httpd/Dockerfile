FROM php:8.1.25-apache-bullseye

WORKDIR /var/www/html

# Define a build-time variables
ARG USERNAME=my-user
ARG GID=1000
ARG UID=1000

# Useful PHP extension installer image, copy binary into your container
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

## Install system dependencies
RUN apt-get update \
    && apt-get install -y vim curl

# Install Composer manually
RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer

# Create a user with UID 1000 and GID 1000
RUN groupadd -g ${GID} ${USERNAME} \
    && useradd -m -r -u ${UID} -g ${USERNAME} ${USERNAME}
