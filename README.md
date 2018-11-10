# DEVELOPMENT ENVIRONMENT SETUP

This is a collection of development tools I use to accomplish different tasks. The setup requires Docker installed on the host machine and then running the docker-compose configuration included here. There are some minor configuration details that will need to be modified to suit as well as some differences based on the OS used on the host machine.

Tools available:

* [Portainer](#portainer)
* [Sonarqube](#sonarqube)
* [Postgres](#postgres)
* [Hound](#hound)

### PORTAINER

[Portainer](https://portainer.io/) is a web-based GUI management tool for Docker. It's dead-simple to install and run and allows for easy management of containers, images, volumes and networks. When run via the docker-compose file included in this project, it can be accessed via [port 480 on localhost](http://localhost:480). More documentation on using Portainer can be found [here](https://portainer.readthedocs.io/en/stable/)

_Windows 10 Portainer Notes_

Open a PowerShell console as Administrator and execute the following two commands:
```
$ netsh interface portproxy add v4tov4 listenaddress=10.0.75.1 listenport=2375 connectaddress=127.0.0.1 connectport=2375
$ netsh advfirewall firewall add rule name="docker management" dir=in action=allow protocol=TCP localport=2375
```
The first line connects 10.0.75.1:2375 to the daemon socket on 127.0.0.1:2375, and the second line adds a pass-through on the firewall for the port 2375. Note that for this to work you need to enable "Expose daemon on tcp://localhost:2375 without TLS" from Docker settings under the "General" tab. According to Docker documentation, "Exposing daemon on TCP without TLS helps legacy clients connect to the daemon. It also makes yourself vulnerable to remote code execution attacts. Use with caution."

### SONARQUBE

_To be filled in with Sonarqube explained_

### POSTGRES

_To be filled in with Postgres explained_

### HOUND

_To be filled in with Hound explained_