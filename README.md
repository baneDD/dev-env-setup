# DEVELOPMENT ENVIRONMENT SETUP

This is a collection of development tools I use to accomplish different tasks. The setup requires Docker installed on the host machine and then running the docker-compose configuration included here. There are some minor configuration details that will need to be modified to suit as well as some differences based on the OS used on the host machine.

Once you've set up Docker on the host machine, you can set these tools up with docker-compose by running `docker-compose up` from this folder. If you wish to run the containers in the background you can use the -d option: `docker-compose up -d`. For other docker-compose options, run `docker-compose` in the shell or check out the documentation [here](https://docs.docker.com/compose/reference/up/).

Tools available:

* [Portainer](#portainer)
* [Sonarqube](#sonarqube)
* [Postgres](#postgres)
* [Hound](#hound)
* [Nginx](#nginx)
* [Jenkins](#jenkins)

### PORTAINER

[Portainer](https://portainer.io/) is a web-based GUI management tool for Docker. It's dead-simple to install and run and allows for easy management of containers, images, volumes and networks. When run via the docker-compose file included in this project, it can be accessed via [port 480 on localhost](http://localhost:480). More documentation on using Portainer can be found [here](https://portainer.readthedocs.io/en/stable/).

_Windows 10 Portainer Notes_

If you're running on Windows, add the following to your PowerShell profile script: `$Env:COMPOSE_CONVERT_WINDOWS_PATHS=1`

### SONARQUBE

[SonarQube](https://www.sonarqube.org/) is an indispensable development tool that highlights issues with the code such as bugs, security vulnerabilities or insufficient test coverage. It allows you to set a quality gate and to monitor code over time for accumulation of technical debt. Using SonarQube as part of your development workflow will help you systematically improve your code quality.

You will need to install sonar-scanner to analyze code and can do so using home brew:

```brew install sonar-scanner```

__NOTE__: The process of installing the Sonar Scanner tool is different on different platforms. Please consult [Sonarqube Documentation](https://docs.sonarqube.org/display/SCAN/Analyzing+with+SonarQube+Scanner) for more on scanner installation and use.

Finally, if you're using the Nginx setup I have here, you will need to edit the sonar-scanner.properties file (run sonar-scanner tool to see where it's installed) and add the following line:

```sonar.host.url=http://localhost/sonarqube```

This will tell the scanner to upload the analysis results there rather than to default localhost:9000 location.

### POSTGRES

Postgres is a powerful, open-source object-relational database system. It's used here as the backing store for SonarQube.

### HOUND

Hound is a simple and lightweight tool used to index your repositories allowing you to search for anything in the code. Particularly useful on large projects or when working with unfamiliar codebases.

NOTE: Because Hound is running in a Docker container, to analyze any local folders, you must mount them in the Docker container as volumes. For example, if you had some source code in `/Projects/sample-project`, you would add the following volume to volumes under `hound` in `docker-compose.yml`:
`Projects/sample-project:sources/sample-project`

Now in your Hound config you could simply add the following config:
```
    "sample project": {
      "url": "file:///sources/sample-project"
    }
```

What we have done here is we have in essence remapped `/Projects/sample-project` to `/sources/sample-project` in our Docker container

### NGINX

[NGINX](https://nginx.org/en/) is an application that can be used as an HTTP and reverse proxy server, a mail proxy server or a TCP/UDP proxy server. Here are we using it as a reverse proxy to allow all of our development tools to appear as they are served by a single application server. We can access the applications as:

    - Portainer - http://localhost/portainer
    - Hound - http://localhost/hound
    - Sonarqube = http://localhost/sonarqube

Note that localhost above can be replaced with another name assuming that it's added to the hostfile. Additionally, it the tools are hosted on a separate server, they can be served under a different domain name with a single IP address.

### Jenkins

[Jenkins](https://jenkins.io/) is an open source automation server. Jenkins provides hundreds of plugins to support building, deploying and automating any project.
