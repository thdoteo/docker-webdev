# docker-webdev

A docker config to develop with web technologies (PHP, MySQL). 

## Features

- Apache
- PHP
- MySQL + PhpMyAdmin
- Maildev
- Folder (+ logs) shared between host and guest (see `docker-compose.yml`)

## Usage

Create and start containers with:

	$ docker-compose up -d

Type the following command to stop services:

	$ docker-compose stop

List containers and check their status:

	$ docker-compose ps

Connect to a container and type commands in it:

	$ docker exec -t -i [container id] /bin/bash