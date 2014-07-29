---
title: Camera Device with Nitrogen
---

## Camera Device

We created an account with the Nitrogen command line tool in the [previous guide](setup.md). Let's now get our first device connected.

To avoid the complexities around actual hardware for the moment, we're going to build a device around something that we all have: a camera on our laptop.

The first step is to clone a repo from the Nitrogen project and walk through the code and make some edits. From within a development directory on your machine, clone the camera project from the Nitrogen GitHub repo:

`> git clone https://github.com/nitrogenjs/camera camera`

### Walkthrough

The camera project you just cloned is an example of what a standalone device application looks like. Let's walk through the camera.js file and understand what's going on.

```javascript
var service = new nitrogen.Service(config);
```

The first thing we do is define the service that we want our device to connect to.  A [service](/docs/concepts/service.html) in Nitrogen connects authenticated [principals](/docs/concepts/principals.html) (devices, users, applications, etc.) together over [messaging](/docs/concepts/messages.html) where the access and visibility of any principal is controlled by the [permissions](/docs/concepts/permissions.html) you have defined for each principal. You don't need to understand the all of the details of that sentence for this guide -- but there is more detail in these links when you want to.

```javascript

var camera = new ImageSnapCamera({
    nickname: 'camera',
    name: "My Computer's Camera"
});

```

This defines the [camera device](/docs/devices/camera.html) that we'd like to use. A device in Nitrogen implements of a set of agreed upon functionality for the commands it is able to execute.

In this case, we are using an implementation of a [camera device](/docs/devices/camera.html) that uses the command line tool `imagesnap` on the Mac to take a picture. If you are using Linux, replace `ImageSnapCamera` with `FSWebcamCamera` and if you are using Windows replace it with `CommandCamCamera`.

The next line connects the camera to the Nitrogen service:

```javascript
service.connect(camera, function(err, session, camera) {
```

This is the key line of code.  In one line of code we have provisioned and authenticated our camera device with the service and established a session that we can communicate securely over.

The next block of code sets up a CameraManager to watch the camera's message stream and execute snapshot commands:

```javascript
new CameraManager(camera).start(session, function(err, message) {
    if (err) return session.log.error(JSON.stringify(err));
});
```

In Nitrogen, users, devices, and applications communicate with each other over messaging. There is a class of messages called [commands](/docs/concepts/commands.html) that control the operation of a device. Principals, if they have the permission to do so, can send messages to devices to ask that a particular operation is performed. Devices watch their stream of messages, take appropriate action(s) in response to commands, and send messages in response.

Because watching these message streams is a common operation, the client library defines a [commandManager](/docs/nitrogen/commandManager.html) class that provides the base functionality that can you can extend. For this device, we are using the [CameraManager](/docs/managers/cameraManager.html) subclass that knows how to control the camera device given a message stream that contains cameraCommands. Behind the scenes, the [CameraManager](/docs/managers/cameraManager.html) opens a message subscription to receive these messages in real time.

We need to make one modification to the project before we can connect our camera. In Nitrogen, every device requires an API key. An API key was automatically created for you when you created your account and you can find this key using the command line tool:

`> n2 apikeys ls`

Copy the key and export an environmental variable to your .bash_profile/.bashrc:

`export API_KEY=[YOUR KEY]`

on Windows:

`set API_KEY=[YOUR KEY]`

Adding this api key will automatically associate this device with your account when the device is created the first time.

### Start 'er up

Before we can start the device, we need to install the command line tool that the camera device uses to capture an image.

* Mac: Install the `imagesnap` package using: `brew install imagesnap`

* Linux (Ubuntu in this case): `sudo apt-get install fswebcam`

* Windows: [Install CommandCam](http://batchloaf.wordpress.com/commandcam/) and place it in your path.

With the binaries available, install the dependencies for our camera app:

`> npm install`

With that done, go ahead and start the application:

`> node camera.js`

The camera device should startup and connect to the service, and display something like this:

```
5/29/2014 20:42:15: Camera: info: CommandManager started.
```

Leave the device app running and lets use the [Nitrogen web admin to control it](admin.html).