<!--![](/images/.jpg?raw=false)-->

# Autonomous Map Based Navigation 

> Typically we want to send the robot to a specific location and the robot should navigate autonomously to that location.

> We just need to send a good location to the robot and the navigation stack will make the robot navigate to it while avoiding obstacles.

Robot map based navigation answers the following questions:

--Where am I?  **Localization:** it helps the robot know where it is

--Where am I going? **Mapping:** the robot needs to have a map of its environment to be able to recognize where he has been moving around so far 
  
--How do I get there? **Motion planning or path planning:** to plan a path, the target position must be well-defined to the robot, which require an appropriate addressing scheme that the robot can understand

To do this there are two types of planners. The Global Planner and Local Planner. Global Planner will determine a clear path to the target location. The Local planner will execute the path of the Global Planner but will also handle dynamic obstacles.

To show this simulation in Gazebo and Rviz, select the 2D nav goal button in RVIZ, in order to define a good location for the robot. For example I want the robot to move to this location and you can see that the robot first plans a static obstacle free path which we call the global path planning and then executes the path using its local path planner which also avoids dynamic obstacles.

![](NavigationSlam.gif)
---

## Table of Contents
- [Built With](#built-with)
- [Turtlebot3 Navigation](#Turtlebot3_Navigation-package)
- [Turtlebot3 Gazebo](#Turtlebot3_Gazebo-package)
---

## Built With
The ROS workspace first needs to be initialized
```javascript
mkdir ~/catkin_ws/src/
cd ~/catkin_ws
catkin_init_workspace
```
afterwards, the repository can be cloned or downloaded and unzipped in the corresponding path. The packages can be compiled, and the environment has to be sourced.

```
catkin_make
source devel/setup.bash
```

Next, the robot is started inside the gazebo world, and the visualization program RVIZ is opened.

```
roslaunch turtlebot3_gazebo turtlebot3_house.launch
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:=/home/ros/ros_map/tb3_house_map.yaml
 
```

If the Gazebo and RVIZ opened up, set location of robot by selecting 2D-Pose Estimate menu button in RVIZ. Set the the Pose Estimate by moving the cursor in RVIZ to the same location in the Gazebo map. This is necessary because RVIZ doesn't know where the robot is located. 

Then select the 2D Nav Goal menu button and select the target location for the robot.  The Global Planner and Local planner will calculate the path for the robot to follow.

## turtlebot3_Navigation-package

One of The TurtleBot3’s core technology is SLAM, **Navigation** and Manipulation. Navigation allows the robot to move from one location to a specified destination in a given environment. For this purpose, a map that contains geometry information of furniture, objects, and walls of the given environment is required. The map was created with the distance information obtained by the sensor and the pose information of the robot itself.

The Navigation enables a robot to move from the current pose to the designated goal pose on the map by using the map, robot’s encoder, IMU sensor, and distance sensor. The procedure for performing this task is as follows.

## turtlebot3_Gazebo-package
The TurtleBot3’s core technology is SLAM, Navigation and Manipulation, making it suitable for home service robots. The TurtleBot can run SLAM(simultaneous localization and mapping) algorithms to build a map and can drive around your room. 

Gazebo offers the ability to accurately and efficiently simulate populations of robots in complex indoor and outdoor environments. At your fingertips is a robust physics engine, high-quality graphics, and convenient programmatic and graphical interfaces. 

---


