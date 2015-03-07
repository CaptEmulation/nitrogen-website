---
title: First Thermometer with Nitrogen
---

## Thermometer Device

We created an account with the Nitrogen command line tool in the [previous guide](setup.html). Let's now get our first device connected.

For this guide, we are going to skip the complexities around actual hardware for the moment and use simulated values for thermometer.

Let's first clone a repo from the Nitrogen project and walk through the code and make some edits. From within a development directory on your machine, clone the camera project from the Nitrogen GitHub repo:

`> git clone https://github.com/nitrogenjs/thermometer thermometer`

### Walkthrough

The thermometer project you just cloned is an example of what a standalone device application looks like. Let's walk through the thermometer.js file and understand what's going on.

```javascript
var service = new nitrogen.Service(config);
```

This first line defines the service to which we want our device to connect. A [service](/docs/concepts/service.html) in Nitrogen connects authenticated [principals](/docs/concepts/principals.html) (devices, users, applications, etc.) together over [messaging](/docs/concepts/messages.html) where access to and visibility of any principal and its message stream is controlled by the [permissions](/docs/concepts/permissions.html) you have defined for each principal. You don't need to understand the all of the details of that sentence for this guide -- but there is more detail in these links when you want to.

The next few lines connects the thermometer to the Nitrogen service:

```javascript
var thermometer = new nitrogen.Device({
    nickname: 'thermometer',
    name: 'Thermometer'
});

service.connect(thermometer, function(err, session, thermometer) {
```

The last line is a key line of code. With this we have provisioned and authenticated our thermometer device with the service and established a session that we can communicate securely over.

The next block of code sets up a periodic interval to measure a temperature and then send a message with a [temperature schema](/docs/schemas/temperature.html) that applications can react to or proces downstream:

```javascript
    // collect a temperature sample every second
    setInterval(function() {
        measureTemperature(function(temp) {

            var temperature = new nitrogen.Message({
                type: 'temperature',
                body: {
                    temperature: temp
                }
            });

            console.log('sending temperature: ' + temp);

            temperature.send(session);
        });
    }, 1000);
```

In Nitrogen, every device requires an API key. An API key was automatically created for you when you created your account and you can find this key using the command line tool:

`> n2 apikeys ls`

On MacOS or Linux, copy the key and export an environmental variable within your to your .bash_profile/.bashrc:

`export API_KEY=[YOUR KEY]`

under Windows add a API_KEY variable to your environmental variables or temporarily on the command line:

`set API_KEY=[YOUR KEY]`

This api key automatically associates new devices with your account when the device is created the first time.

### Start 'er up

With the binaries available, install the dependencies for our thermometer app:

`> npm install`

With that done, go ahead and start the application:

`> node themometer.js`

The thermometer device should startup and connect to the service, and display something like this:

```
sending temperature: 20.23414512
```

Leave the device app running and lets use the [Nitrogen web admin to view the incoming telemetry](admin.html).