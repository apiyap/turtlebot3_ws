# ROS2 GALACTIC 

## install TURTLEBOT3
<pre>


mkdir -p ~/turtlebot3_ws/src
cd ~/turtlebot3_ws/
vcs import src < turtlebot3.repos

# OR cd src/

git clone -b galactic-devel https://github.com/ROBOTIS-GIT/DynamixelSDK.git
git clone -b galactic-devel https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
git clone -b galactic-devel https://github.com/ROBOTIS-GIT/turtlebot3.git
git clone -b galactic-devel https://github.com/ROBOTIS-GIT/turtlebot3_simulations.git
cd ~/turtlebot3_ws

. ~/ros2_galactic/install/setup.bash

export MAKEFLAGS=-j6
colcon build --symlink-install --parallel-workers 6

</pre>

## TEST ON GAZEBO
<pre>
cd ~/turtlebot3_ws
. ~/ros2_galactic/install/setup.bash
. install/setup.bash

#1.Empty World
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo empty_world.launch.py
#2.TurtleBot3 World
export TURTLEBOT3_MODEL=waffle
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
#3.TurtleBot3 House
export TURTLEBOT3_MODEL=waffle_pi
ros2 launch turtlebot3_gazebo turtlebot3_house.launch.py

</pre>

## Run Gazebo
<pre>
. ~/ros2_galactic/install/setup.bash
. install/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
</pre>

## Create Map
<pre>
. ~/ros2_galactic/install/setup.bash
. install/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
</pre>

## Navigation
<pre>
. ~/ros2_galactic/install/setup.bash
. install/setup.bash
export TURTLEBOT3_MODEL=burger
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=$HOME/map.yaml
</pre>