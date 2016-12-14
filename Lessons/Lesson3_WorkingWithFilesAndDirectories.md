# Working with Files and Directories

We now know how to explore files and directories,
but how do we create them in the first place?
Let's go back to our `data` directory on the Desktop
and use `ls -F` to see what it contains:

~~~
$ pwd
~~~

~~~
/Users/kshank/Desktop/data
~~~

~~~
$ ls -F
~~~

~~~
amino-acids.txt   elements/     pdb/          salmon.txt
animals.txt       morse.txt     planets.txt     sunspot.txt
~~~

Let's create a new directory called `thesis` using the command `mkdir thesis`
(which has no output):

~~~
$ mkdir thesis
~~~

As you might guess from its name,
`mkdir` means "make directory".
Since `thesis` is a relative path
(i.e., doesn't have a leading slash),
the new directory is created in the current working directory:

~~~
$ ls -F
~~~

~~~
amino-acids.txt   elements/     pdb/          salmon.txt
animals.txt       morse.txt     planets.txt     sunspot.txt
thesis/
~~~

Using the shell to create a directory is no different than using a file explorer.
If you open the current directory using your operating system's graphical file explorer,
the `thesis` directory will appear there too.
While they are two different ways of interacting with the files,
the files and directories themselves are the same.


[Next: Lesson 2 - Navigating Files and Directories](https://github.com/kylescotshank/IntroToShell/blob/master/Lessons/Lesson2_NavigatingFilesAndDirectories.md)