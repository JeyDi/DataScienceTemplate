# Instruction for Python Images and Containers



WARNING: Remember to create in your pc home folder a new folder called: DockerMount



Build the image (the anaconda python container image)

```bash
docker build -t jeydi/data-science-docker -f conda_container .
```



Run in detach mode for Windows and MacOS

```bash
docker run -d --name data-science -v ~/DockerMount:/root/GitProjects -p 8284:8284 -i jeydi/data-science-docker
docker exec -it data-science bash
```



Run in detach mode for Linux

```bash
docker run -d --name data-science -v ~/DockerMount:/root/GitProjects -p --network=host -i jeydi/data-science-docker
docker exec -it data-science bash
```



Run image interactively in Windows

```bash
docker run -it -v ~/DockerMount:/root/GitProjects -p 8284:8284 -i jeydi/data-science-docker
```



If you want to check the images inside your machine

```bash
docker ps -a
```



If you want to start the image that you have just created

```bash
docker run data-science
```



If you want to stop the execution

```bash
docker stop data-science
```



## Jupyter Notebook Docker Stacks

https://jupyter-docker-stacks.readthedocs.io/en/latest/

There is a custom docker image with jupyter that is much more easy to use because it doesn't require the installation of Ubuntu and it's much more lite.

Official github repo: https://github.com/jupyter/docker-stacks

List of Docker images that you can use: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html



Pull the data-science image

```powershell
docker pull jupyter/datascience-notebook:latest
```



Run the image

```powershell
docker run -d -P --name jupyter -v ~/DockerMount:/home/Work jupyter jupyter/datascience-notebook
```



