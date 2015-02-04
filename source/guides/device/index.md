---
title: Device Side Development
---

## Device Side Development

To connect a device to Nitrogen, you can use either Rest or MQTT. There are other protocols that are interesting such as CoAP and WAMP. If you are running on a platform that supports Node.js, there is an agent called the [Nitrogen Client Library](https://github.com/nitrogenjs/client) that handles the the authentication, sending and receiving messages from the server side. 

The recommendation is that you get started with a virtual device that you can run on your local machine and then move on to physical devices. 

## Virtual Devices

The first device to get started with is a virtual device. Find more information about that at [writing your first device](simpleLED.html). 

## Raspberry PI

An incredibly popular maker device is the Raspberry PI. This is one of the easiest devices to get started with because the Nitrogen Web Admin can actually create a Raspian image that you can copy directly on an SD card and start your device up. 

## Arduino Yun

A relativity new device is the Arduino Yun. It's got both a traditional Amtel chipset like the Arduino Due as well as a Linux system on a chip. It also has WiFi and Ethernet so you don't need an additional shield to connect to the network. 

The easiest way to work with the Yun and Nitrogen is through [Johnny-Five](http://node-ardx.org/). There's a whole set of labs on how to do this at [N2 Labs](http://github.com/joshholmes.com/n2labs).  

## Tessel

The Tessel is an interesting device that runs Lua which is a compiled form of JavaScript. As a result, we can use the MQTT gateway and the Node.js MQTT library. 

Please check out the [Tessel 2 Nitrogen lab](https://github.com/joshholmes/tessel2nitrogen) for more details. 

## Other devices

If you're not using one of the devices that we have listed here, we'd love to hear from you and help you get up and running. 