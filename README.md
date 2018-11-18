# DEVELOPMENT ENVIRONMENT SETUP

This is a collection of development tools I use to accomplish different tasks. The setup requires Docker installed on the host machine and then running the docker-compose configuration included here. There are some minor configuration details that will need to be modified to suit as well as some differences based on the OS used on the host machine.

Once you've set up Docker on the host machine, you can set these tools up with docker-compose by running `docker-compose up` from this folder. If you wish to run the containers in the background you can use the -d option: `docker-compose up -d`. For other docker-compose options, run `docker-compose` in the shell or check out the documentation [here](https://docs.docker.com/compose/reference/up/).

Tools available:

* [Portainer](#portainer)
* [Sonarqube](#sonarqube)
* [Postgres](#postgres)
* [Hound](#hound)
* [Nginx](#nginx)

### PORTAINER

[Portainer](https://portainer.io/) is a web-based GUI management tool for Docker. It's dead-simple to install and run and allows for easy management of containers, images, volumes and networks. When run via the docker-compose file included in this project, it can be accessed via [port 480 on localhost](http://localhost:480). More documentation on using Portainer can be found [here](https://portainer.readthedocs.io/en/stable/).

_Windows 10 Portainer Notes_

If you're running on Windows, add the following to your PowerShell profile script: `$Env:COMPOSE_CONVERT_WINDOWS_PATHS=1`

### SONARQUBE

[SonarQube](https://www.sonarqube.org/) is an indispensable development tool that highlights issues with the code such as bugs, security vulnerabilities or insufficient test coverage. It allows you to set a quality gate and to monitor code over time for accumulation of technical debt. Using SonarQube as part of your development workflow will help you systematically improve your code quality.

### POSTGRES

Postgres is a powerful, open-source object-relational database system. It's used here as the backing store for SonarQube.

### HOUND

Hound is a simple and lightweight tool used to index your repositories allowing you to search for anything in the code. Particularly useful on large projects or when working with unfamiliar codebases.

### NGINX

[NGINX](https://nginx.org/en/) is an application that can be used as an HTTP and reverse proxy server, a mail proxy server or a TCP/UDP proxy server. Here are we using it as a reverse proxy to allow all of our development tools to appear as they are served by a single application server. We can access the applications as:
    - Portainer - http://localhost/portainer
    - Hound - http://localhost/hound
    - Sonarqube = http://localhost/sonarqube

Note that localhost above can be replaced with another name assuming that it's added to the hostfile. Additionally, it the tools are hosted on a separate server, they can be served under a different domain name with a single IP address.

