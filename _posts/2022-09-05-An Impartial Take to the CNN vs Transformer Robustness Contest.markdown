---
layout: post
title: "An Impartial Take to the CNN vs Transformer Robustness Contest"
date: 2022-09-05 11:00:00 +0200
categories: study convnet vit
link: https://arxiv.org/abs/2207.11347
---

<img src="{{site.baseurl}}/assets/img/2022-09-05-An Impartial Take to the CNN vs Transformer Robustness Contest.png" alt="drawing" width="550"/>

#### Context

- It is often claimed that vision transformers (ViT) surpass convolutional networks (CNN) in calibration, robustness to covariate shift, and out-of-distribution (OoD) performance.

- This paper questions the methods to reach these conclusions and proposes new experiments.

- The models compared were: ConvNeXt and BiT (CNNs) vs. vanilla ViT and Swin Transformer (ViTs).

#### Takeaways

- ViTs and CNNs are both susceptible to simplicity bias (a.k.a. shortcut learning). See figure above.

- ViTs and CNNs perform just as well on OoD detection tasks.

- No single model exhibited the lowest Expected Calibration Error (ECE) in all covariate-shift experiments. Also, the model with the highest accuracy is not the most calibrated.

- A low ECE is not enough to assess a classifier's reliability. It is better to complement this analysis with other techniques, such as the Prediction Rejection Ratio (PRR).

- The robustness contest between CNNs and ViTs seems to have no clear winner.
