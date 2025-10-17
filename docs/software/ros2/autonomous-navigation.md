---
title: Autonomous Navigation

version: 1.0.0
date: 16.10.2025
authors:
  - Kacper Marchlewicz, marchlewicz.kac@gmail.com
---
## Sensors
Firo is equipped with three LiDAR scanners:

- **Front horizontal LiDAR** – used for navigation, mapping, and localization. 
- **Two vertical side LiDARs** – mounted on both sides of the robot. Their data is filtered so they only detect obstacles below **1.5 m** in height (slightly higher than Firo’s mast).  
  These scanners prevent the robot from attempting to pass under low shelves or slopes.



## Odometry and Data Fusion
Firo uses three odometry sources — **wheel**, **LiDAR**, and **IMU** — which are fused together:

| Source | Data Provided |
| ------ | ------------- |
| Wheels | vx, ωx        |
| LiDAR  | vx, ωx        |
| IMU    | ωx            |

This forms the **local fusion** layer.  
The **global fusion** layer also includes the position estimated by the global localization algorithm (SLAM or Nav2).

Currently, odometry quality is acceptable but not sufficient for continuous SLAM from slam_toolbox.

### Future Improvements
- Make **LiDAR odometry** the primary source.  
- Reduce usage or enhance **wheel odometry** with error estimation (wheel slip is unavoidable in skid-steer robots).  
- Consider using a **faster, higher-quality LiDAR**, as the current one produces noisy RF2O odometry data.
![[odometry_linear.gif]]
![[odometry_angular.gif]]


## SLAM
Firo uses the **SLAM Toolbox** for map building.

- Map quality is generally acceptable, though multiple mapping attempts may be needed due to odometry imperfections.  
- Currently, map building is performed as a **separate step**, because simultaneous SLAM and navigation require better odometry accuracy than currently available.



## Navigation
Firo’s navigation system is based on the **Nav2 framework**.

The **NavigateToPose** action is implemented with standard recovery behaviors.

### Additional Nodes
- **Twist Stamper** – converts `Twist` messages to `TwistStamped`, which is required by Firo’s drivers.  
- **Dock Approach Manager** – an action server that lets users save and send dock approach pose as navigation goal.

### Localization
Due to not sufficient enough odometry quality, **AMCL (Adaptive Monte Carlo Localization)** is used for global localization.

### Planning and Control
- **Planner:** Smac State Lattice (modified A* for non-circular robots)  
- **Smoother:** ConstrainedSmoother (suitable for Smac State Lattice)  
- **Costmaps:** Include data from vertical LiDARs to detect slopes and shelves.  
- **Controller:** MPPI (Model Predictive Path Integral) with velocity smoothing.  
- **Collision Monitor:**  
  - Slow down by **30%** if an obstacle is within **15 cm**.  
  - Stop completely if within **5 cm**.

### Current Status
Navigation works fine:
- Path planning and dynamic obstacle avoidance are effective.  
- Two known issues:
  1. **Costmap shifting** during rotation (likely odometry error).  
  2. **Path following** – occasionally, instead of turning in place, the robot tries to follow a curved path and fails to reach the target (likely controller cost weighting issue).



## Docking
Docking is based on the **ICP (Iterative Closest Point)** algorithm.

Vertical LiDAR point cloud data is used to detect and verify the docking station’s shape.  
Detected coordinates are saved and used by the docking server, which performs docking and undocking using a **PID controller**.

### Notes
- Start detection when the robot is about **0.5 m** from the docking station.  
- Initiate docking when about **1.5 m** away and facing the station.  
- The **approach pose** can be saved and used as a navigation goal via the **Dock Approach Manager**.

Docking is still a work in progress; the detection algorithms requires further tuning and testing.
