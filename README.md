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

Terminal:

$ docker version

$ docker -v  (only Docker version)

$ docker info

$ docker --help

### Building the image

$ docker -t python-imdb .

$ docker run python-imdb

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


![cheat-sheet-v2.pdf](cheat-sheet-v2.pdf)
