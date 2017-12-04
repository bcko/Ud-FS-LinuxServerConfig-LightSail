# Intro to Linux
Notes from Udacity Linux for Web Developers course

## Introduction
Welcome to Linux for Web Developers.
I'm Mike Wills and I'll be your instructor for this course.
Every time you visit a web application, your browser is requesting a number of
files that are sitting on a server somewhere out there on the Internet.
More often than not, that server is running Linux.
Therefore, as you develop and get ready to launch your own web applications,
it's critical that you understand how these servers work and
how to get your web application up and running on one.
In this course you'll do just that.
You'll start with a quick introduction to Linux, and
you begin exploring the Linux file system.
How are files organized, where do they belong.
I'll then introduce you to a number of Linux security concepts.
Managing users, how to understand permission system, firewalls, and
package or software management.
Finally, you'll get a very basic web application up and
running using the Apache web server, and a postscript SQL database server.
Managing and configuring servers is one of my favorite parts of this career.
There's something very powerful in knowing that you've taken a server from
zero to hero, all on your own and are in full control of it's capabilities.
I think you'll enjoy this experience, and in the end, you'll be able to
truly share your web applications with others while having the most intimate,
low level knowledge of how people are actually receiving and
experiencing your application.

## What is Linux
Linux is by far the most popular operating system of choice for
web servers on the Internet today.
Some estimates say 80% of public Internet servers
are running some flavor of Linux.
So what exactly is Linux?
Linux is an operating system similar to Microsoft Windows or
Apple OS X, which you might be more familiar with.
The biggest difference with Linux though is it's free.
Now, when I say free, you may be thinking of money, and
that's not necessarily the case.
You may have heard the phrases, free as in beer and free as in speech.
It's quite popular within the open source community.
Let's discuss what each of these means and
how they apply to the Linux operating system.

## Free as in Beer
Free as in beer refers to money.
If someone buys you a beer, it costs you nothing.
Many versions of Linux are, in fact, free for you to use.
But just because you get to use it for free, doesn't mean you get to see
the underlying source code or modify it for your own purposes.
Free as in speech refers to your rights or liberties with the software.
You're free to run the software how you like, see how the software works,
redistribute the software, and improve upon or modify the software.
This latter definition, free as in speech, is how Linux became so popular.
There are literally hundreds of versions or distributions of Linux available.
And it's because of this latter definition of freedom,
that this became possible.
So with all these different versions of Linux available,
how do you pick the right one?

## Intro to Distributions
There are many different distributions of Linux out there for
you to choose from.
So how do you make the right choice?
First, you need to understand exactly what a distribution is and
the ways in which they can differ from one another.
Because Linux is free as in speech, people are free to make a variety of
choices when they decide to create their own distribution.
They can choose what software to include,
how that software should be updated, how the community makes contributions, and
even how that particular distribution can be shared with others.
For example, Red Hat Enterprise Linux is a popular distribution for enterprises.
This particular distribution is not free as in beer.
Companies have to pay a licensing fee.
In return for that payment, they have the right to use the software and
receive support from Red Hat.
Ubuntu is another popular distribution that itself has various versions.
Some tailored towards servers, others for desktops, and even mobile phones.
Ubuntu receives consistent updates to it's software,
which is how it differs from it's parent distribution Debian.
Debian is known for it's stability and reliability.
Many Debian servers have been up and
running for years without requiring a reboot.
For this reason its software updates cycle is very slow
when compared to others.

## Getting Started with Vagrant
In this course we’ll be working with Ubuntu. It’s an excellent distribution for a variety of use cases, including web servers. We’ll run our Ubuntu server within a virtual machine, which is a special piece of software running on your computer that acts as if it is a stand-alone computer.

To accomplish this requires a bit of setup but will give everyone the same Linux environment to work within, even if you’re on Windows or OSX currently.

### Required Software
If you've already downloaded and installed these items, perhaps while completing a different course, you do not need to download and install these items again.

1. Download and install [VirtualBox](https://www.virtualbox.org/wiki/Download_Old_Builds_5_1). This is free software that will run the virtual machine.
2. Download and install [Vagrant](https://www.vagrantup.com/). This is an command line utility that makes it easy to manage and access your virtual machines.

> Note: Currently (October 2017), the version of VirtualBox you will want is 5.1. Newer versions do not yet support Vagrant.

### Course Environment
Follow these steps to setup an environment where you can work on this course:

1. Create a new folder on your computer where you’ll store your work for this course, then open that folder within your terminal.
2. Type `vagrant init ubuntu/trusty64` to tell Vagrant what kind of Linux virtual machine you would like to run.
3. Type `vagrant up` to download and start running the virtual machine

This last step could take some time since the virtual machine files can be quite large. While you're waiting for it to download, feel free to continue with this course!

## Linux Distribution Comparison
Let's continue to compare a few different Linux distributions and
identify their target markets.
On the left I have provided four different and unique distributions.
Red Hat, Ubuntu, Linux Mint and CoreOS.
On the right, are four use cases.
Match each letter with the use case.
You may need to do a bit of research on your own before tackling this.
So, I've provided some links to a variety of resources
in the instructor notes.

each of these distributions targets a
unique population of users and use cases
redhat is focused on large enterprises
and corporate customers that require
support you bun two focuses on ease of
use on servers desktops laptops among
many others linux mint is for desktop
users and includes proprietary media
support remember it's a modified version
of you bunt to itself finally core OS is
a newer distribution that targets
companies building clusters of
containerized applications

### Instructor Notes
Some places to start your research:

https://distrowatch.com/ — Distro Watch has been around since 2001 as a source of news about Linux distributions and other Free and Open-Source operating systems.

https://en.wikipedia.org/wiki/Comparison_of_Linux_distributions — Wikipedia article comparing current and former Linux distributions.

## Vagrant Commands
We’re now ready to get started working within our Linux virtual machine. If your download hasn’t completed from the initial setup, go ahead and take a break and come back when that has completed. You won’t be able to make further progress until the virtual machine is up and running as much of the course will take place within this environment.

Before we access our machine, let’s quickly review a few commands that vagrant provides to make managing your virtual machines much simpler. Remember, your vagrant machine lives within this specific folder on your computer so make sure you’re within that same folder your created earlier; otherwise these commands won’t work as expected.

* Type `vagrant status`

This command will show you the current status of the virtual machine. It should currently read “default running (virtualbox)” along with some other information.

* Type `vagrant suspend`

This command suspends your virtual machine. All of your work is saved and the machine is put into a “sleep mode” of sorts. The machines state is saved and it’s very quick to stop and start your work. You should use this command if you plan to just take a short break from your work but don’t want to leave the virtual machine running.

* Type `vagrant up`

This gets your virtual machine up and running again. Notice we didn’t have to redownload the virtual machine image, since it’s already been downloaded.

* Type `vagrant ssh`

This command will actually connect to and log you into your virtual machine. Once done you will see a few lines of text showing various performance statistics of the virtual machine along with a new command line prompt that reads vagrant@vagrant-ubuntu-trusty-64:~$

Here are a few other important commands that we’ll discuss but you do not need to practice at this time:

* `vagrant halt`

This command halts your virtual machine. All of your work is saved and the machine is turned off - think of this as “turning the power off”. It’s much slower to stop and start your virtual machine using this command, but it does free up all of your RAM once the machine has been stopped. You should use this command if you plan to take an extended break from your work, like when you are done for the day. The command vagrant up will turn your machine back on and you can continue your work.

* `vagrant destroy`

This command destroys your virtual machine. Your work is not saved, the machine is turned off and forgotten about for the most part. Think of this as formatting the hard drive of a computer. You can always use vagrant up to relaunch the machine but you’ll be left with the baseline Linux installation from the beginning of this course. You should not have to use this command at any time during this course unless, at some point in time, you perform a task on the virtual machine that makes it completely inoperable.

## This is Not Your Computer
Now this course isn't about vagrant or virtual machines.
That was just some overhead work you needed to accomplish
to get to this point.
You're now logged into a Linux box.
Whenever you get to this prompt, I want you to ignore all of that
virtual machines and vagrant stuff as much as possible.
Yes technically this computer is just a virtual machine sitting on
your computer.
But that's not too different than what you'll be doing as you start setting up
your own web servers.
Most likely you'll be given a virtual machine from a service
provider like Amazon.
And you're log in to it via SSH.
This experience is pretty much the same as what you have configured now
on your computer.
You are remotely connected to a completely different computer.
What does that mean?
You can do anything here on this machine.
And it will have no lasting impact on your personal computer.
Remember, this is an entirely different computer.
You can turn it off.
Throw it away.
Rebuild it any time you want.
So I want you to have no fear when SSHed into that computer.
You will not break anything on your computer.
Now, let's get comfortable with this new computer, your Linux virtual machine.
And see how it organizes all of the files you'll be working with.

## Where are we
Since we're working from a command line only,
we don't have a graphical interface,
it only makes sense that we're currently residing in some place on this computer.
We're within some directory in which whatever we type will be executed from.
This is called our working directory.
Whenever you log into a Linux machine you're automatically placed in your
user's home directory.
We can confirm this by typing the command, pwd.
As you can see, the result of this is /home/vagrant.
Let's unpack this a little bit.
The slash is the root level of the file system.
It's the absolute highest you can go in a Linux file system.
Everything on the machine is in some way,
a child of the route level, usually through a variety of other directories.
Home is a directory you'll find within all Linux systems, and
it houses all the home directories of each user with a few exceptions.
If we cd into this directory and
then list its contents, we'll see that there is a directory for
each user on this machine, including our current user, vagrant.
So let's go back into our own home directory and see what's there.
This is our personal space to store stuff, but
the operating system has already placed a few files there for us.
If we just run ls we won't get any results, so
we'll need to provide a few flags to ls to modify it's behavior.
We'll add the -a flag,
which tells it to show all the files, including hidden ones.
On a Linux system, any file that begins with a dot is considered a hidden file.
We're going to add one more flag to the ls command.
That is the l flag, which will list the results in long format, and
provide a bit more information.
Now, there's a lot of info here, and we'll eventually go over most of it.
For now, I want you to just focus on the first character and
the names themselves.
If the first character is a d, that's a directory.
If it's a dash, that's a file.
So you can see here that the .ssh and .cache are both directories.
The rest of these are files.

## Your Home Directory
Let's take what we've learned thus far about the Linux file system,
particularly our home directory, and answer a few questions.
Provide the full path to the directory you started in and
also provide the full path to one of the files within this directory.
Remember, a full path must start at the top-most root level,
which means it will begin with the slash character

You start in your home directory.
So the full path /home/vagrant is the correct enter here.
The full path to a file within this directory could be
/home/vagrant/.bash_logout.
You could've also used the file .bashrc, or the file .profile.
If you're interested in learning more about what these files actually do,
look at the instructor notes.

### Instructor Notes
A full path is also referred to as an absolute path.

[Bash manual: Bash Startup Files](http://www.gnu.org/software/bash/manual/html_node/Bash-Startup-Files.html)


## Users Home Directory
Now that you know all about your own home directory,
let's imagine that you've created a new user named student.
What would the full path to that user's home directory be?

All users home directories are stored within these slash home directory.
So a user named student would have a home directory of /home/student.

## Other Important Directories
So you're all comfortable with your home directory, but
surely there's more to this computer than just that.
Right?
Oh yeah, there is a lot more.
So let's start exploring some of the other areas of the Linux
operating system.
We'll do this by cding to the top level root folder with cd /.
If we ls -al this directory, we'll see that there's a lot of content here.
We're definitely not going to cover all of these, but
we'll discuss the most important folders.
We're already familiar with home, but there are two other important
directories where you'll be making lots of changes and editing files.
Etc is where configuration files live.
As we start setting up our web and
database server, we'll be modifying some files within this directory.
Var is for variable files.
Which is kind of an odd name.
Variable files are simply files that you expect to grow or
change in size over time.
You'll typically find system and application logs within this directory.
There are a few other directories that are that are important for you to know,
but you probably won't be modifying or directly interacting with them.
Bin is where executable binaries are stored,
that are accessible by all users.
These are applications that you run,
like the LS command we've used a few times already.
If you were to list the contents of this directory,
you would actually see there's a file called LS within it.
SBin is very similar to bin, except that these binaries are to only be
used by the route user for system administration and maintenance purposes.
We'll discuss some of the applications within this directory a bit later.
Lib is for
libraries that support the binaries that are located around the system.
Finally, usr is for user programs.
This could seem a bit confusing compared to the bin directory.
The difference isn't that important.
The only difference really is that the binaries within bin are required for
a boot-up and system maintenance processes,
and the binaries in usr necessarily aren't required for that.

## Traversing the File System
Now that you're familiar with the most important directories on any Linux file
system, in which directory would you find system management applications
that are not normally used by standard users?
You would find these system management applications within the /sbin directory.

## Understanding $PATH
We've used the LS command or application a few times already, and
we know that it's located within the slash bin directory, but
how come we didn't have to type the full path to this file to run it?
Why didn't we have to type /bin/ls?
Linux systems provide a nice little short cut system within the dollar sign
path variable.
Let's take a look at that and
figure out how the operating system saves us some typing.
If you type echo $PATH and you run that,
you're presented with a bunch of paths separated by colon characters.
We see /usr/local/sbin:/usr/local/bin and on and on and on.
These are actually the directories Linux will progress through looking for
a binary when you just type the name of it like ls.
When you type ls, the operating system checks the first directory for
an executable file names ls.
If it's not there, it checks the next.
And on and on and on until it gets here to /bin.
And it does find that file, so it runs it.
If you ever find that your commands aren't being found, or
things are just acting really crazy, you might want to check this variable.
I've placed a link in the instructor notes that will walk you through how to
edit this variable and save it if need be.

[AskUbuntu: How to Update $PATH](http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path)

## Outro
Now that you're pretty comfortable with your shiny new Linux machine,
it's time to get your hands dirty, and really start working with it.
In the next lesson, you'll start addressing some security concerns.
You'll work with user management, authentication, file permissions,
firewalls, and software updates.
It's going to be a lot of material, but it's super important, not only for
your users, but the Internet as a whole.
You're about to unleash your very own server to the internet, and
anyone in the world, at any time is going to be able to talk to it.

