# Docker Basics

## Installation

### Ubuntu: Install via apt

[https://docs.docker.com/engine/install/ubuntu/](https://docs.docker.com/engine/install/ubuntu/)

## Managing containers

```bash
# create / start new container (and detach)
$ docker run --name my-nginx -d -p 8080:80 nginx
# create / start new container with custom command
$ docker run -it --entrypoint /bin/bash nginx
# log into running container
$ docker exec -it my-nginx /bin/sh
# stop / restart container (port mappings are remembered)
$ docker stop my-nginx
$ docker start my-nginx
# list all (also stopped) containers
$ docker ps -a
```

## Managing volumes

```bash
$ docker volume create html
$ docker volume ls
$ docker run --name vol-nginx -d -v html:/usr/share/nginx/html:ro -p 8080:80 nginx
```

## Cleanup

```bash
# remove volumes that are not used by any containers
$ docker volume prune
$ docker image prune
```

## Creating images

* [https://www.scalyr.com/blog/create-docker-image/](https://www.scalyr.com/blog/create-docker-image/)
* [https://thenewstack.io/docker-basics-how-to-use-dockerfiles/](https://thenewstack.io/docker-basics-how-to-use-dockerfiles/)
* [https://spring.io/guides/gs/spring-boot-docker/](https://spring.io/guides/gs/spring-boot-docker/)

## Inspecting images

```bash
# find ports provided by image
docker inspect --format='{{.Config.ExposedPorts}}' mysql:8
# find mount points used by image
docker inspect --format='{{.Config.Volumes}}' mysql:8
```

* [Processes in containers should not run as root](https://medium.com/@mccode/processes-in-containers-should-not-run-as-root-2feae3f0df3b)

