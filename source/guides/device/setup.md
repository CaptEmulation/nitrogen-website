---
title: Setup
---

## Setup

This guide builds on the [first steps guide](/guides/start/setup.md) where we built a connected computer webcam. The step we'll take in this guide is to connect a Raspberry Pi with an attached USB camera to Nitrogen.

For this walkthrough, we'll use a [Raspberry Pi](http://www.adafruit.com/products/998), a USB webcam, and a 4GB SD flash card but any node.js capable embedded hardware platform should work as well.

To prepare our Raspberry Pi device to run Nitrogen applications, we need to:

1. Install Raspbian. [Lifehacker](http://lifehacker.com/5976912/a-beginners-guide-to-diying-with-the-raspberry-pi) has a good walkthrough for doing this.

2. Install node.js on the device from the Pi's shell:

`> wget http://node-arm.herokuapp.com/node_latest_armhf.deb`

`> sudo dpkg -i node_latest_armhf.deb`

`> node --version` (should display version 0.10 or greater)

And with that you have node.js installed. Let's [setup the camera device application](camera.html) next.
