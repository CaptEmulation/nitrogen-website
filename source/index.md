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
    Nitrogen is a cloud framework for the Internet of Things (IoT). The backend is all written in Node.js. Device side, there is an agent written in Node.js but you can use Rest or MQTT and skip the agent completely.
</div>

<div class="row" style="margin-top: 20px">
There are three possible places to get started depending on what you want to do first.
</div>

<div class="row" style="margin-top: 20px">
    <div class="col-md-4">
        <h3>Secure</h3>
        <p style="font-size: 120%">
            Nitrogen provides identity, discovery, authentication, and authorization services for your devices and application via its <a href="http://github.com/nitrogen/registry">Device Registry</a>.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Messaging</h3>
        <p style="font-size: 120%">
            Send and process messages at scale using Nitrogen's <a href="http://github.com/nitrogen/ingestion">Ingestion</a> and <a href="http://github.com/nitrogen/consumption">Consumption</a> servers.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Applications</h3>
        <p style="font-size: 120%">
            Quickly build applications using JavaScript and Cordova using Nitrogen's <a href="http://github.com/nitrogen/oxide">Oxide</a> application seed.
        </p>
    </div>
</div>

<div class="row" style="margin-top: 20px">
    <div class="col-md-4">
        <h3>Any Device</h3>
        <p style="font-size: 120%">
            Nitrogen supports connecting devices via MQTT or using our node.js <a href="http://github.com/nitrogen/client">client library</a>.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Open</h3>
        <p style="font-size: 120%">
            Use the pub sub, scaled message hub, blob storage, and/or archival storage of the infrastructure you've chosen via Nitrogen's <a href="http://github.com/nitrogen/providers">provider plug-in</a> model.
        </p>
    </div>


    <div class="col-md-4">
        <h3>Ready to Deploy</h3>
        <p style="font-size: 120%">
            Nitrogen has a full set of <a href="http://github.com/nitrogen/devops">devops tooling</a> for deploying both development and scaled server environments.
        </p>
    </div>

</div>

<h3>Applications</h3>

<p style="font-size: 120%">
   An application that controls a heater using the measurements of four thermometers could be implemented like this using the JavaScript SDK:
</p>

```javascript
var temperatures = {};
var SETPOINT = 21.0;
var lastCommand;

session.onMessage({ type: 'temperature' }, function(message) {
    temperatures[message.from.id] = message.body.temperature;

    var avg = avgTemperature(temperatures);

    if (avg < SETPOINT) {
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

<a href="/docs/concepts/overview.html" class="btn green"  style="margin-top: 10px">Learn More</a>