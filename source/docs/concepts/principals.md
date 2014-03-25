---
title: Nitrogen Principals
---

# Principals

A principal is the unit of authentication and authorization in Nitrogen. Examples of principals in Nitrogen include devices, users, services, applications, and reactors.

## Properties

* type: The type of principal.  Nitrogen currently defines 4 types of principals:
    * app: An application that runs in a reactor. This principal has a set of permissions that are derived from the principal that installed the application.  For example, an application might only have permission to send messages to one device and follow messages from another device even though the user that installed it can send and follow messages from many more devices.
    * device: Represents a physical piece of hardware.
    * reactor: Application execution environment in Nitrogen.
    * service: A service that acts as a messaging hub for a set of principals.
    * user: A user is a human user of the system.  Users authenticate via email and password.
* name: A human readable name applied to this Principal.