# Pipes and Filters

Now that we know a few basic commands,
we can finally look at the shell's most powerful feature:
the ease with which it lets us combine existing programs in new ways.
We'll start with a directory called `molecules`
that contains six files describing some simple organic molecules.
The `.pdb` extension indicates that these files are in Protein Data Bank format,
a simple text format that specifies the type and position of each atom in the molecule.

~~~
$ ls molecules
~~~

~~~
cubane.pdb    ethane.pdb    methane.pdb
octane.pdb    pentane.pdb   propane.pdb
~~~

Let's go into that directory with `cd` and run the command `wc *.pdb`.
`wc` is the "word count" command:
it counts the number of lines, words, and characters in files.
The `*` in `*.pdb` matches zero or more characters,
so the shell turns `*.pdb` into a list of all `.pdb` files in the current directory:

~~~
$ cd molecules
$ wc *.pdb
~~~

~~~
  20  156 1158 cubane.pdb
  12   84  622 ethane.pdb
   9   57  422 methane.pdb
  30  246 1828 octane.pdb
  21  165 1226 pentane.pdb
  15  111  825 propane.pdb
 107  819 6081 total
~~~

## Wildcards

`*` is a **wildcard**. It matches zero or more
characters, so `*.pdb` matches `ethane.pdb`, `propane.pdb`, and every
file that ends with '.pdb'. On the other hand, `p*.pdb` only matches
`pentane.pdb` and `propane.pdb`, because the 'p' at the front only
matches filenames that begin with the letter 'p'.

`?` is also a wildcard, but it only matches a single character. This
means that `p?.pdb` would match `pi.pdb` or `p5.pdb` (if we had these two
files in the `molecules` directory), but not `propane.pdb`.
We can use any number of wildcards at a time: for example, `p*.p?*`
matches anything that starts with a 'p' and ends with '.', 'p', and at
least one more character (since the `?` has to match one character, and
the final `*` can match any number of characters). Thus, `p*.p?*` would
match `preferred.practice`, and even `p.pi` (since the first `*` can
match no characters at all), but not `quality.practice` (doesn't start
with 'p') or `preferred.p` (there isn't at least one character after the
'.p').

When the shell sees a wildcard, it expands the wildcard to create a
list of matching filenames *before* running the command that was
asked for. As an exception, if a wildcard expression does not match
any file, Bash will pass the expression as a parameter to the command
as it is. For example typing `ls *.pdf` in the `molecules` directory
(which contains only files with names ending with `.pdb`) results in
an error message that there is no file called `*.pdf`.
However, generally commands like `wc` and `ls` see the lists of
file names matching these expressions, but not the wildcards
themselves. It is the shell, not the other programs, that deals with
expanding wildcards, and this is another example of orthogonal design.

***

If we run `wc -l` instead of just `wc`,
the output shows only the number of lines per file:

~~~
$ wc -l *.pdb
~~~

~~~
  20  cubane.pdb
  12  ethane.pdb
   9  methane.pdb
  30  octane.pdb
  21  pentane.pdb
  15  propane.pdb
 107  total
~~~

We can also use `-w` to get only the number of words,
or `-c` to get only the number of characters.

Which of these files is shortest?
It's an easy question to answer when there are only six files,
but what if there were 6000?
Our first step toward a solution is to run the command:

~~~
$ wc -l *.pdb > lengths.txt
~~~

The greater than symbol, `>`, tells the shell to **redirect** the command's output
to a file instead of printing it to the screen. (This is why there is no screen output:
everything that `wc` would have printed has gone into the
file `lengths.txt` instead.)  The shell will create
the file if it doesn't exist. If the file exists, it will be
silently overwritten, which may lead to data loss and thus requires
some caution.
`ls lengths.txt` confirms that the file exists:

~~~
$ ls lengths.txt
~~~

~~~
lengths.txt
~~~

We can now send the content of `lengths.txt` to the screen using `cat lengths.txt`.
`cat` stands for "concatenate":
it prints the contents of files one after another.
There's only one file in this case,
so `cat` just shows us what it contains:

~~~
$ cat lengths.txt
~~~

~~~
  20  cubane.pdb
  12  ethane.pdb
   9  methane.pdb
  30  octane.pdb
  21  pentane.pdb
  15  propane.pdb
 107  total
~~~

## Output Page by Page

We'll continue to use `cat` in this lesson, for convenience and consistency,
but it has the disadvantage that it always dumps the whole file onto your screen.
More useful in practice is the command `less`,
which you use with `$ less lengths.txt`.
This displays a screenful of the file, and then stops.
You can go forward one screenful by pressing the spacebar,
or back one by pressing `b`.  Press `q` to quit.
