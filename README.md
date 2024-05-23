# VINS-RGBD-FAST

**VINS-RGBD-FAST** is a SLAM system based on VINS-RGBD. We do some refinements to accelerate the system's performance in resource-constrained embedded paltform.

## Refinements
* grid-based feature detection
* extract FAST feature instead of Harris feature
* added stationary initialization
* added IMU-aided feature tracking
* added extracted-feature area's quality judgement
* solved feature clusttering problem result frome FAST feature
* use "sensor_msg::CompressedImage" as image topic type
  
## Related Paper:
```
@ARTICLE{9830851,  
  author={Liu, Jianheng and Li, Xuanfu and Liu, Yueqian and Chen, Haoyao},  
  journal={IEEE Robotics and Automation Letters},  
  title={RGB-D Inertial Odometry for a Resource-Restricted Robot in Dynamic Environments},   
  year={2022},  
  volume={7},  
  number={4},  
  pages={9573-9580},  
  doi={10.1109/LRA.2022.3191193}}
```

## RGBD-Inertial Trajectory Estimation and Mapping for Small Ground Rescue Robot

Based one open source SLAM framework [VINS-Mono](https://github.com/HKUST-Aerial-Robotics/VINS-Mono).

The approach contains
+ Depth-integrated visual-inertial initialization process.
+ Visual-inertial odometry by utilizing depth information while avoiding the limitation is working for 3D pose estimation.
+ Noise elimination map which is suitable for path planning and navigation.

However, the proposed approach can also be applied to other application like handheld and wheeled robot.

## 1. Prerequisites
1.1. **Ubuntu** 20.04

1.2. **ROS** version Noetic fully installation

1.3. **Ceres Solver**
Follow [Ceres Installation](http://ceres-solver.org/installation.html)
```
git clone https://github.com/ceres-solver/ceres-solver.git
git checkout facb199 #1.14.0
```


1.4. **Sophus**
```
  git clone http://github.com/strasdat/Sophus.git
  git checkout a621ff
```

## 2. Datasets

Recording by RealSense D435i. Contain 9 bags in three different applicaions:
+ [Handheld](https://star-center.shanghaitech.edu.cn/seafile/d/0ea45d1878914077ade5/)
+ [Wheeled robot](https://star-center.shanghaitech.edu.cn/seafile/d/78c0375114854774b521/) ([Jackal](https://www.clearpathrobotics.com/jackal-small-unmanned-ground-vehicle/))
+ [Tracked robot](https://star-center.shanghaitech.edu.cn/seafile/d/f611fc44df0c4b3d936d/)

Note the rosbags are in compressed format. Use "rosbag decompress" to decompress.

We use the Nodelet of compressed image:

Topics:
+ depth topic: /camera/aligned_depth_to_color/image_raw
+ color topic: /camera/color/image_raw/compressed
+ imu topic: /camera/imu

## 3. Licence
The source code is released under [GPLv3](http://www.gnu.org/licenses/) license.

