---
layout: page # post-wide
hero-bg-color: "#fff" #"#000"  #BLACK
title:  "Computer Vision - based Position Estimation" # appearing title
permalink: /portfolio/work/cv-position
img : "/assets/img/projects/cvpos/cv-position.jpg"
tags: mywork
show-avatar: False
comments: True
category: fun
---

<p>
  Back in the fall of 2018, while I was working at the Fraunhofer IIS (Nürnberg), I stumbled upon a problem, which one of my collegues was working on. The problem itself called inside-out positioning, where a forklift or other kind of moving autonomous system needs to position itself using the RGB cameras and perhaps additional information from other sensors. <a href="https://www.mad.tf.fau.de/files/2018/07/Evaluation-Criteria-for-Inside-Out-Indoor-Positioning-Systems-based-on-Machine-Learning.pdf" target="_blank">(read more here).</a> 

</p>

## Warehouse Dataset
My previous employer (current at that time), Fraunhofer, published the <a href="https://www.iis.fraunhofer.de/en/ff/lv/dataanalytics/opt/warehouse.html" target="_blank">datasets</a>, which consist of the absolute position (X,Y,Z) and the quaternions (w,p,q,r) and the corresponding 360° images (6 in total) for each of them. The data is divided into training and testing sets. The training set consisting of driving through the measurement arena following a predefined horizonthal or vertical path. The testing set contains new independent recordings, which follow 8 different trajectories testing different criteria.

## Image Processing
After following the <a href="https://www.mad.tf.fau.de/files/2018/07/Evaluation-Criteria-for-Inside-Out-Indoor-Positioning-Systems-based-on-Machine-Learning.pdf" target="_blank">publication</a>, I found that they followed the conventional image classification pre-processing scheme, which is depicted below. First the mean image is calculated over the datasets, then these values are used to normalize the images. Additionally a center-crop is performed in order to provide more robustness and mitigate overfitting -  common approach used in image classification.

<div style="text-align:center"><img src="/assets/img/projects/cvpos/1.jpg" /></div>
<br>

After trying to follow the same steps and plotting the images as seen above, I noticed that when we go from the original image on the most left side to the very right side then a lot of valuable information could be lost! 

## Edges!
As I was digging into this problem I also was suprised how come the network did not manage to get good accuracy measures. The training sets both horizonthal and vertical have very good coverage of the whole measurement arena and thus the network should atleast be capabale of overfitting to that.
Furthermore, I did not understand the reason for center cropping as this is usually used when less data is available and should be considered as optional tool. 

<div style="text-align:center"><img src="/assets/img/projects/cvpos/2.jpg" /></div>
<br>

Thus, I decided to try out something new, instead of center cropping I simply scaled the image down to the network input size (224x224) and instead of mean image reduction I performed edge detection on the images... et voila!

<div style="text-align:center"><img src="/assets/img/projects/cvpos/3.jpg" /></div>
<br>

## The Network
Now instead of blurry, shadowy image we have less color channeles meaning instead of having a conventional RGB image of 3 channels, we now have black and white image with 1 channel, hence our CNN would have less parameters to learn! The CNN architecture used in the paper was based on a modification of <a href="https://arxiv.org/pdf/1409.4842.pdf" target="_blank">GoogleNet</a> using special output from the PoseNet. 

<div style="text-align:center"><img src="https://raw.githubusercontent.com/kenkyusha/cv_position/master/pictures/model_plot.png" width="50%"/></div>
<br>

I decided to try something simpler based on some of my earlier work with less layers and designed <a href="https://raw.githubusercontent.com/kenkyusha/cv_position/master/pictures/model_plot.png" target="_blank">the network architecture depicted above.</a> 

## Results

Following are the results testing with the cross dataset:

<div style="text-align:center"><img src="/assets/img/projects/cvpos/4.jpg" /></div>
<br>

From left to right, sys4, sys5, sys6 - these depict the orientation of the camera on the forklift (i.e. which direction the camera is facing).

Implemenatation | MAE    | CEP    | CE95   | deg (CEP)
--------------- | ------ | -------| ------ | ---------
Cross (original)| 1.08 m | 0.86 m | 3.06 m | 0.18 ° 
smallNet (sys4) | 0.35 m | 0.30 m | 0.74 m | 0.10 °
smallNet (sys5) | 0.37 m | 0.35 m | 0.71 m | 0.04 °
smallNet (sys7) | 0.59 m | 0.43 m | 1.48 m | 0.03 °

The numerical results in terms of mean absulte error, circular error probability and CE95.

For implementation details, check out more at my <a href="https://github.com/kenkyusha/cv_position" target="_blank">github page.</a>
