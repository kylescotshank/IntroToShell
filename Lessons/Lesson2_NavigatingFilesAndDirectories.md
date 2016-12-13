# Navigating Files and Directories



The part of the operating system responsible for managing files and directories is called the **file system**. It organizes our data into files, which hold information, and directories (also called "folders"), which hold files or other directories.

Several commands are frequently used to create, inspect, rename, and delete files and directories.
To start exploring them, let's open a shell window. When you have, you'll likely see a prompt with this:

~~~
$
~~~

The dollar sign is a **prompt**, which shows us that the shell is waiting for input. When typing commands, either from these lessons or from other sources, do not type the prompt, only the commands that follow it.

Let's try our first bit of interaction. Type the command `whoami`, then press the Enter key (sometimes marked Return) to send the command to the shell.
The command's output is the ID of the current user, i.e., it shows us who the shell thinks we are:

~~~
$ whoami
~~~

~~~
kshank
~~~