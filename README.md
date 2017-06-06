# Linux-Server-Configuration

## Project Overview
You will take a baseline installation of a Linux server and prepare it to host your web applications. You will secure your server from a number of attack vectors, install and configure a database server, and deploy one of your existing web applications onto it.

### Why this Project?
A deep understanding of exactly what your web applications are doing, how they are hosted, and the interactions between multiple systems are what define you as a Full Stack Web Developer. In this project, you’ll be responsible for turning a brand-new, bare bones, Linux server into the secure and efficient web application host your applications need.

### What will I Learn?
You will learn how to access, secure, and perform the initial configuration of a bare-bones Linux server. You will then learn how to install and configure a web and database server and actually host a web application.

### How does this Help my Career?
Deploying your web applications to a publicly accessible server is the first step in getting users
Properly securing your application ensures your application remains stable and that your user’s data is safe

## Project Details
### How will I complete this project?
This project is linked to the Configuring Linux Web Servers course, which teaches you to secure and set up a Linux server. By the end of this project, you will have one of your web applications running live on a secure web server.

To complete this project, you'll need a Linux server instance. We recommend using Amazon Lightsail for this. If you don't already have an Amazon Web Services account, you'll need to set one up. Once you've done that, here are the steps to complete this project.

#### Get your server.
1. Start a new Ubuntu Linux server instance on Amazon Lightsail. There are full details on setting up your Lightsail instance on the next page.
2. Follow the instructions provided to SSH into your server.

#### Secure your server.
3. Update all currently installed packages.
4. Change the SSH port from 22 to 2200. Make sure to configure the Lightsail firewall to allow it.
5. Configure the Uncomplicated Firewall (UFW) to only allow incoming connections for SSH (port 2200), HTTP (port 80), and NTP (port 123).

Warning: When changing the SSH port, make sure that the firewall is open for port 2200 first, so that you don't lock yourself out of the server. Review this video for details! When you change the SSH port, the Lightsail instance will no longer be accessible through the web app 'Connect using SSH' button. The button assumes the default port is being used. There are instructions on the same page for connecting from your terminal to the instance. Connect using those instructions and then follow the rest of the steps.

#### Give grader access.
In order for your project to be reviewed, the grader needs to be able to log in to your server.

6. Create a new user account named grader.
7. Give grader the permission to sudo.
8. Create an SSH key pair for grader using the ssh-keygen tool.

#### Prepare to deploy your project.
9. Configure the local timezone to UTC.
10. Install and configure Apache to serve a Python mod_wsgi application.
11. Install and configure PostgreSQL:
 * Do not allow remote connections
 * Create a new database user named catalog that has limited permissions to your catalog application database.
12. Install git.

#### Deploy the Item Catalog project.
13. Clone and setup your Item Catalog project from the Github repository you created earlier in this Nanodegree program.
14. Set it up in your server so that it functions correctly when visiting your server’s IP address in a browser. Make sure that your .git directory is not publicly accessible via a browser!


## Get started on Lightsail
We're recommending Amazon Lightsail for this project. If you prefer, you can use any other service that gives you a publicly accessible Ubuntu Linux server. But Lightsail works pretty well and it's what we've tested.

There are a few things you need to do when you create your server instance.

### 1. Log in!

First, log in to Lightsail. If you don't already have an Amazon Web Services account, you'll be prompted to create one.
![Amazon Web Services login page.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e45f9_screen-shot-2017-02-10-at-14.59.35/screen-shot-2017-02-10-at-14.59.35.png)

Amazon Web Services login page.

### 2. Create an instance.
Once you're logged in, Lightsail will give you a friendly message with a robot on it, prompting you to create an instance. A Lightsail instance is a Linux server running on a virtual machine inside an Amazon datacenter.
![When you have no instances, Lightsail gives you a picture of an orange robot and suggests that you create an instance.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e45a0_screen-shot-2017-02-10-at-14.58.17/screen-shot-2017-02-10-at-14.58.17.png)

When you have no instances, Lightsail gives you a picture of an orange robot and suggests that you create an instance.

### 3. Choose an instance image: Ubuntu
Lightsail supports a lot of different instance types. An instance image is a particular software setup, including an operating system and optionally built-in applications.

For this project, you'll want a plain Ubuntu Linux image. There are two settings to make here. First, choose "OS Only" (rather than "Apps + OS"). Second, choose Ubuntu as the operating system.
![When you create an instance, Lightsail asks what kind you want.For this project, choose an "OS Only" instance with Ubuntu.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43c6_screen-shot-2017-02-10-at-14.46.15/screen-shot-2017-02-10-at-14.46.15.png)

When you create an instance, Lightsail asks what kind you want.
For this project, choose an "OS Only" instance with Ubuntu.

### 4. Choose your instance plan.
The instance plan controls how powerful of a server you get. It also controls how much money they want to charge you. For this project, the lowest tier of instance is just fine. And as long as you complete the project within a month and shut your instance down, the price will be zero.
![Lightsail's options for instance pricing.For this project, pick the lowest one to get free-tier access.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43ca_screen-shot-2017-02-10-at-14.46.35/screen-shot-2017-02-10-at-14.46.35.png)
Lightsail's options for instance pricing.
For this project, pick the lowest one to get free-tier access.

### 5. Give your instance a hostname.
Every instance needs a unique hostname. You can use any name you like, as long as it doesn't have spaces or unusual characters in it. Your instance's name will be visible to you and to the project reviewer.

![I've named my instance `silly-name-here`.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43ce_screen-shot-2017-02-10-at-14.47.08/screen-shot-2017-02-10-at-14.47.08.png)

I've named my instance silly-name-here.

### 6. Wait for it to start up.
It may take a few minutes for your instance to start up.
![While your instance is starting up, Lightsail shows you a grayed-out display.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43d2_screen-shot-2017-02-10-at-14.47.34/screen-shot-2017-02-10-at-14.47.34.png)

While your instance is starting up, Lightsail shows you a grayed-out display.

![Once your instance is running, the display gets brighter.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43cb_screen-shot-2017-02-10-at-14.48.29/screen-shot-2017-02-10-at-14.48.29.png)

Once your instance is running, the display gets brighter.

### 7. It's running; let's use it!
Once your instance has started up, you can log into it with SSH from your browser.

The public IP address of the instance is displayed along with its name. In the above picture it's 54.84.49.254. The DNS name of this instance is ec2-54-84-49-254.compute-1.amazonaws.com.
![The main page for my `silly-name-here` instance. The big orange "Connect using SSH" button is the next step.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43c3_screen-shot-2017-02-10-at-14.48.40/screen-shot-2017-02-10-at-14.48.40.png)

The main page for my silly-name-here instance.
The big orange "Connect using SSH" button is the next step.
Explore the other tabs of this user interface to find the Lightsail firewall and other settings. You'll need to configure the Lightsail firewall as one step of the project.

When you SSH in, you'll be logged as the ubuntu user. When you want to execute commands as root, you'll need to use the sudo command to do it. Review sudo here if you need a refresher!
![An SSH window logged into the server instance. From here, it's just like any other Linux server.](https://d17h27t6h515a5.cloudfront.net/topher/2017/February/589e43be_screen-shot-2017-02-10-at-14.49.14/screen-shot-2017-02-10-at-14.49.14.png)
An SSH window logged into the server instance.
From here, it's just like any other Linux server.

### 8. Project time.
Now that you have a working instance, you can get right into the project.

