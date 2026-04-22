# Environment Manipulation Cheat Sheets 📦
===============

### Key frameworks and technologies

* Python (Anaconda)
* Angular (Node.js, Docker)
* Java (Docker)
* Postgresql (Postgres)
* Amazon Web Services (Cloud)

### Brief summary of the project

This repository provides a collection of cheat sheets for manipulating environments in various programming languages and tools. It includes commands for setting up Python on Anaconda, Angular, Node libraries, Java, and Docker environments, as well as Postgresql.

## Contents
- [Github Commands](#github-commands)
- [Postgresql Commands](#postgresql-commands)
- [Conda Environments](#conda-environments)
- [Angular Environments](#angular-environments)
- [AWS Commands](#aws-commands)

## Github Commands

Initialize an existing directory as a Git repository

```bash
git init
```

Set Local Username

```bash
git config user.name "Your Name"
```

Set Local Email

```bash
git config user.email "youremail@example.com"
```

Retrieve an entire repository from a hosted location via URL

```bash
git clone [url]
```

Check current remote repository

```bash
git remote -v
```

Change remote repository if needed

```bash
git remote set-url origin <new_url>
```

Change current branch

```bash
git checkout <branch_name>
```

Add all files as it looks now to your next commit (stage)

```bash
git add *
```

Show modified files in working directory, staged for your next commit

```bash
git status
```

Commit your staged content as a new commit snapshot

```bash
git commit -m “[descriptive message]
```

Transmit local branch commits to the remote repository branch

```bash
git push [alias] [branch]
```

Delete all branches except main

```bash
git branch | grep -v "main" | xargs git branch -D
```

Copy content from main to new branch

```bash
git merge main
```

## Postgresql Commands

Install Postgresql, for Ubuntu and Debian:

```bash
sudo apt update
sudo apt install postgresql postgresql-contrib -y
```

Start postgres and enable automatic startup:

```bash
sudo systemctl start postgresql
sudo systemctl enable postgresql
```

Log into postgres:

```bash
sudo -i -u postgres
```

List databases:

```bash
psql -l
```

Connect to database:

```bash
psql -d database_name
```

Create database inside psql:

```sql
-- 1. Set the password for the default 'postgres' user (Make sure to use single quotes!)
ALTER USER postgres PASSWORD 'password';

-- 2. Create the database for your application
CREATE DATABASE database_name;

-- 3. Grant the postgres user all privileges on this new database
GRANT ALL PRIVILEGES ON DATABASE database_name TO postgres;

-- 4. Type \q and press Enter to exit the SQL prompt
\q
```

Create database inside 

```bash
psql -d database_name
```

### Database shortcuts

List all tables:

```sql
\dt
```

Show DB structure:

```sql
\d table_name
```

Clear screen:

```sql
\! clear
```

Exit database:

```sql
\q
```

## Conda Environments

Create and activate environment:

Open the Conda Prompt as administrator and run the commands

```bash
conda create -n env_name
```

To create a new environment

```bash
conda activate env_name
```

To activate the current environment

```bash
conda install pip
```

So you can install dependencies with pip

```bash
pip install -r requirements.txt
```

To install from the requirements.txt file, if you don't have a requirements file in your project yet, use the following line after you've installed all dependencies

```bash
pip freeze > requirements.txt
```

Continuing with the initialization

```bash
code .
```

To start vscode with the desired environment active and installed

## Angular Environments

Install dependencies:

After downloading [Node.js](https://nodejs.org/en/download), run the following command on the command line

```bash
npm install -g @angular/cli
```

To install Angular CLI and

```bash
ng new <project-name>
```

To create a new project.

To run the project you have to use the command below inside the project directory

```bash
npm start
```

Other method to work with Angular is to use a Dockerfile,

To use Docker, besides downloading the Docker Desktop workbench, you'll have to have a Dockerfile to create the image and Docker ignore file to clean space for your application to run easier.

Run the following commands and create files just like the ones on the [Angular folder](https://github.com/isaiapedro/environment-cheat-sheet/tree/main/angular) in this repository branch.

```bash
docker build -t angular-docker .
```

To build the Docker image and

```bash
docker run -p 4201:4200 angular-docker
```

To run the image.

```bash
docker start|stop <container_name> (or <container-id>)
```

To start or stop container

```bash
docker rm <container_name>
```

To remove existing container

```bash
docker rmi <image_name>
```

To remove existing image

```bash
docker images
```

To list docker images

```bash
docker ps --all
```

And to list all containers (running and stopped)

Other commands:

(a) Creating a component:

```bash
ng generate component [name] [options]
```

(b) Install angular materials:

```bash
npm install --save @angular/material @angular/cdk
```

## AWS Commands

To be able to use aws cli directly from local server, you can install the dependencies using the following command

```bash
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install
aws --version
```

Configure your localhost to be able to read and modify state of services

```bash
aws configure
```
| Prompt  | Information |
| ------------- | ------------- |
| AWS Access Key ID: | your access key  |
| AWS Secret Access Key: | your secret key  |
| Default region name: | sa-east-1 |
| Default output format: | json  |

Now if you want to create a direct connection via SSH to your webserver

```bash
ssh -i your-key.pem ec2-user@<NEW_IP>
```

Find RDS id

```bash
aws rds describe-db-instances \
  --query "DBInstances[*].[DBInstanceIdentifier,DBInstanceStatus]" \
  --output table
```

Find EC2 id

```bash
aws ec2 describe-instances \
  --query "Reservations[*].Instances[*].[InstanceId,State.Name,Tags[?Key=='Name'].Value]" \
  --output table
```

Check if EC2 is running

```bash
aws ec2 describe-instances \
  --region sa-east-1 \
  --query "Reservations[].Instances[].{ID:InstanceId,State:State.Name,IP:PublicIpAddress}" \
  --output table
```
Check if RDS is running

```bash
aws rds describe-db-instances \
  --region sa-east-1 \
  --query "DBInstances[].{ID:DBInstanceIdentifier,Status:DBInstanceStatus}" \
  --output table
```

Find Public IPv4 address

```bash
aws ec2 describe-instances \
  --instance-ids <your-instance-id> \
  --query "Reservations[*].Instances[*].PublicIpAddress" \
  --output text
```

Run EC2

```bash
aws ec2 start-instances --instance-ids i-xxxxxxxxxxxxxxxxx --region sa-east-1
```

Run RDS

```bash
aws rds start-db-instance \
  --db-instance-identifier music-blog \
  --region sa-east-1
```
