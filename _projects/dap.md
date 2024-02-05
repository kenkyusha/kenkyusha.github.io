---
layout: page
tags: multi-sensor-data-acquisition, lidar-radar-camera-integration, autonomous-systems, pedestrian-detection-technology
permalink: /portfolio/work/multi-sensor-data-platform-jetsontx2
title: "Innovative Multi-Sensor Data Acquisition Platform for Autonomous Systems"
img: "/assets/img/projects/dap/2.jpg"
description: Discover how we revolutionized pedestrian detection in autonomous systems by integrating LIDAR, RADAR, and camera technologies on a budget-friendly platform, featuring real-time object detection and tracking capabilities.
subtitle: Bridging the Gap in Autonomous Technology
tags: autonomous-driving, sensor-integration, real-time-detection, object-tracking
comments: true
category: technology
---

<p>
  In 2018, at Fraunhofer IIS, I embarked on a pioneering project aimed at enhancing pedestrian detection for autonomous systems. We explored cost-effective alternatives to high-priced sensors like Velodyne Lidar, leveraging LIDAR, RADAR, and camera technologies to create a comprehensive detection platform.
</p>

## Revolutionizing Sensors: LIDAR, RADAR, CAMERA

<div style="text-align:center"><img src="/assets/img/projects/dap/3.jpg" alt="Sensor Technology for Autonomous Systems"/></div>
<br>
Armed with RPLidar A2, TimeDomain P440 RADAR, and Logitech C270 cameras, we faced the challenge of building a dataset from scratch due to the scarcity of data from budget-friendly sensors.

## Building the Platform
<div style="text-align:center"><img src="/assets/img/projects/dap/4.jpg" width="100%" alt="Multi-Sensor Data Acquisition Platform"/></div>
<br>
Our platform, designed to operate on NVIDIA's Jetson TX2, aimed for 360-degree awareness with an 8-camera array and strategically placed RADAR and LIDAR sensors, overcoming computational limitations to ensure efficient real-time processing.

## Efficient Data Acquisition and Labeling
<div style="text-align:center"><img src="/assets/img/projects/dap/5.jpg" width="80%" alt="Data Acquisition Process"/></div>
Manual data labeling is time-consuming. By harnessing neural network-based object detection algorithms, we achieved semi-automatic labeling, mapping camera detections to LIDAR distances and RADAR reflections, streamlining the data preparation process.

## Demo Platform Insights
With computational resources at a premium, we optimized the system to use a single camera alongside LIDAR and RADAR for effective object detection and tracking, running a neural network-based object detector at 15FPS on the Jetson TX2 for live-demo applications.

<div style="text-align:center"><img src="/assets/img/projects/dap/towards_dap_big.gif" width="70%" alt="Demo of Multi-Sensor Detection and Tracking"/></div>
<br>
The demo showcases the platform's capability to detect and track objects, maintaining tracking accuracy even as objects move out of the camera's field of view, thanks to the integrated sensor data.

## Conclusion: Pushing Boundaries in Autonomous Systems
This project stands as a testament to the potential of integrating machine learning with sensor technology to create efficient, cost-effective solutions for autonomous systems. The challenge of synchronizing diverse data streams was met with innovative solutions, setting a new standard for real-time detection and tracking in autonomous vehicles and systems.
