# Data Science Docker environment with R

This file can help you to configure some useful Data Science environment with R



## Custom Docker R image

In this folder there is my custom docker file for r.  

For some useful info see this blog post:  

https://colinfay.me/docker-r-reproducibility/



Install docker

```bash
docker build -t jeydi/r-data-science -f r_container .
```



Run the image

```bash
docker run -d  -e PASSWORD=yourpassword -p 8787:8787 -v ~/DockerMount:/home/rstudio/Documents jeydi/r-data-science
```



## RStudio

Reference and documentation

https://github.com/rocker-org/rocker/wiki/Using-the-RStudio-image

Official Readme with all the info and customization

https://github.com/rocker-org/rocker-versioned/blob/master/rstudio/README.md



Pull the image

```powershell
docker pull rocker/rstudio:latest
```



Run R Studio docker image

```bash
docker run -d -p 8787:8787 -e PASSWORD=<password> --name rstudio rocker/rstudio 
```

Replace password with your custom password



If you want to run the image and sharing a folder on your PC you can do:

```powershell
docker run -d -p 8787:8787 -e PASSWORD=<password> -v ~/DockerMount:/home/rstudio/foobar --name rstudio rocker/rstudio
```

if you add the command `-e ADD=shiny` you also add the shiny server to your installation

