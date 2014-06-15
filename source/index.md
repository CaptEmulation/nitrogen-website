---
title: A platform for connecting devices and applications.
---

<table width=100%>
    <tr>
        <td>
            <img class="logo" src="images/logo.png" width="166" height="167" />
        </td>
        <td>
            <h1 class="text-center">Nitrogen connects devices together into applications.</h1>
        </td>
    </tr>
</table>

<div class="row" style="margin-top: 20px">
    <div class="col-md-4">
        <h3>Application Platform</h3>
        <p style="font-size: 120%">
            Build applications with a common cloud and device application model based on JavaScript.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Manage devices</h3>
        <p style="font-size: 120%">
            Remotely install applications, monitor their operation, and control and receive telemetry from them with messages. 
        </p>
    </div>

    <div class="col-md-4">
        <h3>Secure</h3>
        <p style="font-size: 120%">
            Nitrogen's built-in authentication and authorization system keeps your devices, users, and data safe.
        </p>
    </div>
</div>

<h3>Applications</h3>
<p style="font-size: 120%">
   Controlling a heater based on the measurements of four thermostats looks like this in a Nitrogen application:
</p>

```javascript
var temperatures = {};
var SETPOINT = 21.0;
var lastCommand;

session.onMessage({ type: 'temperature' }, function(message) {
    temperatures[message.from.id] = message.body.temperature;

    var avg = avgTemperature(temperatures);

    if (avg && avg < SETPOINT) {
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

<p style="font-size: 120%">
    Making an application installable on a device is as simple as using node.js package manager to publish it:
</p>

```javascript
> npm publish
```

<p style="font-size: 120%">
    and installing it on a device is then just:
</p>

```javascript
> n2 app install 'Raspberry Pi' heating-control
```

<a href="/docs/concepts/overview.html" class="btn green"  style="margin-top: 10px">Learn More</a>
