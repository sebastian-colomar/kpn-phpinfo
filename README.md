# phpinfo

https://labs.play-with-docker.com/
```
mkdir phpinfo/
```
```
echo '<?php phpinfo();?>' | tee phpinfo/index.php
```
```
tee phpinfo/Dockerfile 0<<EOF
FROM php
COPY index.php .
EOF
```
```
docker build -t my_image phpinfo/
```
```
# php -f index.php -S 0.0.0.0:8080
docker run --detach --entrypoint php --name phpinfo --publish 8080 --restart always --read-only --user nobody:nogroup my_image -f index.php -S 0.0.0.0:8080
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
