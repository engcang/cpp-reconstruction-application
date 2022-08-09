# Coverage Path Planners for 3D Reconstruction with UAVs - Build and Applications
+ Mainly focusing on build process and explanation

<br>

## How to measure accuracy
+ Ground truth from `Gazebo` world - https://github.com/ethz-asl/voxblox_ground_truth
+ Then, generate `Mesh` with your CPP algorithm
+ Then, use [`CloudCompare`](https://www.danielgm.net/cc/) which provides distance error between `PointCloud` and `Mesh`

<br>

## Online method (Fully online)
+ [OIPP](https://github.com/ethz-asl/mav_active_3d_planning): An Efficient Sampling-Based Method for Online Informative Path Planning in Unknown Environments, ***2020 RA-L***
  + Build
  + Run
  + Parameters and remarks

<br>

## Online method (Explore-then-Exploit)
+

<br>

## Offline method (model-based)
+ [Circular CPP](https://github.com/engcang/circular_path_cpp): Circular coverage path planner coded by [`Duckyu Choi`](https://github.com/duckyu) for comparing with SOTA algorithms
+ [SIPP](https://github.com/ethz-asl/StructuralInspectionPlanner): Structural Inspection Path Planning via Iterative Viewpoint Resampling with Application to Aerial Robotics, ***2015 ICRA***
  + Build
  ```sh
  (Prerequisites)
  $ sudo apt install libeigen3-dev ros-<distro>-tf ros-<distro>-rviz ros-<distro>-octomap ros-<distro>-octomap-msgs
  ```
  ```sh
  $ mkdir catkin_ws_repos # assuming you want to enter a new catkin directory
  $ cd catkin_ws_repos # alternatively just cd your normal catkin workspace
  $ mkdir src # assuming this folder does not exist
  $ cd src/
  $ catkin_init_workspace
  $ git clone git@github.com:ethz-asl/StructuralInspectionPlanner.git
  $ cd ..
  $ catkin build
  $ source devel/setup.bash
  ```
  + Run
  ```sh
  $ roslaunch koptplanner kopt.launch
  $ rviz -d <path_to_SIPP>/sipp.rviz
  $ rosrun request request 
  (If you want to run another example such as Bigben, then launch bigBen.launch and run bigBen instead of uppers)
  ```
  + Parameters and remarks

    You can easily run this open source with your own 3D model(.stl) with a little bit of modification.
    
    (More details will be added later)
  
+ [ASSCPP](https://github.com/kucars/asscpp): Coverage Path Planning with Adaptive Viewpoint Sampling to Construct 3D Models of Complex Structures for the Purpose of Inspection, ***2018 IROS***
  + Build
  + Run
  + Parameters and remarks
+ [MLCPP](https://github.com/sungwook87/mlcpp): MLCPP: Multi-layer coverage path planner for autonomous structural inspection of high-rise structures, ***2018 IROS***
  + Build
  + Run
  + Parameters and remarks
+ [CEO-MLCPP](https://github.com/engcang/ceo-mlcpp): CEO-MLCPP: Control Efficient and Obstacle-aware Multi-Layer Coverage Path Planner for 3D reconstruction with UAVs, ***2022 RiTA***
  + Build
  + Run
  + Parameters and remarks
