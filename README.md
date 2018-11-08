# DEVELOPMENT ENVIRONMENT SETUP

#### Install and configure Docker for the environment being used.

#### Install Sonarqube via console: 

```
$ docker pull sonarqube
```

#### Install MySQL via console:

```
$ docker pull mysql
```

#### Install Portainer

##### Linux/MacOS

```
$ docker volume create portainer_data
$ docker run -d -p 9000:9000 -v /var/run/docker.sock:/var/run/docker.sock -v portainer_data:/data portainer/portainer
```

##### Windows 10

Open a PowerShell console as Administrator and execute the following two commands:
```
$ netsh interface portproxy add v4tov4 listenaddress=10.0.75.1 listenport=2375 connectaddress=127.0.0.1 connectport=2375
$ netsh advfirewall firewall add rule name="docker management" dir=in action=allow protocol=TCP localport=2375
```
The first line connects 10.0.75.1:2375 to the daemon socket on 127.0.0.1:2375, and the second line adds a pass-through on the firewall for the port 2375. Note that for this to work you need to enable "Expose daemon on tcp://localhost:2375 without TLS" from Docker settings under the "General" tab. According to Docker documentation, "Exposing daemon on TCP without TLS helps legacy clients connect to the daemon. It also makes yourself vulnerable to remote code execution attacts. Use with caution."

Install and run Portainer
```
$ docker volume create portainer_data
$ docker run -d -p 9000:9000 -v portainer_data:/data portainer/portainer -H tcp://10.0.75.1:2375
```


