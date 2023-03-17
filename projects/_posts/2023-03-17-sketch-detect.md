---
title: [CVPR'23] What Can Human Sketches Do for Object Detection?
layout: post
comments: true
mathjax: true
author: pinaki
permalink: /sketch-detect/
---

A simple set-based approach using optimal transport (OT) to model cross-modal region associativity in a partially-aware fashion. We improve upon OT to further account for holistic partialness by comparing weighted intra-modal adjacency matrices.

# **Partially Does It: Towards Scene-Level FG-SBIR with Partial Input**

Pinaki Nath Chowdhury, Ayan Kumar Bhunia, Viswanatha Reddy Gajjala, Aneeshan Sain, Tao Xiang, Yi-Zhe Song

SketchX, Center for Vision Speech and Signal Processing

University of Surrey, United Kingdom

**Published at CVPR 2022**

[Paper](/assets/papers/partially-does-it.pdf) / [Github](https://github.com/pinakinathc/partially-does-it)

## **Abstract**

We scrutinise an important observation plaguing scene-level sketch research – that a significant portion of scene sketches are “partial”. A quick pilot study reveals: (i) a scene sketch does not necessarily contain all objects in the corresponding photo, due to the subjective holistic interpretation of scenes, (ii) there exists significant empty (white) regions as a result of object-level abstraction, and as a result, (iii) existing scene-level fine-grained sketch-based image retrieval methods collapse as scene sketches become more partial. To solve this “partial” problem, we advocate for a simple set-based approach using optimal transport (OT) to model cross-modal region associativity in a partially-aware fashion. Importantly, we improve upon OT to further account for holistic partialness by comparing intra-modal adjacency matrices. Our proposed method is not only robust to partial scene-sketches but also yields state-of-the-art performance on existing datasets.

## **Motivation**

<p align="center"><img src="/projects/images/partially-does-it-motivation.png" alt="motivation figure" width="50%;"/></p>

(a): Scene sketches exhibit abstraction on global scene configuration as shown by overlapping sketches on top of their corresponding photos. (b): Existing scene-level FG-SBIR methods collapse as scene sketches become more partial. (c): There are significant empty (white) regions. Also, the sketch of a sheep in the scene might correspond to that in the centre of photo. This calls for a solution modelling region-wise associativity.

## **Network Architecture**

<p align="center"><img src="/projects/images/partially-does-it-framework.png" alt="motivation figure" width="50%;"/></p>

Illustration of our proposed method for scene-level FG-SBIR. Existing baselines typically use Global Average Pooling (GAP) on the convolutional feature-map. This loses localised region-specific feature representation necessary for “partial” scene sketches. Our proposed method models partially-aware region-wise associativity to solve this “partial” problem using: (i) set-based distance of local feature maps using optimal transport ($$\mathcal{L}^{R}_{trip}$$), (ii) a weighted cross-modal comparison of region adjacency matrix to capture holistic scene configuration ($$\mathcal{L}^{G}_{trip}$$).
### **Code**

The code is available at: [https://github.com/pinakinathc/partially-does-it](https://github.com/pinakinathc/partially-does-it)

The main contribution of this paper -- a new distance metric for FG-SBIR that computes a loss on sets of local feature is also given in **Supplemental Section A.**

### **Instructions to Execute the code**

```
python main.py
```

### **TODO**

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

### **Social Media**

<blockquote class="twitter-tweet"><p lang="en" dir="ltr">&quot;Partially Does It: Towards Scene-Level FG-SBIR with Partial Input&quot;, CVPR 2022<br><br>Find me at Poster session 1.1, Number 235a.<a href="https://twitter.com/cvssp_research?ref_src=twsrc%5Etfw">@cvssp_research</a> <a href="https://twitter.com/hashtag/CVPR22?src=hash&amp;ref_src=twsrc%5Etfw">#CVPR22</a> <a href="https://twitter.com/hashtag/NewOrleans?src=hash&amp;ref_src=twsrc%5Etfw">#NewOrleans</a> <a href="https://twitter.com/hashtag/sketch?src=hash&amp;ref_src=twsrc%5Etfw">#sketch</a></p>&mdash; Pinaki N Chowdhury (@pinaki_nc) <a href="https://twitter.com/pinaki_nc/status/1539268760950947841?ref_src=twsrc%5Etfw">June 21, 2022</a></blockquote> 

<blockquote class="twitter-tweet" data-partner="tweetdeck"><p lang="en" dir="ltr">Partially Does It: Towards Scene-Level FG-SBIR with Partial Input<a href="https://t.co/lfpG9JYtT0">https://t.co/lfpG9JYtT0</a></p>&mdash; DeepTweet (@DeepL_Tweet) <a href="https://twitter.com/DeepL_Tweet/status/1516463133602115587?ref_src=twsrc%5Etfw">April 19, 2022</a></blockquote>

<blockquote class="twitter-tweet" data-conversation="none" data-cards="hidden" data-partner="tweetdeck"><p lang="in" dir="ltr">Partially Does It: Towards Scene-Level FG-SBIR with Partial Input. Pinaki Nath Chowdhury, Ayan Kumar Bhunia, Viswanatha Reddy Gajjala, Aneeshan Sain, Tao Xiang, and Yi-Zhe Song <a href="https://t.co/wMhMCrQci8">https://t.co/wMhMCrQci8</a></p>&mdash; cs.CV Papers (@arxiv_cs_cv_pr) <a href="https://twitter.com/arxiv_cs_cv_pr/status/1508652123466379265?ref_src=twsrc%5Etfw">March 29, 2022</a></blockquote>

<script async src="https://platform.twitter.com/widgets.js" charset="utf-8"></script> 
