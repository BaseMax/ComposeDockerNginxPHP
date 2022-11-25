# Docker Compose Nginx PHP MariaDB (LEMP stack)

A ready to use Docker Compose configuration for a LEMP stack (Nginx, PHP, MariaDB, and PHPMyAdmin).

## Requirements

- Docker
- Docker Compose

## Usage

1. Clone this repository
2. Run `docker-compose up -d`
3. Open `http://localhost:80` in your browser for Nginx
4. Open `http://localhost:8080` in your browser for PHPMyAdmin

## Configuration

### Nginx

The Nginx configuration is located in the `nginx` directory. The `nginx.conf` file is the main configuration file. The `sites` directory contains the configuration for each site. The `sites/default.conf` file is the default configuration for all sites. The `sites/example.com.conf` file is the configuration for the `example.com` site.

### PHP

The PHP configuration is located in the `php` directory. The `php.ini` file is the main configuration file.

### MariaDB

The MariaDB configuration is located in the `mariadb` directory. The `my.cnf` file is the main configuration file.

### PHPMyAdmin

The PHPMyAdmin configuration is located in the `phpmyadmin` directory. The `config.inc.php` file is the main configuration file.

## License

GPLv3

This Docker Compose configuration was created in 2022.
