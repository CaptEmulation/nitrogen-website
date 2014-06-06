---
title: Timelapse Photos
---

## Applications

In this guide, we are going to set up your first instance of a Reactor that you can execute an application in. In this case, the reactor is going to reside on your laptop.

Just like you did on the Raspberry Pi in the previous guide step, move to a development directory and clone the Reactor project into this directory:

`git clone https://github.com/nitrogenjs/reactor reactor`

Navigate into the reactor directory. Edit the config.js to name the reactor 'Laptop Reactor' so you can differentiate it from the previous one on your Raspberry Pi, add your API key to apiKey.js, and start the reactor:

`node server.js`

Now that we have the reactor instance running on your computer, we can deploy applications to it just like on your Raspberry Pi.

This time we are going to deploy an application called 'timelapse' that knows how to take timelapse photos using the camera we created in the previous step.

`> n2 reactor install 'Laptop Reactor' timelapse`

The timelapse application takes 20 evenly distributed shots during the daylight hours using a camera. To do that, it needs a camera id and the latitude/longitude of the camera at startup. Let's get the camera ID using the following command:

`> n2 principal ls`

Look up your latitude / longitude using your favorite search engine (remember that west longitudes are negative) and then start the application with these parameters (note the single quote escape around the JSON argument and that the keys are double quoted):

`> n2 reactor start 'Laptop Reactor' timelapse '{"camera_id": "53432d9f32f757d131fbf4a8",`
`     latitude: "36.9720", longitude: "-122.0263", only_daytime: true}'`

This will start the application, compute the sunrise and sunset times using the excellent npm module `suncalc` and then send uniformly distributed [cameraCommands](/docs/schemas/cameraCommand.html) to the camera during the daytime to take photos.