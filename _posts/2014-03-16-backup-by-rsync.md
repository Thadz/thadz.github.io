---
layout: post
title: "Backup By Rsync"
categories: article
tags: linux, rsync
---

Today I was trying to backup my personal documets by copying some files from one partition to another one. Realizing there was a command called **rsync**, I then tried to syncing two destinations using this command. It turned out to be pretty handy.

{% highlight bash %}
rsync -vur --delete <src> <dst>
{% endhighlight %}