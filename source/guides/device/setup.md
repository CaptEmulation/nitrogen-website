---
title: Setup
---

## Setup

This guide builds on the [first steps guide](/guides/start/setup.md) where we built a connected computer webcam. The step we'll take in this guide is to connect a Raspberry Pi with an attached USB camera to Nitrogen.

For this walkthrough, we'll use a [Raspberry Pi](http://www.adafruit.com/products/998), a USB webcam, and a 4GB SD flash card but any node.js capable embedded hardware platform should work as well.

To prepare our Raspberry Pi device to run Nitrogen applications, we need to:

1. Install Raspbian. [Lifehacker](http://lifehacker.com/5976912/a-beginners-guide-to-diying-with-the-raspberry-pi) has a good walkthrough for doing this.

2. Install node.js on the device. You can do that from the Pi's command line shell by executing these commands:

* `> sudo apt-get update`
* `> sudo apt-get install -y python-software-properties python g++ make`
* `> sudo add-apt-repository ppa:chris-lea/node.js`
* `> sudo apt-get update`
* `> sudo apt-get install nodejs`
* `> node --version` (should display version 0.10 or greater)

And with that you are set up. Let's [setup the camera device application](camera.html) next.