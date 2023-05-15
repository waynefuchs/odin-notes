- [Docker Database Setup](#docker-database-setup)
- [Links](#links)
- [Docker Commands](#docker-commands)
- [docker-compose](#docker-compose)
  - [start the databases](#start-the-databases)
  - [stop the databases](#stop-the-databases)
- [Notes for a YouTube Tutorial Video](#notes-for-a-youtube-tutorial-video)
  - [`.dockerignore`](#dockerignore)
  - [`Dockerfile`](#dockerfile)
  - [`.env`](#env)
  - [`app.js` (node/express)](#appjs-nodeexpress)
  - [`docker-compose.yaml`](#docker-composeyaml)
    - [Mongo Service Notes](#mongo-service-notes)
    - [Node/Express Notes](#nodeexpress-notes)
    - [Volumes](#volumes)

# Docker Database Setup

I run these using `docker-compose.yaml` files, which auto-start on system load.

# Links

| Software                                        | Note                                                                                                                                                 |
| ----------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| [Penpot](https://penpot.app/)                   | A _really good_ open source replacement for Figma. The docker-compose file is provided with installation instructions on the self-host install page. |
| [Mongodb](https://hub.docker.com/_/mongo)       | The MongoDB database                                                                                                                                 |
| [PostgreSQL](https://hub.docker.com/_/postgres) | The PostgreSQL database                                                                                                                              |
| [Adminer](https://hub.docker.com/_/adminer)     | A database administration panel                                                                                                                      |

# Docker Commands

| Command                            | Description                                             |
| ---------------------------------- | ------------------------------------------------------- |
| `docker exec -it [hash/name] bash` | get a shell on a running container                      |
| `docker ps`                        | list running docker containers                          |
| `docker compose down`              | Shut down the current `docker-compose.yaml` containers. |
| `docker compose build`             | build an image                                          |
| `docker compose up -d`             | Start containers using the `docker-compose.yaml` file.  |

# docker-compose

> ⚠️ Caution: There may be a better way to write this `docker-compose.yaml` in terms of security, reliability, data persistence, et cetera. This is what has worked (flawlessly) for me, at the time of this writing, for approximately a year. With that said, use this at your own risk.

> ⓘ Note: I combine PostgreSQL and MongoDB into a single docker container to keep database stuff together. This may be better to split out separately.

> ⓘ TODO: Figure out nginx proxy with nodejs. I would love to start "containerizing" my applications.

```
# docker-compose.yaml
version: "3.9"

services:
  # MongoDB service
  mongodb:
    container_name: mongodb
    image: mongo:latest
    restart: always
    networks:
      - dockerdev
    ports:
      - 27017:27017
    volumes:
      - mongodb:/data/db

  # PostgreSQL
  postgres:
    image: postgres
    restart: always
    networks:
      - dockerdev
    environment:
      POSTGRES_PASSWORD: {YOUR-PASSWORD-HERE}
    ports:
      - "5432:5432"
    volumes:
      - pgdata:/var/lib/postgresql/data

  # PostgreSQL Configuration Image
  adminer:
    image: adminer
    restart: always
    networks:
      - dockerdev
    ports:
      - 8080:8080

# Data persistence
volumes:
  mongodb: {}
  pgdata: {}

networks:
  dockerdev:
```

## start the databases

```
docker compose up -d
```

## stop the databases

```
docker compose down
```

# Notes for a YouTube Tutorial Video

I took some notes on a youtube video, [How to dockerize NodeJS and MongoDB application using docker-compose](https://www.youtube.com/watch?v=vm3YfOHf_Cc), that I found covering setting up a mongodb and node/express app using docker.

What follows are those notes.

> ⓘ TODO: Come back when I have more experience and clean this up.

## `.dockerignore`

```.dockerignore
./node_modules
Dockerfile
.dockerignore
docker-compose.yml
```

## `Dockerfile`

1. Download `node:alpine` package
1. Set the location for the application inside the docker container.
1. Copy the `package.json` and `package-lock.json` files into the application dir.
1. Install the node packages with the versions specified in package-lock.json. (`RUN npm ci` stands for continuous integration and is a better practice than `RUN npm install` (bad practice)) (? he doesn't say why ?)
1. Copy the entire project structure into the docker container. (IMPORTANT: make sure the `.dockerignore` file is set up properly to not overwrite work done with the previous COPY and RUN commands)
1. Run the node application (args specified in an array, which is the preferred method for the CMD directive)

```Dockerfile
FROM node:alpine
WORKDIR /usr/src/app
COPY package*.json .
RUN npm ci
COPY . .
# Production
# CMD ["npm", "start"]
# Development
CMD ["npm", "run", "dev"]
```

> Note: This is not the method I want to use to build the docker container. Typically it would be built using the docker-compose.yaml file.
>
> After setting up the project, run: `docker build .` from the shell in the project directory.

## `.env`

These environment variables are for development. They are used in the docker-compose.yaml file also, except with `: ` (space required) instead of `=`. (See below)

```Makefile
PORT=3000
MONGODB_URI=mongodb://localhost:27017
DB_NAME=my_db
NAME=Some Name
```

## `app.js` (node/express)

This is a way to access environment variables within node.

```js
app.get("/", (req, res, next) => {
  res.json({
    message: "Hello World! Environment Variable Test!",
    env_name: process.env.NAME,
  });
});
```

## `docker-compose.yaml`

```yaml
version: "3.9"

services:
  # MongoDB service
  mongo_db:
    container_name: db_container
    image: mongo:latest
    restart: always
    #  ports:
    #    - 2717:27017
    volumes:
      - mongo_db:/data/db

  # Node.js API service
  api:
    build: .
    ports:
      - 4567:3000
    # If you want to develop inside of a docker
    # Map the local directory to /usr/src/app in the container
    #  volumes:
    #    - .:/usr/src/app
    environment:
      PORT: 3000
      MONGODB_URI: mongodb://mongo_db:27017
      DB_NAME: my_db
      NAME: "Some Name"
    depends_on:
      - mongo_db

# Data persistence
volumes:
  mongo_db: {}
```

### Mongo Service Notes

- `db_container` is a custom name (if you have multiple mongodb databases on the same system)
- `image: mongo:latest` is to use the latest mongo from dockerhub
- If the docker container crashes for whatever reason, always restart it
  - no
  - on-failure:[max-retries]
  - always
  - unless-stopped
- `ports` is _not required_. Only if you want to specifically map the ports. (local:container)
- `volumes` directive to set up data persistence
  - The `mongo_db` volume specified is the local volume
  - The `/data/db` path is inside the container and is the required location expected by mongo.

### Node/Express Notes

- `api` can be renamed to whatever you want to call your node application
- execute `docker build .`
- for the ports, specify the local port, and then the container port (so the application would be accessed through localhost:4567)
- generally you do not use volumes for node containers, as the data should be stored in the database

### [Volumes](https://docs.docker.com/storage/volumes/)

- Create the `mongo_db` container if it doesn't exist OR
- Mount it if it does exist
