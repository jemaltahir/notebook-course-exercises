# Rahti Cloud containers advanced course exercises.

This exercise aims to introduce you to Rahti Cloud containers using notebooks. We will go through the deploying Jupyter Notebook Image from the Docker hub and then move to deploy thgis image variant in the Rahti cloud service. 

## Exercise 1: Deploying a Jupyter Notebook Image.

1. Make sure that you have [Docker](https://docs.docker.com/get-docker/) or  [Podman](https://podman.io/getting-started/installation) isntalled on your system.

1. Pull, start and expose the Jupyter Notebook server.
  
   The `jupyter/minimal-notebook` image can be found on [docker hub](https://hub.docker.com/r/jupyter/minimal-notebook), expose the image on port: 8888
   and grab the link from conatiner logs.
 
1. Test the container 

   Create a folder name `test-hello` and a python script `print("Hello")` in the file name `hello.ipynb` execute the script.
   
1. Kill the container 

   After killing the container, create again the container you will notice that the python script and the folder create are no longer availbale. This is becauase conatiners by nature are ephemeral which means that they do not store/save in them. To persist data or configuration changes in a container, containerized applications often use external storage volumes or configuration management tools. 
   
1. Save your work

   To save the created python script we have to mount volume local host to container.
  Using the following command `sudo docker run -it --rm -p 8888:8888 --user root  -e NB_UID=$(id -u) -e NB_GID=$(id -g) -e CHOWN_HOME=yes -e CHOWN_HOME_OPTS='-R' -v "${PWD}":/home/jovyan/work jupyter/minimal-notebook`
The `-v` flag is used in Docker commands to specify a volume, which allows for data to be shared between the host system and a container. The `${PWD}` part of the command is a shell variable that represents the current working directory (PWD stands for "present working directory"). And `/home/jovyan/work` is the path inside the container where the volume will be mounted.
  


   


  
  
