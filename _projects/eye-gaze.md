---
layout: page
# tags: portfolio
permalink: /portfolio/work/eye-gaze
title: "Human Eye-Gaze Tracking"
img : "/assets/img/projects/gaze/eye-gaze.jpg"
subtitle: #Things I've worked on.
tags: mywork
comments: True
category: fun
---

<!-- <h3>70 % complete</h3> -->
<!-- ![Gaze-tracking](/img/projects/eye-gaze.jpg) -->
<p>
  In the beginning of 2020 I was working in a early-stage startup in Paris focusing on computer vision solutions. One of the projects, which I was more envolved in was human eye-gaze tracking using the laptops camera. 
</p>

<!-- ![Humaneye](/img/projects/gaze/1.jpg) -->
## Human Eye
<div style="text-align:center"><img src="/assets/img/projects/gaze/1.jpg" /></div>
<br>

The human eye is very much like a camera, it has:
- **a lens** - directing the light rays onto the screen (the retina)
- **an iris** - controlling the opening of the pupil
- **a pupil** - the hole in the middle of the iris, through which the light passes
- **a cornea** - outer transparent covering on the pupil
- **a retina** - onto which the light coming after it has passed through the pupil and refracted through the lens

<div style="text-align:center"><img src="/assets/img/projects/gaze/2.jpg" /></div>
<br>

The challenge in human-eye gaze detection and projection comes from something very unexpected. Namely, the **optical axis**, which we can extract from images using different eye tracking techniques is not the same as the **visual gaze(axis)**, where the sharpest image is formed. The line connecting from the **fovea** (where focused point is the sharpest) to the center of the lense is called the visual axis. The difference between visual and optical axis is called the **kappa angle** and this is different for each of us. This is why most eye-gaze tracking solutions need some form of person specific calibration, in order to estimate this angle.

As I started working on this problem I quickly noticed that there are very many different approaches to solve this problem:

- 3D model based - using the geometric model of human face
- Regression based - extracting features from 2D image and train a classifier
- Cross-ratio based - needing 4 different light sources, hardware dependant
- Apperance based - using the extracted face or the images of eyes to train a classifier

## Apperance-based gaze
In my work, I focused on the apperance based methods and luckily for me a lot of the work was already done and released publicly by
<a href="https://github.com/hysts/pytorch_mpiigaze_demo" target="_blank">Zhang et al.</a>
They released two different models one using the left and the right eye and other one using the full face for prediction of the gaze angles.

<div style="text-align:center"><img src="/assets/img/projects/gaze/3.jpg" width="100%"/></div>
<br>

The process is roughly divided into 5 steps, where first the image is calibrated and undistorted, followed by face detectiong using the dlib face-detector. The landmarks detected by the dlib library are then used to estimate the head pose and fit the 3D face landmark model. This is useful for estimating the pupil center and hence extracting the left and the right eye from the image. Then the images of eyes are extracted, normalized and combined into 2 channel image. Then they are fed into a model, which returns gaze vectors (pitch and yaw) for each eye.

In order to make this all work a good calibration is needed. This calibration is hardware specific in order to obtain the camera intrinsic parameters and is usually done using <a href="https://docs.opencv.org/2.4/doc/tutorials/calib3d/camera_calibration/camera_calibration.html" target="_blank">checkerboard calibration.</a> 
The rest is using the estimated center of the eye and the predicted gaze vectors in order to calculate the approximate position on the screen. The resulting accuracy is actually pretty good considering that there is no person-specific calibration.

## Performance
In order to make the system more stable, I have done averaging over the facial landmark in order to keep the extracted images bit more stable, furthermore I am doing averaging over the predicted gaze vectors 

<div style="text-align:center"><img src="/assets/img/projects/gaze/4.pdf" width="90%"/></div>
<br>

Here we can see the result of focusing 5 different points on the screen w.r.t. some metrics such as <a href="https://en.wikipedia.org/wiki/Mean_absolute_error" target="_blank">mean absolute error (MAE)</a>, CEP and CE95. Note that blinking is not filtered. 

<div style="text-align:center"><img src="/assets/img/projects/gaze/5.pdf" width="90%"/></div>
<br>

In the figure above, we can see how the MAE changes according to the distance (i.e. we fix the distance). The graphs show the calculated MAE  w.r.t. each eye and if we would average them together over different distances. This plots gives us hints on what could be done in order to improve the model.

Check out more at my <a href="https://github.com/kenkyusha/eyeGazeToScreen" target="_blank">github page.</a>
