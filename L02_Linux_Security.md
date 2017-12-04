# Linux Security

## Intro to Linux Security
Now that you're going to be putting another computer out there on
the Internet, accessible by anyone, we need to discuss security.
Not only for your own application's sake, but
for everyone else out there as well.
If a bad guy gets access to your server, they can do anything they want with it.
Send spam, launch denial of service attacks, and so much more.
In this lesson we'll discuss a number of security-related topics,
including managing users, packages or
the software installed on the server, various methods of authenticating users,
how Linux manages file permissions, and finally, how to configure a firewall.

## The Rule of Least Privilege
One of the most important rules in security is the rule of least privilege.
Put simply, this means a user or
an application only has enough permission to do its job, nothing extra.
You've already experienced this within your virtual machine,
although you may not be aware of it yet.
When we access our virtual machine, using vagrant ssh.
We're logged in as a standard user named, vagrant.
Let's try running a command only an administrative user would be
allowed to run.
Let's list all of the files with in the ubuntu users ssh directory.
You see, we get this error here, permission denied.
Only the ubuntu user or
the root user can read the files within this directory.
You may be thinking, but I am the administrator of this virtual machine.
I am root.
So how do I actually log in as root?
It's time to learn about super user.

## Becoming a Super User
Since every Linux machine comes with the user name root and
that user is super powerful, they can do anything they want on this machine.
It's very common to disable the ability to remotely log in as root.
Instead, we'll log in as a user we create, and
then we can run individual commands as root by using another command.
This is to make any potential attacker's job a little more difficult
by eliminating the username that they already know exists on this on this box.
Our vagrant virtual machine has already set up the security pattern for us and
many other cloud providers will do this for you, as well.
If not, it's highly advised that this be one of the very first things you do when
you're setting up a new server.
We'll cover exactly how to do that a bit later.
>> Let's run that same command again,
except this time we'll prepend the command with this sudo command here.
Now we see the results.
The pseudo command ran this command as if we were root.

## sudo vs su
It's typically regarded as a best practice that you not
use the SU command.
Why?
The rule of least privilege that we discussed earlier.
Do you really need to switch your entire working context over to the root user
to run a single, or even a few, commands?
What happens if you forget that you are currently within SU?
You could potentially do some extremely damaging operations, and
there's no safety net there to warn you when doing so.
Now, not every user has the ability to work as the superuser.
You have to give that user those permissions specifically.
We'll cover that in more detail when we start adding new users.
For now, you know how to perform operations as the root user, and that's
all we need to start managing software known as packages on this machine.
So let's dive into that a bit.

## Package Source Lists
When you need new software, what do you typically do?
You might visit an app store like this and download it or
you could actually walk into a store and buy a physical copy.
You have a lot of different options.
You might even say you have a list of options.
Now how often have you seen software for Linux sitting up on a store shelf?
Not very often, if at all.
But we still have a list of various places we can go to get software.
This is called a package source list.
Let's take a look.
All of your available package sources are listed in this file
/etc/app/sources.list.
Remember when we were discussing distributions,
we said each one approves and releases packages in their own way and
that's one of the big ways in which they differ.
This is the package's list for your current version of Ubuntu.
As you skim through the file, you'll see some pretty recognizable parts.
We see a URL here and the word trusty looks familiar.
That's the code name for the version of Ubuntu we're running.
We know Ubuntu is also based off of Debian, so
that's probably what this deb stands for here.
This is a list of software repositories that Ubuntu set up for us automatically.
There are a lot in this list and each of these would be referenced
when you try to update or install new software.
Speaking of which, let's go ahead and
make sure that all of our software is up to date.

## Updating Available Package Lists
One of the most important and simplest ways to ensure your system is secure
is to keep your software up to date with new releases.
Because Linux systems focus on reliability and they run a variety of
complex applications that have numerous dependencies of their own, most Linux
distributions do not auto-update the software installed on the system.
You'll need to do this yourself and
test your apps to make sure any recent updates don't break your application.
The first step to upgrading your installed software is to update your
package source list.
We do this with the command sudo apt-get update.
See the sudo there?
We have to run this as the root user.
The update command will run through all of the repositories we saw within our
etc/app/sources.list file, and it will check to see what all software is
available and what those version numbers are.
This command doesn't actually perform any changes to the software
on your system.
It just makes sure your system is aware of the latest information stored
within all of these repositories that you're making use of.

## Upgrading Installed Packages
Now that our system is aware of what all software is available, and the most
recent version numbers, it's now time for us to actually update the software.
We do this with the command, sudo apt-get upgrade.
Once again, we have to use sudo.
Remember this is an administrative task that we have to run as the root user.
After a few seconds, you'll be presented with a list of everything that's going
to change on your system.
And this question, do you want to continue, yes or no?
We'll say yes in a second, but let's review this information real quick.
Here we have a list of packages that will be upgraded.
Some of these names look familiar.
See a name python here, python down here.
But others, not so much.
This early in setting up a new machine, you can be pretty safe in just accepting
that the system is always making the best decisions for you.
Later on, when you actually have your web application running on this system,
and it's serving your users.
You're going to want to take more care in reviewing this list.
And testing everything in a non-production environment
before performing similar operations on your production server.
For now, we'll just hit yes and we'll go take a coffee break as
all of these new versions are downloaded and installed.

## Other Package Related Tasks
The apt get application is your main interface to a ton of package related
functionality.
We can check out everything you can do by reading the man page for
it with this command, man apt get.
We see here it can install packages, it can even remove packages,
it can do all sorts of stuff.
For now, let's see if there are some packages that are no
longer required that we can just automatically remove.
We'll do this with the command apt-get autoremove.
And once again, it's an administrative task that has to be run as root.
So we use sudo.
After a few seconds,
we're returned back to our prompt to let us know everything is all done.
Now let's use apt-get to install new software.
We'll install an application called finger.
It's something we'll use a little bit later on when working with users.
We do this by typing the command apt-get install finger, and
once again using sudo.

## Discovering Packages
So how did I know the package I wanted to install was called Finger?
Most of the time the package names are pretty easy to guess, but
not all the time.
For instance Python has two extremely popular versions,
you have Python 2 and Python 3.
It may be a bit more difficult to figure out what the name of that
package would be.
Fortunately, each distribution tends to publish an easy to browse version
of their repositories.
For Ubuntu, you can search for packages at packages.ubuntu.com.
If I were to search for Python and I look at this top result that says 2.7,
so that's Python version 2.
If I search for Python 3 and
I look at the top result it says 3.40, so I know that's Python version 3.

## Using Package Search
Let's get a bit more practice searching for
packages using Ubuntu's package website.
Use the site to search for the package names for Apache HTTP Server,
PostgreSQL, and Memcache on Ubuntu Trusty.
Enter your answers in these boxes.
You don't need to include the full app to get command, just the package name.

The correct answers are apache2, postgresql, and memcached.

## Using Finger
Now that we've installed Finger, let's use it.
This application will look up various pieces of information about a user, and
display it in an easy to read format.
If I type Finger, the command will output information about
all of the users currently logged into the system.
You can see the vagrant user here, that's us, and
the last time we logged in.
You can also pass a username to the Finger application
to see additional information about a specific user.
Type finger vagrant, and you'll see some additional information
including our home directory and what shell we're using.

## Introduction to /etc/passwd
So where is finger retrieving all of this information such as our user name,
our home directories, the shell?
Much of this information is found within a file that stores information
about each user.
This file is called etc/passwd.
Let's take a look at that file using the cat command.
Each line within this file is an entry for a single user, and
each entry has a number of fields that are separated by colon characters.
Let's find the entry for our current user, vagrant.
The line looks like this,
vagrant:x:1000:1000: :/home/vagrant:/bin/bash.
These two numbers 1000:1000 might be different on your system, but
that's okay.
It's nothing to worry about.
The first field reads vagrant and that's this users username.
The second field used to store encrypted passwords.
Historically storing encrypted passwords in this file wasn't an issue
as the hardware was too slow to crack a well chosen password.
These days, almost every distribution will just insert a character that is
ignored in this field.
In this case, ubuntu uses an x.
The third and fourth field store your user ID and group ID.
We'll discuss these a bit more when we get into talking about file permissions.
There's a fifth field here that may be hard to see since it doesn't include
any text.
It's empty.
This field is used to store a better description about this user.
You can see one user does have a better description here.
Gnat's and then this full description, gnats bug reporting system admin.
The last two fields are the user's home directory and finally,
the user's default shell.
Our home directory is /home/vagrant as we already knew.
And our default shell is bin/bash.

**/etc/passwd**
This is a very important file on your system! It's used to keep track of all users on the system. Run cat /etc/passwd and look at the output; each line is organized in this format:

**username:password:UID:GID:UID info:home directory:command/shell**

Let’s run through what each of those mean:

1. username: the user’s login name
2. password: the password, will simply be an x if it’s encrypted
3. user ID (UID): the user’s ID number in the system. 0 is root, 1-99 are for predefined users, and 100-999 are for other system accounts
4. group ID (GID): Primary group ID, stored in /etc/group.
5. user ID info: Metadata about the user; phone, email, name, etc.
6. home directory: Where the user is sent upon login. Generally /home/
7. command/shell: The absolute path of a command or shell (usually /bin/bash). Does not have to be a shell though!



