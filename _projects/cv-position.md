---
layout: page
hero-bg-color: "#fff"  # Emphasizing a clean, professional look
title: "Advanced Computer Vision for Accurate Position Estimation"
permalink: /portfolio/computer-vision-position-estimation
img: "/assets/img/projects/cvpos/cv-position.jpg"
description: Explore how we achieved groundbreaking improvements in inside-out positioning with computer vision technologies at Fraunhofer IIS in 2018, significantly enhancing image processing and simplifying CNN architectures for unparalleled accuracy.
tags: computer-vision, position-estimation, inside-out-positioning, CNN, Fraunhofer-IIS

show-avatar: False
comments: True
category: innovation
---

<p>
  During my tenure at Fraunhofer IIS in Nürnberg in late 2018, I tackled the challenging task of inside-out positioning for autonomous systems using RGB cameras, a crucial technology for navigation and spatial awareness in robotics and autonomous vehicles. <a href="https://www.mad.tf.fau.de/files/2018/07/Evaluation-Criteria-for-Inside-Out-Indoor-Positioning-Systems-based-on-Machine-Learning.pdf" target="_blank">Learn more about inside-out positioning.</a> 
</p>

## Enhancing Warehouse Navigation with Computer Vision

Fraunhofer's groundbreaking <a href="https://www.iis.fraunhofer.de/en/ff/lv/dataanalytics/opt/warehouse.html" target="_blank">warehouse dataset</a> includes absolute positions and 360° imagery, serving as the foundation for our experiments in enhancing autonomous navigation through advanced image processing and CNN architectures.

## Optimizing Image Processing for Precision

Following standard pre-processing protocols, we initially faced challenges in retaining critical image details. A shift in approach from center-cropping to edge detection and image scaling (224x224) preserved valuable contextual information, drastically improving our model's learning efficiency.

## Introducing 'Edges': A Game-Changer in Image Analysis

<div style="text-align:center"><img src="/assets/img/projects/cvpos/2.jpg" alt="Edge Detection in Image Processing"/></div>
<br>

My innovation involved foregoing traditional mean image reduction in favor of edge detection, enhancing the CNN model's accuracy by focusing on structural details critical for precise positioning.

## Streamlining CNN Architecture for Better Performance

Our simplified CNN model, inspired by but less complex than GoogleNet's architecture, proved more effective for our specific use case, requiring fewer parameters and offering improved performance.

<div style="text-align:center"><img src="https://raw.githubusercontent.com/kenkyusha/cv_position/master/pictures/model_plot.png" width="50%" alt="Simplified CNN Architecture"/></div>
<br>

## Breakthrough Results in Position Estimation

Our results demonstrated significant improvements across key metrics, including Mean Absolute Error (MAE), Circular Error Probable (CEP), and the 95% confidence interval (CE95), showcasing the efficacy of our streamlined approach.

<div style="text-align:center"><img src="/assets/img/projects/cvpos/4.jpg" alt="Comparative Analysis of Position Estimation Accuracy"/></div>
<br>

The comparative analysis highlights the superiority of our 'smallNet' system in various operational setups, marking a substantial advancement in computer vision-based positioning technologies.

For a deeper dive into the project and access to our codebase, visit our [GitHub repository](https://github.com/kenkyusha/cv_position).

