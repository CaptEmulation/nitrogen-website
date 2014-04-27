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
        <h3>Platform</h3>
        <p style="font-size: 120%">
            Nitrogen provides a real-time messaging and device management platform so that you can focus on your application or device.
        </p>
    </div>
    <div class="col-md-4">
        <h3>Build Device Grids</h3>
        <p style="font-size: 120%">
            Easily deploy and manage applications on tens to thousands of devices and combine them into applications.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Secure</h3>
        <p style="font-size: 120%">
            Nitrogen has a built-in authentication and authorization system to keep your devices, users, and data safe.
        </p>
    </div>
</div>

<h3>Application Model</h3>

<p style="font-size: 120%">
   Watching the temperatures from four devices and controlling a heater is as simple as:
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
    Nitrogen extensively leverages the node.js ecosystem so publishing this application is as simple as:
</p>

```javascript
> npm publish
```

<p style="font-size: 120%">
    and you can installing it on a device (or hundreds of devices) with just one command:
</p>

```javascript
> n2 reactor install 'Raspberry Pi' my-app
```


<a href="/docs/concepts/overview.html" class="btn green"  style="margin-top: 10px">Learn More</a>
