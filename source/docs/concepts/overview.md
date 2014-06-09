---
title: Nitrogen Overview
---

## Overview

Nitrogen is a platform for connecting together devices into applications.  It provides the device management, security and permissioning scheme, and application platform so that you can focus on building your application and not the infrastructure that surrounds it.

### Messaging Based

The reality of real world devices is that most are often intermittently connected to the network.  This might be because they are battery powered, because they are in motion and out of network coverage, or because they rely on another device for network access, but in the end, for a large class of devices, you can’t assume constant connectivity.

Nitrogen is [built around messaging](messages.html) to overcome this, enabling devices to send and receive messages when they are connected, and nearly everything in Nitrogen revolves around this concept.

Messaging also provides abstraction. Messages in Nitrogen follow well known schemas, which enables devices and applications to communicate with each other without having to know the details of the other's implementation.

### Authorization and Authentication

The real world devices in our lives and our workplaces are in many ways even more sensitive than the computing devices we already have, and therefore any platform for them has to have a mechanism for securing them.

At the same time, security is difficult to implement and even harder to get right. The [Nitrogen service](service.html) provides authentication and authorization for both devices and users out of the box. Nitrogen uses these [security principals](principals.html) throughout the platform in combination with an [ACL based permissions system](permissions.html) to authorize actions whether its sending [command messages](commands.html) to a device or the ability to subscribe to a particular device’s message stream.

### Application Environment

Finally, Nitrogen provides an application environment called [Reactor](reactor.html) that hosts and manages the lifecycle of applications that tie together devices. Applications in Nitrogen are written as node.js modules so that they can leverage the broad JavaScript developer base, the rich node.js package ecosystem, and the ability to publish and update them easily.

Applications in Nitrogen primarily work with the Nitrogen service with a [JavaScript client library](/docs/nitrogen/index.html).

### Getting Started

This section has a rich set of documentation around the core concepts of how everything fits together in Nitrogen but the best way to get started is to [build something](/guides/start/setup.html).  The project has a [set of guides](/guides/start/setup.html) to help you with that but don’t hesitate to reach out if you [need help or have feedback on the platform](mailto:timfpark@gmail.com).

<a href="/guides/start/setup.html" class="btn green"  style="margin-top: 10px">Get Started</a>