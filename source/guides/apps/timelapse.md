---
title: Timelapse Photos
---

## Applications

In this guide, we are going to set up your first 'cloud' instance of a Reactor that you can execute an application in. In this case, the cloud is going to reside on your laptop.

Just like you did on the Raspberry Pi in the previous guide step, move to a development directory and clone the Reactor project into this directory:

`git clone https://github.com/nitrogenjs/reactor reactor`

Navigate into the reactor directory.  Edit the config.js to name the reactor 'Cloud Reactor' so you can differentiate it from the previous one on your Raspberry Pi and start the reactor:

`node server.js`

This will start the reactor, and like any device, will provide you with a claim code:

`This principal (533edfae242d25eab7ff036f) can be claimed using code: FBSC-7703`

Copy this claim code and claim the reactor as your own using the Nitrogen command line tool:

`> n2 principal claim FBSC-7703`

Now that we have the reactor instance running on your computer, we can deploy applications to it just like on your Raspberry Pi.

This time we are going to deploy an application called 'timelapse' that knows how to take timelapse photos using the camera we created in the previous step.

`> n2 reactor install 'Cloud Reactor' timelapse`

The timelapse application takes 20 evenly distributed shots during the daylight hours using a camera. To do that, it needs a camera id and the latitude/longitude of the camera at startup.  Let's get the camera ID using the following command:

`> n2 principal ls`

Look up your latitude / longitude (remember that west longitudes are negative) using your favorite search engine and then start the application with these parameters (note the single quote escape around the JSON argument and that the keys are double quoted):

`> n2 reactor start 'Cloud Reactor' timelapse '{"camera_id": "53432d9f32f757d131fbf4a8",`
`     latitude: "36.9720", longitude: "-122.0263"}'`

This will start the application, which will compute the sunrise and sunset times using the excellent npm module SunCalc and then send twenty uniformly distributed [cameraCommands](/docs/schemas/cameraCommand.html) to the camera you passed. Your camera will dutifully execute these commands when their timestamp goes current. You can see this execution command stack using the [web admin](https://admin.nitrogen.io).

I use this app to take timelapsed photos of my garden so I can watch it grow over the course of a season. Your next challenge is to dream something up and build a Nitrogen application or device of your own. Write me and [tell me about it](mailto:timfpark@gmail.com)!