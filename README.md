# Docker_Cheatsheet

**What Is Docker?**
Docker describes themselves as "an open platform for developers and sysadmins to build, ship, and run distributed applications.

**Commands**

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

