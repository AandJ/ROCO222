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

![Image of motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/041.JPG "Image of motor")
#Video of motor

## Improved Motor
To improve upon the motot we desided we would use more coils of wire, the benefit to this is than with more than one coil the motor 
will be able to start spinning from any position whearas with a single coil no torque will be produced when the wires are at 
90 degrees to the magnet. Another benefit to more coils is that the torque is produced at a more constant rate, this means that
the more coils you have the less the torwue varies.  We decided to only use 60 windings of wire per coil rather than the previous 111,
this is because we need to make sure the wires fit arround the motor.

![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/006.JPG "Image 1 of improved motor")
![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/008.JPG "Image 2 of improved motor")

We also designed an improved stand to hold the motor so that its rotation would be more uniform, we decided to 3D print the stand as it allowed us a more complex shape,
we also chose 3D printing over other options as it is something we had not done before and we wished to gain experience with the technique.

![Image of improved stand design](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/001.JPG "Image of improved stand design")
![Image of improved stand](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/016.JPG "Image of improved stand")

Once all the componets had been printed we assembled the motor, we set up the brushes and ran the motor to check that it spins.

![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/3-2.JPG "Image of improved motor")
#video of motor 2

it was vissible that the motor span significantly faster than the previous design. To confirm this we built and encoder which would allow us to determine the speed at which our motor span, we used an arduino and a circular disk with a slot cut out to measure the number of times a beam of light was broken, the result would then be output to a terminal. we used the arduino line plotter feature to give us a graph of motor speed.

![Image of encoder testing](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/3-1.JPG "Image of encoder testing")
![Image of encoder testing](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/3-4.JPG "Image of encoder testing")

# Monday 18th of December
## Making a ROBOT ARM
We decided to have four degrees of motion, one to rotate the entire base, one for each limb, as well as a gripper. we decided to 3d print the model as we would have an
intricate design for the base and gripper.

#INSERT PIC OF ASSEMBLED ARM

#insert pic of prineted arm

to control this with the ROS sfotware we needed to create a URDF description file of our design, in this file we descriped each link and joint.
a link defenition is shown below  

#pic of link urdf

first we define a name for our link, then for the geometric shape we reference the stl files as a mesh, this accesses our 3d design file so that rviz has the exact shape of our robot,
I also define a material which I have created in the URDF file so that each link is the correct color, finaly I define the origin of the link, the origin is based around the joint that
conects that link to its parent link, for the first link (base_lower) the origin is based around the centre of rviz, I had to adjust the origin due to our artistic design so that this
was also centered. We also had to define the joints in the URDF files, a joint defenition is shown below.

#pic of joint urdf

Once again we have to define a name for the joint, then we can define its type, the types can be revolute which allow for 1 degree of motion around an axis with limits, continous which
allows for 1 degree of motion around the axis without limits, prismatic which is a sliding joint along an axis with set limits, fixed which doesn not allow any movement, floating which
allows movements in all 6 degrees, and planar which allows movement in the plane perpendicular to the axis.
We also need to define the axis in which it rotates aswell as its limit, in the limit we have to defien the effort which is the maximum force that can be applied, we also define the lower
and upper limit which dictates how much the joint can roate, finaly we define velocity which sets the maximum velocity at which the joint can roate. We also have to define the parent and child of the joint, the parent is the link that the joint attaches to and the child is the link it moves. we also have to define the origin of the link. in the case of the gripper we set the joint for the second gear to mimic the first gear, this code is shown below.

#pic of joint mimic

The complete rviz product is shown in the video below

![RVIZ Screen grab](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/RVIZ-SCREENGRAB.PNG "RVIZ Screen grab")
#video of arm

