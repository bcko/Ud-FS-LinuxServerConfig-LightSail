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

