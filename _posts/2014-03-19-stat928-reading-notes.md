---
layout: post
title: "STAT928 Reading Notes, Ongoing"
categories: article
tags: statistical learning, machine learning
---

Following is based on [STAT928 notes](http://www-stat.wharton.upenn.edu/~rakhlin/courses/stat928/stat928_notes.pdf)

# On "what are the learning problems"

For classical statistics, usually a particular form of the distribution would be
assumed, known as the statistical model. Once the parameters of the model is
known, everything is clear. However, for statistical learning, if the ultimate
goal is to predict, then fitting the parameters of the model is not necessary.
If we can go over this step and jump directly to the prediction part smartly,
it may benefit us a lot! For example, it is pretty hard to evaluate the performance of a model if the assumption made on distribution cannot be met. On the other hand, if we have a performance metric for all distribution, this issue will not bother us anymore.

![learning-problems-1](/img/2014-03-19-stat928-reading-notes/learning-problems-1.svg)

That is the motivation for the pursuit of a distribution-free framework. If you
are in the data science field long enough, you must have heard of Vapnik and
Chervonenkis. Their work on VC-dimension is about the distribution-free approach.
Though being distribution free, we also know there is no free lunch. We have to
encode the prior in the framework somehow. So a performance metric, known as
regret, is proposed

$\textit{E}\;\cal{l}(\hat{y}, (X,Y))-\inf_{f\in\cal{F}}\textit{E}\;\cal{l}(f,(X,Y))$

To encode our bias, we simply limit the scope of $\cal{F}$. That is to say, we
are comparing and optimizing the performance of the learner with what we have
known.

Similarly, when dealing with individual sequence prediction, to set a
distribution-free skeleton, one can push the prior into the comparator term

<p>$\frac{1}{n}\sum^n_{t=1}\cal{l}(\hat{y}_t,z_t)-\inf_{\pi\in\cal{\Pi}}\frac{1}{n}\sum^n_{t=1}\cal{l}(\pi_{t}(z^{t-1}),z_t)$</p>

One needs to notice that the regret being small does not mean the predictor is
good. It only means the predictor performs pretty well under the assumption that
$\cal{F}$ captures the nature of sequences being observed.

