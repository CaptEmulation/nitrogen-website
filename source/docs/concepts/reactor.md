---
title: Nitrogen Reactor
---

# Reactor

The Reactor is the application execution environment for Nitrogen. It manages the complete lifecycle of an application: installing, establishing a security context, starting, stopping, upgrades, and uninstalling. Each application in a reactor executes in its own node.js process, and within that process, within an isolated virtual machine where it only has access to its package dependencies in an isolated filesystem.

Reactor applications are just npm modules that expose an object that accepts a session and params object in its constructor and exposes two methods: start and stop. An example of a very simple Nitrogen application looks like this:

```javascript

function HelloWorldApp(session, params) {
    this.session = session;
    this.params = params;

    this.running = false;
    this.interval = null;
}

HelloWorldApp.prototype.start = function() {
    this.running = true;
    this.interval = setInterval(function(){
        session.log.info("Hello World!");
    }, 1000);
}

HelloWorldApp.prototype.stop = function() {
    clearInterval(this.interval);
    this.running = false;
}

module.exports = HelloWorldApp;

```

Nitrogen applications are published like any other npm module and to install them within a reactor, you use the Nitrogen command line tool, where the final argument to this command is the name of the application that you'd like to install:

`n2 reactor install 'My Reactor' hello-world-app`

This will send a reactorCommand message to the reactor named 'My Reactor' and install the application within its own instance. Once installed, you can then start this application using:

`n2 reactor start 'My Reactor' hello-world-app`

And stop it using:

`n2 reactor stop 'My Reactor' hello-world-app`

For a guided tour of using your first Nitrogen application, see the [Applications guide](/guides/apps/reactor.md).