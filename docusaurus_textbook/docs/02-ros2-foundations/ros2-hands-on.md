---
title: "ROS 2 Core Concepts"
description: "Nodes, Topics, Services, Actions, DDS — Deep and Practical Understanding"
---

## S 2 Core Concepts

This chapter provides a deeper exploration of the fundamental building blocks of ROS 2. These concepts form the communication fabric of modern humanoid robots. Each section includes principles, engineering guidelines, and simple diagrams to help you reason about larger robotic systems.

## Nodes

A node is the smallest independent software unit in a ROS 2 system. The philosophy is simple one node equals one responsibility

## Key Principles

1 Single Responsibility Principle SRP
Each node performs one clear well defined function. This ensures modularity easier debugging and maintainability

Examples

- A camera driver node captures images
- A face detection node processes those images
- A head control node adjusts servo motors

2 Lifecycle Management
Certain nodes follow a lifecycle model unconfigured inactive active shutdown
Lifecycle nodes enable predictable startup sequences automated recovery and safer hardware handling

Example
A humanoid leg controller can remain inactive until all IMU sensors are correctly calibrated

Head Tracking Node
Output neck target

- Topics

A topic is a named communication channel for continuous streaming data

Best Uses

Sensor data images IMU LiDAR joint states

Robot internal state velocities estimated pose battery status

Naming Conventions

Adopt clear and hierarchical patterns for readability

**Examples**
camera front image raw
arm left joint states
locomotion footstep plan

Message Rate Guidelines

Define expected publish frequencies upfront

**Example**

IMU 200 to 1000 Hz

Camera 30 to 60 Hz

Joint states 50 to 200 Hz

Knowing expected rates helps diagnose delays dropped messages or scheduling issues

Topic Flow Diagram
Camera Node to camera image raw to Vision Node to vision objects

**Services**

A service is a synchronous request response interaction between nodes

When To Use Services

Use services for short operations that complete quickly and require an immediate answer

Common examples

Query current robot mode

Request calibration

Change configuration parameters

Fetch a specific data snapshot

Client Node request Service Server
Client Node response Service Server

Services should not be used for long operations or streaming data

Actions

An action supports tasks that take time provide ongoing feedback and can be cancelled mid execution

Ideal Use Cases

Walking to a target location

Reaching and grasping an object

Performing a multi step manipulation sequence

Executing a speech synthesis routine

Action Flow Overview
Client send goal to Server
Client feedback loop from Server
Client cancel goal to Server if required
Client final result from Server

**Key Advantage**

Actions prevent blocking the entire system while a long task executes preserving responsiveness

QoS Quality of Service Guidelines

QoS policies define how messages are delivered Proper choices ensure reliability without unnecessary overhead

For Sensor Data High Frequency

BEST EFFORT allows dropped frames to maintain speed

Useful for camera streams LiDAR depth sensors

For Safety Critical Data

RELIABLE ensures no message loss

Use for joint commands IMU data used for balance emergency stop signals

Deadlines and History

Use deadline constraints for tight control loops

Use KEEP LAST with a small history for time sensitive topics

Documentation Requirement

Each topic should have a small specification table

Topic imu data
QoS RELIABLE
History Keep Last 5
Frequency 200 Hz
Reason Used for balance control

Executors and Scheduling

Executors manage the execution of callbacks inside nodes Scheduling determines how fast and how safely those callbacks run

Choosing Executor Type

Single threaded executor

Predictable

Good for low load systems

Easier to debug

Multi threaded executor

Allows parallel callback execution

Required for workloads with heavy perception tasks

Real Time Considerations

Humanoid robots often require millisecond level response

Guidelines

Assign critical control loops to isolated CPU cores

Minimize memory allocation inside loops

Use ROS 2 real time executors where available

Use RT Linux for deterministic scheduling

**Example**

A balance control loop may run at 500 Hz and must never be delayed by a vision node at 30 Hz

Tools and Workflow

A professional ROS 2 development workflow includes conventions tests and shared artifacts

Naming Conventions

Maintain consistency for

Topics

Services

Actions

Parameters

Frames base link map odom

Shared Data Dictionary

A team wide document describing

All message types

Topic names

Valid value ranges

Units m rad Nm C

This prevents mismatches and miscommunication in multi developer robotics teams

Testing Procedures

Include tests for

Message validation check fields units ranges

Message replay play recorded data to test perception planning offline

Stress testing high frequency publishing under load

Diagrams and Patterns

Including diagrams is essential to communicate subsystem interactions clearly

System Level Block Diagram
Perception to Planning to Control

Perception Vision
Planning Path Task
Control Loop Motors Joints

Action Lifecycle Sequence Diagram
Client send goal to Server
Client feedback from Server
Client feedback from Server
Client cancel to Server
Client final result from Server

Failure Mode Considerations

Document what happens when

A node stops publishing

A topic has mismatched QoS

The action server times out

Data arrives late or out of order

These patterns help design robust humanoid robotic systems