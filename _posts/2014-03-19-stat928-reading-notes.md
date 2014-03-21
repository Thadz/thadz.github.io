---
layout: post
title: "STAT928 Reading Notes"
categories: article
tags: statistical learning, machine learning
---

# On "what are the learning problems"

For classical statistics, usually a particular form of the distribution would be
assumed, known as the statistical model. Once the parameters of the model is
known, everything is clear. However, for statistical learning, if the ultimate
goal is to predict, then fitting the parameters of the model is not necessary.
If we can go over this step and jump directly to the prediction part smartly,
it may benefit us a lot!

![learning-problems-1](/img/2014-03-19-stat928-reading-notes/learning-problems-1.svg)

That is the motivation for the pursuit of a distribution-free framework. If you
are in the data science field long enough, you must have heard of Vapnik and
Chervonenkis. Their work on VC-dimension is about the distribution-free approach.
Though being distribution free, we also know there is no free lunch. We have to
encode the prior in the framework somehow. So a performance metric is proposed

<div>$\textit{E}\;\cal{l}(\hat{y}, (X,Y))-\inf_{f\in\cal{F}}\textit{E}\;\cal{l}(f,(X,Y))$</div>

