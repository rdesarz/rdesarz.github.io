---
title: "Movu iFollow - Autonomous Warehouse Robot"
excerpt: "Full-stack robotics development for autonomous logistics robots in warehouse environments."
date: 2024-10-07
tags: [C++, ROS2, Motion Planning, MPC, Localization, Fleet Management]
header:
  teaser: /assets/images/movu-ifollow.png
---

Founding member at Movu Robotics' iFollow autonomous mobile robot (AMR), from early prototype to production deployment in warehouse logistics operations.

## Project Overview

Movu Robotics develops autonomous mobile robots designed to transport heavy carts in warehouse and logistics environments. The iFollow robot follows human operators, autonomously navigates to designated locations, and coordinates with a fleet to optimize warehouse operations.

I contributed across the full robotics stack—from low-level sensor fusion and localization to high-level motion planning and fleet coordination—helping transform an early prototype into a production-ready system.

## Phase 1: Early Prototype Development (Startup Phase)

### Core Robotics Software Foundation
- Built the initial robotics software architecture from scratch in **C++/ROS**
- Took end-to-end ownership of perception, localization, and planning modules
- Worked in a fast-paced startup environment with rapid prototyping cycles

### Localization & Odometry
- Implemented **sensor fusion** combining **2D LiDAR** and **IMU** data
- Developed robust odometry estimation for accurate pose tracking
- Ensured reliable localization in dynamic warehouse environments with moving obstacles

### Multi-Robot Coordination
- Designed **trajectory planning algorithms** for synchronized multi-robot operations
- Implemented fleet coordination logic to prevent collisions and optimize throughput
- Enabled multiple robots to work collaboratively in shared warehouse spaces

## Phase 2: Production System Development

### ROS2 Navigation Stack
- Designed and deployed custom **ROS2 navigation components**:
  - Advanced path planners for warehouse constraints
  - Trajectory controllers optimized for cart transport
  - Custom behavior tree plugins for task execution
- Enhanced AMR safety and reliability for production warehouse operations
- Integrated emergency stop protocols and collision avoidance systems

### High-Performance Control Libraries
- Developed optimized **C++ libraries** for:
  - Trajectory representation and interpolation
  - Velocity profiling and control
  - Real-time constraint satisfaction (acceleration/jerk limits)
- Achieved **throughput exceeding manual forklift operations**
- Optimized for sub-millisecond control loop performance

### Software Engineering & DevOps
- Established **CI/CD pipelines** for automated testing and deployment
- Implemented code quality standards and review processes adopted team-wide
- Set up release management workflows for production deployments
- Introduced static analysis, unit testing, and integration testing frameworks

### Technical Leadership
- Supervised a master's thesis on **leader-follower navigation algorithms**
- Mentored development from simulation prototypes to hardware deployment
- Guided algorithm validation and performance benchmarking

## Technologies Used

- **C++17/20** - Real-time control and high-performance computing
- **ROS2** - Robot Operating System for modular architecture
- **Navigation2** - Advanced navigation stack
- **2D LiDAR** - SLAM and obstacle detection
- **IMU** - Inertial odometry and sensor fusion
- **Model Predictive Control** - Trajectory tracking and optimization
- **CI/CD** - GitLab CI, Docker, automated testing

## Impact

The robotics software enabled Movu's AMRs to:
- Operate safely in complex warehouse environments with humans and other vehicles
- Exceed manual forklift efficiency for cart transport tasks
- Scale from prototype to multi-robot fleet deployments
- Achieve production-level reliability and safety standards

## Skills Demonstrated

- Full-stack robotics software development
- ROS/ROS2 architecture and navigation
- Real-time localization and mapping (SLAM)
- Multi-robot coordination and fleet management
- High-performance C++ development
- CI/CD and software engineering best practices
- Technical mentorship and leadership
