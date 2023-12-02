# Python venv virtual environment cheat sheet
## Create a venv
To create a virtual environment, go to the root of your project and run

``python -m venv <venv_name>``
``conda create -n <venv_name> python=3.9``

It will create a virtual environment called venv

## Activate venv
``.\venv\Scripts\activate``
``conda activate <venv_name>``

## Intall packages
``pip install jupyter matplotlib numpy pandas scipy scikit-learn``

or

``python -m pip install -U jupyter matplotlib numpy pandas scipy scikit-learn``

## Create requirements.txt
``pip freeze > requirements.txt``

``pip list --format=freeze > requirements.txt``

## Deactivate venv
``deactivate``
``conda deactivate``

## Install packages from requirements.txt
``pip install -r requirements.txt``



![Python venv Cheat Sheet](./python-virtual-environments.pdf)
