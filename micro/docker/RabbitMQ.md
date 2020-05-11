# Docker RabbitMQ setup

**RabbitMQ single node setup**

- docker run -d --hostname my-rabbitmq-1 --name my-rabbitmq-1 -p 8080:15672 -p 5672:5672 rabbitmq:3-management
- docker start my-rabbitmq-1 *(Run the command if the container is not running)*
- docker stop my-rabbitmq-1 *(To stop the running container)*
- docker rm -f my-rabbitmq-1 *(To remove the running or stopped container)*


**How to access the Rabbit MQ administration**
- http://localhost:8080 *(default username and password is guest/guest)*
- http://localhost:8080/api *(RabbitMQ api)*

**Listening Ports**
|Protocol | Bound to | Port |
|---|---|---|
|http | 8080 | 15672|
|amqp | 5672 | 5672 |
|cluster| - | 25672 |


