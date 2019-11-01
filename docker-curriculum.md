# Docker Curriculum 

Docker is an open source project that lets you package, ship,  and deliver your app in a standardized way through `containers`.  Containers are a standard unit of software that packages up code.. and that codes dependencies..  so that the app runs efficently and reliably across multiple environments.

**From Docker's website:**

```
A Docker container image is a lightweight, standalone, executable package of 
software that includes everything needed to run an application: code, 
runtime system tools, system libraries and settings.
```

## The Docker Engine Build System

Lightweight containerization tech that runs processes in isolated environments. It has both core applications that run `containers` and a restful HTTP api that lets us interface with the DockerCLI/terminal to control the engine.

```
The Docker CLI uses the Docker REST api to interact with docker `daemon`. 
The daemon creates/manages Docker objects (images, containers, networks, and volumes)
```

## Containers

A container is an instance of an `image` running, as a process, on your machine.

**What's an image?**

An image is an application we want to run. Examples:

* Node
* Ruby
* Postgres

We can find images in the [Docker Hub](https://hub.docker.com).

## Docker Container Lifecycle

Docker containers (& their data) can be built and destroyed very quickly. This makes them perfect for temporal tasks. That being said, they can also run long-running `daemons` like web servers.

## Running Containers

Containers are runtime environments. Example of how to start container

```javascript
docker container run -d -p 8080:80 --name web nginx
```

^When a container starts up it looks for the `image` locally. If it can't find the image it searches for it in the Docker Hub. It then downloads the latest version of the image and creates a new container based off that downloaded image.

Once that's completed, Docker gives the container the virtual IP on the private network inside of the Docker engine. It also opens up a port on your localhost (in the example above this is port 8080) and forwards any traffic to a port in the container (port 80 in the example above). Finally, it starts the container by using the `CMD` in the image's Dockerfile.

Here's an image of the Docker lifecyle:

![Docker](https://cdn-media-1.freecodecamp.org/images/1*easlVE_DOqRDUDkVINRI9g.png)

## Important Docker Commands

List out all options available to you:

```javascript
docker --help
```

Check out the Docker run documentation for a list of options and flags:

```javascript
docker run [OPTIONS] IMAGE[:TAGNUMBER] [COMMAND]
```

Lists all your running containers:

```javascript
docker container ls
```

Lists all your containers (running or stopped):

```javascript
docker container ls -a
```

Return json with the metadata about that specific container:

```javascript
docker container inspect <CONTAINERNAME>
```

Display the running processes of a container:

```javascript
docker container top <CONTAINERNAME>
```

Remove one or more stopped containers:

```javascript
docker container rm <CONTAINERNAME>
```

Stop and remove a running container:

```javascript
docker container rm -f <CONTAINERNAME>
```

Run a command in a running container:

```javascript
docker container run exec
```

## Monitoring Containers

We want to be able to monitor the resources taken up by our processes. We can view this information through the command `docker container stats`. This will return something that looks like:

```
CONTAINER ID        NAME                CPU %               MEM USAGE / LIMIT     MEM %               NET I/O             BLOCK I/O           PIDS
1be21246b909        httpd1              0.02%               5.562MiB / 2.934GiB   0.19%               648B / 0B           98.3kB / 0B         82
4f0ace5722fc        mysql1              2.18%               376.2MiB / 2.934GiB   12.52%              718B / 0B           111kB / 1.26GB      38
1b00fb53a1a6        nginx1              0.00%               1.918MiB / 2.934GiB   0.06%               1.35kB / 0B         0B / 0B             2
```

## Persisting Data in Docker

Although containers are temporal, we can store data to the host machine (persist data) through two different options: `volumes` and `bind mounts`. **Bind Mounts** can be stored anywhere on the container host and mounted on the running container whereas the host filesystem stores **volumes** but they are managed by Docker. 

## Docker Networks

Each container runs one process, but we want these isolated containers to communicate and exchange information with one another. (This ability containers have to connect together with one another/with non-docker workloads is what makes Docker such a powerful tool!)

**Docker high level overview:**

1. You create network which creates subnet for an isolated network
2. You create a container and attach it to this network
3. As long as these containers are on the same network, they can be connected

## Default Bridge Network

Each container is auto-connected to a virtual network called a `bridge`. You can view the list of your current Docker networks with `docker network ls`. For more detailed info use `docker network inspect <NETWORKNAME>`.




