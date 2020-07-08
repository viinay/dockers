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

4] CMD

5] ENTRYPOINT

6] ENV

7] WORKDIR

8] COPY
