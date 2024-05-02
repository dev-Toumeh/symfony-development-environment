# Symfony Development Environment
## Overview
This repository is designed to serve as a foundation for php Symfony Projects.
## Project Tree
    .
    ├── docker
    │   ├── httpd
    │   │   ├── conf
    │   │   │   ├── httpd.conf
    │   │   │   └── httpd-vhosts.conf
    │   │   ├── Dockerfile
    │   │   └── env
    │   │       └── httpd.env
    │   ├── mysql
    │   │   └── Dockerfile
    │   └── php
    │       ├── conf
    │       │   └── www.conf
    │       ├── Dockerfile
    │       ├── env
    │       │   └── php.env
    │       └── ini
    │           ├── extra.ini
    │           ├── extra.ini.template
    │           └── xdebug.ini
    ├── src
    │   └── .gitignore
    ├── docker-compose.dev.yaml
    ├── docker-compose.yaml
    ├── .gitignore.template
    ├── LICENSE
    └── README.md

# Decisions
- the project's main focus is building PHP Environment repository that can server in any situation and under every Circumstances
- other goals are improving my skills in docker and docker-compose
- use GitHub as the main platform (central place for information)
    - version control
    - documentation
    - issues
    - less searching
    - ability to use CI/CD (GitHub Actions) at a later time if necessary

## Technologies used
- PHP-fpm
- Apache
- redis
- mysql

## Docker-Compose Commands

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