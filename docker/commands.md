# Commands

## Clean Up

`docker system prune -a` : remove all containers, images, volumes, networks and build cache
`docker volumes prune` : remove unused volumes

## Containers

- `docker ps` : show all running containers
- `docker ps -a` : show all containers (running or not running)
- `docker stop ${container-name}` : stop a running container
- `docker start ${container-name}` : start a stopped container
- `docker rm ${container-name}` : remove a container by either name or guid
- `docker run` : run an image inside a container
- `docker run -p ${local-port}:${container-port}` : `-p` forwards `local-port` to `container-port` inside running container
- `docker run -d --name ${container-name} ${image-name}` : run container in detached mode (the `--name` parameter comes in handy if need to login to it later)
- `docker exec -it ${container-name} ${bash|sh}` : logs into a detached container and starts either `bash` or `sh`

## Information

`docker info` : get driver info and Docker root directory

## Images

`docker images` : list all docker images
`docker inspect ${image-name}` : get information on specific image
`docker rm ${image-name}` : remove image

## Volumes

- `docker volume create --name ${volume-name}` : creates an independent volume
- `docker run -v ${volume-name}:${container-folder}` : attaches volume to folder inside container

###### Sources

- [source1](https://www.freecodecamp.org/news/where-are-docker-images-stored-docker-container-paths-explained/)
- [source2](https://www.freecodecamp.org/news/docker-image-guide-how-to-remove-and-delete-docker-images-stop-containers-and-remove-all-volumes/)
