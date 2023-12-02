# Virtual Environements and requirements.txt
# Step1 - Working in VENV (create, activate, deactivate)
***********************************************************
CREATE A VIRTUAL ENVIRONMENT VENV

https://docs.python.org/3/library/venv.html
https://www.geeksforgeeks.org/creating-python-virtual-environment-windows-linux/

> pip install virtualenv

Create a venv:
> python -m venv [venv_name]

To activate:
> myenv\Scripts\activate
> 
> . myenv/bin/activate
> 
> .envs\Scripts\activate.bat

$ deactivate

venv — Creation of virtual environments

https://docs.python.org/3/library/venv.html

> python -m venv c:\path\to\myenv

CREATE A VIRTUAL ENVIRONMENT USING CONDA
------------------------------------------------------
https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html

Create venv:
> conda create --name [myenv]
> 
> conda create -n [myenv] python=3.9

To create an environment with a specific version of Python and multiple packages:
> conda create -n myenv python=3.9 scipy=0.17.3 astroid babel

Verify that the new environment was installed correctly:
> conda env list

You can also use:
> conda info --envs

> conda activate [venv_name]
> 
> conda deactivate


# Step 2 -Create your "requirements.txt" file 
***********************************************************
> pip list

TO CREATE FILE - Option 1
> pip install pipreqs
> 
> pipreqs

or
> pipreqs --encoding=utf-8 --force
> 
> pipreqs --encoding=iso-8859-1
> 
> pipreqs --encoding=utf8 C:\Users\root\Desktop\resumes

ALTERNATIVELY - Option 2

> pip freeze > requirements.txt
>
> pip list --format=freeze > requirements.txt

INSTALL "requirements.txt" FILE IN A PROJECT

> pip install -r "requirements.txt"


# Step 3 - Working with Dockers (Dockerfile, Image, Container)
***********************************************************
DOCKERS --> Dokerfile (in the root) same place as requirements.txt

<pre>
FROM python:3.8                      < image >
FROM python

WORKDIR /fastapi-app                 < path to working directory >
WORKDIR c:\\windows\

ADD main.py .                        < source > < destination > 
ADD test1.txt c:\temp\               ["< source >", "< destination >"] -> destination includes white space

COPY requirements.txt .               (Libraries)
COPY ./app ./app                      < source > < destination >  
COPY config* c:/temp/                 ["< source >", "< destination >"] -> destination includes white space
                                        
RUN pip install -r requirements.txt   < command > ["< executable >", "< param 1 >", "< param 2 >"] 
RUN pip install request pandas others....

CMD ["python", "./app/main.py"]       < command >  ["< executable >", "< param >"]
CMD ["c:\\Apache24\\bin\\httpd.exe", "-w"]
</pre>
--------------------------------------------------------
# RUN = pull + create + start

- $ docker pull python:3.9

- $ docker create --name < name_container > python:3.9

- $ docker start < name_container >

$ docker run -it --name < name_container > python:3.9 /bin/bash

or case MySQL

$ docker run -it --name < name_container > -e MYSQL_ROOT_PASSWORD=root -d mysql/mysql -server:5.7 mysql

$ docker exec -it < name_container > /bin/bash

- $ docker container stop < name_container >

## Getting Help
Terminal:

Display Docker version with docker --version

$ docker --version

$ docker -v  (only Docker version)

Display Docker system info with docker info

$ docker info

Get help on Docker with docker --help

$ docker --help

Get help on Docker command usage with docker {command} --help

$ docker run --help

## Building Images

$ docker image ls

Build an image with docker build {path}

$ docker build .

Build a tagged image with docker build --tag {name:tag} {path}

$ docker build --tag myimage:2023-edition .

Build an image without using the cache docker build -no-cache {path}

$ docker build --no-cache .

## Image Management

List all local images with docker images

$ docker images

Show Docker disk usage with docker system df

$ docker system df

Show image creation steps from intermediate layers with docker history {image}

$ docker history alpine

Save an image to a file with docker save --output {filename}
Usually combined with a compression tool like gzip

$ docker save julia | gzip > julia.tar.gz

Load an image from a file with docker load --input {filename}

$ docker load --input julia.tar.gz

Delete an image with docker rmi {image}

$ docker -rmi rocker/r-base


## Inspecting Containers

List all running containers with docker ps

$ docker container ls

$ docker ps

List all containers with docker ls --all

$ docker container ls --all

List all containers matching a conditions with docker ls --filter {key}={value}

$ docker container ls --filter 'name=red1'

Show container log output with docker logs --follow {container}

$ docker run --name bb busybox sh -c "$(echo date)"  --> Print current datetime

$ dockerlogs --follow bb   --> Print what bb container printed



## Running Containers

Run a container with docker run {image}

$ docker run hello-world  --> Runs a test container to check your installation works

Run a container then use it to run a command with docker run {image} {command}

$ docker run python python -c "print('Python in Docker')"  --> Run Python & print text

$ docker run rocker/r-base r -e "print(lm(disc`speed, cars))" --> Run R & print a model

Run a container interactively with docker run --interactive --tty

$ docker run --interactive --tty rocker/r-base  --> Run R interactively

Run a container, and remove it once you've finished with docker run --rm

$ docker run --rm mysql --> Run MySQL, then clean up

Run an image in the background with docker run --detach

$ docker run --detach postgres

Run an image, assigning a name, with docker --name {name} run

$ docker run --name red1 redis --> Run redis, naming the container as red1

Run an image as a user with docker run --user {username}

$ docker run --user doctordocker mongo

## Creating a Network

$ docker network ls

$ docker network --help

$ docker network create my_app_net   < network_name >

$ docker network inspect my_app_net

$ docker container run -d --name <name_container> --network < network_nema > nginx

$ docker container run -d --name new_nginx --network my_app_net nginx

-------
$ docker network connect < network_name > < name_container > (Connect "Id" Network of  "Driver": "bridge", 8facc8c8429a to a Container) 

Connect a container to a network when it starts
$ docker network connect my_app_net db
(-------)

$ docker network inspect < network_name >

$ docker container inspect < name_container >

$ docker network disconnect <network> <container>   (Disconnect a Container to a Network)

$ docker network disconnect bridge db 

$ docker network disconnect bridge webhost

$ docker network disconnect bridge proxy

$ docker network ls ( active only )

$ docker network ls -a  (all = active+stopped)

### After modify your python script build again

$ docker build -t python-imdb .

$ docker run -t -i python-imdb

### Changing to the CMD in the Container

$ docker exec -it 14b15c25c /bin/sh

$ ls


### After modifying your python script build again

$ docker build -t python-fastapi .


$ docker run -p 8000:8000 python-fastapi

Docker Tutorial For Beginners - How To Containerize Python Applications
https://www.youtube.com/watch?v=bi0cKgmRuiA&t=695s


![Docker CheatSheet](./Docker_cheat_sheet.png)
![Image PDF](./cheat-sheet-v2.pdf)
