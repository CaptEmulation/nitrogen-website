---
title: Nitrogen Reactor
---

# Reactor

A Reactor is the application execution environment for Nitrogen. It is a supervisory process that manages the complete lifecycle of an application: installing, establishing a security context, starting, stopping, upgrades, and uninstalling. Each application in a reactor executes in its own node.js process, and within that process, within an isolated virtual machine that only has access to a session, its package dependencies, and the Nitrogen client module.

Reactors themselves watch their stream of reactorCommand messages, perform the appopriate tasks, and emit reactorStatus messages with the new state of all of their instances.

Reactors expect applications to expose a very simple module interface:

* start(session, params): Function called when the reactor starts an application. It is passed the session the instance was told to execute under and a free form params object that the application can use to customize its execution that is provided by the reactorCommand that initiated this start.

* stop(): Function called when the reactor stops an application. Used to perform any required cleanup.

These two functions are the only requirements for a Nitrogen application. In all other ways applications are just node.js modules.