---
title: A platform for connecting devices and applications.
---

<center>
    <img class="logo" src="images/logo.png" width="166" height="167" />
    <h1 class="text-center">A platform for connecting real world devices and applications.</h1>
</center>

<div class="row" style="margin-top: 20px">
    <div class="col-md-4">
        <h3>Device Platform</h3>
        <p style="font-size: 120%">
            Nitrogen provides the real-time messaging, authentication, and authorization for your device so you can focus on building your application.
        </p>
    </div>
    <div class="col-md-4">
        <h3>Open Source</h3>
        <p style="font-size: 120%">
            End to end open source. Built on node.js and runs on any hardware. Nitrogen is about getting things to communicate on the internet -- not building a seperate internet for things.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Secure</h3>
        <p style="font-size: 120%">
            Real world things are often more sensitive than the computing devices we already have. Nitrogen provides a built-in authentication and authorization system to keep your devices, users, and data safe.
        </p>
    </div>
</div>

<h3>Easy Application Model</h3>
<p style="font-size: 120%">
    Let's say you wanted to watch four thermostats in your house and use these to control a heater. With Nitrogen, it only takes a few lines of code to combine the context of these devices into a realtime control application:
</p>

```javascript
var temperatures = {};
var SETPOINT = 21.0;
var lastCommand;

session.onMessage({ type: 'temperature' }, function(message) {
    temperatures[message.from.id] = message.body.temperature;

    var avg = avgTemperature(temperatures);

    if (avg && avg < SETPOINT && (!lastCommand || !lastCommand.body.on)) {
        lastCommand = new nitrogen.Message({
            type: 'switchCommand',
            to: heater.id,
            body: {
                on: true
            }
        }.send(session));
    }

});
```

<a href="/guides/start/setup.html" class="btn green"  style="margin-top: 10px">Learn More</a>
