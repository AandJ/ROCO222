# Monday 25th of September  
## What is Markdown  
Markdown is a lightweight markup language, it is a text to HTML conversion tool which makes code easeir to read and understand.

## Markdown syntax

#-Heading

##-Sub-heading

###-Another deeper heading

Two spaces at the end of a line leave a  
line break.

Text attributes _italic_, *italic*, __bold__, **bold**, `monospace`.

To begin i learnt the basic syntax for a markdown document which i have used to format this page, i then using the terminal entered some basic commands to figure out what they do. 
 
## Commands.  
_LS_ - lists the contents of the current directory

_cd /tmp_ - Sets the directory to a tempary file location

_cd $HOME_ - sets the save directory to home

_mkdir_ - makes a new directory(folder)

_echo "Hello" > hello.md_ - creates a file called "hello.md" containing the contents of the quote marks

_cat hello.md_ - reads the contents of "hello.md"

_cp hello.md hello-again.md_ - copys the contents of the first file to the new second file.

_mv hello-again.md hello-hello.md_ - renames the hello-agian as hello-hello

_rm hello.md_ - removes the file hello.md

_rm -rf_ - rm removes directory -r moves directory and their contents recursively -f ignores nonexistent files and arguments

_cat/proc/cpuinfo_ - reads the cpu info and prints to terminal

_ls -al_ - list contents of directory including hidden files

_git init_ - creates git repository

_git config user.name "FirstName Surname"_ - tells git your user name
_git config user.email "email"_ - tells git your email

_git commit <File>_ - creates a commit
_git log_ - shows previous commits

## Pushing git online
_git remote add origin https://github.com/<UserName>/<RepositoryName>.git_ - states location of repository on github
_git push -u origin master_ - pushes repository online

# Thursday 5th of October  
## Making a Motor  
first we used the adheasice copper tape to cover one end of the cork to create a surphase for the brushes to interract with.
we used aproximatly 10M of copper wire to wind around the cork, this total 111 turns.
we measured the resistance of this to be 5.6 ohms.

![Image of motor](https://raw.githubusercontent.com/AandJ/ROCO222/blob/master/ROCO222_IMG/041.JPG "Image of motor")

## Improved Motor
To improve upon the motot we desided we would use more coils of wire, the benefit to this is than with more than one coil the motor 
will be able to start spinning from any position whearas with a single coil no torque will be produced when the wires are at 
90 degrees to the magnet. Another benefit to more coils is that the torque is produced at a more constant rate, this means that
the more coils you have the less the torwue varies.  We decided to only use 60 windings of wire per coil rather than the previous 111,
this is because we need to make sure the wires fit arround the motor.

![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/blob/master/ROCO222_IMG/006.JPG "Image of improved motor")
![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/blob/master/ROCO222_IMG/008.JPG "Image of improved motor")

We also designed an improved stand to hold the motor so that its rotation would be more uniform, we decided to 3D print the stand as it allowed us a more comple shape,
we also chose 3D printing over other options as it is something we had not done before and we wished to gain experience with the technique.

![Image of improved stand design](https://raw.githubusercontent.com/AandJ/ROCO222/blob/master/ROCO222_IMG/001.JPG "Image of improved stand design")
![Image of improved stand](https://raw.githubusercontent.com/AandJ/ROCO222/blob/master/ROCO222_IMG/016.JPG "Image of improved stand")
