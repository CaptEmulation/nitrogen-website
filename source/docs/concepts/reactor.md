---
title: Nitrogen Reactor
---

# Reactor

A Reactor is the application execution environment for Nitrogen. It is a supervisory process that manages the complete lifecycle of an application: installing, establishing a security context, starting, stopping, upgrades, and uninstalling. Each application in a reactor executes in its own node.js process, and within that process, within an isolated virtual machine that only has access to a session, its package dependencies, and the Nitrogen client module.

Reactors themselves watch their stream of reactorCommand messages, perform the appopriate tasks, and emit reactorStatus messages with the new state of all of their instances.

An example of a very simple stub Nitrogen looks like:

```javascript
var running = false;
var session;
var params;

var interval;

var periodicFunction = function(){
    if (running) {
        session.log.info("app is still running with params: " + JSON.stringify(params));
    } else {
        session.log.info("app was asked to stop.");        
    }
};

var start = function(s, p) {
    session = s;
    params = p;

    running = true;
    interval = setInterval(periodicFunction, 1000);
};

var stop = function() {
    clearInterval(interval);
    running = false;
};

setInterval(function() {
    console.log('app process is still running');
}, 5000);

module.exports = {
    start: start,
    stop:  stop
}
```

Reactors expect the modules that contain Nitrogen applications to expose a very simple interface:

* start(session, params): Function called when the reactor starts an application. It is passed the session the instance was told to execute under and a free form params object that the application can use to customize its execution that is provided by the reactorCommand that initiated this start.

* stop(): Function called when the reactor stops an application. Used to perform any required cleanup.

These two functions are the only requirements for a Nitrogen application. In all other ways applications are just npm modules.