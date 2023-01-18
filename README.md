# LEMP stack on docker

A ready to use Docker Compose configuration for a LEMP stack (Nginx, PHP, MariaDB, and PHPMyAdmin). This configuration allows you to easily set up and run a web server with a database on your local machine using Docker and also this project contain a Ansible playbook that allows you to run this LEMP stack in any number of remote hosts.

<p align="center">
  <img width="90%" src="https://github.com/BaseMax/ComposeDockerNginxPHP/blob/main/images/compose.gif">
</p>

Based on the official Docker images:

* [Nginx](https://hub.docker.com/_/nginx)
* [PHPMyAdmin](https://hub.docker.com/_/phpmyadmin)
* [PHP](https://hub.docker.com/_/php)
* [MariaDB](https://hub.docker.com/_/mariadb)

> **Note**  
> You can change the version and tag of images in [.env](https://github.com/BaseMax/ComposeDockerNginxPHP/blob/main/.env) file.

---

## Requirements

* **Docker**: Docker is a platform that allows you to easily deploy and run applications in containers. It makes it easy to set up and run software in a consistent environment. You can install docker with [this guide](https://docs.docker.com/engine/install/ubuntu/).
* **Docker Compose**: Docker Compose is a tool for defining and running multi-container Docker applications. It allows you to define your application's services, networks, and volumes in a single docker-compose.yml file. You can install Docker Compose with [this guide](https://docs.docker.com/engine/install/ubuntu/).
* **Ansible**: If you want use ansible for deploy this stack on remote servers you must install ansible on you local machine with [this guide](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html) and `python3` on remote servers.

### Host setup

* [Docker Engine](https://docs.docker.com/engine/release-notes/) version **18.06.0** or newer
* [Docker Compose](https://docs.docker.com/compose/release-notes/) version **2.3.4** or newer

> **Warning**  
> For running this stack you must use `docker compose up` instead of `docker-compose up` (see [this](https://github.com/BaseMax/ComposeDockerNginxPHP/issues/2)).
>
> **Note**  
> Especially on Linux, make sure your user has the [required permissions](https://docs.docker.com/engine/install/linux-postinstall/) to interact with the Docker
> daemon.

By default, the stack exposes the following ports:

* 9000: PHP
* 80 and 443: Nginx
* 8080: PHPMyAdmin

---

## Contents

1. [Requirements](#requirements)
   * [Host setup](#host-setup)
2. [Philosophy](#philosophy)
3. [So I must use it?](#so-i-must-use-it)
4. [Usage](#usage)
   * [Bringing up the stack](#bringing-up-the-stack)
5. [Configuration](#configuration)
   * [How to configure Nginx](#how-to-configure-nginx)
   * [How to configure PHP](#how-to-configure-php)
   * [How to configure MariaDB](#how-to-configure-mariadb)
   * [How to configure PHPMyAdmin](#how-to-configure-phpmyadmin)
   * [How to configure Ansible](#how-to-configure-ansible)
6. [License](#license)
7. [Contributors](#contributors)

## Philosophy

**Docker Compose** is a powerful tool for simplifying the process of setting up and running complex applications. This particular Docker Compose configuration for a LEMP stack (Nginx, PHP, MariaDB, and PHPMyAdmin) makes it easy to set up a complete web server environment on your local machine and servers.

One of the main advantages of using this configuration is that it allows you to run all of the services in separate containers, which ensures that they are isolated from each other and from your host system. This makes it easy to manage and update the services independently of each other, and also makes it easy to switch out one service for another if needed.

Another advantage of this configuration is that it makes it easy to configure the services. Each service has its own directory with configuration files that can be easily modified to suit your needs. Additionally, the Ansible integration makes it easy to provision and configure the services.

Furthermore, this configuration is also customizable by adding new services or customizing the existing ones as per your requirement. The flexibility of this configuration makes it easy to use and adapt for different projects, whether for development or production.

In summary, this Docker Compose configuration provides a quick and easy way to set up a complete web server environment on your local machine and remote servers with ansible. It is easy to use, customizable, and allows you to run all of the services in isolated containers, which makes it easy to manage and update them. So, if you're looking for a powerful and flexible tool to help you set up and run your web applications, this Docker Compose configuration is definitely worth checking out.

## So I must use it?

When you manually set up a web server environment on a physical or virtual server, you would typically have to install and configure each service individually. This can be a time-consuming and error-prone process, as you would have to manually install the software, configure it, and make sure that it is running correctly.

Additionally, when you set up a web server environment manually, you would also have to manually manage the dependencies between the services. For example, you would have to make sure that the database service is running before the web server service, and that the web server service is configured to connect to the correct database.

In contrast, using this Docker Compose configuration, all of the services are defined in a single file, docker-compose.yml, and the dependencies between them are also defined in this file. This makes it easy to understand and manage the dependencies between the services, and also makes it easy to add or remove services as needed.

Additionally, when you set up a web server environment manually, the services are running on the host operating system and share the same resources and dependencies. This can lead to conflicts and issues if the services have different requirements. With Docker Compose, each service runs in its own container, which is isolated from the host system and other services. This eliminates the potential conflicts and issues caused by shared dependencies.

Finally, with manual setup, you need to take care of security updates and configuration backups, whereas, with Docker Compose, it's easy to update, backup and restore the services.

In summary, while manually setting up a web server environment on a physical or virtual server can be a time-consuming and error-prone process, using this Docker Compose configuration simplifies the process by allowing you to define and manage all of the services in a single file, and by isolating the services from each other and from the host system.

## Usage

### Bringing up the stack

Clone this repository onto the Docker host that will run the stack:

```console
git clone https://github.com/BaseMax/ComposeDockerNginxPHP.git
```

then navigate to project directory and start the stack's services locally using Docker Compose:

```console
docker compose up
```

> **Note**  
> You can also run all services in the background (detached mode) by appending the `-d` flag to the above command.

Now for test, Open `http://localhost:80` for Nginx. You should see the default Nginx welcome page.
Open `http://localhost:8080` in your browser for PHPMyAdmin. You will be prompted to enter a username and password to log in. The default username is `root` and the default password is `changethis`.

## Configuration

> **Note**  
> Configuration is not dynamically reloaded, you will need to restart individual components after any configuration
> change.

### How to configure Nginx

The nginx configuration file is located in the nginx directory. The `nginx.conf` file is main configuration file. It contains global settings for Nginx such as number of worker processes, the user that Nginx runs as, and the location of the log files. The `sites` directory contains the configuration for each site. The sites/default.conf file is the default configuration for all sites. It defines the server block for the default virtual host and sets the document root to `/var/www/html`. The sites/example.com.conf file is an example configuration for a virtual host for the example.com site. You can add additional virtual host configuration files in this directory for any other sites you want to run on your local machine.

### How to configure PHP

The PHP configuration is located in the php directory. The php.ini file is the main configuration file. It contains settings for PHP such as the maximum execution time, the memory limit, and the error reporting level.

### How to configure MariaDB

The MariaDB configuration is located in the mariadb directory. The my.cnf file is the main configuration file. It contains settings for MariaDB such as the character set, the collation, and the location of the data directory.

### How to configure PHPMyAdmin

The PHPMyAdmin configuration is located in the phpmyadmin directory. The config.inc.php file is the main configuration file. It contains settings for PHPMyAdmin such as the server to connect to, the username and password for the server, and the default language.

### How to configure Ansible

> **Warning**  
> For now only work in ubuntu servers.

Ansible is an open-source software provisioning, configuration management, and application-deployment tool. It is used to automate the management of remote servers, including the installation and configuration of software. If you want deploy this stack on one or more remote servers you must use [ansible playbooj](https://github.com/BaseMax/ComposeDockerNginxPHP/blob/main/ansible/playbook.yml).

First you need to add your server information in `hosts.ini` file:

```ini
[webservers]
<IP_OF_YOUR_SERVER> ansible_ssh_host=<IP_OF_YOUR_SERVER> ansible_ssh_port=<SSH_PORT_NUMBER> ansible_ssh_user=root ansible_ssh_private_key_file=<PATH_TO_PRIVATE_SSH_KEY>
```

> **Warning**  
> In order to Playbook work properly, the name of each host must be exactly th IP of the same server.

This playbook first install latest version of docker and docker compose on remote servers with add docker GPG key and add Docker Repository to ubuntu server. You must specify ubuntu release in playbook var:

```yml
vars:
    ubuntu_release: <UBUNTU_RELEASE>
```

You can specify proxy configuration for docker in server's in file `proxy.conf` in the `ansible` directory. see this:

```ini
[Service]
Environment="HTTP_PROXY=<PUT_YOUR_PROXY_URL_HERE>"
Environment="HTTPS_PROXY=<PUT_YOUR_PROXY_URL_HERE>"
Environment="NO_PROXY="localhost,127.0.0.1,::1"
```

> **Note**  
> It is a good feature for **IRANIAN** people that the use of Docker and Docker Hub in iran is filtered.

After installing docker and setting proxy for that, Playbook uploads the project files to the server in the `/root` directory according to the path you define in playbook:

```yml
vars:
    project_path: <PUT_ABSOLUTE_PATH_HERE>
```

After all above steps you must go in ansible directory and run:

```console
ansible-playbook -i hosts.ini playbook.yml
```

And finally start project with running docker compose file.

> **Warning**  
> In all the above steps you must have `root` access to servers.

## License

This project is licensed under the GPLv3 license. Feel free to use and modify the code as you see fit, but please make sure to comply with the terms of the license.

This Docker Compose and Ansible configuration was created in 2022.

## Contributors

<a href="https://github.com/BaseMax/ComposeDockerNginxPHP">
  <img src="https://contrib.rocks/image?repo=BaseMax/ComposeDockerNginxPHP"/>
</a>
