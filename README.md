# install-run-arm-pkg-ROS
In order to simulate the robot arm motions and positions as it is in the reality. And to discover any physical or logical problems that may surface during the simulation. 

In this project we will use ROS pakages with ROS melodic and Ubuntu 18.04.5
The robot arm pakage will use joint_state_publisher to test the arm motion with both Rvis simulation and gazebo simulation.
Inaddition to 

## Dependencies 

Assuming that you have installed the ROS system within Ubuntu and created a workspace by using catkin_make
Download the robot arm pakage from smart methods github page:
https://github.com/smart-methods/arduino_robot_arm

Add the “arduino_robot_arm” package to “src” folder
  
     $ cd ~/catkin_ws/src
	 $ sudo apt install git
   	 $ git clone https://github.com/smart-methods/arduino_robot_arm 
  
Install all the dependencies 

	$ cd ~/catkin_ws
	$ rosdep install --from-paths src --ignore-src -r -y
	$ sudo apt-get install ros-melodic-moveit
	$ sudo apt-get install ros-melodic-joint-state-publisher ros-melodic-joint-state-publisher-gui
	$ sudo apt-get install ros-melodic-gazebo-ros-control joint-state-publisher
	$ sudo apt-get install ros-melodic-ros-controllers ros-melodic-ros-control

Compile the package

    $ catkin_make
  
## Usage
 # Controlling the robot arm by joint_state_publisher
    $ roslaunch robot_arm_pkg check_motors.launch
    
  Simulation
Run the following instructions to use gazebo. First line will operate gazebo. and the next line will operate the joint_state that associates with gazebo simulator:

    $ roslaunch robot_arm_pkg check_motors_gazebo.launch.  
    $ rosrun robot_arm_pkg joint_states_to_gazebo.py       

(Note: you may need to make the python script executable by changing the permission)
  
  $ cd catkin/src/arduino_robot_arm/robot_arm_pkg/scripts
	$ sudo chmod +x joint_states_to_gazebo.py
  
  
  <img width="588" alt="Screen Shot 2021-06-23 at 4 35 22 PM" src="https://user-images.githubusercontent.com/85841915/123106109-082c0f00-d441-11eb-9263-90f59afaa581.png">

<img width="806" alt="Screen Shot 2021-06-25 at 11 24 03 PM" src="https://user-images.githubusercontent.com/85841915/123481601-a4eed800-d60c-11eb-90f5-bd6d738bdea8.png"> 

gazebo may operate very slowly and to solve this problem go settings-> system -> processor -> increase it up to 4 processors.

  # Controlling the robot arm by Moveit and kinematics

     $ roslaunch moveit_pkg demo.launch

  #Simulation
Run the following instruction to use it with gazebo

     $ roslaunch moveit_pkg demo_gazebo.launch

<img width="805" alt="Screen Shot 2021-06-25 at 11 33 06 PM" src="https://user-images.githubusercontent.com/85841915/123482673-37dc4200-d60e-11eb-9536-33211911e83e.png">

Note: programs may run very slow




  
  
  
  
