FROM php:8.3.3-apache-bullseye

WORKDIR /var/www/html

# Define a build-time variables
ARG USERNAME=my-user
ARG GID=1000
ARG UID=1000

## Install system dependencies
RUN apt-get update \
    && apt-get install -y vim curl git

# PHP extension installer image, https://github.com/mlocati/docker-php-extension-installer
COPY --from=mlocati/php-extension-installer /usr/bin/install-php-extensions /usr/local/bin/

# Install typo3  nesseccery php extensions
RUN set -eux; \
    install-php-extensions  gd pdo_mysql intl zip @composer

# Add typo3 PHP configuration
RUN echo "memory_limit=256M" >> /usr/local/etc/php/conf.d/typo3.ini && \
    echo "max_execution_time=240" >> /usr/local/etc/php/conf.d/typo3.ini && \
    echo "max_input_vars=1500" >> /usr/local/etc/php/conf.d/typo3.ini && \
    echo "post_max_size = 10M" >> /usr/local/etc/php/conf.d/typo3.ini && \
    echo "upload_max_filesize" >> /usr/local/etc/php/conf.d/typo3.ini


# Create a user with UID 1000 and GID 1000
RUN groupadd -g ${GID} ${USERNAME} \
    && useradd -m -r -u ${UID} -g ${USERNAME} ${USERNAME}
