---
title: "VLA Action Systems"
description: "Motion planning, IK, RL, task planning (design-level guidance)"
---

## Action & Control

Action and control systems serve as the final stage of a humanoid robot’s intelligence pipeline. After a planner or VLA model determines what the robot should do, the action system determines how it should physically execute that task. This chapter focuses on the conceptual foundations of motion planning, inverse kinematics, control strategies, and safety layers—without relying on executable code.

1. Motion Planning Frameworks (Conceptual Overview)

Motion planning is the process of determining a feasible path or trajectory that moves the robot from its current configuration to a goal state. Different frameworks offer different tradeoffs in computation time, optimality, and environmental assumptions.

1.1 Sampling-Based Planners

Examples: RRT, RRT*, PRM
Characteristics:

Explore space by randomly sampling robot configurations.

Good for high-dimensional robots (arms, humanoids).

Can find solutions in cluttered or complex environments.

Do not guarantee optimality unless using variants like RRT*.

Planning time can vary; occasionally produces jerky paths.

Use cases:

Navigation around obstacles

Manipulation in unstructured environments

1.2 Optimization-Based Planners

Examples: TrajOpt, CHOMP, nonlinear optimization approaches
Characteristics:

Treat planning as an optimization problem.

Generate smooth, continuous trajectories.

Require good initial guesses and stable numerical solvers.

Can incorporate cost functions (energy, safety margins, smoothness).

Use cases:

Precision manipulation

Whole-body control for humanoids

Tasks requiring smooth, predictable motion

1.3 Graph-Based and Search Planners

Examples: A*, D*
Characteristics:

Discrete grid or graph representation of the workspace.

Guarantee shortest path under certain assumptions.

Limited expressiveness for high-DoF manipulator motion.

Use cases:

Navigation on 2D maps

Mobile base pathfinding

Choosing a Motion Planning Framework
Requirement	Suitable Approach
High-dimensional arms	Sampling-based
Smooth motion needed	Optimization-based
2D navigation	Graph-based
Humanoid whole-body planning	Optimization-based with constraints
2. Inverse Kinematics (IK) – Conceptual Walkthrough

Inverse kinematics converts task-level commands (end-effector pose: position + orientation) into joint angles for the robot. IK is essential for tasks like grasping, reaching, tool manipulation, or adjusting balance.

2.1 Inputs

Desired end-effector pose (x, y, z, roll, pitch, yaw)

Robot kinematic model (joint limits, link geometry)

2.2 Outputs

Joint angle configuration that achieves the target pose within tolerance

2.3 IK Methods (Conceptual)

Analytical IK

Closed-form mathematical solution.

Very fast and deterministic.

Only possible for robots with simple, structured geometries (e.g., 6-DoF arms).

Numerical IK

Uses iterative solvers (Jacobian-based methods).

Works for complex humanoid arms or full-body control.

Can incorporate constraints (balance, collision avoidance).

May converge slowly or get stuck in local minima.

2.4 IK Constraints

Joint limits

Self-collision avoidance

Maintaining balance (for humanoids)

Tool alignment constraints

Example:

“Place the right hand at this 6D pose while keeping the center of mass within the support polygon.”

3. RL vs Model-Based Control

Humanoid robots can execute motions through reinforcement learning (RL), model-based control, or hybrid strategies. Understanding their strengths and limitations is essential for system design.

3.1 Model-Based Control

Includes PID, impedance control, whole-body controllers, and model predictive control (MPC).

Strengths:

Predictable and stable

Works well when dynamics are known

Suited for safety-critical motions (walking, lifting)

Limitations:

Requires accurate dynamics and environment modeling

Can struggle with complex contact interactions

Best for:

Balancing and gait control

Precise industrial-like motions

Safety-critical tasks requiring high reliability

3.2 Reinforcement Learning (RL)

RL policies learn from trial and error—often in simulation—before deployment.

Strengths:

Handles complex dynamics and contact-rich tasks

Learns adaptive strategies (push recovery, object manipulation)

Good for tasks where modeling is difficult

Limitations:

Requires extensive simulation tuning

Sim-to-real transfer can fail without domain randomization

Harder to guarantee safety or interpretability

Best for:

Dexterous manipulation

Locomotion in varied environments

Unstructured or partially known environments

3.3 Hybrid Strategies

Modern humanoid systems frequently combine model-based control with RL.

Pattern:

RL provides high-level actions or policy guidance.

Model-based controllers ensure stability and safety.

Example:

RL decides where to step; MPC ensures the step is executed safely.

Safety Layer (Text Only)

The safety layer ensures that all actions—whether generated by planners, IK solvers, or RL policies—are executed safely. It acts as an independent “gatekeeper” that verifies trajectories before and during execution.

1. Runtime Safety Checks
1.1 Collision Monitoring

Predict collisions with the environment and self-collisions.

Reject or modify unsafe trajectories before execution.

Run continuous checks during motion (closed-loop monitoring).

1.2 Joint Limit Enforcement

Ensure joint angles, velocities, and accelerations remain within safe ranges.

Prevent hyperextension or mechanical stress.

1.3 Torque and Force Thresholds

Monitor actuator torque to detect overloads.

Prevent damage from unexpected impacts or grasp failures.

1.4 Velocity and Workspace Constraints

Cap movement speed around humans.

Respect predefined boundaries (e.g., safe reach zones).

2. Human Override & Safe-Stop Patterns
2.1 Manual Override

Operator can interrupt tasks at any time.

Typical channels: buttons, voice commands, gesture recognition.

2.2 Emergency Stop (E-Stop)

Hardwired, non-software-dependent cutoff.

Immediately disables motors or power supply.

2.3 Safe-Stop Behaviors

When something goes wrong, the robot may:

Freeze joints in a safe posture

Retract to a neutral position

Slowly power down actuators

Inform operator via audio or signals

2.4 Supervisory Safety Logic

Independent safety controllers perform:

Policy auditing (reject suspicious commands)

Monitoring LLM or planner outputs for hallucinations

Ensuring groundedness with sensor data