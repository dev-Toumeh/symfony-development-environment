FROM httpd:latest

WORKDIR /var/www/html

# Define a build-time variables
ARG USERNAME
ARG GID
ARG UID

RUN mkdir -p /var/run/mod_fcgid

RUN apt update && apt install -y vim curl wget gettext-base build-essential libfcgi-dev libaprutil1-dev

RUN cd /usr/src \
    && wget https://downloads.apache.org/httpd/mod_fcgid/mod_fcgid-2.3.9.tar.gz \
    && tar xvfz mod_fcgid-2.3.9.tar.gz \
    && cd mod_fcgid-2.3.9 \
    && APXS=/usr/local/apache2/bin/apxs ./configure.apxs \
    && make \
    && make install

# Copy httpd configuration files
COPY conf/httpd.conf /usr/local/apache2/conf/httpd.conf
COPY conf/httpd-vhosts.conf /usr/local/apache2/conf/extra/httpd-vhosts.conf

# Include the httpd-vhosts.conf in the httpd.conf
RUN echo "Include conf/extra/httpd-vhosts.conf" >> /usr/local/apache2/conf/httpd.conf

# Create a user with UID 1000 and GID 1000
RUN groupadd -g ${GID} ${USERNAME} \
   && useradd -m -r -u ${UID} -g ${USERNAME} ${USERNAME}

# Change ownership or modify permissions of the Apache configuration directory
RUN chown -R ${USERNAME}:${USERNAME} /usr/local/apache2 \
    && chmod -R 755 /usr/local/apache2
