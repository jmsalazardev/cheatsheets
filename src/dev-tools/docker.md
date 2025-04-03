# Docker Cheatsheet

Commonly used Docker commands for managing images, containers, networks, and volumes.

## Images

### Building Images

`docker build -t [image_name]:[tag] [path_to_Dockerfile]`
Builds a Docker image from a Dockerfile.
*   `-t`: Tags the image with a name and optional tag.
*   `[path_to_Dockerfile]`: Specifies the directory containing the Dockerfile (defaults to the current directory).

`docker build -t my-app .`
Builds an image named `my-app` from the Dockerfile in the current directory.

`docker build -t my-app:v1 -f Dockerfile.dev .`
Builds an image named `my-app` with tag `v1` using the `Dockerfile.dev` file in the current directory.

### Listing Images

`docker images`
Lists all Docker images on your system.

`docker images -a`
Lists all images, including intermediate images.

`docker images --filter "dangling=true"`
Lists all dangling images (images not associated with any tagged image).

### Removing Images

`docker rmi [image_id]`
Removes a specific Docker image by its ID.

`docker rmi [image_name]:[tag]`
Removes a specific Docker image by its name and tag.

`docker rmi $(docker images -aq)`
Removes all images.

`docker image prune`
Removes all dangling images.

`docker image prune -a`
Removes all unused images.

### Pulling Images

`docker pull [image_name]:[tag]`
Pulls a Docker image from a registry (defaults to Docker Hub).

`docker pull ubuntu:latest`
Pulls the latest Ubuntu image from Docker Hub.

### Pushing Images

`docker push [image_name]:[tag]`
Pushes a Docker image to a registry.

`docker push my-username/my-app:v1`
Pushes the `my-app` image with tag `v1` to Docker Hub under the `my-username` account.

### Inspecting Images

`docker inspect [image_name]`
Displays detailed information about a Docker image.

## Containers

### Running Containers

`docker run [options] [image_name]:[tag] [command]`
Runs a Docker container from an image.

*   `-d`: Runs the container in detached mode (in the background).
*   `-i`: Keeps STDIN open even if not attached.
*   `-t`: Allocates a pseudo-TTY.
*   `-p [host_port]:[container_port]`: Publishes a container's port to the host.
*   `-v [host_path]:[container_path]`: Mounts a volume.
*   `--name [container_name]`: Assigns a name to the container.
*   `--rm`: Automatically removes the container when it exits.
*   `-e [key=value]`: Set environment variables.

`docker run -d -p 8080:80 --name my-web-app nginx:latest`
Runs an Nginx container in detached mode, maps port 80 to 8080 on the host, and names it `my-web-app`.

`docker run -it --rm ubuntu:latest bash`
Runs an interactive Ubuntu container and opens a bash shell. The container will be removed after exiting.

`docker run -d -v /my/host/data:/app/data my-app`
Runs a container in detached mode and mounts a volume.

### Listing Containers

`docker ps`
Lists running containers.

`docker ps -a`
Lists all containers (running and stopped).

`docker ps -aq`
Lists only the IDs of all containers.

### Stopping Containers

`docker stop [container_id]`
Stops a running container.

`docker stop $(docker ps -aq)`
Stops all running containers.

### Starting Containers

`docker start [container_id]`
Starts a stopped container.

### Removing Containers

`docker rm [container_id]`
Removes a stopped container.

`docker rm $(docker ps -aq)`
Removes all stopped containers.

`docker container prune`
Removes all stopped containers.

### Executing Commands in Containers

`docker exec -it [container_id] [command]`
Executes a command in a running container.

`docker exec -it my-web-app bash`
Opens a bash shell in the `my-web-app` container.

### Inspecting Containers

`docker inspect [container_id]`
Displays detailed information about a container.

### Logs

`docker logs [container_id]`
Shows the logs of a container.

`docker logs -f [container_id]`
Follows the logs of a container in real-time.

`docker logs --tail 100 [container_id]`
Shows the last 100 lines of logs.

### Copying files

`docker cp [container_id]:[path_in_container] [local_path]`
Copies files from a container to the local file system.

`docker cp [local_path] [container_id]:[path_in_container]`
Copies files from the local file system to a container.

## Networks

### Listing Networks

`docker network ls`
Lists all Docker networks.

### Creating Networks

`docker network create [network_name]`
Creates a new Docker network.

`docker network create my-network`
Creates a network named `my-network`.

`docker network create -d bridge my-bridge-network`
Creates a bridge network named `my-bridge-network`.

### Connecting Containers to Networks

`docker network connect [network_name] [container_id]`
Connects a container to a network.

`docker network connect my-network my-web-app`
Connects the `my-web-app` container to the `my-network` network.

### Disconnecting Containers from Networks

`docker network disconnect [network_name] [container_id]`
Disconnects a container from a network.

### Inspecting Networks

`docker network inspect [network_name]`
Displays detailed information about a network.

### Removing Networks

`docker network rm [network_name]`
Removes a network.

`docker network prune`
Removes all unused networks.

## Volumes

### Listing Volumes

`docker volume ls`
Lists all Docker volumes.

### Creating Volumes

`docker volume create [volume_name]`
Creates a new Docker volume.

`docker volume create my-data-volume`
Creates a volume named `my-data-volume`.

### Inspecting Volumes

`docker volume inspect [volume_name]`
Displays detailed information about a volume.

### Removing Volumes

`docker volume rm [volume_name]`
Removes a volume.

`docker volume prune`
Removes all unused volumes.

## Docker Compose

### Starting Services

`docker-compose up`
Starts all services defined in the `docker-compose.yml` file.

`docker-compose up -d`
Starts services in detached mode.

`docker-compose up -d --build`
Starts services in detached mode and rebuilds images if necessary.

### Stopping Services

`docker-compose down`
Stops and removes containers, networks, and volumes defined in the `docker-compose.yml` file.

### Listing Services

`docker-compose ps`
Lists the status of services.

### Executing Commands

`docker-compose exec [service_name] [command]`
Executes a command in a running service container.

`docker-compose exec web bash`
Opens a bash shell in the `web` service container.

### Logs

`docker-compose logs`
Shows the logs of all services.

`docker-compose logs -f`
Follows the logs of all services in real-time.

`docker-compose logs -f web`
Follows the logs of the `web` service in real-time.

### Build

`docker-compose build`
Builds or rebuilds services.
