---
title: Nitrogen Raspberry Pi Camera
---

## Setup Camera Application

This step is nearly the same as what we did for your computer's camera in the [previous guide](../start/camera.md), which also has a walkthrough of the structure of a device application.

Clone the camera project again from the Nitrogen project. In a shell for your Raspberry Pi run:

`> git clone https://github.com/nitrogenjs/camera camera`

This clones the camera device application onto your device. We also need to install the fswebcam command line tool that this device application uses to take photos:

`> sudo apt-get install fswebcam`

Next we need to install the node.js dependencies for this application:

`> npm install`

Like with the laptop camera in the previous guide, we need to the API key to your camera project.  You can find this key using the command line tool:

`> n2 apikeys ls`

Copy the key and either export an environmental variable:

`> export API_KEY=[key]`

or directly edit config.js and assign api_key there to this value.

Adding this api key will automatically associate this device with your account when the device is started.

### Start Application

With that done, go ahead and start the application:

`> node camera.js`

The camera device should startup and connect to the service, and display something like this:

```
5/29/2014 20:42:15: Camera: info: CommandManager started.
```

With this you should we able to use the [web admin](https://admin.nitrogen.io) to claim and control the device like we did in the [previous guide](../start/admin). Try out your newly connected camera and then move on to the next guide, where we'll use the [Nitrogen Reactor](/docs/concepts/reactor.html) to easily install and start applications that use these devices.