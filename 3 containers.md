# docker

This example will create 3 docker containers - mysql, nginx & apache, each one's ports will be diverted to a relevant port.
A flag (set in the environment params) will tell mysql to generate a password. 
This password will be passed to the container's logs and can be found there with the logs command.
Then, we'll stop the containers and remove them.

docker container run --publish 80:80 --name yosi_nginx --detach nginx 
docker container run --publish 8080:80 --name yosi_httpd --detach httpd 
docker container run --publish 3306:3306 --name yosi_mysql --detach --env MYSQL_RANDOM_ROOT_PASSWORD=yes mysql

docker ps

docker container logs yosi_mysql

docker container stop yosi_nginx yosi_mysql yosi_httpd
docker container rm yosi_nginx yosi_mysql yosi_httpd
