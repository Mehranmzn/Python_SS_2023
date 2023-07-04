# Setup Git repository and basic commands

## Content
[[_TOC_]]

## The example
To illustrate all commands and concepts, we will be using an example for these
tutorials. The example will be the git repository of this tutorial. 
Not every file in this repository or step to create the repository as you
see it now will be illustrated, but the concepts will be explained using
this repository as an example.

Now, let's begin!

## What is Git?
Git is a distributed version control system (VCS). 
Everytime you save something to the git repository, git takes a snapshot of 
your files. If some files were not modified since the last snapshot, git will 
link to the previous snapshot for that file, saving time and space.

Git is a distributed VCS, meaning every clone of the repository includes 
the complete history. 
This means you can work practically offline on everything and an internet 
connection is necessary for very few actions.

Another great advantage of git is that everythins is checksummed (this 
string of numbers and letters you see all the time when working with git). 
A checksum can be used to check changes in a file and therefore, 
you cannot make changes unnoticed, because everything is checksummed.

Read more about [version control systems](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control) and [git](https://git-scm.com/book/en/v2/Getting-Started-What-is-Git%3F).

## Setup
To setup a git repository in the command line, 
you should execute the following commands:
```bash
# Move to the location of the directory you want to start a git repository in
$ cd ~/Documents

# Create the directory and move into the directory
$ mkdir git_tutorial
$ cd git_tutorial/

# Check the content of the directory (including hidden files)
$ ls -a

# Initialise the git repository
$ git init

# Check that a hidden directory was created
$ ls -a
```

> :exclamation: Note: code lines preceded by `$` are actual bash commands

The command `git init` will create a hidden `.git` directory. 
The process is illustrated in the below video, 
which you can watch by clicking on the image.
|[![Initialise git repository video](img/init.png)](https://www.youtube.com/watch?v=5YXaTOT1O8I)
|:--:|
|*Initialise the git repository - click on the image to see the video*|

## The basic commands
In the previous step, a hidden git directory was created.
However, nothing is changed yet, because we need to tell git what files it 
should track. After creating the directory and initialising the git
repository, we have created the `README.md` for this repository, which 
explains more about the content of this repository.
Using the following commands, we will start tracking this file:
```bash
# Check for any changes
$ git status

# Start tracking the modified file
$ git add README.md

# Check if there is other changes
$ git status

# Take the snapshot, file will now be saved into history
$ git commit -m "Created README"
```

We will explain the separate commands in greater detail now.

### git status
This command is probably the most used and a very useful command. 
It tells you the status of your git repository in this local copy.
This all sounds very logical, and that is pretty often with the git commands,
they are usually very straightforward, fortunately.

So by running `git status` you might see something like this:
```bash
On branch main

No commits yet

Untracked files:
  (use "git add <file>..." to include in what will be committed)
        README.md

nothing added to commit but untracked files present (use "git add" to track)
```
It tells you on what branch you are (we'll explain this in the 
[branches tutorial](branches.md)) and whether you have made any commits since you last 
pushed (this will be explained in the [Working with a remote tutorial](remote.md)). 
Then, and that is the important part for now, it will also tell you what
changes you have made since your last commit and gives you hints on the
actions you could perform. In this particular case it explains us that we
have added the `README.md` file, but we are not tracking it. 
Therefore it suggests us to use the `git add <file>` command to start
tracking the file. That is what we will be doing then.

### git add
As we already saw before, this command tells git to start tracking the file
specified at the end of the command.
However, after a file is tracked for the first time, you will still be 
using this command everytime you change the files. This is better explained
with the following image:
|![The git concept](img/concept.png)
|:--:|
|*The concept of a git repository*|

This image explains the three "areas" your files can be. The first, the 
*Working Directory* is, as the name suggests, your directory. 
The second, the *Staging Area*, is the area where git tracks modified files.
The third, the *.git directory* is the git repository, where the git history
is saved. By executing `git add README.md` the file `README.md` will be moved
to the staging area (it is therefore *staged*). This means, the next time you
will run `git commit` the snapshot will include this file, but not any other
files present *only* in the working directory.

### git commit
The `git commit` command will move the file that was just added to the staging
area to the actual git repository as indicated in the image above. This means 
that the snapshot is now taken and the files from the staging are saved to 
history. This command requires a message from you: a short description of what
you have done. If you run the command without any option, it will therefore
open a text editor where you are asked to insert a commit message. Another,
quicker way, would be to include the `-m` option and write the message 
after that, for example:
```bash
$ git commit -m "Created README"
```

## The process
To see the commands in action, watch the video below:
|[![Basic commands video](img/add_commit.png)](https://www.youtube.com/watch?v=jHHyy18eNpM)
|:--:|
|*Take a snapshot of your directory - click on the image to see the video*|

Read more on these commands in the [Git book](https://git-scm.com/book/en/v2/Git-Basics-Recording-Changes-to-the-Repository).

Next: [Working with a remote](remote.md)
