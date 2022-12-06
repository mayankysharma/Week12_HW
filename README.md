[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
---

# Gazebo Assignment Week12: TurtleBot3 Walker

## Title

Gazebo Assignment: To implementat a algorithm to run TurtleBot 3 in to avoid obstacles and collisions. 


## ROS2 Dependencies
* ROS2 Humble
* ```gazebo_ros```
* ```turtlebot3```



## Build Instructions
Source setup file first
```
. <path-to-ROS2-installation>/ros2_humble/install/local_setup.bash
```
```
cd <path-to-ROS2-workspace>/ros2_ws/src
git clone the link to this repo
cd ..  
rosdep install -i --from-path src --rosdistro humble -y
colcon build --packages-select Turtle_Bot_3_walker
```

## Run Instructions

### Simulation

In a terminal, navigate to your ROS2 workspace (```ros2_ws```) and source the setup files,
````
export TURTLEBOT3_MODEL=waffle_pi

export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:`ros2 pkg prefix turtlebot3_gazebo `/share/turtlebot3_gazebo/models/
````

````
export TURTLEBOT3_MODEL=waffle_pi

export GAZEBO_MODEL_PATH=$GAZEBO_MODEL_PATH:`turtlebot3_gazebo `/share/turtlebot3_gazebo/models/

ros2 launch turtlebot3_gazebo turtlebot3_world.launch.py
````

and run the ```walker``` node in another terminal as follows:

````
ros2 run turtlebot3_walker walker
````
## Results
### To run Cppcheck
```
cppcheck --enable=all --std=c++17 ./src/*.cpp ./include/turtlebot3_walker/*.hpp --suppress=missingIncludeSystem --suppress=unmatchedSuppression --suppress=unusedFunction --suppress=missingInclude --suppress=useInitializationList > results/cppcheck.txt
```
### To run Cpplint 
```
cpplint --filter=-build/c++11,+build/c++17,-build/namespaces,-build/include_order ./src/*.cpp ./include/turtlebot3_walker/*.hpp > ./results/cpplint.txt
```


### ROS2 bag recording

To record the ros2 bag you need to do the following

```
ros2 bag info walker_bag
ros2 bag play walker_bag
```
### Issues:
* ROS bag file were not recorded due to errors

