---
permalink: /
title: ""
author_profile: true
redirect_from:
  - /about/
  - /about.html
---

<style>
  .proj-list { margin: 0 0 1.5em 0; }
  .proj-card {
    display: flex;
    gap: 20px;
    align-items: flex-start;
    margin-bottom: 28px;
  }
  .proj-card__media { flex: 0 0 40%; }
  .proj-card__media img {
    width: 100%;
    border-radius: 8px;
    object-fit: cover;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  }
  .proj-card__body { flex: 1 1 auto; }
  .proj-card__body h3 { margin-top: 0; }
  .proj-card__body p { margin-bottom: 0; }
  .proj-card__meta {
    font-size: 0.85em;
    opacity: 0.75;
  }
  @media (max-width: 600px) {
    .proj-card { flex-direction: column; }
    .proj-card__media { flex-basis: auto; width: 100%; }
  }
</style>

# Biography 🦁

Hi, I am **Chenyu Gu**, a Ph.D. student in Biomedical Engineering at **Washington University in St. Louis** 🇺🇸, where I am advised by **Dr. Ismael Seanez** in the Seanez Lab. My current work focuses on spatiotemporal control of transcutaneous spinal cord stimulation for people with chronic spinal cord injury.

Before that, I earned my M.S. in Bioengineering from the **Georgia Institute of Technology**, advised by [Dr. Jaydev Desai](https://research.gatech.edu/people/jaydev-desai) in the RoboMed Lab, where I worked on continuum and guidewire robots for minimally invasive surgery. I received my B.S. in Intelligent Medical Engineering from *Southern University of Science and Technology (SUSTech)* in Shenzhen, China 🇨🇳, under [Dr. Mingming Zhang](https://www.sustech.edu.cn/en/faculties/zhangmingming.html).

## Research Interests 🔬

* **Medical & Bio-Robotics:** Surgical robots, continuum and soft robotics, wearable and rehabilitation robotics, data-driven robotic control.
* **Neuromodulation & Neural Engineering:** Spinal cord stimulation, neurophysiological assessment, restoring motor function after injury.
* **Medical Devices & Digital Health:** Wearable and portable devices, surgical navigation, tele-rehabilitation.
* **Biomechanics & Physiological Signals:** Gait and locomotion analysis, motion tracking, multi-modal EMG/IMU sensing and analysis.

## News & Updates 🎉

* **[Nov 2026]** Our paper on the modified COAST guidewire robot was accepted to *npj Robotics*!
* **[Aug 2026]** Started my Ph.D. in Biomedical Engineering at Washington University in St. Louis, joining the Seanez Lab! 🎓
* **[May 2026]** My continuum robotics paper won the **Best Student Paper Award** at ISMR 2026! 🏆
* **[May 2026]** Graduated from Georgia Tech with an M.S. in Bioengineering!
* **[Feb 2026]** My paper on continuum robotics was accepted to ISMR 2026!
* **[Aug 2025]** Started as a Graduate Teaching Assistant for *Machine Learning (CS 7641)* at Georgia Tech.
* **[Jul 2025]** Joined the COAST guidewire robot project and led K–12 outreach as a Georgia Tech CEISMC summer program leader.
* **[Mar 2025]** Our paper on a portable inertial navigation system for total hip arthroplasty was published in *IEEE Transactions on Instrumentation and Measurement*.
* **[Aug 2024]** Started my Master's program at Georgia Tech.
* **[Jun 2024]** Graduated from Southern University of Science and Technology with a Bachelor's degree in Intelligent Medical Engineering.

## Selected Projects 🤖

<div class="proj-list">

  <div class="proj-card">
    <div class="proj-card__body">
      <h3><a href="/projects/scs">Spatiotemporal Control of Transcutaneous Spinal Cord Stimulation</a></h3>
      <p class="proj-card__meta">Seanez Lab, Washington University in St. Louis · Current</p>
      <p>
        Multielectrode transcutaneous spinal cord stimulation can recruit motor pools below a spinal cord injury without surgery, but where and when to stimulate is still an open question. In an ongoing study with chronic spinal cord injury participants, we optimize array positioning to increase targeted joint torque and use frequency modulation to probe posterior root-muscle reflexes, combining high-density EMG, dynamometry, and 3D kinematics.
      </p>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-card__media">
      <img src="/images/projects/hydro_showcase.png" alt="Hydraulic continuum robot bending inside a vascular phantom">
    </div>
    <div class="proj-card__body">
      <h3><a href="/projects/hydro">Design and Modeling of a Hydraulic Continuum Robot</a></h3>
      <p class="proj-card__meta">RoboMed Lab, Georgia Tech · ISMR 2026 Best Student Paper</p>
      <p>
        We designed and modeled a hydraulically actuated, polymer-based continuum robot with a 2.14 mm outer diameter for minimally invasive surgery. A custom coiled hydraulic actuator and internal routing blocks suppress unwanted twisting, and a Preisach hysteresis model makes tip deflection predictable. The robot is demonstrated navigating a 2D aortic-arch phantom.
      </p>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-card__media">
      <img src="/images/projects/DAA_showcase.png" alt="Inertial navigation system used during a hip arthroplasty procedure">
    </div>
    <div class="proj-card__body">
      <h3><a href="/projects/ins">Inertial Navigation System for Total Hip Arthroplasty</a></h3>
      <p class="proj-card__meta">Brain-robot Rehabilitation Lab, SUSTech · IEEE T-IM 2025</p>
      <p>
        In direct anterior total hip arthroplasty, accurate radiographic anteversion and inclination angles are essential but are typically determined using X-ray, exposing patients to radiation. We developed a wireless inertial navigation system with real-time visualization that removes this need, reaching 1.24° and 1.89° RMSE respectively.
      </p>
    </div>
  </div>

  <div class="proj-card">
    <div class="proj-card__media">
      <img src="/images/projects/dip_showcase.png" alt="Reconstructed human motion from sparse inertial sensors">
    </div>
    <div class="proj-card__body">
      <h3><a href="/projects/dip">Deep Learning Framework for Motion Reconstruction</a></h3>
      <p class="proj-card__meta">Brain-robot Rehabilitation Lab, SUSTech</p>
      <p>
        We developed a deep learning framework that reconstructs 3D human motion from sparse IMU data and UWB localization signals. Recurrent networks capture motion dynamics over time, producing accurate full-body reconstruction for biomechanics, rehabilitation monitoring, and virtual reality.
      </p>
    </div>
  </div>

</div>

<p><a href="/projects/">See all projects →</a></p>
