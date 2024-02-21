FROM mariadb:10.9.8-jammy

# Define a build-time variables
ARG USERNAME=my-user
ARG GID=1000
ARG UID=1000

# Create a user with UID 1000 and GID 1000
RUN groupadd -g ${GID} ${USERNAME} \
    && useradd -r -u ${UID} -g ${USERNAME} ${USERNAME}