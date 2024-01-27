---
layout: page
# tags: portfolio
permalink: /portfolio/work/mlpos
title: "CNN-based Position Estimation"
img : "/assets/img/projects/mlpos/11.jpg"
description: We improved high-precision positioning using Convolutional Neural Networks (CNN) for radio signal analysis. Achieved impressive results in challenging multipath scenarios, demonstrating the potential of machine learning for precise positioning. #MachineLearning #Positioning
subtitle: #Things I've worked on.
tags: mywork
comments: True
category: work
---
<div style="text-align:center"> <iframe allowfullscreen="" frameborder="0" height="540" src="https://www.youtube.com/embed/TlWucuVcF5Q" width="860"></iframe> </div>

<p>
Above we can see a demonstrator platform built for the Mobile World Congress Barcelona 2018 in the context of Industrial 5G IOT high precision positioning. The taxi-robot is carrying with it a rack with some boxes, which have tags denoted with colored circles. These tags are emitting bursts of radio signals which are captured by the positioning antenna system. The circles colored in green are being processed by the conventional signal processing chain, whereas the circle in yellow is skipping the conventional signal processing and powered by machine learning model a deep convolutional neural network. We are observing here the non-linear effects caused by the multiple racks and reflector walls, which create massive distortions in the received signal. The conventional signal processing chain has difficulties tracking the tag in this kind of environment whereas the ML-powered approach is quite steady. This work has been carried out as I was working at the Fraunhofer IIS.
</p>

## Channel Impulse Response

<div style="text-align:center"><img src="/assets/img/projects/mlpos/2.png" width="100%"/></div>

In the figure above, we can see plot of a received channel impulse response with direct line-of-sight (in blue) and one with multipath reflections (in red). The the conventional signal processing chain tries to find the time-of-arriva (TOA), which is the peak i.e. the maximum of the signal and disregards everything else. This works well, if we have direct line-of-sight and clear signal as we see above colored in blue. However, in the case of signal reflections, scattering, multipath and other non-linear effects the received signal has several peaks and it is harder to tell which one of them is the correct TOA. The information around the peaks, denoted with green circles, is completly ignored, which actually could carry a lot of additional information regarding the effects we experience on the signal.

## Data Processing
<div style="text-align:center"><img src="/assets/img/projects/mlpos/3.png" width="100%"/></div>
<br>
The received channel impulse response consists of real and imaginary coefficients and since we have signals from several antenna units (in this case 12). The real and imaginary channels are the combined into a 2-dimensional image, where they follow a CxHxW format. That is real and imaginary channels C, then H being the number of antenna units and W number of coefficients. Above on the left figure, we can see the 12 received signals plotted together and on the right side we see them from a birdview prospective after being converted into a 2D image.

## Datasets
<div style="text-align:center"><img src="/assets/img/projects/mlpos/4.png" width="100%"/></div>
<br>

### Meander
The trajectories plotted above, were used for training and testing the methodology. On the left side, we can see the trajectory named "Meander", which has been divided into two different sets. First, the short-slice, where shorts slices are cut out from the trajectory and used only in the testing phase, whereas rest is used for training. Secondly, the long-slice, where the whole sequence is cut out in order to see whether the model could interpolate between the training samples it has seen. 

### Displaced Rectangles
On the right, we can see the trajectory used for testing against the multipath. The trajectory contains a "tunnel" for signal propagation created by absorber walls and other reflective material. This is a scenario, where the conventional signal processing does not work very well.

## Results

### Slicing Evaluation
<div style="text-align:center"><img src="/assets/img/projects/mlpos/5.png" width="100%"/></div>
<br>
The figures above show the results of the slicing evaluation. The color difference shows the size of the error, i.e. the more green the more closer to the ground-truth position.

Implemenatation | MAE    | CEP    | CE95   |
--------------- | ------ | -------| ------ |
Short Slices| 0.265 m | 0.236 m | 0.571 m | 
Long Slices| 0.339 m | 0.265 m | 0.771 m | 


### Multipath Scenario
<div style="text-align:center"><img src="/assets/img/projects/mlpos/6.png" width="100%"/></div>
<br>
This scenario as been split into 2 sections, one in the multipath area, which is where the signal "tunnel" is created with the absorber walls and other reflective material. And the second one in the line of sight conditions.

Implemenatation | MAE    | CEP    | CE95   |
--------------- | ------ | -------| ------ |
Multipath (EKF)| 2.11 m | 1.45 m | 5.29 m | 
Multipath (CNN)| 0.292 m | 0.229 m | 0.683 m | 
LOS (EKF)| 0.148 m | 0.141 m | 0.270 m | 
LOS (CNN)| 0.154 m | 0.146 m | 0.283 m | 


The results show that, the model learned from channel impulse response signals performs very similarly with the conventional signal processing methodology. In the case of multipath, the CNN (our trained model) is superior as it has learned how to deal with signals experiencing heavy non-linear effects.

## Conclusions
This was the first project on which I worked after joining Fraunhofer IIS in Nürnberg. It was also one with most accomplishments (2 publications, 1 best paper award and demonstrator at the MWC). Working on this project, I learned a lot about radiowave-based positioning in terms of theory and practise. 
Furthermore, I gained very good intuition in designing and training convolutional neural networks.

More details in the publications listed below!
## Publications
<a href="https://ieeexplore.ieee.org/document/8533766" target="_blank">A Deep Learning Approach to Position Estimation from Channel Impulse Responses</a>
<a href="https://www.mdpi.com/1424-8220/19/5/1064" target="_blank">Convolutional Neural Networks for Position Estimation in TDoA-Based Locating Systems</a>