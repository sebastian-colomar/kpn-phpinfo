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
