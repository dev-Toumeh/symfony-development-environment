# Docker-Based TYPO3 Development Environment Setup

## Overview
This project was built to serve as a TYPO3 development and deployment environment, based on the
[TYPO3 System Requirements](https://docs.typo3.org/m/typo3/tutorial-getting-started/main/en-us/SystemRequirements/Index.html).

## Project Tree
    ├── docker
    │   ├── httpd
    │   │   ├── conf
    │   │   │   ├── mywebsite_vhost.conf
    │   │   │   ├── extra.ini
    │   │   │   └── xdebug.ini
    │   │   ├── Dockerfile
    │   │   └── env
    │   │       ├── extra.env
    │   │       ├── extra.env.template
    │   │       └── httpd.env
    │   └── mysql
    │       └── Dockerfile
    ├── src
    ├── docker-compose.dev.yaml
    ├── docker-compose.yaml
    ├── LICENSE
    └── README.md

## Prerequisites

Before setting up the project, ensure you have Docker and docker-compose installed on your machine. Follow the instructions below to install them:

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
