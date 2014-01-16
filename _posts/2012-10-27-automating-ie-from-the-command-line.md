---
title: Automating web page capture with Internet Explorer
layout: post
---
For a side project I've been working on I needed a way to take the rendered content of a web page and save it to an image file. I needed this to happen in a completely automated manner so that it could be set up to run as a scheduled task for regular updates.

I couldn't find anything that did exactly what I needed so I ended up writing one instead. I needed to use IE (some sites relied on integrated auth in an NT domain) and I wanted to be able to specify the exact dimensions of the resulting image.

For a side project I've been working on I needed a way to take the rendered content of a web page and save it to an image file. I needed this to happen in a completely automated manner so that it could be set up to run as a scheduled task for regular updates.

I couldn't find anything that did exactly what I needed so I ended up writing one instead. I needed to use IE (some sites relied on integrated auth in an NT domain) and I wanted to be able to specify the exact dimensions of the resulting image.

* [IEsnapper source](https://github.com/206industries/IEsnapper)

Next we can look at how this tool can be used with and a [Raspberry Pi](http://raspberrypi.org) to drive large displays.

