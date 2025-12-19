---
title: "Interaction between Heart and Movement: Gait Analysis with Single IMU"
excerpt: "Investigating the physiological synergy between the cardiac and locomotor systems using a single chest-mounted Inertial Measurement Unit (IMU). <br/><img src='/images/projects/heart_gait/synergy_concept.png' width='500'>"
permalink: /projects/heart-gait
collection: projects
published: true
# date: 2024-01-08
---

## Overview

The human body functions through complex synergies between systems. A critical but often overlooked interaction exists between the **locomotor system** (muscles used for movement) and the **cardiac system** (heart function). Research suggests that synchronizing gait with the cardiac cycle—specifically "Diastolic Stepping"—can alter heart rate response and improve blood flow efficiency.

This project aims to quantify this interaction by developing a robust gait analysis framework using a **single chest-mounted Inertial Measurement Unit (IMU)**. By correlating gait phases with cardiac cycles, we can explore how the "skeletal muscle pump" assists the "cardiac pump" during exercise.

<div style="text-align: center;">
    <img src="/images/projects/heart_gait/synergy_concept.png" alt="Cardiac and Locomotor Synergy" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: The physiological concept of the skeletal muscle pump working in synergy with the cardiac pump to aid blood flow.</em></p>
</div>

## Theoretical Background

The study focuses on the timing of foot strikes relative to the cardiac cycle:
* **Diastolic Stepping:** Occurs when the foot strike happens during the heart's relaxation phase (diastole). This is hypothesized to aid venous return.
* **Systolic Stepping:** Occurs when the foot strike coincides with the heart's contraction phase (systole).

By analyzing the **Step Rate (SR)** to **Heart Rate (HR)** ratio, we can determine if a coupling exists ($SR/HR \approx 1$).

## System Design & Methodology

Unlike traditional gait analysis that uses multi-node sensor networks or optical motion capture, this system utilizes a **single off-the-shelf IMU (Movesense)** attached to the chest. This configuration minimizes intrusiveness while allowing for the capture of both gross body movement and physiological vibrations.

### 1. Hardware Setup
* **Sensor:** Movesense 6-axis IMU (Accelerometer + Gyroscope).
* **Placement:** Sternum (Chest), fixed with elastic straps.
* **Data Acquisition:** Raw acceleration ($m/s^2$) and angular velocity ($deg/s$) are recorded and synchronized for post-processing.

<div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap; margin-top: 20px;">
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/heart_gait/hardware_setup.png" alt="IMU Chest Placement" width="90%" style="border-radius: 5px;">
        <p><em>Single-IMU Chest Placement</em></p>
    </div>
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/heart_gait/raw_signals.png" alt="Raw IMU Signals" width="90%" style="border-radius: 5px;">
        <p><em>Raw Accelerometer & Gyroscope Data</em></p>
    </div>
</div>

### 2. Algorithm Design
The core challenge is extracting precise orientation and gait events from a noisy chest-mounted sensor.
* **Orientation Estimation:** We implement sensor fusion algorithms to process raw acceleration and gyroscope data, estimating the 3D orientation of the torso.
* **Parameter Extraction:** By analyzing the vertical acceleration peaks and trunk rotation, the system detects **Heel Strikes (HS)** and calculates step cadence.

<div style="text-align: center;">
    <img src="/images/projects/heart_gait/algorithm_flow.png" alt="Algorithm Flowchart" width="85%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 3: Filter design.</em></p>
</div>

## Experimental Workflow

Experiments were conducted in a corridor environment involving natural walking tasks.
1.  **Subject Preparation:** The subject wears the chest strap with the IMU.
2.  **Protocol:** The subject walks back and forth at a normal speed.
3.  **Analysis:** The data is processed to visualize the gait cycle and overlay it with cardiac timing (derived from heart rate monitoring).


<div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap; margin-top: 20px;">
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/heart_gait/results1.png" alt="IMU Chest Placement" width="90%" style="border-radius: 5px;">
        <!-- <p><em>Single-IMU Chest Placement</em></p> -->
    </div>
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/heart_gait/results2.png" alt="Raw IMU Signals" width="90%" style="border-radius: 5px;">
        <!-- <p><em>Raw Accelerometer & Gyroscope Data</em></p> -->
    </div>
</div>
<div style="text-align: center;">
<p><em>Fig 4: Results.</em></p>
</div>
<!-- <div style="text-align: center;">
    <img src="/images/projects/heart_gait/results.png" alt="Results" width="85%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 4: Results.</em></p>
</div> -->

## Demo Video

<!-- <div style="display: flex; align-items: center;">
    <div style="flex: 0 0 76%; text-align: center;">
      <video width="98%" controls>
          <source src="/videos/heart-gait_demo1.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>
    </div>
    <div style="flex: 0 0 24%; text-align: center;">
      <video width="98%" controls>
          <source src="/videos/dip_demo2.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>
    </div>
</div> -->

<div style="text-align: center;">
    <video width="80%" controls>
        <source src="/videos/heart-gait_demo1.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <!-- <p><em>Real-time visualization of cup orientation during model simulation.</em></p> -->
</div>
<div style="text-align: center;">
    <video width="80%" controls>
        <source src="/videos/heart-gait_demo2.mp4" type="video/mp4">
        Your browser does not support the video tag.
    </video>
    <!-- <p><em>Real-time visualization of cup orientation during model simulation.</em></p> -->
</div>

## Future Directions

This framework establishes the baseline for "Heart-Gait" interaction studies. Future work involves:
* Integrating ECG data to precisely timestamp R-peaks relative to heel strikes.
* Testing biofeedback mechanisms to encourage "Diastolic Stepping" for improved athletic performance or cardiac rehabilitation.