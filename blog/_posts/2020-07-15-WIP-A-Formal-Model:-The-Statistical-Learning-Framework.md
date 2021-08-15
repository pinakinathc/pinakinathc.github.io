---
layout: post
comments: true
mathjax: true
author: pinaki
---


this is a work in progress...please view later.

## **Can we get some theoretical guarantees of *how successful learning can be achieved in a relatively simplified setting?***

In this blog, I shall answer the aforementioned question. While third-party materials like this blog might help to introduce some concept, I encourage readers to also go through the sources from which I learned it. This section is primarily taken from a single source -- "Understanding Machine Learning: From Theory to Algorithms" by Shai Shalev-Shwartz and Shai Ben-David. More specifically, this blog essentially trims and embarrasingly simplifies Chapter 2.

*So let's get cracking...*

### Introduction, Objective, and Motivation

---

We need to first focus on **what do we want to learn** and then define what do we mean by the word *learning* or more specifically a **successful learning** -- i.e., what does it means to have a *successful learning*. 

First let me quote Vladimir N. Vapnik from "The Nature of Statistical Learning Theory": >>*`we consider the learning problem as a problem of finding a desired dependence using a **limited** number of observations.`*<<

To get a better perspective of *what do we want to learn* consider this quote (again from Vapnik): >>*`What must one know a priori about an unknown functional dependency in order to estimate it on the basis of observations?`*<<

While I shall provide a more mathematical definition of *"learning"*, maybe we should spend a bit more time on the philosophy of what exactly we mean by learning. 

Now I shall introduce the example that Shalev-Shwartz and Ben-David used in their book -- "*learn how to predict whether a papaya you **see** in the market is tasty or not*".

Before diving into, let us first **define** the learner's input i.e.  the basic statistical learning *setting* that the learner has access to:


---------------

- **Domain set**: This is a set of objects that we *wish* to label. **Each domain points is referred to as instances** in the instance space represented by $$\mathbf{\mathcal{X}}$$.

- **Label set**: Consider we have only 2 labels i.e. {0,1} or {-1, +1}. We shall denote this *set of possible labels* with $$\mathbf{\mathcal{Y}}$$.

- **Training data**: As mentioned, that our Domain set consists of *instances* we **wish to label**. But it is not possible to label the entire Domain set. So consider that we label a **finite** $$\mathbf{m}$$ instances. Hence, $$S = ((x_{1}, y_{1}), (x_{2}, y_{2}), \dots, (x_{m}, y_{m}))$$ is a *finite sequence of pairs* in $$\mathcal{X}\times\mathcal{Y}$$. It is important to keep in mind that despite the "set" notation of $$S$$, it is a sequence i.e. the same example may appear *twice* in $$S$$. This finite set or the *training data* are often called **training examples**.

- **The learner's output**: The objective of the learner is to output a mapping function or a *prediction rule* $$h: \mathbf{\mathcal{X}} \rightarrow \mathbf{\mathcal{Y}}$$. This function is also called a {*predictor*, *hypothesis*, *classifier*}.

- **Data generation Model**: We consider that the probability distribution over $$\mathbf{\mathcal{X}}$$ be denoted by $$D$$. It is *important* to note that **we do not assume** that the learner knows anything about this distribution.

- **Assumption**: We *assume* that there is some "correct" labelling function, $$f:\mathbf{\mathcal{X}} \rightarrow \mathbf{\mathcal{Y}}$$. We shall relax this assumption in our next blog.

- **Measure of success**: The error of our prediction rule $$h: \mathbf{\mathcal{X}} \rightarrow \mathbf{\mathcal{Y}}$$ is **defined** to be ($$\stackrel{\text{def}}{=}$$ symbol represent *is defined*):

$$L_{D, f}(h) \stackrel{\text{def}}{=} \mathbb{P}_{x \sim D} [h(x) \neq f(x)] \stackrel{\text{def}}{=} D(\{x \sim D: h(x) \neq f(x)\})$$


 The error of $$h$$ is the probability of randomly choosing an example $$x \sim D$$ for which $$h(x) \neq f(x)$$. The subscript $$(D, f)$$ indicates that the error is measured with respect to the probability distribution $$D$$ and the correct labelling function $$f$$. $$L_{D, f}$$ is knows as: {*generalization error*, *the risk*, *true error*} of $$h$$.

- **Note**: Since the learner is blind to the underlying distribution $$D$$ and the correct labelling function $$f$$, it cannot calculate the *true error*. To overcome this problem, the learner uses what is known as the *Empirical Risk* for guidance.

---------------------------------


