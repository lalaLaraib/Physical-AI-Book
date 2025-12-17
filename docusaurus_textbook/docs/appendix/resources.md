## Resources

This page compiles official documentation, simulation tools, reference papers, tutorials, and learning materials relevant to Physical AI, Humanoid Robotics, and Vision-Language-Action systems. Resources are organized by topic for easy navigation.

1. Robotics Middleware & Software
ROS 2 (Robot Operating System 2)

Official Documentation and Tutorials: https://docs.ros.org/en/foxy/index.html

Provides step-by-step tutorials for nodes, topics, services, actions, and QoS configurations.

Key Paper: Quigley et al., ROS: an open-source Robot Operating System, ICRA Workshop, 2009.

Use Case: Middleware to integrate perception, planning, and control modules in humanoid robots.

ROS 2 Tools

RViz2: Visualization for robot models, sensors, and simulation outputs.

ros2_control: Hardware abstraction and controller framework.

Gazebo ROS Integration: Simulation plugin to test ROS 2 nodes in virtual environments.

2. Robot Modeling & Simulation
URDF/Xacro

URDF Guide: https://wiki.ros.org/urdf

Xacro Guide: https://wiki.ros.org/xacro

Description: Standard formats to define modular robot geometry, kinematics, and sensor configurations.

Simulation Platforms

Gazebo: Physics-based robot simulation with sensor and actuator modeling. https://gazebosim.org/docs

Unity Robotics Hub: High-fidelity rendering for human-robot interaction experiments and synthetic dataset generation. https://github.com/Unity-Technologies/Unity-Robotics-Hub

NVIDIA Isaac Sim: Advanced simulation for robotics perception, planning, and AI training. https://developer.nvidia.com/isaac-sim

3. Digital Twins & Sim-to-Real

Domain Randomization Techniques: Tobin et al., Domain Randomization for Sim-to-Real Transfer, IROS 2017.

Sim-to-Real Learning: Rusu et al., Progressive Nets for Robot Learning, CoRL 2017.

Best Practices:

Randomize textures, lighting, and object properties.

Validate perception pipelines with synthetic and real datasets.

Version control models, simulation parameters, and synthetic datasets.

4. Vision & Perception
Object Detection & Segmentation

YOLO (You Only Look Once) for real-time detection

Mask R-CNN for pixel-accurate segmentation

Key Papers:

Redmon et al., YOLO: Unified Real-Time Object Detection, CVPR 2016

He et al., Mask R-CNN, ICCV 2017

Depth & 3D Perception

PointNet: Qi et al., Deep Learning on Point Sets for 3D Classification and Segmentation, CVPR 2017

RGB-D Cameras: Intel RealSense, Microsoft Kinect

Best Practices: Downsampling, noise filtering, and timestamp synchronization for multi-sensor fusion

Synthetic Dataset Generation

Unity & Gazebo for generating annotated images, depth maps, and segmentation masks

Domain randomization for sim-to-real robustness

Annotation: Object IDs, segmentation masks, 3D coordinates, metadata

5. Vision-Language-Action (VLA) Systems

Concepts: Integrates perception, language understanding, and action planning.

Key Papers:

Shridhar et al., Perceiver-Actor: Generalist Model for Embodied AI, arXiv 2022

Brohan et al., RT-1: Robotics Transformer for Real-World Manipulation, arXiv 2022

Shah et al., Multimodal Language for Robotic Manipulation, CoRL 2021

Applications: Command parsing, task planning, human-robot collaboration, and autonomous navigation.

6. Reinforcement Learning & Control

Core Text: Sutton & Barto, Reinforcement Learning: An Introduction, MIT Press, 2018

Policy Learning: Levine et al., End-to-End Training of Deep Visuomotor Policies, JMLR 2016

Hierarchical Control: Peng et al., DeepLoco: Dynamic Locomotion Skills via Hierarchical RL, SIGGRAPH 2018

Practice Notes:

Simulate RL policies before deployment

Use hierarchical planners to dispatch skills and subagents

Domain randomization for sim-to-real transfer

7. Humanoid Robotics & Gait

Textbooks:

Craig, J. J., Introduction to Robotics: Mechanics and Control, 4th Edition, Pearson

Springer Handbook of Robotics, Humanoid Robotics: Gait, Balance, and Dynamics

Key Papers:

Kajita et al., Biped Walking Pattern Generation by Using Preview Control of ZMP, ICRA 2003

Practice: Design URDF/Xacro limbs, analyze gait using CoM and ZMP, plan step timing, and foot placement

8. Edge AI & Hardware Platforms

NVIDIA Jetson Series: Orin, Xavier, Nano — for real-time edge AI inference and VLA computation
https://developer.nvidia.com/embedded-computing

Peripherals: RealSense cameras, IMUs, force sensors, and microcontrollers

Design Notes: Balance computation, power consumption, and latency for safe deployment

9. Ethics, Safety & Human-Robot Interaction

Winfield et al., 2019, Ethical Principles for Robotics and AI, Springer Handbook of Robotics

Goodrich & Schultz, 2007, Human-Robot Interaction: A Survey, Foundations and Trends in HCI

Practical Guidelines:

Human-in-the-loop policies for safety-critical commands

Runtime checks: collision detection, torque limits, safe-stop patterns

10. Additional Learning Resources

Online Courses:

ROS 2 Tutorials (ROS website)

NVIDIA Deep Learning & Robotics courses

Coursera: “Modern Robotics: Mechanics, Planning, and Control”

Community Forums:
 
ROS Answers: https://answers.ros.org

Gazebo Q&A: https://community.gazebosim.org

NVIDIA Developer Forums: https://forums.developer.nvidia.com

This Resources page can be used by students to navigate documentation, replicate experiments, and deepen conceptual understanding across all modules of your textbook.