# Ud-FSND-LinuxServerConfiguration
Udacity Full Stack Web Developer Nanodegree Project : Linux Server Configuration

## [Project Description](Project_Description.md)

## [Project Specification](Project_Specification.md)

## IP address and SSH port
* Public IP : 18.217.
* SSH port : 2200

## Complete URL to hosted web application


## Summary of software installed and configuration changes made

### Secure server
#### Update all currently installed packages
```bash
sudo apt update     # update available package lists
sudo apt upgrade    # upgrade installed packages
sudo apt autoremove # automatically remove packages that are no longer required
```



```bash
# Change the SSH port from 22 to 2200
sudo nano /etc/ssh/sshd_config  # change port to 2200

sudo service ssh restart


```


#### Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).

### Give grader access

### Prepare to deploy your project

### Deploy the Item Catalog project

```bash
# update all system packages to most recent versions
sudo apt update && sudo apt upgrade

# Change the SSH port from 22 to 2200
sudo nano /etc/ssh/sshd_config

# configure the Lightsail firewall to allow it

# Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for 
# SSH (port 2200), HTTP (port 80), and NTP (port 123).
# Warning: When changing the SSH port, make sure that the firewall is open for port 2200 first, 
# so that you don't lock yourself out of the server.When you change the SSH port, 
# the Lightsail instance will no longer be accessible through the web app 'Connect using SSH' button. 
# The button assumes the default port is being used. 
# There are instructions on the same page for connecting from your terminal to the instance. 
# Connect using those instructions and then follow the rest of the steps.

# Create a new user account named grader.
sudo adduser grader

# Give grader the permission to sudo.

# Create an SSH key pair for grader using the ssh-keygen tool.


# Configure the local timezone to UTC.

# Install and configure Apache to serve a Python mod_wsgi application

# Install the Python 3 mod_wsgi package on your server: 
sudo apt-get install libapache2-mod-wsgi-py3.

# Install and configure PostgreSQL:

# Do not allow remote connections

# Create a new database user named catalog that has limited permissions 
# to your catalog application database.

# Install git
sudo apt install git

# Clone and setup your Item Catalog project from the Github repository 
# you created earlier in this Nanodegree program.

# Set it up in your server so that it functions correctly 
# when visiting your server’s IP address in a browser. 
# Make sure that your .git directory is not publicly accessible via a browser!
```


## List of any third-party resources you made use of to complete this project
https://bash.cyberciti.biz/guide/Shell_Comments
