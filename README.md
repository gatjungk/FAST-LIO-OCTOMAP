# FAST-LIO-OCTOMAP
This repository allows the 3D point cloud data from FAST-LIO-ROS2 to be converted into a 2D occupancy map. 

# Implementation
## 1. Setup the Launch File
Copy the ```octomap_mapping.launch.py``` file included in this repository into the launch/ directory of the fast_lio package.

Destination Path Example: ```./src/FAST_LIO/launch/octomap_mapping.launch.py```

## 2. Build
Since a new launch file was added to the package, we must rebuild the workspace to register it:
```
colcon build 
source install/setup.bash
```

## 3. Execution
To get the 2D map, launch in this order:
```
ros2 run tf2_ros static_transform_publisher 0 0 0 0 0 0 map camera_init
```
The FAST LIO:
```
ros2 launch fast_lio mapping.launch.py
```
The Octomap:
```
ros2 launch fast_lio octomap_mapping.launch.py
```
