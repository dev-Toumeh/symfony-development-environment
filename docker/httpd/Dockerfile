FROM php:8.3.3-apache-bullseye

WORKDIR /var/www/html

# Define a build-time variables
ARG USERNAME
ARG GID
ARG UID




## Install system dependencies
RUN apt-get update \
    && apt-get install -y vim curl git

## PHP extension installer image, https://github.com/mlocati/docker-php-extension-installer
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

## The following is based on typo3 System Requirements
# Install typo3  nesseccery php extensions
RUN set -eux; \
    install-php-extensions   pdo_mysql intl zip @composer # gd \

# Copy typo3 php config
COPY ./conf/typo3.ini /usr/local/etc/php/conf.d/typo3.ini
#typo3 php variables
ENV PHP_MAX_EXECUTION_TIME=240 \
    PHP_POST_MAX_SIZE=10M \
    PHP_UPLOAD_MAX_FILE_SIZE=10M \
    PHP_MEMORY_LIMIT=256

# Create a user with UID 1000 and GID 1000
RUN groupadd -g ${GID} ${USERNAME} \
    && useradd -m -r -u ${UID} -g ${USERNAME} ${USERNAME}