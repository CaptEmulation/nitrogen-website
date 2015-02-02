---
title: Nitrogen Principals
---

# Principals

A principal is the unit of authentication and authorization in Nitrogen. Examples of principals in Nitrogen include devices, users, services, applications, and reactors.

## Properties

* <b>type</b>: The type of principal.  Nitrogen currently defines 6 types of principals:
    * <b>app</b>: An application that runs in a reactor. This principal typically has a set of permissions that are derived from the principal that installed the application. For example, an application might only have permission to send messages to one device even though the user that installed it has permissions to send and follow messages to all of their devices.
    * <b>device</b>: Represents a device that produces data messages, for example, a camera or temperature sensor.
    * <b>group</b>: Represents a group of principals. Sending a message to a group principal will fan out the message to all of the member principals.
    * <b>reactor</b>: The application execution environment in Nitrogen.
    * <b>service</b>: A service acts as a messaging hub for a set of principals and enforces permissions between them.
    * <b>user</b>: A user is a human user of the system. Users authenticate via email and password.
* <b>members</b>: An array of principal ids that form the members that belong to a group.
* <b>name</b>: A human readable name for this Principal.
* <b>nickname</b>: A local name for this Principal that is used to store the principal locally
* <b>nickname</b>: A local name for this Principal that is used to store the principal locally
