## AGV Navigation with Pure Pursuit Planner

This package enables autonomous navigation for an Automated Guided Vehicle (AGV) using the Pure Pursuit planner in a Gazebo simulation. The setup includes the robot model, control interfaces, localization, map server, and planner integration for real-time path tracking.
### Package Components

    agvs_gazebo – Launches the AGV and simulation environment in Gazebo

    agvs_robot_control – Starts low-level robot control interfaces

    agvs_complete – Provides map server and localization (AMCL)

    purepursuit_planner – Implements the Pure Pursuit path tracking algorithm

### Full Launch Instructions

To launch all components manually for complete control, execute the following in order:

Launch the AGV simulation
```bash
roslaunch agvs_gazebo agvs.launch
```
Start robot control nodes
```bash
roslaunch agvs_robot_control agvs_robot_control.launch
```
Optional: Static transform between map and odom (if needed)
```bash
rosrun tf static_transform_publisher 0 0 0 0 0 0 /map /odom 100
```
Launch the map server
```bash
roslaunch agvs_complete map_server.launch
```
Start localization using AMCL
```bash
roslaunch agvs_complete amcl_diff_2.launch
```
Start RViz for visualization
```bash
rosrun rviz rviz
```
Launch the Pure Pursuit planner
```bash
roslaunch purepursuit_planner purepursuit.launch
```
Launch visualization markers for the planner
```bash
roslaunch purepursuit_planner purepursuit_marker.launch
```
### Quick Start (Recommended)

To launch the full AGV navigation system with a single command sequence:

Launch simulation and robot
```bash
roslaunch agvs_gazebo agvs.launch
```
Launch full navigation stack with Pure Pursuit
```bash
roslaunch agvs_complete agv_navigation.launch
```
This will bring up the simulation, control nodes, localization, map, and the Pure Pursuit navigation planner in one go.

