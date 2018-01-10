This example will take a node.js image,
copy a website into it, install its
dependencies and configure the container to run it

The sample website can be found on udemy-docker-mastery/dockerfile-assignment-1


# Dockerfile:

FROM node:6-alpine

RUN apk add --update tini &&\
    mkdir -p /usr/src/app

EXPOSE 3000

WORKDIR /usr/src/app

COPY package.json package.json

RUN npm install &&\
    npm cache clean --force

COPY . .

CMD [ "tini", "--", "node", "./bin/www" ]


# Commands to build this:

docker image build -t sample-node-app .
docker container run -d -p 80:3000 container_name sample-node-app

* Goto localhost:80 & check it out.

docker container stop container_name
docker container rm container_name

docker login
docker image tag sample-node-app ygoldgur/sample-node-app
docker image push ygoldgur/sample-node-app
docker logout


* Check the online repository

docker image rm sample-node-app
docker image rm ygoldgur/sample-node-app

docker container run -d -p 80:3000 container_name ygoldgur/sample-node-app

* See that it downloads it from the repository.


