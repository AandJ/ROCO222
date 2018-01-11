# Monday 25th of September  
## What is Markdown  
Markdown is a lightweight markup language, it is a text to HTML conversion tool and a plain text formatting syntax which makes code easier to read and understand.

## Markdown syntax

```md
# Heading

## Sub-heading

### Another deeper heading

[Hyper Link](http://PAGE-ADRESS.com)

[Image Name](Image_Path ADRESS.JPG "ALT TEXT")

<a href="https://www.youtube.com/watch?v=Video_ID" target="_blank"><img src="http://img.youtube.com/vi/Video_ID/0.jpg" alt="ALT TEXT" width="640" height="360" border="0" /></a>

_italic_, *italic*, __bold__, **bold**, `monospace`,~~Crossed out~~.
```
Two spaces at the end of a line leave a  
line break.

To begin I learnt the basic syntax for a markdown document which I have used to format this page, I then using the terminal entered some basic commands to figure out what they do. 
 
## Commands.  
`LS` - lists the contents of the current directory

`cd /tmp` - Sets the directory to a temporary file location

`cd $HOME` - sets the save directory to home

`mkdir` - makes a new directory(folder)

`echo "Hello" > hello.md` - creates a file called "hello.md" containing the contents of the quote marks

`cat hello.md` - reads the contents of "hello.md"

`cp hello.md hello-again.md` - copies the contents of the first file to the new second file

`mv hello-again.md hello-hello.md` - renames the hello-again as hello-hello

`rm hello.md` - removes the file hello.md

`rm -rf` - rm removes directory -r moves directory and their contents recursively -f ignores non-existent files and arguments

`cat/proc/cpuinfo` - reads the cpu info and prints to terminal

`ls -al` - list contents of directory including hidden files

`git init` - creates git repository

`git config user.name "FirstName Surname"` - tells git your user name
`git config user.email "email"` - tells git your email

`git commit` - creates a commit
`git log` - shows previous commits

`git add <FILE>` - add new file to the .git repository

## Pushing git online
`git remote add origin https://github.com/<UserName>/<RepositoryName>.git` - states location of repository on github  
`git push -u origin master` - pushes repository online  
`git pull origin master` - pull the repository from github, used to update if a second contributor has modified the repository

## Navigation
__Introduction to markdown and GIT__
***
[Making a Motor](https://github.com/AandJ/ROCO222/blob/master/journal-2.md)
***
[Making a robotic Arm](https://github.com/AandJ/ROCO222/blob/master/journal-3.md)
