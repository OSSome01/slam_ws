# Simultaneous Localization and Mapping
Simulation of a differential drive robot which can perform autonomous navigation.

## Prerequisites

* [ROS](http://wiki.ros.org/kinetic)
* [Gazebo](http://wiki.ros.org/gazebo_ros_pkgs)
* [Turtlebot3](https://emanual.robotis.com/docs/en/platform/turtlebot3/overview/)


## Getting Started

1. Clone this repository.
2. Run `catkin_make`.
3. Run `source slam_ws/devel/setup.bash`.

### Mapping
  * Run `roslaunch slamBot_gazebo slamBot_test_world.launch` to launch the world in gazebo
  * In a separate terminal run `roslaunch slamBot_navigation slamBot_slam.launch slam_methods:=gmapping` to start building the map. This also launches rviz.
  * In a separate terminal run `roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch` to start the teleoperation of the robot
  * Move the robot around steadly to generate a map.
  * In a separate terminal run `rosrun map_server map_saver -f /tmp/test_map` to save the map in a yaml file.
  
  [![Mapping the environment by using gmapping](https://raw.githubusercontent.com/OSSome01/slam_ws/master/assets/mapping.png?token=ALKIIA4EKYI7AKSNPECYMHS7LXJN2)](https://youtu.be/n91CMrL0g-4)
  
### Localization
  * Launch the gazebo world by running `roslaunch slamBot_gazebo slamBot_test_world.launch`
  * In a separate terminal run `roslaunch slamBot_navigation slamBot_navigation.launch map_file:=/tmp/test_map.yaml`, to start navigation in the map
  * In rviz, estimate initial pose by `2D Pose Estimate`
  * In a separate terminal run `roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch` to start the teleoperation of the robot. You'll see that the estimate of robot's pose will coverge pretty quickly.
  
  [![Mapping the environment by using gmapping](https://raw.githubusercontent.com/OSSome01/slam_ws/master/assets/localization.jpg?token=ALKIIA4LUOO66MX7THE5SOK7LXJGU)](https://youtu.be/MMK123eTdbs)
  
## References
This work was done taking reference from [here](http://moorerobots.com/blog/post/1)
