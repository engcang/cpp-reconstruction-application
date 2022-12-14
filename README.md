# Coverage Path Planners for 3D Reconstruction with UAVs - Build and Applications
+ Mainly focusing on build process and explanation

<br>

## How to measure accuracy
+ Ground truth from `Gazebo` world - https://github.com/engcang/voxblox_ground_truth (modified version to generated `.pcd` file)
+ Then, generate `Mesh` in `.ply` format (or `.pcd`) with your CPP algorithm
+ Then, use [`CloudCompare`](https://www.danielgm.net/cc/) which provides distance error between `PointCloud` and `Mesh`

<br>

## Depth generation
+ With only camera images
  + [REMODE](https://github.com/uzh-rpg/rpg_open_remode)
  + [CasMVSNet](https://github.com/alibaba/cascade-stereo)
+ With Depth sensors (RGB-D, LiDAR, etc.)
  + [Voxblox](https://github.com/ethz-asl/voxblox)

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

  <details><summary>[Unfold to see]</summary>

  + Build
    ```sh
    (Prerequisites)
    $ sudo apt install libeigen3-dev ros-<distro>-tf ros-<distro>-rviz ros-<distro>-octomap ros-<distro>-octomap-msgs
    ```
    ```sh
    $ mkdir -p catkin_ws/src # assuming you want to enter a new catkin directory
    $ cd catkin_ws/src
    $ catkin_init_workspace # assuming you want to enter a new catkin directory
    $ git clone git@github.com:ethz-asl/StructuralInspectionPlanner.git
    $ cd ..
    $ catkin build
    $ source devel/setup.bash
    $ echo "source ~/catkin_ws/devel/setup.bash" >> ~/.bashrc # assuming you want to enter a new catkin directory
    ```
  + Run
    ```sh
    $ roslaunch koptplanner kopt.launch
    $ rviz -d <path_to_SIPP>/sipp.rviz
    $ rosrun request {node_name} 
    (node_name: request, bigBen, hoaHakanaia, solarPlant)
    ```

  + If `Segmentation fault` in `rosrun request {node_name}`, there are two cases.
      + Modify code in `StructuralInspectionPlanner/request/src/{node_name}.cpp` as below. (I'm not sure why exactly, but in my case it worked well.)
  
      ```cpp
      //assert(line = (char *) malloc(80));
      line = (char *) malloc(MaxLine = 80);
      if (line ==NULL){
        ROS_WARN("malloc error");
        exit(1);
      }
      ```
  
  + If you want to run this open source with your own 3D model (`.stl`), need to check that it is `ASCII` format. 
  + If your 3D model `.stl` file is too big, use [`ACVD`](https://github.com/valette/ACVD) to downsample / simplify it.
    ```sh
    1. Download and install VTK
    Get source file at: https://vtk.org/download/
    $ tar xf VTK-version.tar.gz
    $ cd VTK-version
    $ mkdir build && cd build
    $ cmake .. -DCMAKE_BUILD_TYPE=Release
    $ sudo make install -j16
  
    2. Download and install ACVD
    $ git clone https://github.com/valette/ACVD.git
    $ cd ACVD
    $ git checkout origin/vtk9
    $ cmake . -DCMAKE_BUILD_TYPE=Release
    $ make -j16

    if sort error, add below header files at the top of AVCD/Common/vtkSurface.cxx file
    #include <algorithm>
    #include <functional>
    #include <array>

  
    3. Run ACVD to simplify your .stl file
    $ cd ACVD/bin
    $ ./ACVD stl_file.stl 3000 0 -o /home/mason -of output.ply -d 1
    #(number of mesh desired, gradation or curvature, output directory, output filename, display)
    Note, output file must be .ply format. It should be converted to .stl file with VTK or Blender
    ```

    
  ---

  <br>

  </details>

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
