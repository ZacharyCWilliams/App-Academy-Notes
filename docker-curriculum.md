# Docker Curriculum 

Docker is an open source project that lets you package, ship,  and deliver your app in a standardized way through `containers`.  Containers are a standard unit of software that packages up code.. and that codes dependencies..  so that the app runs efficently and reliably across multiple environments.

**From Docker's website:**

```javascript
A Docker container image is a lightweight, standalone, executable package of software that includes everything needed to run an application: code, runtime, system tools, system libraries and settings.
```

## The Docker Engine Build System

Lightweight containerization tech that runs processes in isolated environments. It has both core applications that run `containers` and a restful HTTP api that lets us interface with the DockerCLI/terminal to control the engine.

```
The Docker CLI uses the Docker REST api to interact with docker `daemon`.  The daemon creates/manages Docker objects (images, containers, networks, and volumes)
```


