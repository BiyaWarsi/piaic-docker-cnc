# Docker

#### Build Image

> docker build -t &lt;image-name&gt;:&lt;tag&gt; .
```sh
$ docker build -t myapp:1 .
```

#### Run Container
> docker run --name &lt;container_name&gt; -p &lt;host_port&gt;:&lt;container_port&gt; &lt;image_name&gt;:&lt;tag&gt;
```sh
$ docker run --name cont-name -p 8080:80 myapp:1
```

#### For Test

```sh
$ curl http://localhost:8080
```
#### Cleanup
Running container can be stopped by
```sh
$ docker stop cont-name
```
and removed by
```sh
$ docker rm cont-name
```
With the image it is even simpler. In order to remove it run
```sh
$ docker rmi myapp:1
```
(before removing any Docker image you always must stop all containers that uses the image).

***

### Cheat Sheet

| Command | Description |
| ------ | ------ |
| docker pull user_name/&lt;image_name&gt;:&lt;tag&gt; | Pulls the image from the docker hub |
| build -t &lt;image_name&gt;:&lt;tag&gt; . | Builds the image from the Dockerfile with the mentioned name and tag |
| docker image ls | Shows the list of the images present on your system. short-hand 'docker images' |
| docker container ls | Displays the running containers only. short-hand 'docker ps'  |
| docker container ls -a | Displays all the containers present on your system. short-hand 'docker ps -a' |
| docker inspect &lt;image_name&gt;:&lt;tag&gt; | Shows the detailed information about the image in JSON format. |
| docker history &lt;image_name&gt;:&lt;tag&gt; | Used to inspect the layers of the image. |
| docker tag &lt;source_image&gt;:&lt;tag&gt; &lt;user_name/new_image_name&gt;:&lt;tag&gt; | Create a tag of the new image that refers to source image.  |
|docker push &lt;user_name/image_name&gt;:&lt;tag&gt; | Push an image to a registry |
| docker image rm &lt;image_name&gt;:&lt;tag&gt; | Remove the image. short-hand 'docker rmi &lt;image_name&gt;:&lt;tag&gt;' |
| docker run --name &lt;container_name&gt; -p &lt;host_port:container_port&gt; -d &lt;image_name&gt; | Create the container with the specified name and assign the specified port from the image. Press Ctrl + pq it will detach terminal and leave container running in background. |
| docker run --name &lt;container_name&gt; -it -p &lt;host_port:container_port&gt; &lt;image_name&gt;:&lt;tag&gt; sh | To run a container from an image in an interactive mode.|
| docker exec -it &lt;container_name&gt; sh | To go in the running container's shell. Write exit to detach from the shell |
| docker stop <container_name> | It will stop the running container. |
| docker start <container_name> | It restart the stopped container. |
| docker rm <container_name> | It removes the container. |
| docker logs <container_name> | Fetch the logs of the container |
| docker volume create <volume_name> | Create your Volume for Persistent Data |
| docker volume ls | List down the volume(s) |
| docker volume inspect <created_volume_name> | Inspect the volume(s) |
| docker volume rm <created_volume_name>  | Removes volume |
| docker run -d --name <container_name> -v <created_volume_name:/container-directory-path> <image_name:tag> | Start container with -v flag (volume mount) |
| docker run -d --name <container_name> --mount source=created-volume-name,target=/container-directory-path <image_name:tag> | Start container with --mount flag |
| docker run -d -it --name <container_name> -v "$(pwd)"/host-directory-path:/container-directory-path <image_name:tag> | Start container with bind mounts using -v flag |
| docker run -d -it --name <container_name> --mount type=bind,source="$(pwd)"/host-dirctory-path,target=/container-directory-path <image_name:tag> | Start container with bind mounts using --mount flag |


