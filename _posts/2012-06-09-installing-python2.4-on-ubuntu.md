---
layout: post
title: Building Python 2.4.3 on Ubuntu 12.04
---

The ConnectPort series of gateways from Dia run an embedded version of Python 2.4. Python 2.4 is no longer readily available in recent distros so here's how I installed it. Having had to do this painful exercise twice now so writing it down to make it easier next time.

1. Download 2.4.3 source from [python.org](http://www.python.org/download/releases/2.4.3/) and unpack.
1. Install prereqs: `sudo apt-get install zlib1g-dev`
1. Configure. `./configure BASECFLAGS=-U_FORTIFY_SOURCE -with-zlib=/usr/include`
1. Edit `Modules/Setup` and uncomment the line starting with `zlib`
1. Build: `make`
1. Install: `sudo make install`
1. Remove new symlink that install creates. `sudo rm /usr/local/bin/python`. The symlink in `/usr/bin/python` will still point to 2.7ish.

Python 2.4 can now be involved with `python2.4`.