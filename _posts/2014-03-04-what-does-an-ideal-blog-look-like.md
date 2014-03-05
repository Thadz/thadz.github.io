---
layout: post
title: "What does an ideal blog look like?"
categories: article
tags: blog, web techs
---
As a programmer, I read Hacker News a lot. After being a year or so addicted to reading tech blogs, I am thinking of having my own tech blog as well. Here are some features that the ideal blog should have.

## Serif Fonts

Since I am a heavy LaTeX user, the first thing I care about when it comes to reading is the font. Any long article that is not written in serif will turn readers away. Another thing worth noting is that the reading experience will be perfect only if strikes of each letter are wide enough such that words can look quite dense when displayed in small. Vollkorn is such a font and was really being popular in 2013. My bet is that it will still be in 2014. So for now on, Vollkorn is used. Also for careful web designers who are reading this article, Vollkorn is made in a German manner basically covering only German-like characters. Greek letters in the title are in GFS Didot, almost the only beautiful serif font that I can find in the internet.

## High Contrast Color

As you can see the background color is not pure white so that it will not blind the eyes of readers. Most of the words are in black while a small portion of words are in dark blue-ish color.

An ideal blog should also support changing the color theme on the fly. Well, currently this is not supported.

## One Column

No offense. Personally I just find reading blogs that are more than one column is annoying. Hey readers only care about the body of the article not the author's personal information nor some popular comments others have made. If they are so important, why don't put them in a new blog post? They are acting like ads for reading newspapers. One column is not fancy but good enough for readers.

## Fully Responsive

Mobile platforms are becoming unavoidable. Nobody would like to bother writing different websites for different platforms. Being fully responsive means that the webpage itself can adjust its size accordingly. To achieve this, I did some research and tried several popular grid frameworks. In my case, the Pure CSS from Yahoo works the best. It is so pure of CSS that no JQuery or other Javascript is needed, but still friendly to use and responsive in the expected manner.

## Posts in Markdown

As a personal blog, readers only care about the meaty part -- articles themselves, which are also the focus of the author. Writing a blog post directly in HTML is riduculous and unproductive. Given the popularity of markdown, why not give it a try? To build this blog system, Jekyll, yes that Jekyll coming along with Ruby, is used.

## Static

Static is simple and hosting static website requires little. After having done some meaty projects involving scalability, what can scale better than a static website. Jekyll is the solution here. In the future, I am thinking moving all the server-side jobs to the front-end and let the browser emit Javascript jobs on the client side. For example, quering database can be done in this fashion. The only thing I am not sure of is the security issue. Given the rising of Node.js, Emscripten and asm.js, moving most of the back-end code to the front is the trend. Well, since I don't know much about this, I will just stop here.

## Comments Anywhere

What is the difference between reading a blog and reading newspaper? I would say for newspaper, I can put a mark anywhere I want. Why a static blog can't? [Real World Haskell](http://book.realworldhaskell.org/read/getting-started.html) is really a good exemplar for this. Right now, this blog will only display comments at the bottom powered by Disqus, though I am seriously thinking about changing it very soon.

## Images, Video and Links

Being a static blog designed for reading doesn't necessarily mean it has to stay still. Images should be able to fold and unfold like the [origami](http://oridomi.com/). Videos should be playable for sure. Also links can be opened in a flipboard way. Sadly all of these are not supported in this blog presently.



What other features are you expecting for an awesome tech blog? Let me know how you think.