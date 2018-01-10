# Complete URDF file
```xml
<?xml version="1.0"?>
<robot name="roco_arm">

 <material name="blue">
  <color rgba="0 0 1 1"/>
 </material>

 <material name="white">
  <color rgba="1 1 1 1"/>
 </material>

 <material name="green">
  <color rgba="0.2 0.6 0.3 1"/>
 </material>

 <material name="red">
  <color rgba="1 0 0 1"/>
 </material>

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

  <link name="first_limb">
    <visual>
      <geometry>
        <!-- <box size="0.040 0.005 0.125"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/first_limb.stl" scale="0.001 0.001 0.001" />
      </geometry>
      <origin rpy="0 1.57 0" xyz="0 0 0" />
      <material name="green"/>
    </visual>
  </link>

  <link name="second_limb">
    <visual>
      <geometry>
        <!-- box size="0.040 0.005 0.125"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/second_limb.stl" scale="0.001 0.001 0.001" />
      </geometry>
      <origin rpy="0 1.57 0" xyz="0 0 0" />
      <material name="green"/>
    </visual>
  </link>

  <link name="gripper_main">
    <visual>
      <geometry>
        <!--cylinder length="0.040" radius="0.070"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/Gripper Main.stl" scale="0.001 0.001 0.001" />
      </geometry>
	  <material name="green"/>
	  <origin rpy="-1.57 3.14 -1.57" xyz="0 0 0" />
    </visual>
  </link>

  <link name="gripper_cap">
    <visual>
      <geometry>
        <!--cylinder length="0.040" radius="0.070"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/Gripper cap.stl" scale="0.001 0.001 0.001" />
      </geometry>
	  <material name="green"/>
	  <origin rpy="-1.57 3.14 -1.57" xyz="0 0 0" />
    </visual>
  </link>
  
  <link name="gripper_gear_right">
    <visual>
      <geometry>
        <!--cylinder length="0.040" radius="0.070"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/Gripper Gear right.stl" scale="0.001 0.001 0.001" />
      </geometry>
	  <material name="green"/>
	  <origin rpy="-1.57 -1.57 -1.57" xyz="0 0 0" />
    </visual>
  </link>

  <link name="gripper_gear_left">
    <visual>
      <geometry>
        <!--cylinder length="0.040" radius="0.070"/> -->
	<mesh filename="file://home/home/bonnie/Robot-ARM/Gripper Gear left.stl" scale="0.001 0.001 0.001" />
      </geometry>
	  <material name="green"/>
	  <origin rpy="-1.57 3.14 -1.57" xyz="0 0 0" />
    </visual>
  </link>

  <joint name="BR" type="fixed">
    <!-- <axis xyz="0 0 1" />
    <limit effort="1000" lower="-3.14" upper="3.14" velocity="0.5" /> -->
    <parent link="base_lower"/>
    <child link="base_upper"/>
    <origin xyz="0 0 0" />
  </joint>

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

  <joint name="Gripper_gear_rot" type="fixed">
    <!-- <axis xyz="1 0 0" />
    <limit effort="1000" lower="-1" upper="0" velocity="0.1" /> -->
    <parent link="gripper_main"/>
    <child link="gripper_gear_right"/>
    <origin xyz="0.0045 0.04 0" />
  </joint>

  <joint name="Gripper_gear_mimic" type="fixed">
    <!-- <axis xyz="1 0 0" />
    <limit effort="1000" lower="0" upper="1" velocity="0.5" />
    <mimic joint="Gripper_gear_rot" multiplier="-1" /> -->
    <parent link="gripper_main"/>
    <child link="gripper_gear_left"/>
    <origin xyz="0.0045 0 0" />
  </joint>

</robot>
```  
  

## Navigation
[Back to making a robot](https://github.com/AandJ/ROCO222/blob/master/journal-3.md)
