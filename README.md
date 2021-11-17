## robotiq_hande_ros_driver
This is the ROS driver for Robotiq Hand-E gripper connected to a Universal Robots e-series robot arm. We assuming that the gripper is mounted on the arm, and your host PC is connected to the robot through and ethernet cable.

You need to properly configure your networks such that PC and Robot can ping each other.

## Install
Simply clone this package to your ROS catkin src folder then build the catkin workspace.
```bash
cd ~/your_ws/src
git clone https://github.com/cbteeple/robotiq_hande_ros_driver.git
cd ..
catkin_make
```

## Usage
1. Make note of your robot's IP address (we will use **192.168.1.2** as an example from our UR5e robot)
2. Start the robot arm with tool communication:
```bash
roslaunch ur_robot_driver ur5e_bringup.launch robot_ip:=192.168.1.2 use_tool_communication:=true
```
3. Start the gripper driver by and pass the `robot_ip` argument.
```bash
roslaunch robotiq_hande_ros_driver gripper_bringup.launch robot_ip:=192.168.1.2
```
4. The gripper can now be controlled using a ROS service.
5. See [`test.py`](https://github.com/cbteeple/robotiq_hande_ros_driver/blob/master/src/test.py) for example usage. 
```bash
rosrun robotiq_hande_ros_driver test.py
```

Services allows the driver to send feedback when the finger action completes. This is useful when you want the program to wait until gripper complete its movement. 

## Questions
This is a fork of a driver by macs-lab. If you have questions about this package, open up an issue [with me](https://github.com/cbteeple/robotiq_hande_ros_driver/issues) or a discussion with [macs-labs](https://github.com/macs-lab/robotiq_hande_ros_driver/discussions).
