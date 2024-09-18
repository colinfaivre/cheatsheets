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
# Show container command help
$ docker container --help
# Download nginx image, start a container from it
# Bind local 80 port to container 80 port with --publish or -p
$ docker container run -p 80:80 nginx
# Add --detach or -d to run the command on the background
$ docker container run -p 80:80 -d nginx
# Give a specific name to the container
$ docker container run -p 80:80 -d --name newname nginx
# Show log from that named container
$ docker container logs newname

# List running containers
$ docker container ls
# List all containers (up and exited)
$ docker container ls -a
# Stop a container
$ docker container stop <container_ID>
# Remove a container
$ docker container rm <container_ID>
# Remove a container even if it is up
$ docker container rm -f <container_ID>
```
## What happens in `docker container run`
- Looks for the image locally in the image cache
- Then looks in remote image repo
- Dowloads the latest version
- Creates a new container based on that image and prepares to start
- Gives a virtual IP on private network inside docker engine
- Starts the container by using CMD in the image Dockerfile

## What is happening inside a container
```bash
# List processes inside a container
$ docker container top
# Detail one container config
$ docker container inspect
# Show performance stats for all containers
$ docker container stats
```

## Run a shell inside a container
```bash
# Run bash command in a new nginx container
$ docker container run -it --name mynginx nginx bash
# Start a stopped container with a shell
$ docker container start -ai myubuntu
# Execute bash in a running container
$ docker container exec -it myubuntu bash
```
