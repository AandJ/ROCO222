# Monday 25th of September  
## What is Markdown  
Markdown is a lightweight markup language, it is a text to HTML conversion tool which makes code easier to read and understand.

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
__LS__ - lists the contents of the current directory

__cd /tmp__ - Sets the directory to a tempary file location

__cd $HOME__ - sets the save directory to home

__mkdir__ - makes a new directory(folder)

__echo "Hello" > hello.md__ - creates a file called "hello.md" containing the contents of the quote marks

__cat hello.md__ - reads the contents of "hello.md"

__cp hello.md hello-again.md__ - copys the contents of the first file to the new second file.

__mv hello-again.md hello-hello.md__ - renames the hello-agian as hello-hello

__rm hello.md__ - removes the file hello.md

__rm -rf__ - rm removes directory -r moves directory and their contents recursively -f ignores nonexistent files and arguments

__cat/proc/cpuinfo__ - reads the cpu info and prints to terminal

__ls -al__ - list contents of directory including hidden files

__git init__ - creates git repository

__git config user.name "FirstName Surname"__ - tells git your user name
__git config user.email "email"__ - tells git your email

__git commit__ - creates a commit
__git log__ - shows previous commits

__git add <FILE>__ - add new file to the .git repository

## Pushing git online
__git remote add origin https://github.com/<UserName>/<RepositoryName>.git__ - states location of repository on github  
__git push -u origin master__ - pushes repository online  
__git pull origin master__ - pull the repository from github, used to update if a second contributer has modified the repository.

## Navigation
__Introduction to markdown and GIT__
***
[Making a Mottor](https://github.com/AandJ/ROCO222/blob/master/journal-2.md)
***
[Making a robotic Arm](https://github.com/AandJ/ROCO222/blob/master/journal-3.md)
