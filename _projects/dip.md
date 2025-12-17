---
title: "Deep Learning-Enhanced UWB-IMU Motion Capture System"
excerpt: "A full-scene motion capture solution fusing Ultra-Wideband (UWB) positioning with Inertial Measurement Units (IMU) using Recurrent Neural Networks for precise rehabilitation monitoring. <br/><img src='/images/projects/dip/system_overview.png' width='500'>"
permalink: /projects/dip
collection: projects
published: true
# venue: "Undergraduate Innovation Training Program (National Level)"
# date: 2024-04-25
---

## Overview

Accurate motion capture is essential for medical diagnosis and rehabilitation, particularly for assessing gait and balance in Parkinson's disease or post-stroke recovery. Traditional optical systems are expensive and spatially restricted, while standalone Inertial Measurement Unit (IMU) systems suffer from position drift over time.

This project presents a **low-cost, full-scene motion capture system** that fuses **UWB (Ultra-Wideband)** positioning technology with IMU data. By leveraging a **Deep Learning framework (RNN)**, the system reconstructs full-body poses from sparse sensor nodes (only 6 sensors), achieving high precision suitable for home-based digital rehabilitation.

<div style="text-align: center;">
    <img src="/images/projects/dip/architecture.png" alt="System Architecture" width="70%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: System architecture showing the fusion of on-body UWB-IMU sensors and the base station network.</em></p>
</div>

## System Hardware & Architecture

We developed a custom hardware ecosystem to support real-time, wireless data acquisition:

* **Wearable Sensor Nodes:** Integrated modules containing a 9-axis IMU and a UWB communication chip. These nodes are placed on 6 key body segments: Left/Right Forearms, Left/Right Lower Legs, Head, and Pelvis.
* **Base Stations:** A network of UWB anchors that synchronize via clock references to provide Time Difference of Arrival (TDOA) measurements.
* **Communication Protocol:** A custom wireless protocol manages the "Link Phase" (device discovery) and "Work Phase" (TDMA-based data streaming) to support multiple active tags simultaneously.

<!-- <div style="display: flex; justify-content: space-around; align-items: center; flex-wrap: wrap;">
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/dip/uwb_imu_node.png" alt="Sensor Node PCB" width="95%">
        <p><em>Custom UWB-IMU Sensor Node</em></p>
    </div>
    <div style="flex: 1; text-align: center; min-width: 300px;">
        <img src="/images/projects/dip/base_station.png" alt="Base Station" width="95%">
        <p><em>UWB Base Station Design</em></p>
    </div>
</div> -->

<div style="text-align: center;">
    <img src="/images/projects/dip/base_node.svg" alt="System Architecture" width="70%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 2: Custom UWB-IMU Sensor Node and Base Station Design.</em></p>
</div>

## Methodology: Fusion & Reconstruction

The core innovation lies in the multi-stage algorithmic pipeline that processes raw sensor data into a realistic 3D human pose.

### 1. UWB Positioning & Signal Classification
UWB signals are susceptible to Non-Line-of-Sight (NLOS) errors caused by body occlusion. We implemented:
* **NLOS Classification:** A threshold-based classifier analyzes the Received Signal Strength (RSS) and First Path power to identify and filter out unreliable NLOS signals (Accuracy: 72.4%).
* **TDOA Calculation:** The CHAN algorithm computes the initial 3D coordinates of each tag based on time-difference measurements.

### 2. Sensor Fusion (Kalman Filter)
To mitigate IMU drift and UWB jitter, we employed an **Kalman Filter (KF)**. The IMU acceleration drives the state prediction, while UWB position data serves as the measurement update.
* **Result:** The fusion significantly reduced noise, achieving a Root Mean Square Error (RMSE) of **4.64 cm** even under simulated noise conditions of 10 cm.

### 3. Deep Learning Pose Reconstruction
We designed a **Recurrent Neural Network (RNN)** framework to map sparse sensor data to a full-body **SMPL model**:
* **Input:** A 72-dimensional vector combining normalized IMU data (acceleration + rotation) and corrected leaf node positions (from the EKF fusion).
* **Architecture:** Two stacked RNNs. **RNN1** estimates the positions of all joints, and **RNN2** converts these positions into joint rotation matrices for the SMPL model.

<div style="text-align: center;">
    <img src="/images/projects/dip/rnn_pipeline.png" alt="Deep Learning Pipeline" width="85%">
    <p><em>Fig 3: The pipeline flowing from raw UWB/IMU data through the EKF and RNN to output the final human pose.</em></p>
</div>

## Experimental Results

### IMU-UWB Kalman filter fusion positioning results
<div style="text-align: center;">
    <img src="/images/projects/dip/results_graph.png" alt="Tracking Results" width="70%">
    <p><em>Fig 4: The first row compares the ground truth (blue) with the filtered UWB data (orange), and the second row compares the unfiltered UWB (blue) with the filtered one (orange).</em></p>
</div>

### Deep Learning Motion Reconstruction Results
The system was evaluated using the **DIP-IMU dataset** and simulated UWB noise profiles. Our method ("Ours UIP*") was benchmarked against state-of-the-art methods like TransPose and DIP.

### Performance Comparison
Our fused approach demonstrated superior tracking accuracy, particularly in global positioning, which is a common weakness in IMU-only systems.

| Method        | SIP Err (&deg;) | Angle Err (&deg;) | Pos Err (cm) | Mesh Err (cm) | Jitter (km/s&sup3;) |
| :------------ | :-------------: | :---------------: | :----------: | :-----------: | :-----------------: |
| DIP           |      15.16      |       15.16       |     8.96     |     7.33      |          -          |
| TransPose     |      16.68      |       8.85        |     5.95     |     7.09      |        1.46         |
| TIP           |      5.49       |       16.20       |     9.17     |     6.61      |          -          |
| **Ours UIP*** |    **9.63**     |     **6.31**      |   **3.48**   |   **4.03**    |      **0.42**       |

* **Lowest Position Error:** 3.48 cm (vs. 5.95 cm for TransPose).
* **High Stability:** Lowest jitter score (0.42), indicating smooth motion reconstruction essential for clinical analysis.


## Conclusion

This project successfully demonstrated a prototype for a full-scene rehabilitation motion capture system. By combining the absolute positioning of UWB with the high update rate of IMUs via a deep learning framework, we achieved a low-cost, high-accuracy solution that outperforms existing sparse-IMU methods in positional tracking.

## Demo Video

<div style="display: flex; align-items: center;">
    <div style="flex: 0 0 24%; text-align: center;">
      <video width="98%" controls>
          <source src="/videos/dip_demo1.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>
    </div>
    <div style="flex: 0 0 76%; text-align: center;">
      <video width="98%" controls>
          <source src="/videos/dip_demo2.mp4" type="video/mp4">
          Your browser does not support the video tag.
      </video>
    </div>
</div>

## Achievements
<!-- This work was published in **IEEE Transactions on Instrumentation and Measurement (2025)**. -->
This work is also patented under **CN Patent No. CN118634071A**.
This work won a **$3,000 Innovation and Entrepreneurship Grant**.