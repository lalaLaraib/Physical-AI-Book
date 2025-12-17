---
title: "Glossary"
description: "Key terms used throughout the textbook"
---

## Glossary

## ROS 2 (Robot Operating System 2)
Middleware framework for robotics that manages communication between software components.

Supports distributed computing, real-time communication, and multiple programming languages (Python, C++).

Example: A humanoid robot uses ROS 2 nodes to handle perception, planning, and motor control.

URDF (Unified Robot Description Format)
XML-based format for representing robot models.

Describes links, joints, sensors, and physical properties.

Example: Defining a humanoid arm with all its joints and link dimensions for simulation in Gazebo.

Xacro (XML Macro Language)
Macro language used to generate parameterized URDF files.

Facilitates modularity and reusability of robot models.

Example: A single Xacro file can generate different limb lengths or sensor configurations without rewriting URDF.

DDS (Data Distribution Service)
Underlying communication layer used by ROS 2.

Provides reliable, real-time, and decoupled data exchange between nodes.

Supports Quality-of-Service (QoS) policies like reliability, durability, and deadline enforcement.

VLA (Vision-Language-Action)
Multimodal robotics architecture integrating vision, natural language understanding, and action generation.

Enables robots to interpret human commands and act in dynamic environments.

Example: Robot receives “pick up the red block,” detects it with cameras, and executes a grasp.

Sim-to-Real
The process of transferring models, controllers, or policies trained in simulation to physical robots.

Requires domain randomization and careful validation to ensure real-world performance.

Example: A walking gait optimized in Gazebo simulation is deployed on a real humanoid robot.

Jetson (NVIDIA Embedded AI Devices)
Family of compact, high-performance devices for edge AI inference and robotics.

Examples: Jetson Orin, Jetson Xavier, used for real-time perception, control, and VLA computations on robots.

Inverse Kinematics (IK)
Mathematical method to compute joint angles required to achieve a desired end-effector pose.

Example: Moving a humanoid hand to grasp a cup while maintaining balance.

Forward Kinematics (FK)
Calculation of end-effector pose from given joint angles.

Example: Predicting the hand position of a robot arm for collision checking.

Zero Moment Point (ZMP)
A point on the support surface where the net moment of forces is zero.

Used to maintain balance in humanoid walking.

Example: Step placement ensures the ZMP stays within the support polygon to prevent tipping.

Domain Randomization
Technique to randomize simulation parameters (lighting, textures, object positions) for robust sim-to-real transfer.

Example: Training a grasping policy on objects with varied colors and sizes to improve real-world generalization.