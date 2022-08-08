# cpp-reconstruction-application
Build and applying Coverage Path Planners for 3D reconstruction with UAVs

<br>

## How to measure accuracy
+ Ground truth from `Gazebo` world - https://github.com/ethz-asl/voxblox_ground_truth
+ Then, generate `Mesh` with your CPP algorithm
+ Then, use `[CloudCompare](https://www.danielgm.net/cc/)` which provides distance error between `PointCloud` and `Mesh`

## Online method (Fully online)
+ [OIPP](https://github.com/ethz-asl/mav_active_3d_planning): An Efficient Sampling-Based Method for Online Informative Path Planning in Unknown Environments, 2020 RA-L
  + Build
  + Run
  + Parameters and remarks

## Online method (Explore-then-Exploit)
+

## Offline method (model-based)
+ [Circular CPP](https://github.com/engcang/circular_path_cpp): Circular coverage path planner coded by `[Duckyu Choi](https://github.com/duckyu)` for comparing with SOTA algorithms
+ [SIPP](https://github.com/ethz-asl/StructuralInspectionPlanner): Structural Inspection Path Planning via Iterative Viewpoint Resampling with Application to Aerial Robotics, 2015 ICRA
  + Build
  + Run
  + Parameters and remarks
+ [MLCPP](https://github.com/sungwook87/mlcpp): MLCPP: Multi-layer coverage path planner for autonomous structural inspection of high-rise structures, 2018 IROS
  + Build
  + Run
  + Parameters and remarks
+ [CEO-MLCPP](https://github.com/engcang/ceo-mlcpp): CEO-MLCPP: Control Efficient and Obstacle-aware Multi-Layer Coverage Path Planner for 3D reconstruction with UAVs, 2022 RiTA
  + Build
  + Run
  + Parameters and remarks
