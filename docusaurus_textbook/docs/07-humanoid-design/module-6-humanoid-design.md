---
title: "Module 6: Designing Humanoid Robots"
description: "Kinematics, dynamics, URDF/Xacro, bipedal locomotion, hands and manipulation"
module: 6
duration: "8-12 hours"
prerequisites: "Mechanics basics, ROS 2"
objectives:
  - Model humanoid kinematics in URDF/Xacro (conceptual)
  - Understand dynamic stability, ZMP, and gait cycles
  - Design manipulators and end-effector control
---


## Module 6: Humanoid Design

This module introduces the design principles, modeling techniques, and conceptual analysis required to develop humanoid robots. Students will learn how to structure modular robot descriptions, understand kinematics and dynamics, and integrate hands and manipulation capabilities. The focus is on conceptual understanding, design patterns, and planning workflows, not executable code.

1. URDF/Xacro Design Patterns

URDF (Unified Robot Description Format) and Xacro (XML Macros) are standard ways to define a robot’s structure, joints, sensors, and links. Key design patterns include:

1.1 Modularity

Break the robot into functional components (arms, legs, torso, head, hands).

Each component defined as a separate Xacro macro or file.

Enables reuse and simplifies simulation or testing of individual modules.

1.2 Reusability

Define parameterized links and joints for rapid configuration changes.

Example: scaling limb lengths or replacing actuators without rewriting the URDF.

Facilitate swapping sensors, grippers, or foot modules for different experiments.

1.3 Best Practices

Assign meaningful names to links, joints, and sensors.

Maintain consistent reference frames (base_link, end_effector, camera_link).

Version control URDF/Xacro files for reproducibility and collaboration.

2. Kinematics Overview

Kinematics defines the motion of the robot without considering forces. Key concepts include:

2.1 Forward Kinematics (FK)

Compute the position and orientation of end-effectors given joint angles.

Useful for visualization, trajectory planning, and collision checking.

2.2 Inverse Kinematics (IK)

Compute joint angles required to reach a desired end-effector pose.

Iterative solvers or closed-form solutions depending on robot complexity.

Must consider joint limits, reachability, and workspace constraints.

2.3 Joint Chains & Task Spaces

Humanoids have multiple kinematic chains: arms, legs, spine, head.

Task space: Cartesian space for a given end-effector.

Joint space: Vector of all joint angles controlling the chain.

Mapping between spaces is essential for planning and control.

3. Dynamics & Stability

Humanoid robots must account for forces, mass distribution, and balance. Key topics:

3.1 Center of Mass (CoM)

Location of the robot’s mass weighted across all links.

Critical for maintaining balance during motion.

3.2 Zero Moment Point (ZMP)

Point on the support polygon where net moment is zero.

ZMP control is used to design stable walking or standing gaits.

3.3 Gait Generation Concepts

Step timing: sequence and duration of swing and stance phases.

Foot placement: location of support foot to maintain balance.

Dynamic margins: safety buffer for CoM relative to support polygon.

Stability analysis: predicting tipping, slip, or dynamic failure.

4. Hands & Manipulation

Humanoid manipulation requires understanding grasp mechanics, compliance, and sensor integration.

4.1 Grasp Taxonomy

Power grasp: entire hand envelops object (e.g., carrying a box).

Precision grasp: fingertips control object (e.g., picking up a pen).

Support grasps: stabilizing objects while another limb interacts.

4.2 Compliance

Mechanical or software-based compliance allows safe interaction with humans and objects.

Reduces risk of damage during misaligned grasps or unexpected forces.

4.3 Sensor Integration

Tactile sensors for contact detection.

Force/torque sensors to estimate applied forces.

Vision for object localization and grasp planning.

Conceptual Workflow:

Perception detects a target object → Planner selects grasp type → Controller executes motion with compliant forces → Feedback ensures stability.

5. Lab & Deliverables (Static)
5.1 Humanoid Limb Design Checklist

Students should produce a design checklist including:

Link dimensions and mass properties

Joint types, limits, and actuation method

Sensor placement (encoders, force/torque, tactile)

Compliance features

Reference links to textbooks, URDF/Xacro examples, and standards

5.2 Gait Analysis Plan

Students should produce a conceptual gait analysis, including:

Step sequence and timing (swing vs stance)

Foot placement strategy (support polygon, CoM alignment)

Stability margins (ZMP, CoM relative to polygon)

Key performance metrics (stride length, step width, dynamic stability)

Optional simulations for predicted balance or tipping scenarios

6. Conceptual Summary

URDF/Xacro enables modular and reusable humanoid design.

Kinematics and dynamics analysis ensures reachability, stability, and balance.

Hands and manipulation modules require careful integration of grasp types, compliance, and sensors.

Lab deliverables provide students with structured planning skills for humanoid design and gait analysis.