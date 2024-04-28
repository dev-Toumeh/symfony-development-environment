# php-dockerCompose-devstack
## Overview
This repository is designed to serve as a foundation for projects based on PHP.
**Every branch in this repository will serve different PHP Framework**,
in case you didn't find the Framework you are looking for you can use the main Branch
## Project Tree
    ├── docker
    │   ├── httpd
    │   │   ├── conf
    │   │   │   ├── mywebsite_vhost.conf
    │   │   │   ├── extra.ini.template
    │   │   │   └── xdebug.ini
    │   │   ├── Dockerfile
    │   │   └── env
    │   │       ├── extra.env
    │   │       ├── extra.env.template
    │   │       └── httpd.env
    │   └── mysql
    │       └── Dockerfile
    ├── src
    ├── .gitignore.template
    ├── docker-compose.dev.yaml
    ├── docker-compose.yaml
    ├── LICENSE
    └── README.md

# Decisions
- the project's main focus is building PHP Environment repository, that can server in any situation and under every Circumstances
- other goals are improving my skills in docker and docker-compose
- use GitHub as the main platform (central place for information)
    - version control
    - documentation
    - issues
    - less searching
    - ability to use CI/CD (GitHub Actions) at a later time if necessary
- learn Kubernetes
## Technologies used
- PHP
- Apache
## Available Branches
### Typo3
### Symfony
## Development Environment Configuration
### General commands

- docker compose  run
```bash
 docker-compose up -d
```
- docker compose stop
```bash
 docker-compose stop
```
- docker-compose stop and remove the Services
```bash
 docker-compose down
```
- start Terminal inside docker-compose service
```bash
docker-compose exec -it <service-name> /bin/bash
```
- start Terminal inside docker-compose service as root user
```bash
docker-compose exec -it -u 0 <service-name> /bin/bash
```
- build the service again after you made changes in dockerfile
```bash
 docker-compose build <service-name>
```
- build the service again after you made changes in dockerfile without cache
```bash
 docker-compose build <service-name> --no-cache
```
- run and build the service after you made changes in dockerfile
```bash
 docker-compose up -d <service-name> --build
```