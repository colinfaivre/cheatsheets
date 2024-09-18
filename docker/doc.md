# Docker

> A container is an instance of an image running as a process

## Installation
- on ubuntu desktop: https://docs.docker.com/desktop/install/linux/ubuntu/
- on ubuntu server: https://get.docker.com/
```bash
$ curl -fsSL https://get.docker.com -o install-docker.sh
```

```bash
$ docker version  #show version
$ docker info     #show info
$ docker          #show commands
```

## Basic commands
```bash
# Download nginx image, start a container from it
# Bind local 80 port to container 80 port
$ docker container run --publish 80:80 nginx
# Add --detach to run the command on the background
$ docker container run --publish 80:80 --detach nginx
# List containers
$ docker container ls
```

