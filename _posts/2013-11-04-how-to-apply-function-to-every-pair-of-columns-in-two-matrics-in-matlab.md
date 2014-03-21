---
layout: post
title: How to apply function to every pair of columns in two matrices in MATLAB
date: 2013-11-04 10:08:00
categories: article
tags: matlab
---

One may try

{% highlight matlab %}
newvector = bsxfun(@(j,k)(func(A(j,:),B(k,:)),1:na,(1:nb)');
{% endhighlight %}

Note this trick cannot be applied to sparse matrices.