----
# trajectory_tracker package

## trajectory_tracker

trajectory_tracker node controls vehicle velocity to follow given path.

### Sources

* src/trajectory_tracker.cpp

### Subscribed topics

* ~/path (nav_msgs::Path)
* ~/odom (nav_msgs::Odometry)
* ~/speed (std_msgs::Float32)
* /tf

### Published topics

* ~/cmd_vel (geometry_msgs::Twist)
* ~/status (trajectory_tracker::TrajectoryTrackerStatus)
* ~/tracking (geometry_msgs::PoseStamped)

### Services


### Called services


### Parameters

* "frame_robot" (string, default: std::string("base_link"))
* "path" (string, default: std::string("path"))
* "odom" (string, default: std::string("odom"))
* "cmd_vel" (string, default: std::string("cmd_vel"))
* "hz" (double, default: 50.0)
* "look_forward" (double, default: 0.5)
* "curv_forward" (double, default: 0.5)
* "k_dist" (double, default: 1.0)
* "k_ang" (double, default: 1.0)
* "k_avel" (double, default: 1.0)
* "k_dcel" (double, default: 0.2)
* "dist_lim" (double, default: 0.5)
* "dist_stop" (double, default: 2.0)
* "rotate_ang" (?, default: M_PI / 4)
* "max_vel" (double, default: 0.5)
* "max_angvel" (double, default: 1.0)
* "max_acc" (double, default: 1.0)
* "max_angacc" (double, default: 2.0)
* "path_step" (int, default: 1)
* "distance_angle_factor" (double, default: 0.0)
* "switchback_dist" (double, default: 0.3)
* "goal_tolerance_dist" (double, default: 0.2)
* "goal_tolerance_ang" (double, default: 0.1)
* "stop_tolerance_dist" (double, default: 0.1)
* "stop_tolerance_ang" (double, default: 0.05)
* "no_position_control_dist" (double, default: 0.0)
* "min_tracking_path" (?, default: noPosCntlDist)
* "allow_backward" (bool, default: true)
* "limit_vel_by_avel" (bool, default: false)
* "check_old_path" (bool, default: false)

----

## trajectory_recorder

trajectory_recorder node generates Path message from TF.

### Sources

* src/trajectory_recorder.cpp

### Subscribed topics

* /tf

### Published topics

* ~/recpath (nav_msgs::Path)

### Services


### Called services


### Parameters

* "frame_robot" (string, default: std::string("base_link"))
* "frame_global" (string, default: std::string("map"))
* "path" (string, default: std::string("recpath"))
* "dist_interval" (double, default: 0.3)
* "ang_interval" (double, default: 1.0)

----

## trajectory_saver

trajectory_saver node saves Path message to file.

### Sources

* src/trajectory_saver.cpp

### Subscribed topics

* ~/recpath (nav_msgs::Path)
* /tf

### Published topics


### Services


### Called services


### Parameters

* "path" (string, default: std::string("recpath"))
* "file" (string, default: std::string("a.path"))

----

## trajectory_server

trajectory_server node loads Path from file and publishes it.

### Sources

* src/trajectory_server.cpp
* src/filter.cpp

### Subscribed topics

* /tf

### Published topics

* ~/path (nav_msgs::Path)
* ~/status (trajectory_tracker::TrajectoryServerStatus)

### Services

* ~/ChangePath (trajectory_tracker::ChangePath)

### Called services


### Parameters

* "path" (string, default: std::string("path"))
* "file" (string, default: std::string("a.path"))
* "hz" (?, default: double(5))
* "filter_step" (double, default: 0.0)

----


# Acknowledgement

This research was supported by a contract with the Ministry of Internal Affairs and Communications entitled, 'Novel and innovative R&D making use of brain structures'


This software was implemented to accomplish the above research.
Original idea of the implemented control scheme was published on:  
S. Iida, S. Yuta, "Vehicle command system and trajectory control for autonomous mobile robots," in *Proceedings of the 1991 IEEE/RSJ International Workshop on Intelligent Robots and Systems (IROS)*, 1991, pp. 212-217.

