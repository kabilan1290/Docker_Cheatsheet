# Docker_Cheatsheet

**What Is Docker?**
Docker describes themselves as "an open platform for developers and sysadmins to build, ship, and run distributed applications.

**🔧 Commands**

docker images - To list the number of available docker images.

docker search - Used to search the docker images.

docker run image - Running a docker image.

docker run -d image - Running a docker image in background.

docker run -it image /bin/bash - Running a docker image in foreground mode.

docker run -d image:3.2 - Running a docker image with particular version.

```
By default docker will run on latest version
```

docker ps - To list all running containers.

docker stats <name> - To find the stats of the container.
  
docker ps -q | xargs docker stats - Stats of the entire containers.

docker inspect <image/ContainerID> - Detailed information on the specific image.

docker logs <image/ContainerID> - Display messages the container has written to standard error or standard out.

docker run --name redisHostPort -p 6379:6379 Redis - Redis will be accessed in the standard port 6379

docker run --name redisDynamic -p 6379 redis - Dynamic port allocation,redis will be accessed in a dynamic port.

```
To view the port use $ docker port redisDynamic 6379
0.0.0.0:32768

By default Docker is stateless,so no data will be saved until we enforce the saves.

Path for save data : /opt/docker/data/image_name
```
docker run -d --name redisMapped -v /opt/docker/data/redis:/data redis - Any data which needs to be saved on the Docker Host, and not inside containers, should be stored in /opt/docker/data/redis.

```
Docker Images are built based on the contents of a Dockerfile.
```
docker build -t name - This command should used in build directory.The t flag is used to give a name for the build.

```
Creating a Dockerfile:
All Docker images start from a base image. A base image is the same images from the Docker Registry which are used to start containers.

To define a base image we use the instruction FROM <image-name>:<tag>

Example : FROM nginx:1.11-alpine

Run <command> - used to install packages.

COPY <src> <dest> - allows you to copy files from the directory containing the Dockerfile to the container's image.

EXPOSE <port> - command you tell Docker which ports should be open and can be bound to.

CMD ["a","b"] - cmd a b - command that launches the application.

Docker build - To build the image.

WORKDIR - We can define a working directory.

LABEL vendor=Katacoda - Labeling in dockerfile.

Note:
With Docker, environment variables can be defined when you launch the container.Using -e option, you can set the name and value.

To prevent sensitive files or directories from being included by mistake in images, you can add a file named .dockerignore.
```
docker network create backend-network - creates a network for multiple dockers to communicate.

When we launch new containers, we can use the --net attribute to assign which network they should be connected to. 

```
Example : docker run -d --name=redis --net=backend-network redis
```
docker network ls - To view the listt of networks.

docker logs <name> - To access the standard out and standard error outputs.

docker run -d --name restart-3 --restart=on-failure:3 <image> - The option --restart=on-failure:# allows you to say how many times Docker should try again on failure.

docker run -d --name restart-always --restart=always <image> - The option will restart container until it works perfectly,we can manually stop this.
  
docker run -l user=12345 -d redis - The option -l used to label the docker.

docker run --label-file=labels -d redis - To add a label using a label file,we use this command.it will create a label for each line in the file.

docker ps --format '{{.Names}} container is using {{.Image}} image' - The option --format is used to manipulate the output as user needs.

docker ps -q | xargs docker inspect --format '{{ .Id }} - {{ .Name }} - {{ .NetworkSettings.IPAddress }} - Command for listing all the IP addresses of the running containers.

docker swarm init - To Initialize swarm mode.

docker node ls - To list the nodes connected.

docker service ls - To list the services running on the cluster.

**The art challenges the technology, and the technology inspires the art.❤**
