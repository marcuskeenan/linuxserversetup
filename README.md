<p align="center">
  <h1>Udacity Full Stack Nanodegree Linux Server Configuration</h1>
  <img src="" width="460"/>
</p>


## Description
This project was created as part of my coursework for the Udacity [Full Stack Web Developer Nanodegree](https://www.udacity.com/course/full-stack-web-developer-nanodegree--nd004). The objective for this project is to setup and secure a Linux server that will host a web application.

## Features
1. Linux Ubuntu 16.04 LTS VM hosted on Azure
2. RESTful JSON endpoints
3. Third-party OAuth 2.0 authentication using google sign in

## Prerequisites
1. [Python](https://www.python.org/downloads/) installed
2. VirtualBox
3. Vagrant
4. Git


# Getting Started

## Set up your server
### Amazon Lightsail
1. Start a new Ubuntu Linux server instance on Amazon Lightsail. There are full details on setting up your Lightsail instance on the next page.
2. Follow the instructions provided to SSH into your server.
Get started on Lightsail
We're recommending Amazon Lightsail for this project. If you prefer, you can use any other service that gives you a publicly accessible Ubuntu Linux server. But Lightsail works pretty well and it's what we've tested.

There are a few things you need to do when you create your server instance.

1. Log in!
First, log in to Lightsail. If you don't already have an Amazon Web Services account, you'll be prompted to create one.

Amazon Web Services login page.
2. Create an instance.
Once you're logged in, Lightsail will give you a friendly message with a robot on it, prompting you to create an instance. A Lightsail instance is a Linux server running on a virtual machine inside an Amazon datacenter.

When you have no instances, Lightsail gives you a picture of an orange robot and suggests that you create an instance.
3. Choose an instance image: Ubuntu
Lightsail supports a lot of different instance types. An instance image is a particular software setup, including an operating system and optionally built-in applications.

For this project, you'll want a plain Ubuntu Linux image. There are two settings to make here. First, choose "OS Only" (rather than "Apps + OS"). Second, choose Ubuntu as the operating system.

When you create an instance, Lightsail asks what kind you want.
For this project, choose an "OS Only" instance with Ubuntu.
4. Choose your instance plan.
The instance plan controls how powerful of a server you get. It also controls how much money they want to charge you. For this project, the lowest tier of instance is just fine. And as long as you complete the project within a month and shut your instance down, the price will be zero.

Lightsail's options for instance pricing.
For this project, pick the lowest one to get free-tier access.
Be aware: If you enable additional features in Lightsail, you may be charged extra for them.
5. Give your instance a hostname.
Every instance needs a unique hostname. You can use any name you like, as long as it doesn't have spaces or unusual characters in it. Your instance's name will be visible to you and to the project reviewer.

I've named my instance silly-name-here.
6. Wait for it to start up.
It may take a few minutes for your instance to start up.

While your instance is starting up, Lightsail shows you a grayed-out display.

Once your instance is running, the display gets brighter.
7. It's running; let's use it!
Once your instance has started up, you can log into it with SSH from your browser.

The public IP address of the instance is displayed along with its name. In the above picture it's 54.84.49.254. The DNS name of this instance is ec2-54-84-49-254.compute-1.amazonaws.com.

The main page for my silly-name-here instance.
The big orange "Connect using SSH" button is the next step.
Explore the other tabs of this user interface to find the Lightsail firewall and other settings. You'll need to configure the Lightsail firewall as one step of the project.

When you SSH in, you'll be logged as the ubuntu user. When you want to execute commands as root, you'll need to use the sudo command to do it. Review sudo here if you need a refresher!

An SSH window logged into the server instance.
From here, it's just like any other Linux server.
8. Project time.
Now that you have a working instance, you can get right into the project!

### Or

### Microsoft Azure
https://docs.microsoft.com/en-us/azure/virtual-machines/linux/quick-create-portal

VirtualBox is the software that actually runs the VM. [You can download it from virtualbox.org, here.](https://www.virtualbox.org/wiki/Downloads)  Install the *platform package* for your operating system.  You do not need the extension pack or the SDK. You do not need to launch VirtualBox after installing it.

**Ubuntu 14.04 Note:** If you are running Ubuntu 14.04, install VirtualBox using the Ubuntu Software Center, not the virtualbox.org web site. Due to a [reported bug](http://ubuntuforums.org/showthread.php?t=2227131), installing VirtualBox from the site may uninstall other software you need.

## Install Vagrant

Vagrant is the software that configures the VM and lets you share files between your host computer and the VM's filesystem.  [You can download it from vagrantup.com.](https://www.vagrantup.com/downloads) Install the version for your operating system.

**Windows Note:** The Installer may ask you to grant network permissions to Vagrant or make a firewall exception. Be sure to allow this.

## Get the Udacity fullstack-nanodegree-vm VM

**Windows:** Use the Git Bash program (installed with Git) to get a Unix-style terminal.  
**Other systems:** Use your favorite terminal program.

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
