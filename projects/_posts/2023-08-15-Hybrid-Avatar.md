---
title: "Hybrid Rendering of Dynamic Scenes"
layout: post
comments: false
mathjax: true
author: pinaki
permalink: /hybridnerf/
excerpt_separator: <!--more-->
---

<!--more-->

## **Hybrid Rendering of Dynamic Scenes: Integrating NeRF into 3D Graphics Pipelines**

<br>

We extract a canonical pose DECA mesh and learn its offsets given a 10s video (with 30fps). Simultaneously, we also predict its texture map and Flame expression vectors. Next, we use the fast rasterisation as in MobileNeRF to generate Neural Head Avatars. 

## **Dataset Description**

### Mathhias Unseen Expression Split:

Train, Validation, and Testing have different expressions. Hence, we need to extract expressions from test frames and apply them to the underlying asset learned from the train set.

<iframe src="https://player.vimeo.com/video/854702809?h=d486240538&autoplay=1&loop=1&autopause=false" style="width:32%;height:32%;"  frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
<iframe src="https://player.vimeo.com/video/854702776?h=299202cdc4&autoplay=1&loop=1&autopause=false" style="width:32%;height:32%;" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>
<iframe src="https://player.vimeo.com/video/854702745?h=95d9856b95&autoplay=1&loop=1&autopause=false" width="32%" height="32%" frameborder="0" allow="autoplay; fullscreen; picture-in-picture" allowfullscreen></iframe>

### Matthias Seen Expression Split:

Train, Validation, and Testing share the same expression vectors. We achieve this split by assigning `first` frame to training, the `second` frame to validation, and the `third` frame to testing.

`status -- low priority`

### Facebook Dataset:

`status -- pending`

## **Comparative Methods**

- ### PointAvatar
Uses SDF to generate Point Clouds in Flame canonical space. Then extracts Flame expression and pose from test frames and applies it on the Point Cloud for dynamics. Finally, applies shading on the vertices using a small MLP.

- ### Neural Head Avatar

- ### NeRSemble

## **Metrics**

### Dataset: Matthias Unseen Expression Split

| Methods | PSNR | SSIM | LPIPS | Training (Hrs) | Inference (Sec) |
| ---     | ---  | ---  | ---   | ---           | ---            |
|  PointAvatar | 23.73 | 0.813 | 0.124 | 6 | 0.378 |
| NHA | xxx | xxx | xxx | xxx | xxx |
| NeRSemble | xxx | xxx | xxx | xxx | xxx |
| **Ours** | xxx | xxx | xxx | xxx | xxx |

## **Qualitative Results**

### Method: PointAvatar
<img src='/projects/images/hybrid-avatar/mathhias-unseen-eval1.png' width='32%' height='32%'>
<img src='/projects/images/hybrid-avatar/mathhias-unseen-eval2.png' width='32%' height='32%'>
<img src='/projects/images/hybrid-avatar/mathhias-unseen-eval3.png' width='32%' height='32%'>