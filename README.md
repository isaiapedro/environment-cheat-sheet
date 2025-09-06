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

<br>

## Angular Environments
Install dependencies:

After downloading [Node.js](https://nodejs.org/en/download), run the following command on the command line

	npm install -g @angular/cli
To install Angular CLI and

	ng new <project-name>

To create a new project.

To run the project you have to use the command below inside the project directory

	npm start

Other method to work with Angular is to use a Dockerfile,

To use Docker, besides downloading the Docker Desktop workbench, you'll have to have a Dockerfile to create the image and Docker ignore file to clean space for your application to run easier.

Run the following commands and create files just like the ones on the [Angular folder](https://github.com/isaiapedro/environment-cheat-sheet/tree/main/angular) in this repository branch.

	docker build -t angular-docker .

To build the Docker image and

	docker run -p 4201:4200 angular-docker

To run the image.
