---
layout: post
title: "Nicely Amending Git Message"
categories: article
tags: git
---

Sometimes one would like to amend the git commit message and reset the author
and date at the same time. One could try

{% highlight bash %}
git commit --amend --date="$(date -R)" --reset-author
{% endhighlight %}
