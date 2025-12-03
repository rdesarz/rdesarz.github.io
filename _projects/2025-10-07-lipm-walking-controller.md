---
title: "Biped Walking Controller"
excerpt: "LIPM + ZMP preview control with IK/QP and PyBullet simulation."
date: 2025-10-07
featured: true
tags: [C++, Control Theory, Robotics, Simulation]
header:
  teaser: /assets/images/biped-walking-controller.gif
---

Open-source implementation of **Linear Inverted Pendulum Model (LIPM)** walking pattern generator based on **preview control of the Zero-Moment Point (ZMP)**, following the formulation by _Kajita et al., "Biped Walking Pattern Generation by Using Preview Control of the Zero-Moment Point," ICRA 2003_.

<p align="center">
  <img src="/assets/images/biped-walking-controller.gif" alt="Walking controller simulation" />
</p>

[View on GitHub](https://github.com/rdesarz/biped-walking-controller){: .btn .btn--primary}
[Documentation](https://rdesarz.github.io/biped-walking-controller/){: .btn .btn--info}

---

## Key Features

- **Preview Control**: Optimal ZMP trajectory tracking with anticipation of future reference changes
- **LIPM Dynamics**: Discrete-time Linear Inverted Pendulum Model implementation
- **Inverse Kinematics**: Full-body IK solver using quadratic programming
- **Swing Foot Trajectory**: Sinusoidal time-law based trajectory generation
- **PyBullet Simulation**: Real-time 3D visualization and testing environment
- **Configurable Parameters**: Adjustable step length, height, timing, and control gains

## Technologies Used

- **C++17** - Core controller implementation
- **Eigen** - Linear algebra and matrix operations
- **Python** - Simulation and visualization
- **PyBullet** - Physics simulation
- **CMake** - Build system

---

## Introduction

Humanoid walking requires the generation of dynamically stable trajectories of the Center of Mass (CoM) with 
respect to the Zero-Moment Point (ZMP). This project implements the **discrete-time LIPM** dynamics and 
the associated **optimal preview control law**, reproducing the approach used in model-based humanoid locomotion 
control. The framework includes controller and inverse kinematics modules. The controller is tested in simulation using 
Pybullet, enabling reproducible experiments on trajectory generation and tracking. 

---

## Overview

The objective is to reproduce and analyze the ZMP preview control pipeline:

- Model the robot’s CoM using the 3D LIPM
- Compute optimal CoM trajectories given a reference ZMP sequence using preview control 
- Generate corresponding foot trajectories
- Apply inverse kinematics to produce consistent joint motions
- Apply computed joint positions to the simulated robot in Pybullet

The implementation prioritizes **simplicity** and **experimental reproducibility**, making it suitable for education
purpose.

A documentation is available [here](https://rdesarz.github.io/biped-walking-controller/)

---

## Methodology

### Zero Moment Point and Balance Criterion

The Zero Moment Point (ZMP) is the point on the ground where the resultant contact forces between the feet and the 
ground produce no moment about the horizontal axes. To maintain balance, the ZMP must remain within the robot’s support 
polygon, defined as the convex hull of the contact areas of the feet. Intuitively, this ensures that the ground reaction
forces can generate a counteracting moment to keep the feet flat and prevent tipping, maintaining dynamic equilibrium.
For a more thorough explanation I recommend [this blog post](https://scaron.info/robotics/zero-tilting-moment-point.html) by Stéphane Caron.

### Linear Inverted Pendulum Model

The first step of the controller is to define a reference ZMP trajectory, alternating from one foot to the other at each step.
The objective is to establish a relationship between the position of this reference ZMP and the robot’s Center of Mass (CoM).
This relationship can be derived from a simplified model of the robot’s dynamics known as the Linear Inverted Pendulum Model (LIPM).

The LIPM is derived under the following assumptions:

* The mass of the body is concentrated at a single point, the Center of Mass (CoM).  
* Legs are massless and do not contribute to the system dynamics.  
* The CoM moves on a horizontal plane at a constant height, eliminating vertical motion coupling.  
* No angular momentum is generated about the CoM, meaning the upper body remains still to avoid producing additional moments.

Under these assumptions and for small angles, the inverted pendulum dynamics can be linearized, leading to the following second-order linear equation:

$$
\ddot{x}_c = \frac{g}{z_c} (x_c - x_z)
$$

where $x_z$ denotes the ZMP, $x_c$ the CoM projection, and $z_c$ the constant CoM height.

### Preview Control

In Kajita's paper, the idea is to use a preview control in order to track and anticipate the ZMP reference change.
The control input minimizes a quadratic cost over a finite horizon:

$$
J = \sum_{k=0}^{\infty} \left( Q_e e_k^2 + x_k^T Q_x x_k + R \Delta u_k^2 \right)
$$

yielding a feedback + integral + preview law.  
The resulting controller anticipates future ZMP references, ensuring stable walking trajectories.

The result of the preview controller can be observed with the first example provided in the repository.

### Swing foot trajectory generation

Walking is organized into fixed-duration phases: Single Support (SS) and Double Support (DS). In SS one foot is the 
swing foot and the other is the stance foot; in DS both feet are in contact and no swing foot exists. The swing foot 
horizontal position follows a sinusoidal time law along the world x-axis from $x_0$ to $x_1$ over duration $T_SS$. 
The lateral position $y$ stays constant. The vertical motion is a simple bump with peak clearance $h$ above the ground
reference, returning to the ground at touchdown. Foot orientation is kept constant with yaw=0; 
the sole remains parallel to the floor. All phase durations are configurable.
