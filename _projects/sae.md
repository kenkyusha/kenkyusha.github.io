---
layout: page
# tags: portfolio
permalink: /portfolio/work/sae
title: "Stacked AutoEncoder"
img : "https://upload.wikimedia.org/wikipedia/commons/3/37/Autoencoder_schema.png"
subtitle: #Things I've worked on.
tags: mywork
comments: True
show-avatar: False
category: work
---

Implementing a stacked autoencoder was one of the first projects I worked as I dived into the ML and DL topics. Back in 2015, as I was doing my HiW-i job (working student) at the International Audio Labratories, lasange and theano on top of keras was the big deal and implementing neural networks. This work was inspired by the authors of [Deep Neural Network Based Instrument Extraction From Music](http://150.162.46.34:8080/icassp2015/pdfs/0002135.pdf), which explained roughly how they implemented and trained their Stacked Autoencoder.

## Autoencoder

<div style="text-align:center"><img src="https://upload.wikimedia.org/wikipedia/commons/3/37/Autoencoder_schema.png" width="50%"/></div>

An autoencoder is a type of neural network, which usually is used to learn an efficient encoding. The way it works is that layer after layer the number of neurons each later is reduced to a desired size after which the encoding process starts, which tries to reconstruct the input signal.
<a href="https://en.wikipedia.org/wiki/Autoencoder" target="_blank">Read more about it here.</a>

### Stacked autoencoder
In the [paper](http://150.162.46.34:8080/icassp2015/pdfs/0002135.pdf), they describe a special way of training an autoencoder. Namely they start with 1 layer network where the weights are initialized either with the Identity function, meaning there are 1s on the main diagonal of the matrix and rest is filled with 0s. The second initialization they propose ise the lease-squares method, which uses the input data and performs cross-correlation computation. 

<div style="text-align:center"><img src="/assets/img/projects/sae/1.svg" size="100%"/></div>
<br>

When the weights are initialized they train the network with features extracted from audio frame of combination different musical instruments and target being the features of a single instrument (piano, drums, guitar, ...). This one layer network, is trained for certain epochs after, which another layer is added to the network, its weights again initialized while preserving the first layer weights. The network is trained again and this process is repeated till **depth + 1** times.

<div style="text-align:center"><img src="/assets/img/projects/sae/0.svg" size="100%"/></div>
<br>

## Training loss
The result of this architecture should be a staircase of training and validation loss, where after each addition of new layer the error jumps downwards as described in the paper.

<div style="text-align:center"><img src="/assets/img/projects/sae/2.png" size="100%"/></div>
<br>

Check out more at my <a href="https://github.com/kenkyusha/SAE" target="_blank">github page</a> and the <a href="https://github.com/kenkyusha/SAE/blob/master/example.ipynb" target="_blank">notebook example.</a> 
