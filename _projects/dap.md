---
layout: page
# tags: portfolio
permalink: /portfolio/work/dap
title: "Multi-Sensor Data Acquisition Platform"
img : "/assets/img/projects/dap/2.jpg"
subtitle: #Things I've worked on.
tags: mywork
comments: True
# show-avatar: False
category: work
---

<p>
  In early 2018, as I was working at the Fraunhofer IIS, one of the exciting projects I was working on involved several sensors such as camera, RADAR, LIDAR and the problem to be solved was pedestrian detection. The whole idea resolved around the theme of autonomous systems (driving) and part of the work was to find out how can we use consumer good radar and lidar sensors instead of expensive systems such as Velodyne Lidar costing more than 10K back at that time.
</p>

## Sensors: LIDAR, RADAR, CAMERA

<div style="text-align:center"><img src="/assets/img/projects/dap/3.jpg" /></div>
<br>
In my disposal was the RPLidar A2 (left), TimeDomain P440 RADAR (middle) and Logitech C270 cameras (right) depicted above. 
One of the problems with cheap sensors is the lack of data. What this means that for using machine learning methods, everything had to be measured and labeled from scratch.  
Neither the RADAR or the lidar had any pre-existing datasets such as the more expensive systems such as the Velodyne Lidar, which have datasets of point clouds from the real environment.

## Platform
<div style="text-align:center"><img src="/assets//img/projects/dap/4.jpg" width="100%"/></div>
<br>
Another problem at hand was that the system had to run on a embedded computing device from NVIDIA such as the <a href="https://developer.nvidia.com/embedded/jetson-tx2" target="_blank">Jetson TX2</a>. Thus, the computational limitations, were very strict considering how much processing could be done real-time. The idea was to build a camera field of view of 360 degrees, such that we would attach 8 Logitech Cameras on a platter covering the whole surrounding. On top of the camera array, on another level was sitting the Jetson TX2 board with the TimeDomain radar and on the third "floor" the lidar in order have the least occlusion with other obstacles. Now that we had the platform set for the first part i.e. the data recording and gathering, we could start making measurements. 

## Data Acquisition
<div style="text-align:center"><img src="/assets/img/projects/dap/5.jpg" width="80%"/></div>
Working with data, labeling and measurements is one of the most time-consuming effort. It is very inefficient to label the data manually, hence more efficent methods are desirable. 
One of the benefits of having a camera sensor is that, there is already bunch of really good neural network based object detection algorithms. And this is a huge benefit, the camera detection could easily be mapped into the lidar domain, from where the distance to the object could be extracted. This distance could be then used to find the object reflection peak in the RADAR domain.. et voila! We can do semi-automatic labeleing! The challenge now was to make enough recordings and preprocess the measured data on a more powerful computer with good object detector algorithm. In this particular project I used the <a href="https://github.com/facebookresearch/Detectron" target="_blank">Facebook Detectron</a>.

## Demo Platform
Since there are only limited computational resources available. Instead of using the all of the cameras, only one camera together with lidar and radar are used for deployment. This is sufficient in terms of what we want to achieve, namely to detect what is in front of the autonomous system, using a neural network based object detector (<a href="https://github.com/chuanqi305/ssd" target="_blank">Single Shot Detector</a> running at 15FPS on Jetson TX2), classify it and track it. And as soon as, there is a detection of a person, we track them until they have left the operational zone of the platform using the data points in lidar and radar domains.

<div style="text-align:center"><img src="/assets/img/projects/dap/towards_dap_big.gif" width="70%"/></div>
<br>
Above we can see, the detection in the camera domain, which initiates the  tracking the points in the lidar domain. In this example, we can see how the system works walking towards and backwards from the sensor. In the lidar domain even the static points are flickering (makes the problem bit harder), but as we can see the points associated with the person are clearly distinguishable. Observing the radar domain, we can see the red dots moving closer and further away on the waterfall plot.

<div style="text-align:center"><img src="/assets/img/projects/dap/out_fov_big.gif" width="70%"/></div>
<br>
In the gif above, we can see the person being tracked in the camera field of view and at the same time in the lidar and radar domain. Notice, how the tracking persist in the lidar and radar domain after the person has already left the camera field of view. 

## Conclusion
This was one of the most challenging and exciting projects I've worked on. The beauty of this project was that I could combine my previously acquired knowledge in machine learning, take some state of the art classifiers such as the FB Detectron for offline Semi-autonomous data labeleing and Single Shot Detector (SSD) for the live-demo version. The hardest part was the combination and synchronization of the different data streams from sensors. For the live-demo each of the sensor had to be tuned down to work at the rate of the SSD (image detector) speed as this was the most compute heavy task. 

