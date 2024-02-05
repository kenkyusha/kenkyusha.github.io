---
layout: page
tags: eye-gaze-tracking, computer-vision, webcam-gaze-tracking, digital-accessibility
permalink: /portfolio/work/eye-gaze-tracking-webcam
title: "Human Eye-Gaze Tracking Using Webcam Technology"
img: "/assets/img/projects/gaze/eye-gaze.jpg"
description: In 2020, I spearheaded a groundbreaking project on human eye-gaze tracking using webcam technology. This method, leveraging advanced appearance-based techniques, revolutionized how we predict gaze directions with impressive accuracy, setting new standards in digital accessibility.
subtitle: Exploring the Frontier of Computer Vision
tags: eye-tracking, gaze-tracking, computer-vision, user-interface-design
comments: true
category: technology
---

<p>
  In early 2020, I joined an innovative startup in Paris, diving into the world of computer vision. Our focus was revolutionizing user interaction through eye-gaze tracking technology, employing a standard laptop camera.
</p>

## Understanding the Human Eye
<div style="text-align:center"><img src="/assets/img/projects/gaze/1.jpg" alt="Anatomy of the Human Eye" /></div>

Just like a camera, the human eye features several key components:
- **Lens:** Directs light rays onto the retina.
- **Iris:** Controls the pupil's size.
- **Pupil:** Allows light to enter the eye.
- **Cornea:** Transparent front layer of the eye.
- **Retina:** Captures the light, turning it into visual signals.

## The Challenge of Eye-Gaze Detection
<div style="text-align:center"><img src="/assets/img/projects/gaze/2.jpg" alt="Eye-Gaze Detection Challenges" /></div>

Eye-gaze tracking technology encounters a unique challenge: the **optical axis** differs from the **visual gaze axis**. This discrepancy, known as the **kappa angle**, varies among individuals, necessitating personalized calibration for accurate tracking.

## My Approach: Appearance-Based Gaze Tracking
<div style="text-align:center"><img src="/assets/img/projects/gaze/3.jpg" width="100%" alt="Appearance-Based Gaze Tracking Process"/></div>

I employed appearance-based methods, heavily relying on the pioneering work by Zhang et al., which utilized images of the eyes or the full face to accurately predict gaze angles. Our process involved:
1. Calibrating and undistorting the image.
2. Detecting faces with dlib's face-detector.
3. Estimating head pose and fitting a 3D face landmark model.
4. Extracting, normalizing, and combining eye images into a two-channel image for the model.
5. Predicting gaze vectors (pitch and yaw) for accurate tracking.

## Enhancing Performance
To improve stability and accuracy, I implemented averaging techniques over facial landmarks and predicted gaze vectors. This approach significantly reduced errors and enhanced system reliability.

## Results and Insights
<object data="/assets/img/projects/gaze/4.pdf" type="application/pdf" width="100%" height="500" alt="Gaze Tracking Performance Results"></object>
<br>

Our findings, documented in detailed performance metrics, showcase the potential for further advancements in gaze tracking technology. The analysis of mean absolute error (MAE) across various distances offers valuable insights for model improvement.

## Explore More on My GitHub
For a deeper dive into this project and more of my work in computer vision, visit my [GitHub page](https://github.com/kenkyusha/eyeGazeToScreen).
