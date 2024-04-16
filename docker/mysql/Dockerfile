FROM mariadb:10.9.8-jammy

# Define a build-time variables
ARG USERNAME
ARG GID
ARG UID

RUN groupadd -g ${GID} ${USERNAME} \
    && useradd -m -r -u ${UID} -g ${USERNAME} ${USERNAME}

RUN chown -R ${USERNAME}:${USERNAME} /var/lib/mysql

CMD ["mysqld", "--user=${USERNAME}"]
