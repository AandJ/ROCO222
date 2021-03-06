# Monday 18th of December
## Making a ROBOT ARM
We decided to have four degrees of motion, one to rotate the entire base, one for each limb, as well as a gripper. we decided to 3d print the model as we would have an
intricate design for the base and gripper.

![Image of design file](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/STL-IMG.jpg "Image of design file")
![Image of printed arm](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/ROBOT-IMG.jpg "Image of printed arm")

To control this with the ROS software we need to create a URDF description file of our design, in this file we describe each link and joint.
a link definition is shown below.  

```xml
 <link name="base_lower">
    <visual>
      <geometry>
        <!--cylinder length="0.040" radius="0.070"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/base_lower.stl" scale="0.001 0.001 0.001" />
      </geometry>
	  <material name="red"/>
	  <origin rpy="1.57 0 0" xyz="-0.005 0.005 0.020" />
    </visual>
  </link>

  <link name="base_upper">
    <visual>
      <geometry>
        <!-- cylinder length="0.015" radius="0.070"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/base_upper.stl" scale="0.001 0.001 0.001" />
      </geometry>
	  <material name="white"/>
	  <origin rpy="1.57 0 1.57" xyz="0 0 0.005" />
    </visual>
  </link>
```

First we define a name for our link, then for the geometric shape we reference the stl files as a mesh, this accesses our 3d design file so that rviz has the exact shape of our robot,
I also define a material which I have created in the URDF file so that each link is the correct colour, finally I define the origin of the link, the origin is based around the joint that
connects that link to its parent link, for the first link (base_lower) the origin is based around the centre of rviz, I had to adjust the origin due to our artistic design so that this
was also centred. We also had to define the joints in the URDF files, a joint definition is shown below.

```xml
  <joint name="BtF" type="revolute">
    <axis xyz="0 1 0" />
    <limit effort="1000" lower="-1.57" upper="1.57" velocity="0.1" />
    <parent link="base_upper"/>
    <child link="first_limb"/>
    <origin xyz="0 0.02 0.105" />
  </joint>

  <joint name="FtS" type="revolute">
    <axis xyz="0 1 0" />
    <limit effort="1000" lower="-1.57" upper="1.57" velocity="0.1" />
    <parent link="first_limb"/>
    <child link="second_limb"/>
    <origin xyz="0 -0.015 0.085" />
  </joint>

  <joint name="Gripper_main" type="fixed">
    <parent link="second_limb"/>
    <child link="gripper_main"/>
    <origin xyz="-0.0075 -0.02 0.145" />
  </joint>

  <joint name="Gripper_cap" type="fixed">
    <parent link="gripper_main"/>
    <child link="gripper_cap"/>
    <origin xyz="0.005 0 0" />
  </joint>
```

Once again we have to define a name for the joint, then we can define its type, the types can be revolute which allow for 1 degree of motion around an axis with limits, continuous which
allows for 1 degree of motion around the axis without limits, prismatic which is a sliding joint along an axis with set limits, fixed which doesn't not allow any movement, floating which
allows movements in all 6 degrees, and planar which allows movement in the plane perpendicular to the axis.
We also need to define the axis in which it rotates as well as its limit, in the limit we have to define the effort which is the maximum force that can be applied, we also define the lower
and upper limit which dictates how much the joint can rotate, finally we define velocity which sets the maximum velocity at which the joint can rotate. We also have to define the parent and child of the joint, the parent is the link that the joint attaches to and the child is the link it moves. we also have to define the origin of the link. in the case of the gripper we set the joint for the second gear to mimic the first gear, this code is shown below.

```xml
  <joint name="Gripper_gear_rot" type="revolute">
    <axis xyz="1 0 0" />
    <limit effort="1000" lower="-1" upper="0" velocity="0.5" />
    <parent link="gripper_main"/>
    <child link="gripper_gear_right"/>
    <origin xyz="0.0045 0.04 0" />
  </joint>

  <joint name="Gripper_gear_mimic" type="revolute">
    <axis xyz="1 0 0" />
    <limit effort="1000" lower="0" upper="1" velocity="0.5" />
    <mimic joint="Gripper_gear_rot" multiplier="-1"/>
    <parent link="gripper_main"/>
    <child link="gripper_gear_left"/>
    <origin xyz="0.0045 0 0" />
  </joint>
```

The complete rviz product is shown in the video below

![RVIZ Screen grab](https://raw.githubusercontent.com/AandJ/ROCO222/master/ROCO222_Img/RVIZ-SCREENGRAB "RVIZ Screen grab")

### Video
<a href="https://www.youtube.com/watch?v=HuHuthRY6EE" target="_blank"><img src="http://img.youtube.com/vi/HuHuthRY6EE/0.jpg" alt="Video of RVIZ" width="640" height="360" border="0" /></a>

[LINK TO FULL URDF CODE](https://github.com/AandJ/ROCO222/blob/master/journal-urdf.md)

To control the physical robot we needed to code the Arduino so that it would subscribe to the ros joint state topic and use the received values to control the servo motors.

```cpp
  nh.initNode();
  nh.subscribe(sub);
  nh.advertise(pub_debugR);
  nh.advertise(pub_js);

  servo1.attach(BASESERVO);                               //Base servo attached to pin 5
  servo2.attach(ARMSERVO);                                //Arm joint servo attached to pin 6
```

We use "nh.subscribe" (node handler subscribe) to subscribe to the joint state topic in ROS, once these values have been taken from ROS we can use them to control the PWM of the servo motors. "nh.advertise" is used to send data back to ros. I used the servo library function servo.attach to control each servo. To call the function that controls the motor we use the node handler spin once function as shown below.

```cpp
void loop(){
  pos_msgs.data = angle1;
  pub_debugR.publish(&pos_msgs);
  pos_msgs.data = angle2;
  pub_debugR.publish(&pos_msgs);
//  pos_msgs.data = angle3;
//  pub_debugR.publish(&pos_msgs);
  
  
  
  nh.spinOnce();
  delay(1);
} 
```

In "loop" we publish the current content of the angle variables via one of the advertised topics for the purpose of debugging. We also us the "nh.spinOnce" command, this calls all the callbacks waiting to be called. Below is the servo control call back.

```cpp
void servo_cb( const sensor_msgs::JointState& cmd_msg){
    js = cmd_msg;
    pub_js.publish(&js);
    pos = cmd_msg.position[0];
    angle1 = map(pos*100, -157, 157, 0, 179);     // scale it to use it with the servo (value between 0 and 180)
    pos = cmd_msg.position[1];
    angle2 = map(pos*100, -157, 157, 0, 179);     // scale it to use it with the servo (value between 0 and 180)
//  pos = cmd_msg.position[2];
//  angle3 = map(pos*100, -100, 0, 0, 85);        // scale it to use it with the micro servo
    
  
  servo1.write(angle1);                           //set servo angle, should be from 0-180
  servo2.write(angle2);                           //set servo angle, should be from 0-180 
//servo3.write(angle3);                           //set servo angle, should be from 0-85
  digitalWrite(13, HIGH-digitalRead(13));  	  //toggle led
}
```

In the call back I subscribed to the ROS topic js to print a string for the purpose of debugging, I then saved the position data to a local variable which I then inserted into the map function, the first value of the function is the value to be mapped followed by the lowest possible value and then the highest possible value, the last two numbers are the minimum and maximum of the generated mapped value. Once the values have been mapped to between 0 and 180 I then use `Servo.write(VALUE)` function from the servo library to move the servo to the desired position. When we tried to run our code for the first time we encountered issues, this was because the amount of data in the subscribed ros topic exceeded the buffer of our Arduino, we had to reduce the degrees of motion to be able to run our code, for a preliminary test we used two degrees of motion, this test is shown in the video below.

### Video
<a href="https://www.youtube.com/watch?v=289UI_HXdns" target="_blank"><img src="http://img.youtube.com/vi/289UI_HXdns/0.jpg" alt="Video of Arm" width="640" height="360" border="0" /></a>

We later added a third degree of motion, this would have allowed our gripper to move however we found the micro servo did not have enough torque to move our gripper.

## Navigation
[Introduction to markdown and GIT](https://github.com/AandJ/ROCO222/blob/master/journal.md)
***
[Making a Motor](https://github.com/AandJ/ROCO222/blob/master/journal-2.md)
***
__Making a robotic Arm__
