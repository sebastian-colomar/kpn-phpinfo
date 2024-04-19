# phpinfo

https://labs.play-with-docker.com/
```
mkdir phpinfo/
echo '<?php phpinfo();?>' | tee phpinfo/index.php
```
- https://hub.docker.com/_/php
- https://github.com/docker-library/php/blob/master/8.3/alpine3.19/cli/Dockerfile
```
docker images
```
```
docker pull docker.io/library/php:alpine
```
```
docker images
```
# php -f index.php -S 0.0.0.0:8080
```
docker run --detach --name phpinfo --publish 8080 --volume $PWD/phpinfo:/phpinfo --workdir /phpinfo docker.io/library/php:alpine php -f index.php -S 0.0.0.0:8080
```
```
docker ps
docker top phpinfo
docker logs phpinfo
```
```
docker swarm init --advertise-addr $( hostname -i )
```
```
docker node ls
```
```
tee docker-compose.yaml 0<<EOF

services:
  phpinfo:
    command:
      - php
      - -f
      - index.php
      - -S
      - 0.0.0.0:8080
    image: docker.io/library/php:alpine
    ports:
      - 8080
    volume:
      - /tmp/phpinfo:/phpinfo
    working_dir: /phpinfo
version: "3.8"

EOF
```
```
docker stack deploy -c docker-compose.yaml phpinfo
```
```
docker stack ls
docker stack ps phpinfo
docker stack services phpinfo
```
