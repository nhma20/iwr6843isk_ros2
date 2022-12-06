# IWR6843ISK simple ROS2 package

![mmw_pcl_gif](https://user-images.githubusercontent.com/76950970/194247603-18e9031a-7d34-4747-9926-9d35d6e3df4e.gif)

Python ROS2 pointcloud retriever for IWR6843ISK mmWave device

Derived from: https://github.com/nhma20/iwr6843aop_pub


### Prerequisites

- ROS2 (Ubuntu 18.04.5 & dashing tested  // Ubuntu 20.04.3 & foxy tested)
- Python3 (3.6.9 & 3.8.10 tested)
- IWR6843ISK mmWave radar device flashed with out-of-box firmware (either from this repo or inside downloaded mmwave_industrial_toolbox_x_x_x/labs/Out_Of_Box_Demo/prebuilt_binaries/ folder. Use uniflash to flash device (https://training.ti.com/hardware-setup-iwr6843isk-and-iwr6843isk-ods)). Set up switches as seen here:

<img src="https://user-images.githubusercontent.com/76950970/194248928-3aab1551-55ec-4969-842a-8e87486cdbc7.jpg" width="350">



### Installation

1. Clone the repo to workspace
   ```sh
   cd ~/ros2_ws/src/
   ```
   ```sh
   git clone https://github.com/nhma20/iwr6843isk_pub.git
   ```
2. Colcon build package
   ```sh
   cd ~/ros2_ws/
   ```
   ```sh
   colcon build --packages-select iwr6843isk_pub
   ```


<!-- USAGE EXAMPLES -->
## Usage

0. Plug in IWR6843ISK, make sure ports match (default /dev/ttyUSB0, /dev/ttyUSB1)
1. Run ros package (make sure /opt/ros/<ros2_version>/setup.bash and <ros2_workspace>/install/setup.bash are sourced)
   ```sh
   ros2 run iwr6843isk_pub pcl_pub
   ```
   or with ROS2 parameters:
   ```sh
   ros2 run iwr6843isk_pub pcl_pub --ros-args -p cli_port:=/dev/ttyUSB0 -p data_port:=/dev/ttyUSB1 -p cfg_path:=/home/nm/ros2_ws/src/iwr6843isk_ros2/cfg_files/xwr68xx_profile_30Hz.cfg
   ```
   When loading a cfg with a different antenna configuration than the previous, IWR6843AOP device must be power cycled - can be done easily by pressing the RST_SW switch, or simply unplugging and replugging the USB cable.
   
2. Visualize with rviz
   ```sh
   rviz2
   ```
3. 'Add' a new display (lower left corner)
4. Select 'By topic' ribbon
5. Find 'iwr6843_pcl PointCloud2' and add it
6. (Optional) Set point size at PointCloud2 -> Size (m) to 0.1 for better clarity

## Modify

All functional code (for the purpose of this ROS2 package) is located at
   ```sh
   <ros2_workspace>/src/iwr6843isk_ros2/iwr6843isk_pub/publisher_member_function.py
   ```
Two .cfg files are provided which dictate the functionality of the mmWave device. More profiles can be made with the mmWave Demo Visualizer tool: https://dev.ti.com/gallery/view/mmwave/mmWave_Demo_Visualizer/ver/3.5.0/
