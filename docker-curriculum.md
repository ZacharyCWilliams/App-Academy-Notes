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

![Docker](https://cdn-media-1.freecodecamp.org/images/1*easlVE_DOqRDUDkVINRI9g.png)