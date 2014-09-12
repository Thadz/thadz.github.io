---
layout: post
title: "How To Avoid Accidental Git Push"
categories: article
tags: git
---

If you are working on something experimental in your local branch, you don't really want to accidentally push the half-way result to the master. Well, we all know that but our hands have their own muscle memory. Pushing something to the master could go wild without your brain's acknoledgement! If you don't trust your hands, or you deeply believe that mortals are destined to make silly mistakes, there is one simple way to prevent that from happening when you are working with git! Hooray!

{% highlight bash %}
git config remote.origin.receivepack /bin/false
{% endhighlight %}

Then you are all set. If you have doubts in what I have said, you may double check it by

{% highlight bash %}
git remote show origin
{% endhighlight %}

You can see that you are still allowed to pull from the upstream, but no longer able to push upstream. What's more interesting is that, such limitation only takes effect in your present branch. What a glorious dark magic!