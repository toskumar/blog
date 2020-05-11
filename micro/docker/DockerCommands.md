# Docker Commands

## Docker System Commands

| Command | Description |
| --- | --- |
|`docker system df` |	Show docker disk usage |
|`docker system events` |	Get real time events from the server |
|`docker system info`	| Display system-wide information |
|`docker system prune` | Remove unused data |


## Docker Important Commands
| Command | Description |
| --- | --- |
|`docker version` | Show the Docker version information|
|`docker images` | List the most recently created images|
|`docker ps` | <p>Shows running container <br/> docker ps *(Shows running containers)* <br/> docker ps -a *(Shows all containers)*</p>|
|`docker pull NAME:TAG` | <p>Pull an image from a repository <br/> docker pull debian *(pull the lastest debian image)* <br/> docker pull debian:jessie *(Pull the jessie version/tag of debian)*</p> |
|`docker run [OPTIONS] IMAGE [COMMAND] [ARG...]`| <p>Run a command in a new container <br/> docker run --name debian debian:latest <br/> docker run --name debian -it debian:latest *(instructs docker as i-interactive bash shell, t - tty connected con)*</p>|
|`docker start CONTAINER [CONTAINER...]` | <p>Start one or more stopped containers <br/> docker start debian<p> |
|`docker stop CONTAINER [CONTAINER...]` | <p>Stop one or more running containers <br/> docker stop debian</p> |
|`docker restart CONTAINER [CONTAINER...]` | <p>Restart one or more containers <br/> docker restart debian</p> |
|`docker kill CONTAINER [CONTAINER...]` | <p>Kill one or more running containers<br/> docker kill debian<p> |
|`docker port CONTAINER [CONTAINER...]` | <p>List port mappings or a specific mapping for the container <br/> docker port debian</p> |
|`docker stats CONTAINER [CONTAINER...]` | <p>Display a live stream of container resource usage statistics<br/> docker stats debian</p>|
|`docker exec [OPTIONS] CONTAINER COMMAND [ARG...]` | <p>Run a command in a running container <br/> docker exec debian -it bash </p>| 

