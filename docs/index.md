---
title: FIRO
hide:
  - title
---

<style>
    .md-content .md-typeset h1 { display: none; }
</style>

<center>
    ![[logo.png]]{: style="height: 150px"}
</center>

<p align="center">
    <em>FIRO (FLASH Inspection Rover, also known as Facility Inspection Rover)</em>
</p>

---

**Technical Documentation**: <a href="https://rxsio.github.io/firo-docs/" target="_blank">https://rxsio.github.io/firo-docs/</a>

**User Manual**: <a href="https://rxsio.github.io/firo-user-manual" target="_blank">https://rxsio.github.io/firo-user-manual</a>

---

![[firo_in-flash2.jpg]]

**FIRO** is a mobile robot designed to operate in environments where human presence is restricted due to hazardous radiation levels. It is a student project developed mostly during Erasmus internships at the FLASH particle accelerator at DESY (hence the name of the robot). FIRO's capabilities are primarily driven by FLASH demands and requirements.

## Objectives

- **Radiation Measurements**  
  Measuring radiation levels throughout the accelerator tunnel to detect and pinpoint anomalies, particularly sources of radiation scattering. Essentially, this generates a high-resolution map of radiation along the accelerator, as an alternative to data from a few radiation sensors at designated locations. Such capability is valuable because scattering sources negatively affect beam quality.

- **Real-Time Monitoring**  
  Providing a live camera stream to enable on-demand monitoring of the accelerator's machinery. This is especially useful during the commissioning process when the correct operation of the new equipment has to be confirmed, often by visual monitoring.

- **Incident Response**  
  Providing a local view in case of incidents such as gas leaks. This is important because the accelerator tunnel cannot be accessed immediately by personnel after an incident occurs. First, the accelerator has to be shut down, and conditions in the tunnel have to be confirmed in case additional safety precautions are necessary. By providing an immediate local view, the incident can be diagnosed faster, leading to quicker repairs and shorter accelerator downtime.

## Additional Functionalities

The FIRO robot has additional capabilities that are not specific to the needs of restricted access environments, however, they are still desired at FLASH.  

- **Virtual Tour**  
  Utilizing a 360-degree camera to update virtual tours of the FLASH tunnel. This functionality is used to automate a process currently performed by humans. During FLASH development, virtual tours are used to document progress and particularly to provide detailed information on the current status of FLASH through imagery. Automating this task can lead to several improvements:  
  - Improved repeatability allowing better visual difference comparison (such differences can be automatically highlighted).  
  - Better spatial resolution: Virtual Tours can be updated much faster by the robot, hence if desired, the 360 photos can be taken more densely with no additional cost as long as the robot is not swamped by other tasks.  
  - Better temporal resolution: Virtual Tours could also be updated more often, or even on-demand, after someone applies key modifications to the accelerator or when someone needs to confirm the current status of the FLASH development.  
