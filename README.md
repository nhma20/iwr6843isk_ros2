# iwr6843aop_pub
Python ROS2 pointcloud retriever for IWR6843ISKEVM mmWave device

Derived from: https://github.com/nhma20/iwr6843aop_pub


### Prerequisites

ROS2 (Ubuntu 20.04 dashing tested)
Python3 (3.8 tested)

### Installation

1. Clone the repo to workspace
   ```sh
   cd ~/dev_ws/src/
   ```
   ```sh
   git clone https://github.com/nhma20/iwr6843isk_pub.git
   ```
2. Colcon build package
   ```sh
   cd ~/dev_ws/
   ```
   ```sh
   colcon build
   ```


<!-- USAGE EXAMPLES -->
## Usage

0. Plug in IWR6843ISKEVM, make sure ports match (default /dev/ttyUSB0,1)
1. Run ros package (make sure /opt/ros/dashing/setup.bash and ~/dev_ws/install/setup.bash are sourced)
   ```sh
   ros2 run iwr6843isk_pub pcl_pub
   ```
   or with parameters:
   ```sh
   ros2 run iwr6843isk_pub pcl_pub /dev/ttyUSB0 /dev/ttyUSB1
   ```
2. Visualize with rviz
   ```sh
   rviz2
   ```
3. 'Add' a new display (lower left corner)
4. Select 'By topic' ribbon
5. Find 'iwr6843_scan/pcl PointCloud2' and add it
6. (Optional) Set point size at PointCloud2 -> Size (m) to 0.25 for better clarity

## Modify

All functional code (for the purpose of this ROS package) is located at
   ```sh
   /iwr6843isk_pub/iwr6843isk_pub/publisher_member_function.py
   ```
Two .cfg files are provided which dictate the functionality of the mmWave device. More profiles can be made with the mmWave Demo Visualizer tool: https://dev.ti.com/gallery/view/mmwave/mmWave_Demo_Visualizer/ver/3.5.0/
