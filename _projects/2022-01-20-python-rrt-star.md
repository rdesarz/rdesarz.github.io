---
title: 'Python RRT*'
excerpt: "Python implementation of the RRT* motion planning algorithm."
date: 2022-01-20
tags: [Python, Motion Planning, Robotics, Algorithms]
header:
  teaser: /assets/images/02-python-rrt-star.png
---

Python implementation of the RRT* (Rapidly-exploring Random Tree Star) algorithm for optimal path planning in 2D environments with obstacles.

[View on GitHub](https://github.com/rdesarz/rrtstar){: .btn .btn--primary}

## Features

- **RRT* algorithm**: Asymptotically optimal sampling-based path planner
- **Obstacle avoidance**: Collision detection with arbitrary 2D polygons
- **Path optimization**: Rewiring for improved solution quality
- **Visualization**: Real-time plotting of tree growth and final path
- **Configurable parameters**: Step size, search radius, goal bias

## Technologies

- **Python 3** - Implementation language
- **NumPy** - Numerical computations
- **Matplotlib** - Visualization and plotting

## Algorithm Details

RRT* improves upon the basic RRT algorithm by:
1. Selecting best parent node based on cost
2. Rewiring existing nodes when better paths are found
3. Converging to optimal solution as iterations increase

Ideal for mobile robot navigation and path planning research.
