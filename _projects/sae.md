---
layout: page
permalink: /portfolio/deep-learning-stacked-autoencoder
title: "Enhancing Data Encoding with Stacked AutoEncoders (SAEs)"
img: "https://upload.wikimedia.org/wikipedia/commons/3/37/Autoencoder_schema.png"
description: Dive into our 2015 project on Stacked AutoEncoders (SAEs), a pioneering approach in deep learning for efficient data encoding, inspired by advancements in neural network-based instrument extraction from music. Discover how SAEs optimize encoding processes and structure through unique training methodologies.
tags: stacked-autoencoder, deep-learning, neural-networks, data-encoding, machine-learning
comments: True
show-avatar: False
category: machine-learning
---

In 2015, at the International Audio Laboratories, I embarked on an exploratory project into Machine Learning (ML) and Deep Learning (DL), focusing on Stacked AutoEncoders (SAEs). Inspired by groundbreaking research in [Deep Neural Network Based Instrument Extraction From Music](http://150.162.46.34:8080/icassp2015/pdfs/0002135.pdf), this project aimed to leverage SAEs for advanced data encoding.

## Understanding Autoencoders

<div style="text-align:center; background-color: white;"><img src="https://upload.wikimedia.org/wikipedia/commons/3/37/Autoencoder_schema.png" width="50%" alt="Autoencoder Schema"/></div>

Autoencoders, a cornerstone of neural network architecture, are designed to learn efficient data encodings automatically. By progressively reducing neuron count layer by layer, autoencoders distill input data into a concise, efficient encoding before attempting to reconstruct the original input. [Learn more about Autoencoders.](https://en.wikipedia.org/wiki/Autoencoder)

### The Innovation of Stacked Autoencoders

Our approach, as detailed in the referenced [paper](http://150.162.46.34:8080/icassp2015/pdfs/0002135.pdf), introduces a novel training method for autoencoders. Starting with a single-layer network, we experiment with two initial weight settings: the Identity function and the least-squares method, focusing on optimizing the encoding of complex audio data.

<div style="text-align:center"><img src="/assets/img/projects/sae/1.svg" size="100%" alt="Stacked Autoencoder Training Process"/></div>
<br>

This methodical layering and training process, repeated until the network reaches a specified depth, preserves initial weights while adapting to new complexities, resulting in a finely tuned SAE.

## Observing Training Loss Evolution

The hallmark of our stacked autoencoder's architecture is its characteristic "staircase" pattern of training and validation loss. This pattern demonstrates the effectiveness of our training methodology, with each new layer contributing to a significant leap in performance and accuracy.

<div style="text-align:center"><img src="/assets/img/projects/sae/2.png" size="100%" alt="Training and Validation Loss"/></div>
<br>

For an in-depth look at the development and application of this technology, including a step-by-step guide and example implementations, visit our [GitHub repository](https://github.com/kenkyusha/SAE) and explore the [notebook example](https://github.com/kenkyusha/SAE/blob/master/example.ipynb).

