---
title: Building a simple GPS logger
layout: post
---
In the spirit of "there's no data like more data" I've been looking for ways to generate a relatively high fidelity geospatial log of my location and travel behavior. There are commercial products on the market for this too but none did quite what I have in mind. The current unit is very simple and doesn't even have a separate microprocessor although I will likely need one as I add more functionality.

##Materials
* [Venus GPS with SMA connector](http://www.sparkfun.com/products/11058)
* [0.2F/3.3V supercap](http://www.sparkfun.com/products/10317)
* [OpenLog](http://www.sparkfun.com/products/9530)
* [SMA antenna](http://www.sparkfun.com/products/464)
* Buck converter 12V->3.3V (ordered on Ebay)
* Andersen PowerPoles
* 4GB Micro SD card
* [Enclosure](http://www.radioshack.com/product/index.jsp?productId=2062279)

##Construction
Install the DC converter in the enclosure. It's an unnecessarily large converter (physically as well as current) but was cheap and easy. The OpenLog fits nicely down one side. Although not visible here there is a header soldered to the bottom side at right angles to the board sitting under the converter which provides some nice stability on insert/eject.

![](http://photos.andyoakley.com/photos/i-pQ5ZW4j/0/M/i-pQ5ZW4j-M.jpg)

The Venus unit only requires three connections for this purpose (VCC, ground and TX). The TX line goes directly into the RX line on the logger. Both units are configured at 9600 bps 8N1 by default. Although not visible here the supercap has been soldered to the underside of the board to provide fast reaquisition of signal. 

![](http://photos.andyoakley.com/photos/i-9vqzM7b/0/M/i-9vqzM7b-M.jpg)

The Powerpoles make it easy to install/remove the unit. I have this wired into the vehicle to receive power only when the ignition is on.

![](http://photos.andyoakley.com/photos/i-C4CWT92/0/M/i-C4CWT92-M.jpg)

The magnetic antenna sits on the roof and enters the cab through a hole in the floor.

##Next
This project isn't finished by a long stretch. It's capturing data reliably now but still requires the unit to be opened up to read the card which is something I do about once a week or so. I'd like to add some vehicle info from the [OBDII interface](http://en.wikipedia.org/wiki/OBDII) and also have the unit upload its data wirelessly when in range of my home wifi or Xbee network.