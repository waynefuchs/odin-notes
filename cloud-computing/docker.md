# Docker <!-- omit from toc -->

Docker is a set of platform as a service (PaaS) products that use OS-level virtualization to deliver software in packages called containers. The oftware that hosts the containers is called [Docker Engine](https://docs.docker.com/engine/install/).

- [Docker Commands](#docker-commands)

# Docker Commands

| Command                            | Description                                                              |
| ---------------------------------- | ------------------------------------------------------------------------ |
| `docker exec -it [hash/name] bash` | get a shell on a running container (try `sh` if `bash` is unavailable)   |
| `docker ps`                        | list running docker containers                                           |
| `docker compose up -d`             | Start containers in the background using the `docker-compose.yaml` file. |
| `docker compose down`              | Shut down the current `docker-compose.yaml` containers.                  |
| `docker compose build`             | build an image                                                           |
