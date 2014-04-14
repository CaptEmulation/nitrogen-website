---
title: Nitrogen Reactor
---

## Nitrogen Applications

As you've seen in the previous two guides, there were a lot of repeated steps in setting up the typical device application. In this guide, we'll see how we can reduce this and at the same time be able to share device applications with each other using the [Nitrogen Reactor](/docs/concepts/reactor.md).

This guide builds on the [hardware device guide](/guides/device/setup.md) and assumes you have already have a Raspberry Pi device up and running. If you don't, jump back to the previous guide and complete that first.

The [Reactor](/docs/concepts/reactor.md) is Nitrogen's application execution environment. Applications in Nitrogen are simply JavaScript objects that are passed a sessions and parameters at creation.

In this guide, we'll see how we can use the Reactor for both device and cloud applications.

Let's start with setting up a Reactor on the Raspberry Pi to execute the camera device application.

You can do this by cloning the Reactor project into its own directory on your device:

`> git clone https://github.com/nitrogenjs/reactor reactor`

Navigate into the reactor directory. First install its dependencies:

`> npm install` 

Then start the reactor.  The reactor needs to run as root so that it can create a secure jail
for executing applications:

`> sudo node server.js`

This will start the reactor, and like any device, will provide you with a claim code:

`This principal (533edfae242d25eab7ff036f) can be claimed using code: FBSC-7703`

Copy this claim code and claim the reactor as your own using the Nitrogen command line tool:

`> n2 principal claim FBSC-7703`

Now that we have the reactor instance running on the Raspberry Pi, we can deploy applications to it.  Let's deploy the fswebcam-app application to it that can take photos with fswebcam.

The first thing we need to do is create a camera device pricipal in Nitrogen. This will be the security principal this application runs under in the Reactor:

`> n2 principal create --type --capabilities cameraCommand --name 'RPi Camera'`

We then install the application to the reactor, passing it the name of this principal and asking it to execute the application under this principal instead of our user principal:

`> n2 reactor install 'Reactor' fswebcam-app --executeAs 'RPi Camera'`

This will install the usb-camera module onto this Nitrogen reactor from node.js's npm package registry. You can watch the status in the console logs or via the state command:

`> n2 reactor state 'Reactor'`

Once the usb-camera instance has installed and is in the state 'stopped', start it up using:

`> n2 reactor start 'Reactor' fswebcam-app`

This will start the application, which will discover and connect your USB attached camera to Nitrogen as a new device. You can now use the [web admin](https://admin.nitrogen.io) to control it and take snapshots.

Once you've tried that out, continue on to find out how we can use the reactor for [applications that use our devices](/guides/apps/timelapse.html).
