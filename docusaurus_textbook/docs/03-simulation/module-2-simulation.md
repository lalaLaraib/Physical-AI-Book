---
title: "Module 2: Simulation & Digital Twins"
description: "Physics simulation, Gazebo, Unity, and building digital twins"
module: 2
duration: "8-12 hours"
prerequisites: "ROS 2 basics"
objectives:
  - Understand Gazebo and Unity for robot simulation
  - Build digital twins and simulate sensors
  - Prepare environments for sim-to-real transfer
---

## Module 2: Simulation & Digital Twins

Simulation serves as the critical bridge between robotic design and real-world deployment. It allows teams to test algorithms, evaluate hardware assumptions, and refine control architectures before risking physical prototypes. This module provides a structured foundation for building simulation pipelines using Gazebo for physics-accurate modeling and Unity for high-fidelity rendering, allowing students to integrate both platforms into a coherent digital-twin workflow.

By the end of this module, learners will understand how to construct robot models using URDF/SDF formats, configure sensor simulations, and plan synthetic dataset generation for perception systems. The module also emphasizes the principles of sim-to-real transfer so that simulation assets remain consistent, validated, and reproducible across development teams.

## What You Will Learn

How to set up concept-level robot models in Gazebo using URDF and SDF files.

How to leverage Unity for advanced visuals, human-robot interaction experiments, and high-resolution dataset production.

How to simulate essential robotic sensors including RGB and depth cameras, LiDAR, IMU units, force/torque sensors, and contact detectors.

How to design pipelines for generating synthetic datasets suitable for training modern perception and machine learning models.

How to plan and document domain randomization, system identification, and other techniques essential for robust sim-to-real transfer.

Learning Activities (Static)
1. Simulated Environment Design Checklist

Students will create a structured checklist covering:

Physics Configuration: gravity vector, solver settings, friction and restitution coefficients, time-step selection, collision layer definitions.

Lighting & Visuals: ambient lighting, directional lights, noise profiles, shadow settings, HDR environments, texture resolution.

Environment Assets: object placement rules, scaling, material definitions, scene variability for dataset generation.

Performance Considerations: CPU vs GPU physics loads, expected frame rate, simulation determinism requirements.

2. Synthetic Dataset Planning

Students will design a dataset strategy that includes:

Object Categories: classes relevant to perception tasks (tools, obstacles, surfaces, human models).

Pose and Motion Variations: ranges of rotation, translation trajectories, motion primitives, and occlusion conditions.

Lighting & Texture Variations: domain randomization settings, reflectivity ranges, noise injection, chromatic shifts.

Annotation Schema: bounding boxes, segmentation masks, depth maps, optical flow, keypoints, and metadata fields.

3. Sim-to-Real Transfer Planning

Students will define a complete transfer process, including:

Domain Randomization List: textures, lighting variations, geometry perturbations, sensor noise profiles, motion noise, and latency models.

System Identification Parameters: robot mass distribution, joint friction values, actuator delays, controller gains.

Model Export & Reproducibility: how simulation parameters are recorded, validated, version-controlled, and mirrored onto real robots.