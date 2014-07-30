---
layout: post
title: Beautiful Git Log
categories: article
tags: git
---

If one ever wonders how to view git log in a formatted way, here is the [solution](https://coderwall.com/p/euwpig).

{% highlight bash %}
git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"
{% endhighlight %}

Then the next time when you try to see the log, simply type

{% highlight bash %}
git lg
{% endhighlight %}

To see the lines changed,

{% highlight bash %}
git lg -p
{% endhighlight %}