---
title: A platform for building amazing devices.
---

<center>
    <img class="logo" src="images/logo.png" width="166" height="167" /> 
    <h1 class="text-center">A platform for building amazing devices</h1>
</center>

<div class="row" style="margin-top: 20px">
    <div class="col-md-4">
        <h3>Device Platform</h3>
        <p style="font-size: 120%">
            Nitrogen provides the real-time messaging, authentication, and authorization for your device so you can focus on building your devices and applications.
        </p>
    </div>
    <div class="col-md-4">
        <h3>Open Source</h3>
        <p style="font-size: 120%">
            End to end open source. No proprietary client languages, no lock-in to cloud services, no required hardware. Nitrogen aims at getting things on the internet, not building a seperate internet for things.
        </p>
    </div>

    <div class="col-md-4">
        <h3>Secure</h3>
        <p style="font-size: 120%">
            Real world things are often more sensitive than the computing devices we already have. Nitrogen provides a built-in authentication and authorization system to keep your devices, users, and data safe.
        </p>
    </div>
</div>

<h2 style="margin-bottom: 20px">Connecting and controlling your devices should be this easy:</h2>

```javascript
var light = new Light({ nickname: 'livingRoomLight' });
service.connect(light, function(err, session) {

    // listen for messages of type lightCommand and act on them
    session.onMessage({ type: 'lightCommand' }, function(err, message) {
        light.set(message.body.command);
    });
});
```
<a href="/guides" class="btn green"  style="margin-top: 10px">Learn More</a>