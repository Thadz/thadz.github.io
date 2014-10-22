---
layout: post
title: "Alert Me When Job Is Done"
categories: article
tags: ubuntu, terminal
---

When developing in Ubuntu, very often a command may take so long that I stop staring at the terminal anymore. It would be pretty sweet if there is a way to alert me when the job is done, while me is reading a book or doing something else.

First thing to do is to turn the motherboard speaker on.
{% highlight bash %}
sudo modprobe pcspkr
{% endhighlight %}

Then, one is free to play with the beep command.
{% highlight bash %}
sudo apt-get install beep
{% endhighlight %}

Now you are good to go.
{% highlight bash %}
anyCommandYouWant; beep
{% endhighlight %}