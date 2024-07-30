# Launch-TurtleBot-navigation

## Install ROS on Remote PC
Open the terminal with Ctrl+Alt+T and enter below commands one at a time.
In order to check the details of the easy installation script, please refer to the script file.

```
$ sudo apt update
$ sudo apt upgrade
$ wget https://raw.githubusercontent.com/ROBOTIS-GIT/robotis_tools/master/install_ros_noetic.sh
$ chmod 755 ./install_ros_noetic.sh 
$ bash ./install_ros_noetic.sh
```

![image](https://github.com/user-attachments/assets/efc71671-6190-40df-98ee-23a45e5b14b5)


### Install Dependent ROS Packages
```
$ sudo apt-get install ros-noetic-joy ros-noetic-teleop-twist-joy \
  ros-noetic-teleop-twist-keyboard ros-noetic-laser-proc \
  ros-noetic-rgbd-launch ros-noetic-rosserial-arduino \
  ros-noetic-rosserial-python ros-noetic-rosserial-client \
  ros-noetic-rosserial-msgs ros-noetic-amcl ros-noetic-map-server \
  ros-noetic-move-base ros-noetic-urdf ros-noetic-xacro \
  ros-noetic-compressed-image-transport ros-noetic-rqt* ros-noetic-rviz \
  ros-noetic-gmapping ros-noetic-navigation ros-noetic-interactive-markers
```


![image](https://github.com/user-attachments/assets/7439c463-678d-4c85-861c-6a7ba94061a5)


### Install TurtleBot3 Packages

```
$ sudo apt install ros-noetic-dynamixel-sdk
$ sudo apt install ros-noetic-turtlebot3-msgs
$ sudo apt install ros-noetic-turtlebot3
```



### Catkin workspace
```
$ cd ~/catkin_ws/src/
$ git clone -b noetic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
$ cd ~/catkin_ws && catkin_make
```

![image](https://github.com/user-attachments/assets/3802b066-f167-4ae6-933f-13755d76302a)



### Launch Simulation World

```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_gazebo turtlebot3_world.launch
```
![image](https://github.com/user-attachments/assets/a70bcb7d-f26a-4104-97ee-5088c792a253)


### Run SLAM Node
 ```
roslaunch turtlebot3_slam turtlebot3_slam.launch slam_methods:=gmapping
```
![image](https://github.com/user-attachments/assets/66a0273e-4481-4444-a049-9f616217e254)


  create a map and save it
```
rosrun map_server map_saver -f ~/map
```
then run this command:
```
roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```
![image](https://github.com/user-attachments/assets/a91d5e7a-10e3-4ddf-85d8-5743510301b8)





### Run Teleoperation Node
```
$ export TURTLEBOT3_MODEL=waffle
$ roslaunch turtlebot3_teleop turtlebot3_teleop_key.launch
```

![image](https://github.com/user-attachments/assets/4e1143d6-c757-4751-ae52-c29973c58c10)



###  navigation

start the navigation and load the saved map, using this command:
```
roslaunch turtlebot3_navigation turtlebot3_navigation.launch map_file:='/home/muh/map.yaml'
```

![image](https://github.com/user-attachments/assets/3e009ec6-5164-432f-9d66-c3b7a95769de)



# Source of all steps

https://emanual.robotis.com/docs/en/platform/turtlebot3/quick-start/


