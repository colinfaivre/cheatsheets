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
## Networks
```bash
# List port mappings for the container
$ docker container port myubuntu
# Show networks
$ docker network ls
# Inspect a network
$ docker network inspect <network_ID>
# Create a network (use --driver to specify a driver, defaults to 'bridge')
$ docker network create <new_network_name>
# Attach a network to container
$ docker network connect <network_ID> <containerID>
# Detach a network from container
$ docker network disconnect`<networkID> <containerID>
# Create a container attached to a specific network
$ docker container run -d --name new_nginx --network test_network nginx
```

## Images
```bash
# Get image history
$ docker image history <image_repo>
# Get meta data about an image
$ docker image inspect <image_repo>
# Give a new tag to an image
$ docker image tag <current_tag> <new_tag>
# Push a user tagged image to dockerhub
$ docker image push dockerhub_user_name/nginx
```
## Building images: Dockerfile

```Dockerfile
# Image uppon which this image is layered
FROM debian:jessie
# Optional env variable that will be used below
ENV NGINX_VERSION 1.11.10-1-jessie
# Optional commands to run at shell inside container at build time
RUN apt-get update && apt-get install some-package
# Forward request and error logs to docker log collector
RUN ln -sf /dev/stdout /var/log/nginx/access.log \
    && ln -sf /dev/stderr /var/log/nginx/error.log
# Expose these ports on the docker network
# you still need to use -p or -P to open/forward these ports on host
EXPOSE 80 443
# Required: run this command when container is launched
# only one command
CMD ["nginx", "-g", "daemon off;"]
```

```bash
# Build from a Dockerfile in the same directory with a tagname
$ docker image build -t <tag_name> .
```

## Persistant data: Volumes

## Docker compose

```yaml
version: '3.1' # If no version is specified, default is 1. Recommand v2 minimum

services: # Containers, same as docker run
    servicename: # A friendly name, this is also DNS name inside network
        image: # Optional if you use build
        command: # Optional, replace the default CMD specified by the image
        environment: # Optional, same as -e in docker run
        volumes: # Optional, same as -v in docker run
    servicename2:

volumes: # Optional, same as docker volume create 

networks: # Optional, same as docker network create
    
```

```bash
# Setup volumes/neworks and start all containers
$ docker compose up
# Stop all containers and remove containers/networks
$ docker compose down
# Stop all containers and remove containers/volumes/networks
$ docker compose down -v
# Display docker compose running processes
$ docker compose top
# Display docker compose running containers
$ docker compose ps
```
