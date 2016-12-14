# Working with Files and Directories

<p align="center">
<kbd>
  <img src="https://github.com/kylescotshank/IntroToShell/blob/master/Images/linux-from-scratch.jpg"/>
</kbd>
</p>


We now know how to explore files and directories,
but how do we create them in the first place? Let's learn how to build things! 

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

## Good names for files and directories

Complicated names of files and directories can make your life very painful
when working on the command line. Here we provide a few useful
tips for the names of your files from now on.

  1. Don't use whitespaces.

    White spaces can make a name more meaningful
    but since whitespace is used to break arguments on the command line
    is better to avoid them on name of files and directories.
    You can use `-` or `_` instead of whitespace.

  2. Don't begin the name with `-` (dash).

    Commands treat names starting with `-` as options.

  3. Stick with letters, numbers, `.` (period), `-` (dash) and `_` (underscore).

    Many other characters have a special meaning on the command line
    that we will learn during this lesson. Some will only make your command not work,
    but some of them may even cause you to lose some data!

 If you need to refer to names of files or directories that have whitespace
 or another non-alphanumeric character, you should surround the name in quotes (`""`).

***

Let's change our working directory to `thesis` using `cd`,
then run a text editor called Nano to create a file called `draft.txt`:

~~~
$ cd thesis
$ nano draft.txt
~~~

## Which Editor?

When we say, "`nano` is a text editor," we really do mean "text": it can
only work with plain character data, not tables, images, or any other
human-friendly media. We use it in examples because almost anyone can
drive it anywhere without training, but please use something more
powerful for real work. On Unix systems (such as Linux and Mac OS X),
many programmers use [Emacs](http://www.gnu.org/software/emacs/) or
[Vim](http://www.vim.org/) (both of which are completely unintuitive,
even by Unix standards), or a graphical editor such as
[Gedit](http://projects.gnome.org/gedit/). On Windows, you may wish to
use [Notepad++](http://notepad-plus-plus.org/).  I recommend [Sublime Text](https://www.sublimetext.com) if you plan on becoming a code junky.
Windows also has a built-in editor called `notepad` that can be run from the command line in the same
way as `nano` for the purposes of this lesson.  

No matter what editor you use, you will need to know where it searches
for and saves files. If you start it from the shell, it will (probably)
use your current working directory as its default location. If you use
your computer's start menu, it may want to save files in your desktop or
documents directory instead. You can change this by navigating to
another directory the first time you "Save As..."

***

Let's type in a few lines of text.
Once we're happy with our text, we can press `Ctrl-O` (press the Ctrl or Control key and, while
holding it down, press the O key) to write our data to disk
(we'll be asked what file we want to save this to:
press Return to accept the suggested default of `draft.txt`).

![Nano in Action](https://github.com/swcarpentry/shell-novice/blob/gh-pages/fig/nano-screenshot.png?raw=true)

[Next: Lesson 2 - Navigating Files and Directories](https://github.com/kylescotshank/IntroToShell/blob/master/Lessons/Lesson2_NavigatingFilesAndDirectories.md)