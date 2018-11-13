# DEVELOPMENT ENVIRONMENT SETUP

This is a collection of development tools I use to accomplish different tasks. The setup requires Docker installed on the host machine and then running the docker-compose configuration included here. There are some minor configuration details that will need to be modified to suit as well as some differences based on the OS used on the host machine.

Once you've set up Docker on the host machine, you can set these tools up with docker-compose by running `docker-compose up` from this folder. If you wish to run the containers in the background you can use the -d option: `docker-compose up -d`. For other docker-compose options, run `docker-compose` in the shell or check out the documentation [here](https://docs.docker.com/compose/reference/up/).

Tools available:

* [Portainer](#portainer)
* [Sonarqube](#sonarqube)
* [Postgres](#postgres)
* [Hound](#hound)

### PORTAINER

[Portainer](https://portainer.io/) is a web-based GUI management tool for Docker. It's dead-simple to install and run and allows for easy management of containers, images, volumes and networks. When run via the docker-compose file included in this project, it can be accessed via [port 480 on localhost](http://localhost:480). More documentation on using Portainer can be found [here](https://portainer.readthedocs.io/en/stable/).

_Windows 10 Portainer Notes_

If you're running on Windows, add the following to your PowerShell profile script:
``` $Env:COMPOSE_CONVERT_WINDOWS_PATHS=1

### SONARQUBE

_To be filled in with Sonarqube explained_

### POSTGRES

_To be filled in with Postgres explained_

### HOUND

_To be filled in with Hound explained_