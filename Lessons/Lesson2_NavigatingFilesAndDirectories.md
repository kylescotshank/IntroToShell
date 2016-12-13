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

On my own machine, the output was as follows:

~~~
kshank
$
~~~

Pretty neat! What happened here? 

When we typed `whoami` the shell performed the following series of commands:

1.  found a program called `whoami`,
2.  ran that program,
3.  displayed that program's output
4.  displayed a new prompt to tell us that it's ready for more commands.

***

Next, let's find out where we are by running a command called `pwd` (which stands for "print working directory"). At any moment, our **current working directory** is our current default directory, i.e., the directory that the computer assumes we want to run commands in unless we explicitly specify something else. On my machine, the computer's response is `/Users/kshank`, which is my **home directory**:

~~~
$ pwd
~~~

~~~
/Users/kshank
~~~

## Home Directory

The home directory path will look different on different operating systems. On Linux it may look like `/home/kshank`, and on Windows it will be similar to `C:\Documents and Settings\nkshank` or `C:\Users\kshank`. (Note that it may look slightly different for different versions of Windows.) In future examples, we've used Mac output as the default - Linux and Windows output may differ slightly, but should be generally similar.  

To understand what a "home directory" is, let's have a look at how the file system as a whole is organized.  For the sake of example, we'll be illustrating the filesystem on our scientist Nelle's computer.  After this illustration, you'll be learning commands to explore your own filesystem, which will be constructed in a similar way, but not be exactly identical.  

On Nelle's computer, the filesystem looks like this:

<p align="center">
<kbd>
  <img src="../Images/directory.png"/>
 </kbd>
 </p>

At the top is the **root directory** that holds everything else. We refer to it using a slash character `/` on its own.

Inside that directory are several other directories: `bin` (which is where some built-in programs are stored), `data` (for miscellaneous data files), `Users` (where users' personal directories are located), `tmp` (for temporary files that don't need to be stored long-term), and so on.  

We know that our current working directory -- in this example, `/Users/nelle` -- is stored inside `/Users` because `/Users` is the first part of its name. Similarly, we know that `/Users` is stored inside the root directory `/` because its name begins with `/`.

Notice that there are two meanings for the `/` character. When it appears at the front of a file or directory name, it refers to the root directory. When it appears *inside* a name, it's just a separator.

## Listing Files

Now let's learn the command that will let us see the contents of our own filesystem.  We can see what's in our home directory by running `ls`, which stands for "listing":

~~~
$ ls
~~~

The output of which (on my machine) looks like this:

~~~
Applications Documents    Library      Music        Public
Desktop      Downloads    Movies       Pictures
~~~

*Note*: Remember =  your results may be slightly different depending on your operating system and how you have customized your filesystem.

`ls` prints the names of the files and directories in the current directory in alphabetical order, arranged neatly into columns. We can make its output more comprehensible by using the **flag** `-F`, which tells `ls` to add a trailing `/` to the names of directories:

~~~
$ ls -F
~~~

~~~
data
papers
personal
~~~

`ls` has lots of other options. To find out what they are, we can type:

~~~
$ ls --help
~~~

The output being:

~~~
Usage: ls [OPTION]... [FILE]...
List information about the FILEs (the current directory by default).
Sort entries alphabetically if none of -cftuvSUX nor --sort is specified.

Mandatory arguments to long options are mandatory for short options too.
  -a, --all                  do not ignore entries starting with .
  -A, --almost-all           do not list implied . and ..
      --author               with -l, print the author of each file
  -b, --escape               print C-style escapes for nongraphic characters
      --block-size=SIZE      scale sizes by SIZE before printing them; e.g.,
                               '--block-size=M' prints sizes in units of
                               1,048,576 bytes; see SIZE format below
  -B, --ignore-backups       do not list implied entries ending with ~
  -c                         with -lt: sort by, and show, ctime (time of last
                               modification of file status information);
                               with -l: show ctime and sort by name;
                               otherwise: sort by ctime, newest first
  -C                         list entries by columns
      --color[=WHEN]         colorize the output; WHEN can be 'always' (default
                               if omitted), 'auto', or 'never'; more info below
  -d, --directory            list directories themselves, not their contents
  -D, --dired                generate output designed for Emacs' dired mode
  -f                         do not sort, enable -aU, disable -ls --color
  -F, --classify             append indicator (one of */=>@|) to entries
      --file-type            likewise, except do not append '*'
      --format=WORD          across -x, commas -m, horizontal -x, long -l,
                               single-column -1, verbose -l, vertical -C
      --full-time            like -l --time-style=full-iso
  -g                         like -l, but do not list owner
      --group-directories-first
                             group directories before files;
                               can be augmented with a --sort option, but any
                               use of --sort=none (-U) disables grouping
  -G, --no-group             in a long listing, don't print group names
  -h, --human-readable       with -l and/or -s, print human readable sizes
                               (e.g., 1K 234M 2G)
      --si                   likewise, but use powers of 1000 not 1024
  -H, --dereference-command-line
                             follow symbolic links listed on the command line
      --dereference-command-line-symlink-to-dir
                             follow each command line symbolic link
                               that points to a directory
      --hide=PATTERN         do not list implied entries matching shell PATTERN
                               (overridden by -a or -A)
      --indicator-style=WORD  append indicator with style WORD to entry names:
                               none (default), slash (-p),
                               file-type (--file-type), classify (-F)
  -i, --inode                print the index number of each file
  -I, --ignore=PATTERN       do not list implied entries matching shell PATTERN
  -k, --kibibytes            default to 1024-byte blocks for disk usage
  -l                         use a long listing format
  -L, --dereference          when showing file information for a symbolic
                               link, show information for the file the link
                               references rather than for the link itself
  -m                         fill width with a comma separated list of entries
  -n, --numeric-uid-gid      like -l, but list numeric user and group IDs
  -N, --literal              print raw entry names (don't treat e.g. control
                               characters specially)
  -o                         like -l, but do not list group information
  -p, --indicator-style=slash
                             append / indicator to directories
  -q, --hide-control-chars   print ? instead of nongraphic characters
      --show-control-chars   show nongraphic characters as-is (the default,
                               unless program is 'ls' and output is a terminal)
  -Q, --quote-name           enclose entry names in double quotes
      --quoting-style=WORD   use quoting style WORD for entry names:
                               literal, locale, shell, shell-always,
                               shell-escape, shell-escape-always, c, escape
  -r, --reverse              reverse order while sorting
  -R, --recursive            list subdirectories recursively
  -s, --size                 print the allocated size of each file, in blocks
  -S                         sort by file size, largest first
      --sort=WORD            sort by WORD instead of name: none (-U), size (-S),
                               time (-t), version (-v), extension (-X)
      --time=WORD            with -l, show time as WORD instead of default
                               modification time: atime or access or use (-u);
                               ctime or status (-c); also use specified time
                               as sort key if --sort=time (newest first)
      --time-style=STYLE     with -l, show times using style STYLE:
                               full-iso, long-iso, iso, locale, or +FORMAT;
                               FORMAT is interpreted like in 'date'; if FORMAT
                               is FORMAT1<newline>FORMAT2, then FORMAT1 applies
                               to non-recent files and FORMAT2 to recent files;
                               if STYLE is prefixed with 'posix-', STYLE
                               takes effect only outside the POSIX locale
  -t                         sort by modification time, newest first
  -T, --tabsize=COLS         assume tab stops at each COLS instead of 8
  -u                         with -lt: sort by, and show, access time;
                               with -l: show access time and sort by name;
                               otherwise: sort by access time, newest first
  -U                         do not sort; list entries in directory order
  -v                         natural sort of (version) numbers within text
  -w, --width=COLS           set output width to COLS.  0 means no limit
  -x                         list entries by lines instead of by columns
  -X                         sort alphabetically by entry extension
  -Z, --context              print any security context of each file
  -1                         list one file per line.  Avoid '\n' with -q or -b
      --help     display this help and exit
      --version  output version information and exit

The SIZE argument is an integer and optional unit (example: 10K is 10*1024).
Units are K,M,G,T,P,E,Z,Y (powers of 1024) or KB,MB,... (powers of 1000).

Using color to distinguish file types is disabled both by default and
with --color=never.  With --color=auto, ls emits color codes only when
standard output is connected to a terminal.  The LS_COLORS environment
variable can change the settings.  Use the dircolors command to set it.

Exit status:
 0  if OK,
 1  if minor problems (e.g., cannot access subdirectory),
 2  if serious trouble (e.g., cannot access command-line argument).

GNU coreutils online help: <http://www.gnu.org/software/coreutils/>
Full documentation at: <http://www.gnu.org/software/coreutils/ls>
or available locally via: info '(coreutils) ls invocation'
~~~

Whew! That's a lot to take in. Many bash commands, and programs that people have written that can be run from within bash, support a `--help` flag to display more information on how to use the commands or programs.

For more information on how to use `ls` we can type `man ls`. `man` is the Unix "manual" command: it prints a description of a command and its options, and (if you're lucky) provides a few examples of how to use it.

To navigate through the `man` pages, you may use the up and down arrow keys to move line-by-line, or try the "b" and spacebar keys to skip up and down by full page. Quit the `man` pages by typing "q".

Here, we can see that our home directory contains mostly **sub-directories**. Any names in your output that don't have trailing slashes, are plain old **files**. And note that there is a space between `ls` and `-F`: without it, the shell thinks we're trying to run a command called `ls-F`, which doesn't exist.

We can also use `ls` to see the contents of a different directory.  Let's take a look at our `Desktop` directory by running `ls -F Desktop`, i.e.,
the command `ls` with the **arguments** `-F` and `Desktop`. The second argument --- the one *without* a leading dash --- tells `ls` that
we want a listing of something other than our current working directory:

~~~
$ ls -F Desktop
~~~

~~~
data/
papers/
personal/
~~~

Your output should be a list of all the files and sub-directories on your Desktop. Take a look at your Desktop to confirm that
your output is accurate.  

As you may now see, using a bash shell is strongly dependent on the idea that your files are organized in an hierarchical file system.  
Organizing things hierarchically in this way helps us keep track of our work: it's possible to put hundreds of files in our home directory, just as it's possible to pile hundreds of printed papers on our desk, but it's a self-defeating strategy.

## Changing Directories

We now know how to look at the contents of a folder, we can learn how to change directories. 

The command to change locations is `cd` followed by a directory name to change our working directory. `cd` stands for "change directory", which is a bit misleading: the command doesn't change the directory, it changes the shell's idea of what directory we are in.

Let's say we want to move to the `data/` directory we saw above.  We can use the following series of commands to get there:

~~~
$ cd Desktop
$ cd data
~~~

These commands will move us from our home directory onto our Desktop, then into the `data` directory. `cd` doesn't print anything, but if we run `pwd` after it, we can see that we are now.

~~~
$ pwd
~~~

~~~
/Users/kshank/Desktop/data
~~~

And now we can take a peek around:

~~~
$ ls -F
~~~

~~~
amino-acids.txt   elements/     pdb/          salmon.txt
animals.txt       morse.txt     planets.txt     sunspot.txt
~~~

Great! You can see that the directory contains several files and sub-directories. Now that we know how to go **down** a directory, how do we go **up**? We might first try the following:

~~~
cd Desktop
~~~

~~~
-bash: cd: data: No such file or directory
~~~

Huh! We get an error.  Why is this?  

With our methods so far, `cd` can only see sub-directories inside your current directory. It thus looked for a directory called `Desktop` inside of `data`, which doesn't exist.  There are different ways to see directories above your current location; we'll start with the simplest.  

There is a shortcut in the shell to move up one directory level that looks like this:

~~~
$ cd ..
~~~

`..` is a special directory name meaning "the directory containing this one", or more succinctly, the **parent** of the current directory. Sure enough, if we run `pwd` after running `cd ..`, we're back in `/Users/kshank/Desktop/`:

~~~
$ pwd
~~~

~~~
/Users/kshank/Desktop
~~~

The special directory `..` doesn't usually show up when we run `ls`.  If we want to display it, we can give `ls` the `-a` flag:

~~~
$ ls -F -a
~~~

~~~
./                  .secret/         papers/
../                 data/            personal/
~~~