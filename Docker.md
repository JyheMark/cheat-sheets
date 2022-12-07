# Docker Cheat Sheet

# Docker Cheat Sheet

1. [Basic Commands](#basic-commands)
   - [Run a Docker container](#run-a-docker-container)
   - [List all running Docker containers](#list-all-running-docker-containers)
   - [List all Docker containers (including stopped containers)](#list-all-docker-containers-including-stopped-containers)
   - [Stop a running Docker container](#stop-a-running-docker-container)
   - [Remove a Docker container](#remove-a-docker-container)
   - [Remove all stopped Docker containers](#remove-all-stopped-docker-containers)
   - [Run a Docker container in the background](#run-a-docker-container-in-the-background)
2. [Image Commands](#image-commands)
   - [List all Docker images](#list-all-docker-images)
   - [Pull an image from a Docker registry](#pull-an-image-from-a-docker-registry)
   - [Remove a Docker image](#remove-a-docker-image)
   - [Remove all unused Docker images](#remove-all-unused-docker-images)
3. [Networking Commands](#networking-commands)
   - [List all Docker networks](#list-all-docker-networks)
   - [Create a new Docker network](#create-a-new-docker-network)
   - [Connect a Docker container to a network](#connect-a-docker-container-to-a-network)
   - [Disconnect a Docker container from a network](#disconnect-a-docker-container-from-a-network)
   - [Remove a Docker network](#remove-a-docker-network)
4. [Volume Commands](#volume-commands)
   - [List all Docker volumes](#list-all-docker-volumes)
   - [Create a new Docker volume](#create-a-new-docker-volume)
   - [Remove a Docker volume](#remove-a-docker-volume)
   - [Remove all unused Docker volumes](#remove-all-unused-docker-volumes)
5. [Other Commands](#other-commands)
   - [Get the version of Docker installed](#get-the-version-of-docker-installed)
   - [Get help with a Docker command](#get-help-with-a-docker-command)


## Basic Commands

#### Run a Docker container:

```Bash
docker run [image]
```

#### List all running Docker containers:

```Bash
docker ps
```

#### List all Docker containers (including stopped containers):

```Bash
docker ps -a
```

#### Stop a running Docker container:

```Bash
docker stop [container_name]
```

#### Remove a Docker container:

```Bash
docker rm [container_name]
```

#### Remove all stopped Docker containers:

```Bash
docker container prune
```

#### Run a Docker container in the background:

```Bash
docker run -d [image]
```

## Image Commands

#### List all Docker images:

```Bash
docker images
```

#### Pull an image from a Docker registry:

```Bash
docker pull [image]
```

#### Remove a Docker image:

```Bash
docker rmi [image]
```

#### Remove all unused Docker images:

```Bash
docker image prune
```

## Networking Commands

#### List all Docker networks:

```Bash
docker network ls
```

#### Create a new Docker network:

```Bash
docker network create [network_name]
```

#### Connect a Docker container to a network:

```Bash
docker network connect [network_name] [container_name]
```

#### Disconnect a Docker container from a network:

```Bash
docker network disconnect [network_name] [container_name]
```

#### Remove a Docker network:

```Bash
docker network rm [network_name]
```

## Volume Commands

#### List all Docker volumes:

```Bash
docker volume ls
```

#### Create a new Docker volume:

```Bash
docker volume create [volume_name]
```

#### Remove a Docker volume:

```Bash
docker volume rm [volume_name]
```

#### Remove all unused Docker volumes:

```Bash
docker volume prune
```

## Other Commands

#### Get the version of Docker installed:

```Bash
docker -v
```

#### Get help with a Docker command:

```Bash
docker [command] --help
```