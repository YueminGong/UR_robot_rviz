# tutorial for remote control of UR robot by using ur robot driver


1. ur_robot driver setting up
mainly based on the source
https://github.com/UniversalRobots/Universal_Robots_ROS_Driver?tab=readme-ov-file
#pc should be in the same ethenet
pc ip >>>> ros bash ifconfig

2. ur driver environment setting up in remote pc
$ roscore
$ roslaunch ur_calibration calibration_correction.launch robot_ip:=192.168.0.102 target_filename:="${HOME}/my_robot_calibration.yaml"
$ roslaunch ur_robot_driver ur10e_bringup.launch robot_ip:=192.168.0.102  kinematics_config:=${HOME}/my_robot_calibration.yaml
#robot ip can be found on the teaching panel "about" button

3. moveit install and setting up
$ sudo apt install ros-noetic-moveit
$ source devel/setup.bash
$ catwin_make

4. moveit-rviz simulation setting up
$ roslaunch ur10e_moveit_config moveit_planning_execution.launch
$ roslaunch ur10e_moveit_config moveit_rviz.launch rviz_config:=$(rospack find ur10e_moveit_config)/launch/moveit.rviz

