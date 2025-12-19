---
title: "Autonomous Aerial CPR Robot"
excerpt: "A flying robotic system designed to deliver immediate, high-quality Cardiopulmonary Resuscitation (CPR) to cardiac arrest victims in hard-to-reach locations. <br/><img src='/images/projects/cpr_robot/concept_art.png' width='300'>"
permalink: /projects/cpr-robot
collection: projects
published: true
# date: 2024-06-01
---

## Overview

Cardiac arrest is a critical medical emergency where every second counts. While **Cardiopulmonary Resuscitation (CPR)** is the standard first-aid treatment, manual CPR is physically exhausting, often inconsistent in quality, and difficult to sustain for the required 30+ minutes. Furthermore, traffic and terrain can delay the arrival of emergency medical services.

This project proposes a **Flying Mechanical CPR Robot**—an autonomous aerial vehicle capable of flying directly to a patient's location and performing mechanical chest compressions. This system aims to solve the "last mile" problem in emergency response, ensuring consistent, high-quality CPR delivery before an ambulance arrives.

<!-- <div style="text-align: center;">
    <img src="/images/projects/cpr_robot/concept_art.png" alt="Flying CPR Robot Concept" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: Concept of the aerial robot deploying to perform CPR on a patient.</em></p>
</div> -->


<div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap;">
    <div style="flex: 1; text-align: center; min-width: 300px;">
    <img src="/images/projects/cpr_robot/concept_art.png" alt="Flying CPR Robot Concept" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: Concept of the aerial robot deploying to perform CPR on a patient.</em></p>
    </div>
    <div style="flex: 1; text-align: center; min-width: 300px;">
      <video width="98%" controls>
          <source src="/videos/cpr_demo2.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>
    <p><em>Demonstration of the aerial CPR robot design.</em></p>
    </div>
</div>

## System Workflow

The robot operates through a multi-stage autonomous workflow designed to minimize human intervention and maximize speed:

1.  **Deployment:** Upon receiving an emergency signal, the drone takes off and navigates to the GPS coordinates.
2.  **Visual Targeting:** Using onboard cameras and computer vision, the robot identifies the patient and determines the optimal landing position.
3.  **Positioning:** The drone lands on the patient's chest area, utilizing its landing gear to stabilize against the body.
4.  **Execution:** The mechanical arm deploys to perform rhythmic chest compressions according to international CPR standards (depth and frequency).

In this project phase, we focus on the control algorithms and simulation of the compression and holding mechanism to ensure safe and effective operation.


<!-- <div style="text-align: center;">
    <img src="/images/projects/cpr_robot/workflow_diagram.png" alt="Operational Workflow" width="90%">
    <p><em>Fig 2: The operational sequence from takeoff to active resuscitation.</em></p>
</div> -->

## Control & Simulation

To ensure patient safety and compression efficacy, we developed a robust control system validated through **MATLAB/Simulink** simulations.

### Dynamics Modeling
We modeled the robot's kinematics and dynamics to account for the reaction forces generated during chest compressions. The system utilizes:
* **Inverse Kinematics Solver:** To calculate the necessary joint angles for precise end-effector positioning.
* **Inverse Dynamics Solver:** To compute the required motor torques.

<div style="text-align: center;">
    <img src="/images/projects/cpr_robot/dynamic.png" alt="Dynamics Simulation" width="90%">
    <p><em>Fig 2: Dynamics simulation.</em></p>
</div>

### PID Control Strategy
A **PID (Proportional-Integral-Derivative)** controller was implemented to manage the position and force of the compression arm. This ensures:
* **Disturbance Rejection:** The system maintains stability even when subjected to external disturbances (e.g., wind or patient movement).
* **Precision:** The compression depth is tightly regulated to prevent injury while ensuring effective blood circulation.

<div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap; margin-top: 20px;">
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/cpr_robot/control_architecture.png" alt="Control Architecture" width="95%" style="border-radius: 5px;">
        <p><em>Fig 3: Control System Block Diagram</em></p>
    </div>
    <div style="flex: 1; text-align: center; min-width: 300px;">
      <video width="98%" controls>
          <source src="/videos/cpr_demo1.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>
        <p><em>System response with PID control, showing stabilized trajectory tracking.</em></p>
    </div>
</div>

## Results

Simulation results demonstrated that the PID-controlled system could effectively reject disturbances and track the desired compression trajectory. The system maintained stable operation, proving the feasibility of an aerial manipulator performing high-force tasks like CPR.

## Future Work
* **Computer Vision Integration:** Implementing real-time patient detection and pose estimation.
* **Prototype Fabrication:** Building a physical scale model to validate the flight and compression mechanics.
* **Safety Protocols:** Developing emergency stop mechanisms and soft-landing protocols to protect the patient.