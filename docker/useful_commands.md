# Useful Commands in Docker

List of useful command in docker that you have to know



Stop all containers running in docker

```bash
docker container stop $(docker container ls -aq)
```



If you want to see all docker container in your machine

```bash
docker ps -a
```



If you want to remove docker container

```bash
docker run --rm image_name
```



If you want to list all the docker images that you have installed

```
docker images -a 
```



If you want to check the docker systems info

```bash
docker system df
```



Check the volume info

```bash
docker volume ls
```



Prune the image to reduce the volume space occupation

```bash
docker system prune
```

