---
title: Nitrogen Principals
---

# Principals

A Principal is the unit of authentication and authorization in Nitrogen.  

Nitrogen currently defines 4 types of principals:

* device: A device is a principal that represents a physical piece of hardware.  A device authenticates using a secret that is known to only it and the service.
* user: A user is a human user of the system.  Users authenticate via email and password combinations (currently).
* service: A service is a Nitrogen service that acts as a messaging hub for a set of principals that are interacting with it.
* app: An application that runs in a reactor. This principal has a set of permissions that are derived from the principal that installed the application.  For example, an app might only have permission to send messages to one device and follow messages from another device even though the user that installed it can send and follow messages from many more devices.
