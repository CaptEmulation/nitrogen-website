---
title: Nitrogen Raspberry Pi Camera
---

## Setup Camera Application

This step is nearly the same as what we did for your computer's camera in the [previous guide](../start/camera.md), which also has a walkthrough of the structure of a device application.

Clone the camera project again from the Nitrogen project. In a shell for your Raspberry Pi run:

`> git clone https://github.com/nitrogenjs/camera camera`

This clones the camera device application onto your device. We also need to install the fswebcam command line tool that this device application uses to take photos:

`> sudo apt-get install fswebcam`

Finally, we need to install the node.js dependencies for this application:

`> npm install`

### Start Application

With that done, go ahead and start the application:

`> node camera.js`

The camera device should startup, connect to the service, and display something like this:

```
This principal (5321e2debe46b41671000662) can be claimed using code: IQGY-0080
```

With this you should we able to use the [web admin](https://admin.nitrogen.io) to claim and control the device like we did in the [previous guide](../start/admin). Try out your newly connected camera and then move on to the next guide, where we'll use the [Nitrogen Reactor](/docs/concepts/reactor.html) to easily install and start applications that use these devices.