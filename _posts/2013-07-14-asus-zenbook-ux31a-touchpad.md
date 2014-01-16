---
layout: post
title: Customizing the Asus Zenbook UX31A touchpad 
---
 
I recently started using the Asus Zenbook UX31A. Overall I've been pleased -- it's a solid machine with decent battery life, the screen is vivid and I'm using touch more than I expected to.

My only real complaint has been around the touchpad which has a few quirks. An updated driver and a few registry tweaks have made things much more familiar. The result is a trackpad acts and behaves much more like a Macbook touchpad (no taps, click to select; no right button, two finger click for right click).

1. Download and install the Elantech drivers. I'm using [11.6.8][elan] from Acer.
1. Make the following registry changes under `HKEY_CURRENT_USER\Software\Elantech\Smartpad`.
	* Make a click on the right lower corner the same as a click anywhere. Set `ClickPad_RightCorner_Click_Func` to `0`.
    * Disable tap-to-click. Set `Tap_Enable` to `0`.
    * Map two-finger-click to right click. Set `ClickPad_TwoFinger_Click_Func` to `1`.
1. Adjust sensitivity under `HKEY_CURRENT_USER\Control Panel\Mouse` by setting `MouseSensitivity` to `14`.

Done! 



[elan]:http://global-download.acer.com/GDFiles/Driver/TouchPad/TouchPad_ELANTECH_11.6.8.001_W8x64_A.zip?acerid=634843401245976100&Step1=Notebook&Step2=Aspire&Step3=Aspire%20M3-581TG&OS=8cn1&LC=en&BC=Acer&SC=EMEA_1
