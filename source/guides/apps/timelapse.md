---
title: Timelapse Photos
---

## Timelapse Photo Application

In this guide, we are going to set up your first instance of a Reactor that you can execute an application in. In this case, the Reactor is going to reside on your laptop.

Just like you did on the Raspberry Pi in the previous guide step, move to a development directory and clone the Reactor project into this directory:

`git clone https://github.com/nitrogenjs/reactor reactor`

Navigate into the reactor directory. Edit the config.js to name the reactor 'Laptop Reactor' so you can differentiate it from the previous one on your Raspberry Pi.

If you haven't already, set the environmental variable API_KEY to your api key (you can find this under API Keys) in

Start the reactor:

`node server.js`

Now that we have the reactor instance running on your computer, we can deploy applications to it just like on your Raspberry Pi.

This time we are going to deploy an application called 'timelapse' that knows how to take timelapse photos using the camera we created in the previous step.

We want to run this application in its own security context. You can create this principal using the command line tool:

`> n2 principal create --type app --name 'Timelapse App'`

And install the application to the Reactor that will execute as this application:

`> n2 reactor install 'Laptop Reactor' timelapse --executeAs 'Timelapse App'`

The timelapse application takes a photo every 15 minutes during the daylight hours using a camera. To do that, it needs a camera id and the latitude/longitude of the camera at startup. Let's get the camera ID using the following command:

`> n2 device ls`

Look up your latitude / longitude using your favorite search engine (remember that west longitudes and south latitudes are negative) and then start the application with these parameters (note the single quote escape around the JSON argument and that the keys are double quoted):

`> n2 reactor start 'Laptop Reactor' timelapse '{"camera_id": "53432d9f32f757d131fbf4a8",`
`     latitude: "36.9720", longitude: "-122.0263", only_daytime: true}'`

This will start the application, compute the sunrise and sunset times using the excellent npm module `suncalc` and then send uniformly distributed [cameraCommands](/docs/schemas/cameraCommand.html) to the camera during the daytime to take photos.

With that you have run your first application that controls a Nitrogen device.  Continue on to [the next guide](/guides/apps/web.html) see how you can write a web application that uses the output of your Nitrogen devices.