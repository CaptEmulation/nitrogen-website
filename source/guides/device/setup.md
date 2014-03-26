---
title: Setup
---

## Setup

For this guide, we are going to walk through getting a Raspberry Pi device setup as a connected camera. This builds on the previous [first steps guide](/guides/start/setup.md) where we built a connected webcam. We're now going to use a real device with an attached USB camera.

In this section, we're going to connect a camera connected to a Raspberry Pi to Nitrogen. We're using a [Raspberry Pi](http://www.adafruit.com/products/998), a USB webcam, and a 4GB SD flash card for this guide but any node.js capable platform should work as well. 

To prepare our Raspberry Pi device to run Nitrogen applications, we need to:

1. Install Rasbian. [Lifehacker](http://lifehacker.com/5976912/a-beginners-guide-to-diying-with-the-raspberry-pi) has a good walkthrough for doing this.

2. Install node.js on the device. You can do that from the Pi's command line shell by executing these commands:
    
* `> sudo apt-get update`
* `> sudo apt-get install -y python-software-properties python g++ make`
* `> sudo add-apt-repository ppa:chris-lea/node.js`
* `> sudo apt-get update`
* `> sudo apt-get install nodejs`
* `> node --version` (should display version 0.10 or greater)

And with that you are set up. Let's [setup the camera device application](camera.html) next.