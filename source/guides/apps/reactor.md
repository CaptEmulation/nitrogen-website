---
title: Nitrogen Reactor
---

## Device Applications

As you've seen in the previous two guides, there were a lot of repeated steps in setting up the typical device application. In this guide, we'll see how we can automate 
all of these steps while at the same time being able to remotely manage our devices using the [Nitrogen Reactor](/docs/concepts/reactor.md).

The [Reactor](/docs/concepts/reactor.md) is Nitrogen's application execution environment. Applications in Nitrogen are written in JavaScript, are passed a session and parameters at startup, and implement <b>start</b> and <b>stop</b> methods. The [Reactor](/docs/concepts/reactor.md) manages the execution of these modules based on command messages that are sent to it. This allows us to install, start, stop, and uninstall applications to it without having to have network or shell access to the device.

For the Raspberry Pi, the Nitrogen project mantains prebuilt versions of the Raspbian distribution with the Reactor preinstalled. You can download this image from the [web admin](https://admin.nitrogen.io) under the API Keys top navigation item. The image you download will also automatically be personalized with your API key so no configuration of this image is needed.

Once you have the image, shutdown the Raspberry Pi if necessary and remove the SD card.  Insert this SD card into your computer and flash this image to your SD card with the method appropriate for your operating system:

#### Windows:
  + Install [Win32DiskImager](http://sourceforge.net/projects/win32diskimager/) and use its GUI to burn the image to the SD card.

#### MacOS: 
  + sudo diskutil list (note the disk number for your flash drive in the listing that follows the form /dev/rdiskX)
  + sudo diskutil unmountDisk /dev/rdiskX 
  + sudo dd bs=128m if=raspbian-xxxxxxxxxxxxxxx.img of=/dev/rdiskX`

#### Linux:
  + [Follow these instructions](http://xmodulo.com/2013/11/write-raspberry-pi-image-sd-card.html)

With the SD card flashed, put the SD card back into the Raspberry Pi, connect it to ethernet and power it on. The Raspberry Pi will boot and automatically provision itself with the Nitrogen service. It will appear as a reactor principal type, which means that it can receive and execute Nitrogen applications.

Now that we have the reactor instance running on the Raspberry Pi, we can deploy applications to it. Let's deploy the <b>fswebcam-app</b> application to it that can take photos.

We want to run this device application in the security context of a camera device. You can create this principal using the command line tool:

`> n2 principal create --type device --name 'Camera'`

We then install the application to the reactor, passing it the name of this principal and asking it to execute the application under this principal:

`> n2 reactor install 'Reactor' fswebcam-app --executeAs 'Camera'`

This will install the <b>fswebcam-app</b> module into its own container within this Nitrogen reactor from node.js's npm package registry. You can watch the status in the console logs or via the state command:

`> n2 reactor state 'Reactor'`

Once the fswebcam-app instance is installed it will show as being in 'stopped' state.  When that happens, start it up using:

`> n2 reactor start 'Reactor' fswebcam-app`

This will start the application, which will discover and connect your USB attached camera to Nitrogen as a new device. You can now use the [web admin](https://admin.nitrogen.io) to control it and take snapshots as we have seen in the previous guides.

Once you've tried that out, continue on to the next guide that will show how you can also use the reactor to write [applications that use devices](/guides/apps/timelapse.html).