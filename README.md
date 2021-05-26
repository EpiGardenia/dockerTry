# Part 1

## Add dockerfile
Image support for each language is available in dockerhub
Check Tag for available images

## Add docker-compose.yaml
1. Choose a compose file version
2. Add service for each language, connect to github account

## Build 
### 
```yaml
run docker-compose build [language]
```
This will download the coresponding image for the language
for example: docker-compose build python

### 
```yaml
run docker-compose build
```
This will build everything defined in docker-compose.yaml



# Part 2
## docker run config
Instead of directly running below command, docker-compose configure it seperately.
```yaml
docker run -it -v ${PWD}:/work -w /work -p 5003:5000 epigardenia/python:1.0.0 /bin/sh
```
 1. Mount path as working directory, 
 2. Create container over image epigardenia/python:1.0.0,
 3. Execute command inside current working directory
 4. Publish to ports 5003:5000

Corresponding setup:
 ```yaml
    working_dir: /work
    entrypoint: /bin/sh
    stdin_open: true
    tty: true
    volumes:
    - ./python/src/:/work
    ports:
    - 5003:5000
 ```


## create docker containers
```yaml
 docker-compose up -d
``` 
-d: Detach mode: start in the background mode
more on [docker-compose up](https://docs.docker.com/compose/reference/up/)


## see all containers
```yaml
docker ps
```
CONTAINER ID   IMAGE                              COMMAND                  CREATED              STATUS              PORTS                                       NAMES
c9d607556a13   epigardenia/python:1.0.0           "/bin/sh"                About a minute ago   Up About a minute   0.0.0.0:5003->5000/tcp, :::5003->5000/tcp   python

## run app from container
```yaml
docker exec -it python sh
```
 
/work #



# Part3

## Divide into stage 

we can make make stage image of some layers, to reuse in a later stage.
For example, if we need dev (debug) and prod (release) two images.
Without build from the beginning twice, we can build common layes  then use

```yaml
COPY --from=dev /<commonImageFolder>/ /<newImageFolder>
```
to save some work.

 
# Part 4 

Create base, debug, and prod for different purpose

 
# Part 5 Debugging

# Credit
[video](https://www.youtube.com/watch?v=wyjNpxLRmLg)

