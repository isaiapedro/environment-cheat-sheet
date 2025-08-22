Environemnt Manipulation Cheat Sheets
===============

How to setup Python on Anaconda, Angular and Node libraries, Java and Docker environemnts

## Conda Environments
Create and activate enviornment:

Open the Conda Prompt as administrator and run the commands

	conda create -n env_name
To create a new environemnt

	conda activate env_name

To activate the current environemnt

	conda install pip
	
So you can install dependencies with pip

	pip install -r requirements.txt
	
To install from the requirements.txt file, if you don't have a requirements file in your project yet, use the following line after you've installed all dependencies
	
	pip freeze > requirements.txt
	
Continuing with the initialization

	code .

To start vscode with the desired environment active and installed
