---
published: true
title: "Todays Notes 2016-01/08"
layout: post
date: "2016-01-08 19:35"
tags:
  - whitenoise
  - chipolte
categories:
  - dailynotes
---


Just some notes about things I found today.

#Office Life
There has been some office discussion about white noise generators. I happened to take a look to see what my linux box could put out and found the following post: [Need to play high-fidelity white noise? Listen to /dev/urandom on OSX!](https://blogs.fsfe.org/marklindhout/2013/02/need-to-play-high-fidelity-white-noise-listen-to-devurandom-on-osx/)

I was able to get this going with the following command:
{% highlight sh %}
cat /dev/urandom | sox -traw -r44100 -b16 -e unsigned-integer - -d
{% endhighlight %}

But also saw this in the comments and decided to use it instead:
{% highlight sh %}
play -n synth whitenoise
{% endhighlight %}

#Lunch
This isn't really important, but why am I only now getting bowls at Chipolte? Far less messy than burritos. :P
