# Virtual Environements and requirements.txt
***********************************************************

CREATE A VIRTUAL ENVIRONMENT VENV
------------------------------------------------------
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

============================================================================================

## CREATE YOUR "requirements.txt" FILE 

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

ALTERNATIVALLY - Option 2

> pip list --format=freeze > requirements.txt

INSTALL "requirements.txt" FILE IN A PROJECT

> pip install -r "requirements.txt"

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////

DOCKERS --> Dokerfile (in the root) same place as requirements.txt

# Dockerfile, Image, Container

FROM python:3.8

WORKDIR /fastapi-app

ADD main.py .  (Source)

COPY requirements.txt .   (Libraries)

RUN pip install -r requirements.txt  (or pip install request others....)

COPY ./app ./app

CMD ["python", "./app/main.py"]

--------------------------------------------------------

Terminal:

$ docker -v

### Building the image

$ docker -t python-imdb .

$ docker run python-imdb

### After modify python script build again

$ docker build -t python-imdb .

$ docker run -t -i python-imdb

### Changing to the CMD in the Container

$ docker exec -it 14b15c25c /bin/sh

$ ls


### After modifying script python build again

$ docker build -t python-fastapi .
$ docker run -p 8000:8000 python-fastapi

Docker Tutorial For Beginners - How To Containerize Python Applications
https://www.youtube.com/watch?v=bi0cKgmRuiA&t=695s
