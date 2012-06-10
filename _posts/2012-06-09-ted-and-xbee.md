---
layout: post
title: Adding an XBee radio to The Energy Detective TED 1001
---

Several years ago I bought [The Energy Detective](http://www.theenergydetective.com/), a two-piece kit for measuring electricity consumption. One unit connects inside the main electrical panel, the second plugs into a regular outlet and shows a display of power consumption in real time.

![](http://photos.andyoakley.com/Other/Blog/i-w4thzmq/0/S/31ToBzwabnLSL500AA300-S.jpg)

The device also comes with a USB port and corresponding Windows software to allow computer logging. The implementation mixes a Windows service (with unfortunate memory leak) and a Flash-based interface. There service hosts an HTTP API which makes it reasonably easy to pull current numbers.

Here's an example for pulling the numbers in PowerShell:

<script src="https://gist.github.com/2901757.js?file=gistfile1.ps1">

</script>

The stock solution has a few drawbacks: sometimes the numbers just stop getting updated, the memory leak requires regular restarts, and the level of granularity of the usage numbers of rounded to the minute.

Fortunately I came across a [TED Modification for real-time data output](http://gangliontwitch.com/ted/) which shows where to tap the PCB to get the raw output from the modem. The output is a simple 1200 bps 8N1 serial stream. With the case open it was clear that was enough room to sneak an [Xbee 2mW Series 2 radio](http://www.sparkfun.com/products/10414) inside. The great think about Xbees is that they will happily transmit a serial stream over the air right out of the box.

## Hardware

Setting up the hardware interface was trivial. Just three connections are required:

Power:
Ground is supplied by the third pin on programming jumper. A 3.3v supply for Xbee Vcc is conveniently available on the second pin on programming jumper.

![](http://photos.andyoakley.com/Other/Blog/i-fqWShNV/0/M/201-M.jpg)

The data line, connected to DIN on the Xbee is tapped off R20 on the PCB. 

![](http://photos.andyoakley.com/Other/Blog/i-rjXFsK5/0/M/200-M.jpg)

## Software

The Xbee is paired with a coordinator unit inside a [ConnectPort X2 gateway](http://www.digi.com/products/wireless-routers-gateways/gateways/connectportx2gateways#overview). The gateway runs an embedded version of Python and Digi provides a framework called [Dia](http://www.digi.com/wiki/developer/index.php/IDigi_Dia_Wiki) which defines a pattern for interfacing with devices.

Writing the driver for the TED was relatively easy and is a subject for another post.


## Reference

For reference here are some other interesting TED hacking sites out there:

* [APIs of various forms](http://www.bananabend.net/energy_detective/)
* [TED wire protocol decoded](http://misterhouse.svn.sourceforge.net/viewvc/misterhouse/trunk/lib/TED.pm)
* [Building your own decoder interface](http://scanlime.org/2008/10/interfacing-with-the-energy-detective/). Extreme!
