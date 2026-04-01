Environemnt Manipulation Cheat Sheets
===============

How to setup Python on Anaconda, Angular and Node libraries, Java and Docker environemnts

## Github Commands

Initialize an existing directory as a Git repository

	git init
Retrieve an entire repository from a hosted location via URL

	git clone [url]
	
Check current remote repository

	git remote -v

Change remote repository if needed

	git remote set-url origin <new_url>


In the same vein, change current branch

	git checkout <branch_name>

Add all files as it looks now to your next commit (stage)

	git add *
	
Show modified files in working directory, staged for your next commit

	git status
	
Commit your staged content as a new commit snapshot
	
	git commit -m “[descriptive message]
	
Transmit local branch commits to the remote repository branch

	git push [alias] [branch]

<br>

## Postgresql Commands

Install Postgresql, for Ubuntu and Debian:

	sudo apt update
	sudo apt install postgresql postgresql-contrib -y

Start postgres and enable automatic startup:

	sudo systemctl start postgresql
	sudo systemctl enable postgresql
	
Log into postgres

	sudo -i -u postgres

Connect to database

	psql -d database_name

Create database inside psql

```
-- 1. Set the password for the default 'postgres' user (Make sure to use single quotes!)
ALTER USER postgres PASSWORD 'password';

-- 2. Create the database for your application
CREATE DATABASE music_blog;

-- 3. Grant the postgres user all privileges on this new database
GRANT ALL PRIVILEGES ON DATABASE music_blog TO postgres;

-- 4. Type \q and press Enter to exit the SQL prompt
\q

```

Create database inside 

	psql -d database_name

### Database shortcuts

List all tables

	\dt

Show DB structure

	\d table_name
	
Clear screen

	\! clear
	
Exit database
	
	\q
	
You can also use SQL queries inside the database prompt!

<br>

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

<br>

	docker start|stop <container_name> (or <container-id>)

To start or stop container

	docker rm <container_name>

To remove existing container

	docker rmi <image_name>

To remove existing image

	docker images

To list docker images

	docker ps --all

And to list all containers (running and stoped)

Other commands:

<br>

(a) Creating a component:

	ng generate component [name] [options]

(b) Install angular materials:

	npm install --save @angular/material @angular/cdk
	



