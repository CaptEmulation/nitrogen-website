---
title: Camera Device with Nitrogen
---

## Camera Device

With an account created and the Nitrogen command line tool [set up](setup.md), let's build our first device.

To avoid the complexities around actual hardware for the moment, we're going to build a device around something that we all have: a camera on our laptop.  Let's make that camera internet controllable.

Instead of writing the device application from scratch, let's clone a repo from the Nitrogen project and walk through the code and make some edits.  Change to a development directory on your machine and run:

`> git clone https://github.com/nitrogenjs/camera camera`

### Walkthrough

This camera project is a canonical example for what a standalone device application looks like. Let's walk through the camera.js file and understand what's going on.

```javascript
var service = new nitrogen.Service(config);
```

The first thing we do is define the service that we want our device to connect to.  A [service](/docs/concepts/service.html) in Nitrogen connects authenticated [principals](/docs/concepts/principals.html) (devices, users, applications, etc.) together over [messaging](/docs/concepts/messages.html) where the access and visibility is controlled by the [permissions](/docs/concepts/permissions.html) you have defined for each principal.  You don't need to understand that in detail at the moment -- but there is more detail in these links when you want to.

```javascript

var camera = new ImageSnapCamera({
    nickname: 'camera',
    name: "My Computer's Camera"
});

``` 

This defines the [camera device](/docs/devices/camera.html) that we'd like to use.  A device in Nitrogen implements of a set of functionality behind an interface.

In this case, we are using an implementation of a [camera device](/docs/devices/camera.html) that uses the command line tool `imagesnap` on the Mac to take a picture.  If you are using Linux, replace this class with `FSWebcamCamera`.

```javascript
service.connect(camera, function(err, session, camera) {
```

With the service and camera created, we now connect the camera to the service.  This is the key  line of code.  In one line of code we have provisioned and authenticated the device with the service, established a session with the service that we can communicate securely over, and also wrapped this session such that it will restart in the case of network interruptions.

```javascript
new CameraManager(camera).start(session, function(err, message) {
    if (err) return session.log.error(JSON.stringify(err));
});
```

In Nitrogen, users, devices, and applications communicate with each other over messaging. There is a class of messages called [commands](/docs/concepts/commands.html) that control the operation of a device. Principals, if they have the permission to do so, can send messages to devices to ask that a particular operation is performed. Devices watch their stream of messages, take appropriate actions to commands, and send messages in response.

Because monitoring these message streams is a common operation, the client library defines a [commandManager](/docs/nitrogen/commandManager.html) class that provides this base level of functionality. For this device, we are using the [CameraManager](/docs/managers/cameraManager.html) subclass that knows how to control the camera device we are instantiating it with given a message stream that contains cameraCommands.  Behind the scenes, it opens a message subscription to receive these messages in real time.

That's it.  Let's start it up!

### Start 'er up

Before we can start the device, we need to install the command line tool that the camera device uses to capture an image.  If you're on a Mac, install the `imagesnap` package using:

`> brew install imagesnap`

or if you're using Linux:

`> sudo apt-get install fswebcam`

Finally, we need to install the dependencies for our camera app:

`> npm install`

With that done, go ahead and start the application:

`> node camera.js`

The camera device should startup, connect to the service, and display something like this:

```
This principal (5321e2debe46b41671000662) can be claimed using code: IQGY-0080
```

In Nitrogen, you need to claim your devices with the service using proof that you are the rightful owner of the device.  This claim code is the mechanism that you use to do that.  Copy this code to your clipboard, leave the device app running, and let's move on to using the [Nitrogen web admin to control it](admin.html).