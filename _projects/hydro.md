---
title: "Design and Modeling of a Polymer-based Hydraulic Continuum Robot"
excerpt: "A 2.14 mm OD hydraulically actuated soft robot designed for minimally invasive surgery, featuring a novel routing design to minimize twisting and hysteresis modeling for precise control. <br/><img src='/images/projects/hydro/robot_design.png' width='500'>"
permalink: /projects/hydro
collection: projects
published: true
# venue: "2026 International Symposium on Medical Robotics (ISMR)"
# date: 2026-04-01
---

## Overview

Minimally Invasive Surgery (MIS) relies on tools that can navigate complex anatomical pathways without causing trauma. While continuum robots offer inherent compliance and steerability, actuating them at the meso-scale (millimeter scale) remains challenging. Tendon-driven systems suffer from friction, and magnetic systems require bulky external setups.

This project presents a **hydraulically actuated polymer-based continuum robot** with an outer diameter (OD) of just **2.14 mm**. By utilizing hydraulic pressure within a custom-fabricated actuator, the robot achieves large bending angles and smooth motion. The research focuses on optimizing force transmission, minimizing undesirable twisting effects ("screw motion"), and accurately modeling the non-linear hysteresis inherent in soft actuators.

<div style="text-align: center;">
    <img src="/images/projects/hydro/robot_design.png" alt="Robot Design and Actuation" width="80%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
    <p><em>Fig 1: (a) CAD model of the joint showing the routing blocks and notched sheath. (b-d) Fabrication process of the coiled hydraulic actuator.</em></p>
</div>

## System Design

The robot is constructed from MRI-compatible materials to ensure future clinical viability:

* **Outer Sheath:** A laser-micromachined Polyimide (PI) tube with a Unidirectional Asymmetric Notch (UAN) pattern to facilitate bending.
* **Hydraulic Actuator:** A silicone tube wrapped in a helical polymer coil (fishing line) to constrain radial expansion and promote linear extension.
* **Routing Blocks:** 3D-printed blocks placed internally to constrain the actuator to the centerline, ensuring efficient force transmission.

<!-- ### Twist Reduction Analysis
A common issue with coiled hydraulic actuators is "screw motion"—unwanted twisting during extension. We compared three design variations:
1.  **$S_1$:** Actuator fixed at the tip, no routing blocks.
2.  **$S_2$:** Actuator fixed at the tip, with routing blocks.
3.  **$S_3$ (Proposed):** Actuator **floating** at the tip (unaffixed), with routing blocks.

**Result:** The proposed design ($S_3$) reduced joint twisting by **58.8%** compared to the fixed-tip designs, achieving dominant planar bending with minimal out-of-plane motion.

<div style="text-align: center;">
    <img src="/images/projects/hydro/fig4_characterization.png" alt="Characterization Results" width="85%">
    <p><em>Fig 2: Experimental comparison showing the significant reduction in twisting angle (d) and out-of-plane Z-displacement (e) for the proposed S3 design.</em></p>
</div> -->


## Twist Reduction Analysis
<div style="display: flex; align-items: center; gap: 30px; flex-wrap: wrap; margin-top: 20px;">
    <div style="flex: 0 0 60%; text-align: center;">
        <img src="/images/projects/hydro/fig4_characterization.png" alt="Characterization Results" width="100%" style="border-radius: 5px; box-shadow: 0px 0px 10px #ccc;">
        <p><em>Fig 2: Experimental comparison showing the significant reduction in twisting angle (d) and out-of-plane Z-displacement (e) for the proposed S<sub>3</sub> design.</em></p>
    </div>
    <div style="flex: 1; min-width: 200px;">

        <p>A common issue with coiled hydraulic actuators is "screw motion" — unwanted twisting during extension. We compared three design variations:</p>
        <ul>
            <li><strong>S<sub>1</sub>:</strong> Actuator fixed at the tip, no routing blocks.</li>
            <li><strong>S<sub>2</sub>:</strong> Actuator fixed at the tip, with routing blocks.</li>
            <li><strong>S<sub>3</sub> (Proposed):</strong> Actuator <strong>floating</strong> at the tip (unaffixed), with routing blocks.</li>
        </ul>
    </div>
</div>
<p><strong>Result:</strong> The proposed design (S<sub>3</sub>) reduced joint twisting by <strong>58.8%</strong> compared to the fixed-tip designs, achieving dominant planar bending with minimal out-of-plane motion.</p>
## Hysteresis Modeling

Soft polymer actuators exhibit significant hysteresis (a lag between input force and output bending). To enable precise control, we implemented a **Preisach Hysteresis Model**.

* **Calibration:** The model was trained on cyclic loading/unloading data.
* **Performance:** The model predicted tip deflection with a Root Mean Square Error (RMSE) of just **2.26&deg;** across validation trials with varying bending amplitudes.

<div style="text-align: center;">
    <img src="/images/projects/hydro/fig5_hysteresis.png" alt="Preisach Modeling Results" width="80%">
    <p><em>Fig 3: (First row) Preisach model fitted to training data. (Second row) Validation of the model against different loading profiles, showing accurate tracking of the bending angle.</em></p>
</div>

## Phantom Demonstration

To demonstrate clinical relevance, the robot was navigated through a **2D aortic arch phantom**. The joint successfully negotiated tortuous paths, navigating through the vessel bifurcations and achieving tip deflections greater than **180&deg;**.

<div style="display: flex; align-items: center;">
    <div style="flex: 0 0 33%; text-align: center;">
      <img src="/images/projects/hydro/fig6_phantom.png" alt="Phantom Navigation" width="98%" style="border-radius: 5px;">
    </div>
    <div style="flex: 0 0 67%; text-align: center;">
      <video width="98%" controls>
          <source src="/videos/hydro_demo.mov" type="video/mp4">
          Your browser does not support the video tag.
      </video>
      <p><em>Video: Navigation through the aortic arch phantom.</em></p>
    </div>
</div>

## Publication
This work was submitted at the **2026 International Symposium on Medical Robotics (ISMR)**.

**Citation:**
> **C. Gu**, T. A. Brumfiel, N. Malhotra, and J. P. Desai, "Design and Modeling of a Polymer-based Hydraulic Continuum Robot for Minimal Invasive Surgery," in *2026 International Symposium on Medical Robotics (ISMR)*, Atlanta, GA, USA, 2026.

[Download Paper (PDF)](/files/papers/2026_ISMR_Hydro_Robot.pdf){: .btn .btn--info}