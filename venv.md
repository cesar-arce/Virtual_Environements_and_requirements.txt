# Python venv virtual environment Cheat_Sheet and requirements.txt

# Step 1 - Working in VENV (create, activate, deactivate)
***********************************************************
CREATE A VIRTUAL ENVIRONMENT VENV

https://docs.python.org/3/library/venv.html
https://www.geeksforgeeks.org/creating-python-virtual-environment-windows-linux/
```
pip install virtualenv
```
Create a venv:
```
python -m venv <venv_name>
```
To activate:
```
myenv\Scripts\activate
```

```
. myenv/bin/activate
```

```
.envs\Scripts\activate.bat
```

```
deactivate
```
venv — Creation of virtual environments

https://docs.python.org/3/library/venv.html
```
python -m venv c:\path\to\myenv
```
CREATE A VIRTUAL ENVIRONMENT USING CONDA
------------------------------------------------------
https://conda.io/projects/conda/en/latest/user-guide/tasks/manage-environments.html
```
conda update --all
```
Create venv:
```
conda create --name <venv_name>
```

```
conda create -n <venv_name> python=3.9
```

To create an environment with a specific version of Python and multiple packages:
```
conda create -n myenv python=3.9 scipy=0.17.3 astroid babel
```
Verify that the new environment was installed correctly:
```
conda env list
```
You can also use:
```
conda info --envs
```
Conda rename venv
```
conda rename -n <env-oldname> <env-newname>
```

```
conda activate <venv_name>
```

```
conda deactivate
```
Remove venv:
```
conda env remove -n <venv_name> --all
```

# Step 2 -Create your "requirements.txt" file 
***********************************************************
```
pip list
```
TO CREATE FILE - Option 1
```
pip install pipreqs
```

```
pipreqs
```
or
```
pipreqs --encoding=utf-8 --force
```

```
pipreqs --encoding=iso-8859-1
```

```
pipreqs --encoding=utf8 C:\Users\root\Desktop\resumes
```

ALTERNATIVELY - Option 2
```
pip freeze > requirements.txt
```
 (recommended)
```
pip list --format=freeze > requirements.txt
```

INSTALL "requirements.txt" FILE IN A PROJECT

```
pip install -r "requirements.txt"
```


![Python venv Cheat Sheet](./python-virtual-environments.pdf)
