<p align="center">
  <h1>Udacity Full Stack Nanodegree Linux Server Configuration</h1>
  <img src="" width="460"/>
</p>


## Description
This project was created as part of my coursework for the Udacity [Full Stack Web Developer Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004). The objective for this project is to setup and secure a Linux server that will host a web application.

# Getting Started

## Set up your server on Amazon Lightsail
### Amazon Lightsail
Start a new Ubuntu Linux server instance on [Amazon Lightsail] (https://lightsail.aws.amazon.com/ls/docs/all).
### Configure the server

1. SSH to your server
2. Add a user called "grader".    
Run:
```
	useradd -m -s /bin/bash grader
```


Run:
```
  git clone https://github.com/udacity/fullstack-nanodegree-vm.git
```

## Run the virtual machine!

Using the terminal, change directory to fullstack-nanodegree-vm/vagrant (**cd fullstack-nanodegree-vm/vagrant**), then type **vagrant up** to launch your virtual machine. (This could take a few minutes)

## SSH to the Vagrant VM
Once it is up and running, type **vagrant ssh**. This will log your terminal into the virtual machine, and you'll get a Linux shell prompt. When you want to log out, type **exit** at the shell prompt.  To turn the virtual machine off (without deleting anything), type **vagrant halt**. If you do this, you'll need to run **vagrant up** again before you can log into it.

Change to the Vagrant shared folder, type **cd /vagrant**.
Type **ls** to see the contents of the directory. **catalog forum  tournament  Vagrantfile**

Remove the existing **catalog** folder by typing: ("catalog" will be replaced by "Catalog" in the next step"
```
  rm -rf catalog
```
## Get the catalog app code
While in the **/vagrant** directory clone this repo, Type:
```
  git clone https://github.com/marcuskeenan/Catalog.git
```
This will create a new folder inside the catalog directory called **Catalog**.

# Setup the application
Change to the Catalog directory **cd Catalog** and **ls** and **ls** to make sure the directory contains **application.py**, **database_setup.py**, and **seed_database.py**.

## Set up the database
Run:
```
  python database_setup.py to initialize the database.
```
This will create a sqlite database called catalog.db.

## Add fake data to the database
Run:(Optional)
```
python seedatabase.py
```
This will seed the database with some catalog categories and associated items.

## Configure the app
Type:
```
  sudo chmod +x ./pg_config.sh
```
Run:
```
  sudo ./pg_config.sh
```
## Run the application
Run:
```
python application.py
```
This will run the Flask web server. In your browser visit **http://localhost:5000** to view the catalog app. After loggin in, you should be able to view, add, edit, and delete catalog items and categories.
