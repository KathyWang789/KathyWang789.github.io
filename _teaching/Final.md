---
title: "Vision Transformer for Underwater Image Enhancement"
collection: Projects
type: "Undergraduate Final Project(CV Research)"
permalink: /Projects/Final
venue: "BUPT & QMUL"
date: Sept.2022 - Jun.2023
location: "Remote"
---

This is an underwater image enhancement research, Vision Transformer and Wavelet Transform are used for underwater image
processing to avoid the current problems such as colour cast and detail blur.

# Supervisor: [Changjae Oh](http://eecs.qmul.ac.uk/~coh/)

<img src="../images/final.png"/>

Abstract
======
People now give the development and utilization of marine resources more consideration. The area of underwater computer vision has seen a rise in research, particularly in the area of underwater robot detection of objects. However, because of scattering and attenuation that depends on wavelength and distance, underwater images have color casts and lack clarity. Convolutional neural networks ( CNNs) are frequently utilized in tasks connected to picture restoration since it has been demonstrated that they are effective at learning from large-scale data. In many computer vision tasks, the Vision Transformer(ViT) method outperforms traditional CNNs structures and has lately emerged as one of the primary neural network architectures for image processing. The article presents a Vision Transformer-based network to enhance the quality of underwater images. ViT is more efficient at capturing non-local contextual information than CNNs, improving the quality of underwater images. In order to be more precise, we deconstruct the input image using the discrete wavelet transform, create subsampled structure and detail images, and then input those images into the structure and detail networks. The issues of colour bias are solved using the structure network (SNet), while the issues of fuzzy image details are resolved using the detail network (DNet). The outcomes of the experiments show how well the suggested model handles the problems of color distortion and image blurring. We verified the excellent performance of the proposed model in processing the whole image and details on NYU-v2, UIEB, LSUI and ColorChecker.

Proposed Method
=====
## Overview
The network is splited into the structure network (SNet) and the detail network (DNet). We aim to deal with problems more efficiently and in a more targeted way.
<img src="../images/finaloverview.png"/>

## Image Processing

### Discrete Wavelet Decomposition(DWT)
<img src="../images/DWT.png"/>

When processing an underwater image I, we first decompose it into a subband image using the DWT. The low-frequency sub-band image (𝐼𝐿𝐿) is composed of the half-resolution approximation of the original image. In contrast, the high-frequency sub-band image contains the high-frequency information in the original image, which is divided into three directions: vertical direction (𝐼𝐿𝐻), horizontal direction (𝐼𝐻𝐿), and diagonal direction (𝐼𝐻𝐻). By decomposing into multiple sub-band images, the different frequency information in the image can be processed more effectively, so as to achieve better underwater image enhancement effects. After obtaining the sub-band estimations using DWT, they are integrated and reconstructed back to the original size of the image using IDWT. The process of IDWT involves performing an inverse wavelet transform on the sub-band estimations to obtain a reconstructed image that is the same size as the original image. This reconstructed image is then used for further processing or analysis.

### Multi-colour Space Fusion 
<img src="../images/fusion.png"/>

Before input to the network, we also perform a multi-color space fusion operation on 𝐼𝐿𝐿. Multi-color space fusion is a technique to combine the features of multiple color Spaces into a multi-channel image. The HSV color space represents colors based on their hue, saturation, and value, which makes it useful for adjusting brightness and contrast. On the other hand, the Lab color space represents colors based on their lightness, a (green-red), and b (blue-yellow) values, which is more perceptually uniform and better suited for color correction tasks. 

## Structure Network
Structure Network consists of Transformer module and conventional convolutional module. The model generally adopts U-net encoding and decoding structure to solve problems such as image colour bias.
<img src="../images/SNET.png"/>

## Detailed Network
<img src="../images/DNET.png"/>

## Loss Function
<img src="../images/Ltotal.png"/>

Results
======
## Results on NYU-v2 dataset
<img src="../images/nyuv2.png"/>

## Results on LSUI dataset
<img src="../images/LSUI.png"/>

## Results on UIEB dataset
<img src="../images/UIEB.png"/>

<img src="../images/scores.png"/>