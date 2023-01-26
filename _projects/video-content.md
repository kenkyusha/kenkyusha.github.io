---
layout: page
# tags: portfolio
permalink: /portfolio/work/video-content
title: "Video-Image Content Understanding"
img : "/assets/img/projects/vidcont/1.jpg"
subtitle: #Things I've worked on.
tags: mywork
comments: True
show-avatar: False
category: work
---

<p>
  In the late summer of 2019, while I was visiting my cousins in Portland, Oregon and travelling across the west coast of USA through California I had a bit of unluck travelling between San Fransisco (SF) and San Diego (SD). As my rideshare cancelled the night before I was supposed to travel from SF-SD, I was in a bit of trouble. Looking through various options and finally as I was about to pick up a rental car the airport somebody called me and offered to pick me up and take me to LA if I am willing to drive. As we were driving, he explained the business he was building and that he might look for a ML engineer to work as a freelance contractor.
</p>

## Content Understanding
The platform they were working on was similar to the social media platforms such as Instagram, Snapchat or Tiktok. Users could share their images and videos with their friends or general public. These videos and videos, must be however filtered in terms of detecting nudity and violence. Furthermore, one of the key aspects of those platforms is selling ads and adtargeting. 

## Object Detection
In order to do the object detection and classification, the biggest problem is related to speed. There are a lot of solutions running on the VGG, Resnet and R-CNN architecture, all of them deliver very good detection results however a quite slow when it comes to volume and speed. 
This is where, I found that the <a href="https://pjreddie.com/darknet/" target="_blank">pjreddie's darknet</a> architecture and the pretrained model of <a href="https://www.youtube.com/watch?v=MPU2HistivI&" target="_blank">Yolov3 (You-Only-Look-Once)</a> was best fit. I build a image and video classification pipeline, which ran the corresponding images through the network and yielded the most predominant objects, as they were appearing more in the image or in the video, delivered in a standard json format.

## Video-Action Detection

<img src="https://github.com/NVlabs/STEP/blob/master/example.gif?raw=true" width="800" />
<!-- <div style="text-align:center"><img src="/assets/img/projects/mlpos/6.png" width="100%"/></div> -->

Compared to working with images/frames, detecting and classifying actions in videos is complicated. The number of parameters of these networks are huge, there is not enough data available, meaning training those models is hard. It is not as straight forward as object detection and classification in images as a lot of information comes from the temporal flow of the activities and actions happening. Luckily the <a href="https://github.com/NVlabs/STEP" target="_blank">NVIDIA-STEP</a> 

## Speech Transcription
Another interesting point for content understanding is the speech! The speech in a video gives us even more relevant information, what is the mood, the subject, the activity and more contextual knowledge of what currently is happening. 

<div style="text-align:center"><img src="/assets/img/projects/vidcont/2.png" /></div>
<br>

The big tree: Amazon, Microsoft and Google - have pretty powerful speech transcription API-s already available. I personally used Google for this part as my work platform was anyways set up using the Google Cloud Platform (GCP). 
The steps, are pretty straight forward, first extracting the audio from videos, then setting up the <a href="https://cloud.google.com/speech-to-text" target="_blank">Google Speech-to-text API</a>, which then retrives you the list of concatenated strings of the words it managed to recognize. 


## Automatic Text Summarization
<!-- (Talk about abstractive and extractive summarization) -->
<a href="https://arxiv.org/abs/1904.00688" target="_blank">Automatic text summarization </a> is the next big thing in content understanding. Essentially what we want to do is to extract the audio from the video and now using the speech transcription, we get messy composition of words, which might look chaotic. The two different approaches, <a href="https://arxiv.org/pdf/1909.03186.pdf" target="_blank">abstractive and extractive summarization</a> try to make sense of the context. We can think of extractive summarization as a highlighter pen, where we highlight the most meaningful parts. Whereas, abstractive summarization aims to summarize the text more like a human, i.e. generating new sentences from the input text.



## Challenges
The hardest part about this project was definetly getting the hang of video-action detection part. There is a lot of research done recently and some of the work is publicly available, while the most powerful models either were in the process of being published or waiting to be accepted to the conferences.
Another big challenge was making it all run in an parallel manner. This meant that first the audio had to be extracted from the video, then the video converted into images, which was then fed into object detection pipeline and action-detection pipeline at the same time. Using multiprocessing and some designs tricks, all the processes could be ran in parallel.

<div style="text-align:center"><img src="/assets/img/projects/vidcont/1.jpg" /></div>
<br>

Check out more at <a href="https://video.io" target="_blank">this page.</a>
