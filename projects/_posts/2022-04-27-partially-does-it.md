---
layout: post
comments: true
mathjax: true
author: pinaki
permalink: /partially-does-it/
---

A simple set-based approach using optimal transport (OT) to model cross-modal region associativity in a partially-aware fashion. We improve upon OT to further account for holistic partialness by comparing weighted intra-modal adjacency matrices.

# Partially Does It: Towards Scene-Level FG-SBIR with Partial Input

Pinaki Nath Chowdhury, Ayan Kumar Bhunia, Viswanatha Reddy Gajjala, Aneeshan Sain, Tao Xiang, Yi-Zhe Song

SketchX, Center for Vision Speech and Signal Processing

University of Surrey, United Kingdom

**Published at CVPR 2022**

[Paper](/assets/papers/partially-does-it.pdf) / [Github](https://github.com/pinakinathc/partially-does-it)

## Abstract

We scrutinise an important observation plaguing scene-level sketch research – that a significant portion of scene sketches are “partial”. A quick pilot study reveals: (i) a scene sketch does not necessarily contain all objects in the corresponding photo, due to the subjective holistic interpretation of scenes, (ii) there exists significant empty (white) regions as a result of object-level abstraction, and as a result, (iii) existing scene-level fine-grained sketch-based image retrieval methods collapse as scene sketches become more partial. To solve this “partial” problem, we advocate for a simple set-based approach using optimal transport (OT) to model cross-modal region associativity in a partially-aware fashion. Importantly, we improve upon OT to further account for holistic partialness by comparing intra-modal adjacency matrices. Our proposed method is not only robust to partial scene-sketches but also yields state-of-the-art performance on existing datasets.

## Motivation

<p align="center"><img src="/projects/images/partially-does-it-motivation.png" alt="motivation figure" width="50%"/></p>

(a): Scene sketches exhibit abstraction on global scene configuration as shown by overlapping sketches on top of their corresponding photos. (b): Existing scene-level FG-SBIR methods collapse as scene sketches become more partial. (c): There are significant empty (white) regions. Also, the sketch of a sheep in the scene might correspond to that in the centre of photo. This calls for a solution modelling region-wise associativity.

## Network Architecture

<p align="center"><img src="/projects/images/partially-does-it-framework.png" alt="motivation figure" width="50%"/></p>

Illustration of our proposed method for scene-level FG-SBIR. Existing baselines typically use Global Average Pooling (GAP) on the convolutional feature-map. This loses localised region-specific feature representation necessary for “partial” scene sketches. Our proposed method models partially-aware region-wise associativity to solve this “partial” problem using: (i) set-based distance of local feature maps using optimal transport ($$\mathcal{L}^{R}_{trip}$$), (ii) a weighted cross-modal comparison of region adjacency matrix to capture holistic scene configuration ($$\mathcal{L}^{G}_{trip}$$).
### Code

The code is available at: [https://github.com/pinakinathc/partially-does-it](https://github.com/pinakinathc/partially-does-it)

The main contribution of this paper -- a new distance metric for FG-SBIR that computes a loss on sets of local feature is also given in **Supplemental Section A.**

### Instructions to Execute the code

```
python main.py
```

### TODO

Add a detailed instruction to run the code.

### Citation/Bibtex

```
@inproceedings{partially-does-it,
    title={Partially Does It: Towards Scene-Level FG-SBIR with Partial Input},
    author={Pinaki Nath Chowdhury, Ayan Kumar Bhunia, Viswanatha Reddy Gajjala, Aneeshan Sain, Tao Xiang, Yi-Zhe Song},
    booktitle={The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    month={June},
    year={2022}
}
```
