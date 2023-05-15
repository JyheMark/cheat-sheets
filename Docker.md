# Docker Cheat Sheet

1. [Resource Management](#resource-management)
   - [Get Resources](#get-resources)
   - [Delete Resources](#delete-resources)
2. [Containers](#containers)
   - [Starting a container](#start-a-stopped-container)
   - [Stopping a container](#stop-a-running-container)
3. [Images](#images)
   - [Create a container](#create-and-start-a-container-based-on-image)
   - [Build image from dockerfile](#build-image-from-dockerfile)
   - [Push image to repo](#push-image-to-external-repo)
   - [Pull image from repo](#pull-image-from-external-repo)

## Resource Management

#### Get resources

Resource types:
- image
- container

```Bash
docker <resource-type> ls
```

```Bash
docker <resource-type> ls -a
```

#### Delete resources

```Bash
docker <resource-type> rm <resource-id>
```

## Containers

#### Start a stopped container

```Bash
docker start <container-id>
```


```Bash
docker start <container-id> -d
```

#### Stop a running container

```Bash
docker stop <container-id>
```

## Images

#### Create and start a container based on image

```Bash
docker run <image-name>:<tag>
```

Start with host port 123 forwarded to container port 456, with env variable

```Bash
docker run -d -p 123:456 -e SOME_VARIABLE=SOME_VALUE
```

#### Build image from dockerfile

```Bash
docker build -t <image-name>:<tag> .
```

#### Push image to external repo

```Bash
docker push <image-name>:<image-tag>
```

#### Pull image from external repo

```Bash
docker pull <image-name>:<image-tag>
```