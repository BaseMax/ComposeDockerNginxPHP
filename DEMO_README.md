# Docker Compose Nginx PHP MariaDB (LEMP stack)

A ready to use Docker Compose configuration for a LEMP stack (Nginx, PHP, MariaDB, and PHPMyAdmin). This configuration allows you to easily set up and run a web server with a database on your local machine using Docker.

## Requirements
- Docker: Docker is a platform that allows you to easily deploy and run applications in containers. It makes it easy to set up and run software in a consistent environment. You can download Docker from here.
- Docker Compose: Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to define your application's services, networks, and volumes in a single docker-compose.yml file. You can download Docker Compose from here.
- Ansible installed on your local machine

## Usage

Clone this repository by running git clone https://github.com/basemax/ComposeDockerNginxPHP.git in your terminal.
Navigate to the cloned repository by running cd docker-compose-lemp
Run docker-compose up -d to start the containers in detached mode.
Open http://localhost:80 in your browser for Nginx. You should see the default Nginx welcome page.
Open http://localhost:8080 in your browser for PHPMyAdmin. You will be prompted to enter a username and password to log in. The default username is root and the default password is password.

## Configuration
Nginx
The Nginx configuration is located in the nginx directory. The nginx.conf file is the main configuration file. It contains global settings for Nginx such as the number of worker processes, the user that Nginx runs as, and the location of the log files. The sites directory contains the configuration for each site. The sites/default.conf file is the default configuration for all sites. It defines the server block for the default virtual host and sets the document root to /var/www/html. The sites/example.com.conf file is an example configuration for a virtual host for the example.com site. You can add additional virtual host configuration files in this directory for any other sites you want to run on your local machine.

Ansible
Ansible is an open-source software provisioning, configuration management, and application-deployment tool. It is used to automate the management of remote servers, including the installation and configuration of software.

PHP
The PHP configuration is located in the php directory. The php.ini file is the main configuration file. It contains settings for PHP such as the maximum execution time, the memory limit, and the error reporting level.

MariaDB
The MariaDB configuration is located in the mariadb directory. The my.cnf file is the main configuration file. It contains settings for MariaDB such as the character set, the collation, and the location of the data directory.

PHPMyAdmin
The PHPMyAdmin configuration is located in the phpmyadmin directory. The config.inc.php file is the main configuration file. It contains settings for PHPMyAdmin such as the server to connect to, the username and password for the server, and the default language.

## License

  This project is licensed under the GPLv3 license. Feel free to use and modify the code as you see fit, but please make sure to comply with the terms of the license.

This Docker Compose and Ansible configuration was created in 2022.


  
