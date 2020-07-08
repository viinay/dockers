# dockers
docker projects and notes


## Various Commands in Dockerfile

1] FROM - used to define the base image, on which we will be building

  `FROM <image-tag>` usually the 1st line of a Dockerfile
  
  Example:
    `FROM ubuntu:18.04` OR `FROM python:latest`
    
2] ADD - used to add files to the container being build
   
   `ADD <source> <destination in container>`
   
   Example:
      `ADD . /var/www/html`

3] RUN - used to add layers to the base image,by installing components.Each RUN statement,adds a new layer to the docker image
  
  `RUN <command to install pkgs>`
  
 Example:
    `RUN apt-get update` OR `RUN apt-get -y install apache2`

4] CMD - used to run commands on the start of the container.These commands run only when there is no argument specified while running the container.CMD command gets skipped if argument is specified while running the docker.
  
  `CMD <cmd>`
  
  Example:
  `CMD apachectl -D FOREGROUND`

5] ENTRYPOINT - used strictly run commands the moment the container initializes.The difference between CMD and ENTRYPOINT will run irrespective of the fact whether argument is specified or not.
 
`ENTRYPOINT <cmd>`

Example: `ENTRYPOINT apachectl -D FOREGROUND`

6] ENV - used to define environment variables in the container run-time.

`ENV <name> <value>`

Example: `ENV name superman`

7] WORKDIR

8] COPY

## Dockerfile Example to install and run Apache2
```FROM ubuntu
ARG DEBIAN_FRONTEND=noninteractive
RUN apt-get -y update
RUN apt-get -y install apache2
ADD . /var/www/html
ENTRYPOINT apachectl -D FOREGROUND
ENV name superman
```

## Run docker without sudo

`sudo usermod -aG docker $USER`

## Build docker image from Dockerfile
`sudo docker build . -t <image-tag>`

`sudo docker build - < Dockerfile`

## Run docker 

`sudo docker run -it -d -p <host-port>:<container-port> <image-tag>`


## Access container shell

`sudo docker exec -it <container-Id> bash`

