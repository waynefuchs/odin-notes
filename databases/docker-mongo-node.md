# Dockerize: MongoDB + Node/Express

[Notes](https://www.youtube.com/watch?v=vm3YfOHf_Cc) on setting up a mongodb and node/express app using docker. The reason I took notes from a different source was that the Odin references were out of date and the tutorial linked actually didn't work. Also, Odin doesn't really get into the deployment of applications, which is something that I need to concern myself with as I already have hosting.

## Requirements

- Create a `.dockerignore`, which functions similarly to .gitignore.
- Create a `Dockerfile` for the Node application. (See below)
- Create a `docker-compose.yaml` for launching all docker containers.
- dockerhub: [node.js](https://hub.docker.com/_/node) image.
- dockerhub: [mongoDB](https://hub.docker.com/_/mongo) image.

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
1. Install the node packages with the versions specified in package-lock.json. (`RUN npm ci` stands for continuous integration and is a better practice than `RUN npm install` (bad practice))
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

## Docker Commands

| Command                          | Description                                             |
| -------------------------------- | ------------------------------------------------------- |
| docker compose down              | Shut down the current `docker-compose.yaml` containers. |
| docker compose build             | build an image                                          |
| docker compose up -d             | Start containers using the `docker-compose.yaml` file.  |
| docker exec -it [hash/name] bash | get a shell on a running container                      |
