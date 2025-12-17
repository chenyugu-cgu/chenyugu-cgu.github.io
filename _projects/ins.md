---
title: "Portable Inertial Navigation System for Total Hip Arthroplasty"
excerpt: "A wireless, high-precision inertial navigation system designed for the Direct Anterior Approach (DAA) in hip replacement surgeries. <br/><img src='/images/projects/ins/system_overview.png' width='500'>"
permalink: /projects/ins
collection: projects
published: true
venue: "IEEE Transactions on Instrumentation and Measurement"
# date: 2025-03-06
---

## Overview

Total Hip Arthroplasty (THA) is a critical procedure for treating end-stage hip disorders. While the **Direct Anterior Approach (DAA)** is gaining popularity for its minimally invasive nature and faster recovery times, precise prosthesis placement remains a challenge. Traditional navigation methods like CT are costly, complex, and involve radiation exposure.

This project introduces a **novel, portable, and wireless Inertial Navigation System (INS)** tailored specifically for DAA THA. The system provides real-time, radiation-free quantification of acetabular cup orientation—specifically the Radiographic Anteversion (RA) and Radiographic Inclination (RI) angles—helping surgeons achieve optimal implant positioning.

<div style="text-align: center;">
    <img src="/images/projects/ins/fig1_concept.png" alt="Concept of the INS for THA" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: The proposed system in a surgical setting versus traditional methods.</em></p>
</div>

## System Architecture

The system integrates custom hardware and software to ensure seamless clinical workflow:

### 1. Hardware Design
The system consists of two compact, wireless sensor modules designed with integrated circuitry and sanitizable housing:
* **On-Body Module:** Attached to the Anterior Superior Iliac Spine (ASIS). It utilizes a gyroscope to monitor pelvic rotation and ensure the reference frame remains consistent.
* **On-Handle Module:** Attached to the cup impact handle. It features a 9-axis IMU (Accelerometer, Gyroscope, Magnetometer) to track the handle's pitch and yaw in real-time.

Both modules utilize **ESP32 MCUs** for high-speed Wi-Fi data transmission and feature magnetic contact charging for ease of use in sterile environments.

<!-- <div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap;">
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/ins/hardware_modules.png" alt="Hardware Modules" width="95%">
        <p><em>Fig 2: Integrated On-Handle and On-Body Sensor Modules</em></p>
    </div>
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/ins/circuit_design.png" alt="Circuit Design" width="95%">
        <p><em>PCB Design with ESP32 and IMU</em></p>
    </div>
</div> -->

<div style="text-align: center;">
    <img src="/images/projects/ins/hardware_modules.png" alt="Hardware Modules" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 2: Integrated On-Handle and On-Body Sensor Modules</em></p>
</div>

### 2. Software & Visualization
Data is transmitted via UDP to a host computer running a custom **Unity 3D** application. This provides surgeons with:
* Real-time numerical feedback of **RA** and **RI** angles.
* A 3D visualization of the pelvic model and instrument orientation.
* Color-coded "safe zones" to guide placement accuracy.

<!-- <div style="text-align: center;">
    <img src="/images/projects/ins/fig1_concept.png" alt="Concept of the INS for THA" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: The proposed system in a surgical setting versus traditional methods.</em></p>
</div> -->

## Experimental Design

To ensure clinical viability, the study employed a rigorous two-phase validation protocol, testing the system at both the individual sensor level and the full system level.

### Phase 1: Sensor Validation (Robotic Reference)
The fundamental accuracy and stability of the sensors were evaluated using a high-precision commercial robotic arm (GLUON-6L3) as the ground truth.
* **Static Validation:** Sensors were rotated in discrete 5&deg; increments from 0&deg; to 90&deg; across all three Degrees of Freedom (DoF) to measure mean error and standard deviation.
* **Dynamic Validation:** The robot executed sinusoidal motion profiles at varying angular velocities (from &pi;/8 to &pi;/20 rad/s). We calculated the Root Mean Square Error (RMSE) to assess performance under motion.
* **Stability Testing:** A 5-minute continuous operation test simulated the typical measurement window of a DAA surgery to quantify sensor drift and reliability.

### Phase 2: System Validation (Model Simulation)
A realistic surgical simulation was conducted to validate the calculation of RA and RI angles in a clinical-like setup
* **Setup:** An **Optical Motion Capture (OMC)** system (Raptor-4S) was used as the "gold standard" reference. Markers were placed on a plastic pelvic model and the surgical tools.
* **Procedure:** The operator performed a standardized trajectory simulating the cup impact process: aligning with the central axis, rotating approximately 60&deg; along the Z-axis, and then 60&deg; along the X-axis.
* **Evaluation:** The RA and RI angles calculated by our INS were compared against the OMC reference data to determine the cumulative probability distribution of absolute error.

<div style="text-align: center;">
    <img src="/images/projects/ins/experiment_setup.png" alt="Experimental Setup with Robotic Arm and OMC" width="80%">
    <p><em>Fig 3: Experimental setup showing (a) Sensor validation with robotic arm and (b) System validation with Optical Motion Capture.</em></p>
</div>

## Validation & Results

The system was rigorously validated through sensor-level experiments (using a robotic arm) and system-level simulations (using a pelvic model and Optical Motion Capture as ground truth).

### Key Performance Metrics
* **Accuracy:** The system achieved a Root Mean Square Error (RMSE) of **1.24° for RA** and **1.89° for RI**.
* **Reliability:** Intra-session correlation coefficients (CC) exceeded **0.995**.
* **Stability:** Dynamic sensor drift was measured at less than **0.13°/min**, ensuring consistent performance throughout typical surgical durations.

<div style="text-align: center;">
    <img src="/images/projects/ins/results_graph.png" alt="Validation Results" width="80%">
    <p><em>Fig 4: Dynamic validation showing minimal error compared to optical motion capture references.</em></p>
</div>

## Demo Video

<div style="text-align: center;">
    <video width="80%" controls>
        <source src="/videos/ins_demo.mov" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <p><em>Real-time visualization of cup orientation during model simulation.</em></p>
</div>

## Achievements
This work was published in **IEEE Transactions on Instrumentation and Measurement (2025)**.
This work is also patented under **CN Patent No. CN118870291A**.
This work was funded by **Shenzhen People Hospital with $15,000 USD**.

**Citation:**
> **C. Gu**, Y. Yu, X. He, L. Zhang, Z. Xi, Y. Liu, G. Li, and M. Zhang, "A Portable Inertial Navigation System for Total Hip Arthroplasty Targeting Direct Anterior Approach," in *IEEE Transactions on Instrumentation and Measurement*, vol. 74, 2025.

[Download Paper (PDF)](/files/papers/2025_IEEE_TIM_INS_THA.pdf){: .btn .btn--info}