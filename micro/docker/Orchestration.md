#Orchestration


## Deploy on Swarm

You can deploy a stack on Kubernetes with docker stack deploy command, docker-compose.yaml and the name of the stack

1. Create a docker-compose.yaml file as below
```yaml
version: '3.3'
services:
  web:
    image: dockersamples/k8s-wordsmith-web
    ports:
     - "8080:80"
  words:
    image: dockersamples/k8s-wordsmith-api
    deploy:
      replicas: 5
      endpoint_mode: dnsrr
      resources:
        limits:
          memory: 50M
        reservations:
          memory: 50M
  db:
    image: dockersamples/k8s-wordsmith-db
```
2. Set the orchestrator variable to **swarm** and run the docker stack deploy command
```
set DOCKER_STACK_ORCHESTRATOR=swarm
docker stack deploy --compose-file ./docker-compose.yml my-swarm-stack
```
3. Access the service from http://localhost:8080
4. To remove the stack 
```
docker stack rm my-swarm-stack
```

## Deploy on Kubenetes

1. Enable kubernetes settings in Docker for Windows
2. Set the orchestrator variable to **kubernetes** and run the docker stack deploy command
```
set DOCKER_STACK_ORCHESTRATOR=kubernetes
docker stack deploy --compose-file ./docker-compose.yml my-kube-stack
```
3. Access the service from http://localhost:8080
4. To remove the stack 
```
docker stack rm my-kube-stack
```
5. docker system prune -a *(delete all the unused containers, images)*