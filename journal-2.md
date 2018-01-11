# Thursday 5th of October  
## Electro magneic principles behing a motor
Apere's right hand rule - as current travels through a wire a magnetic field is formed arround it as shown in the picturebelow.
![Ampere's right hand rule](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/Field_Arround_wire.png "Ampere's right hand rule")
![Ampere's right hand rule](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/Field_Arround_wire_2.png "Ampere's right hand rule")
Fleming left hand rule - shows direction of force acting on a straight wire
![Fleming's Left hand rule](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/Left_hand_rule.png "Fleming's Left hand rule")

In a motor we use a coil of wire (a loop) between two magnets, this is shown in the picture below.
![Force on motor coil](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/DC_Motor_Principles.png "Force on motor coil") 
As the current flows through the wire it generates a magnetic field. According to flemings left hand rule a force will eb genrated as shown in the above photo, with current going from the possitive to the negative and with flux going from the N pole to the S pole, as shown in the picture above. This can be applied for both sides of the motor were the coil of wire is close to the other pole of the magnet, since the current is oposite the force is also opisite, shown below.
![Force on motor coil](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/DC_Motor_Principles_2.png "Force on motor coil")

## Making a Motor 
Our first motor willbe made from a cork, two nails, some copper tape, 4 paper clips and 4 neodynium magnets.
First we need to make the commutator, to do this we used the adhesive copper tape to cover one end of the cork to create a surface for the brushes to interact with, we also inserted a nail into either end of the cork to create a shaft. The paper clips were screwed to a wooden base and used to hold the shaft and the magnets as shown in the image below. We used approximately 10M of copper wire to wind around the cork, this cameto a total of 111 turns, each end of the copper wire was soldered to a different half of the copper tape and when one side of the copper tape was conected to the positive of the power supply and the other was conected to the ground it would complete thecircuit around the coil of wire. We measured the resistance of the coil to be 5.6 ohms.

![Image of motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/041.JPG "Image of motor")

### Video
<a href="https://www.youtube.com/watch?v=IyP9AZi4azg" target="_blank"><img src="http://img.youtube.com/vi/IyP9AZi4azg/0.jpg" alt="Video of Motor" width="640" height="360" border="0" /></a>

As our first design was only a single coil the motor would not self start, this is because when the coil is 90 degrees out of phase to the magnets it is unable to generate torque, its torque was also very uneven due to the single coils phase with the magnets. by adding more coils we would make sure that the motor can generate torque from any position alowing it to self start, aswell as this as the number of coils increases the torque would become more constant. Another issue we face with this motor is that its rotation was uneven as its shaft was not alligned, this could be fixed by having a shaft that goes straight through the commutator and using a pillar drill to make the shaft, this would ensure it is centered throughout the commutator.

## Improved Motor
To improve upon the motor we decided to add more coils because as described above this would allow the motor to start from any position, we wanted to use as many coils as possible so that we could get the torque to be generated at a constant rate.  We decided to only use 60 windings of wire per coil rather than the previous 111,
this is because we need to make sure the wires fit around the motor as there would be a totalof 6 coils. We 3d printed our commutator and added copper tape to be used for the brushes. The finished commutator is shown below.

![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/006.JPG "Image 1 of improved motor")
![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/008.JPG "Image 2 of improved motor")

We also designed an improved stand to hold the motor so that its rotation would be more uniform, we decided to 3D print the stand as it allowed us a more complex shape,
we also chose 3D printing over other options as it is something we had not done before and we wished to gain experience with the technique.

![Image of improved stand design](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/001.JPG "Image of improved stand design")
![Image of improved stand](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/016.JPG "Image of improved stand")

Once all the components had been printed we assembled the motor, we set up the brushes and ran the motor to check that it spins.

![Image of improved motor](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/3-2.JPG "Image of improved motor")

### Video
<a href="https://www.youtube.com/watch?v=8vkcDZ_r6UE" target="_blank"><img src="http://img.youtube.com/vi/8vkcDZ_r6UE/0.jpg" alt="Video of improved motor" width="640" height="360" border="0" /></a>

It was visible that the motor span significantly faster than the previous design. To confirm this we built and encoder which would allow us to determine the speed at which our motor span, we used an Arduino and a circular disk with a slot cut out to measure the number of times a beam of light was broken, the result would then be output to a terminal. we used the Arduino line plotter feature to give us a graph of motor speed.

![Image of encoder testing](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/3-1.JPG "Image of encoder testing")
![Image of encoder testing](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/3-4.JPG "Image of encoder testing")

Our motors speed varied significantly due to are low quality componets and the fact that the contact between the brushes of the motor were loose meaning at some points of its rotation more than one coil was conected, this could be fixed by designer a better more stable brush.

## Further possible improvements
Although our improved design was greatly superior to our first design there were many other improvemts tat could have been made, as previously stated we could have designed our brushees better, but one of the bigger improvemnts we could have done was to use a metal (ferrous) core for the motor, this would have greatly increased the size of magnetic field generated by our coils and therefore increased the torque.

## Navigation
[Introduction to markdown and GIT](https://github.com/AandJ/ROCO222/blob/master/journal.md)
***
__Making a Motor__
***
[Making a robotic Arm](https://github.com/AandJ/ROCO222/blob/master/journal-3.md)

