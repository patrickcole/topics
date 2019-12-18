# Docker Troubleshooting

- the `.dockerignore` file will be truly ignored if the files that are supposed to be ignored are inside the folder being shared via a volume
- to keep the `node_modules` only on the container, set an additional data mount volume to the `node_modules` folder from within the container
- this effectively just sets a 1-way mount and the host machine does not reflect the container
- the example `volume` declaration should ease some confusion:

```yaml
    volumes:
      - .:/usr/app/
      - /usr/app/node_modules/
```

- [source](https://stackoverflow.com/questions/29181032/add-a-volume-to-docker-but-exclude-a-sub-folder)

- the example above sets a volume for the current development directory on the host machine `.` and then the workdir `/usr/app/` inside the container
- now updates can be made the source code and the `node_modules` folder is retained in the container and does not need to be on the host machine

- [source1](https://blog.codeship.com/using-docker-compose-for-nodejs-development/)

## Environment Variables

- [source](https://docs.docker.com/compose/environment-variables/)
- [source2, with how to do inside Dockerfile](https://vsupalov.com/docker-arg-env-variable-guide/)

## Get inside Node Alpine Shell

`docker exec -it {container_id} sh`

- [source](https://github.com/smebberson/docker-alpine/issues/43#issuecomment-217697747)

## Docker-Compose PORT vs EXPOSE

- [source](https://stackoverflow.com/questions/40801772/what-is-the-difference-between-docker-compose-ports-vs-expose)