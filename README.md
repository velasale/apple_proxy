# Apple Proxy
This repo is meant to bring all the UR5e and Apple Proxy in-house configurations into our proxy setup.

The intent of each subfolder:
1) config: 
   * joint_limits.yaml: Set the speed and accelerations of the robot's joints
   * kinematics.yaml: Set the parameters of the inverse kinematics solver
   * ur5e.srdf: This is the Semantic Robot Description Format, and is useful to define stuff like:
      * Define some links that shouldn't be included in the collision avoidance.
      * Define default position (e.g. home).
      * Define link groups.

2) meshes: All the 3d model (stl) of the scene. In this case it has the models of the furniture, apple proxy and hand.
   *  collision: simplified version of the stl, to make the solver run faster
   *  visual: these are stl specificly more visualization purposes
      
3) urdf: Includes the Universal Robot Description Format.
4) launch: Launch files for different purposes.

# Instructions

## 1 - Install additional required packages

* Install the UR5e ROS package from [Universal Robots](https://github.com/UniversalRobots/Universal_Robots_ROS_Driver). 
* Install the ros-serial package from [Ros Drivers](https://github.com/ros-drivers/rosserial).
   ```console 
   git clone https://github.com/ros-drivers/rosserial.git
   ```

## 2 - Make sure to source your ws
Option 1 - Everytime you open a terminal:
```console
source ~/YOUR_WS/devel/setup.bash
```

Option 2 - Edit the ".bashrc" file, so you do not need to run it everytime:
```console
gedit ~/.bashrc
```

and add the text from Option 1 at the end of this file.


## 3 - Run the package

### 3.1 - Only visualization (Rviz) 
Terminal 1 (Motion planner - MoveIt & visualization - Rviz):  
```console
roslaunch apple_proxy pickApp.launch
```

Terminal 2 (Your code):

### 3.2 - With the real UR5e and visualize it in Rviz
Terminal 1 (UR5e drivers):  
```console
roslaunch apple_proxy ur5e_bringup.launch robot_ip:=169.254.177.232
```

Terminal 2 (Motion planner - MoveIt & visualization - Rviz):  
```console
roslaunch apple_proxy pickApp_real.launch
```

Terminal 3 (Your code):


## Notes:
Robots' ip addresses:
* Joe's UR5 ip address: 169.254.174.50
* Cindy's UR5 ip address: 169.254.177.232

Host pc's ip addresses:
* Desktop: 169.254.133.21
* Laptop: 169.254.177.231




