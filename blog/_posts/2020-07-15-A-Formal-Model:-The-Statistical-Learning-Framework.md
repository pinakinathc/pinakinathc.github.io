---
layout: post
comments: true
mathjax: true
author: pinaki
---
Can we get some theoretical guarantees of *how successful learning can be achieved in a relatively simplified setting?*

In this blog, I shall answer the aforementioned question. Before starting, I must mention that I learnt about this concept from "Understanding Machine Learning: From Theory to Algorithms" by Shai Shalev-Shwartz and Shai Ben-David, Chapter 2 page 33.

*So let's get cracking...*

Before diving deep into theory let us first define **the learner's input** i.e.  the basic statistical learning *setting* that the learner has access to:

- **Domain set**: This is a set of objects that we *wish* to label. Borrowing an example from the chapter, suppose you want to **predict** whether a papaya you see in the market is tasty or not. So here, the *domain set* will the *set of ALL papayas*. Usually, these domain points will be represented by a vector of *features* (like the papaya's color and softness). **Each domain points is referred to as instances** in the instance space represented by $$\mathbf{\mathcal{X}}$$.

- **Label set**: Consider we have only 2 labels i.e. {0,1} or {-1, +1}. We shall denote this *set of possible labels* with $$\mathbf{\mathcal{Y}}$$. Example: consider that 1 represents that our papaya is tasty while 0 stands for being non-tasty.

- **Training data**: As mentioned, that our Domain set consists of *instances* we **wish to label**. But it is not possible to label the entire Domain set. So consider that we label a **finite** $$\mathbf{m}$$ instances. Hence, $$S = ((x_{1}, y_{1}), (x_{2}, y_{2}), \dots, (x_{m}, y_{m}))$$ is a *finite sequence of pairs* in $$\mathcal{X}\times\mathcal{Y}$$. It is important to keep in mind that despite the "set" notation of $$S$$, it is a sequence i.e. the same example may appear *twice* in $$S$$.

Consider that the learner gets access to a finite set of papayas which it can taste and then decide whether it is 1 (tasty) or 0 (non-tasty). This finite set or the *training data* are often called **training examples**.

 $$ \nabla_\boldsymbol{x} J(\boldsymbol{x}) $$
