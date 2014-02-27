---
title: Nitrogen Messages
---

# Messages

Messages are the core of the Nitrogen framework.  Applications, devices, and services use Messages to communicate with and issue commands to each other. All messages that don't begin with an underscore are checked against a schema chosen by the messages 'type' and 'ver' fields such that messages of a given type are known to conform to a particular structure. For custom message types, an application may use an unscore prefix (eg. '_myMessage') with any schema that they'd like.  This supports communication between principals of the same organization over a private schema.  That said, it is strongly encouraged to use standard schemas wherever possible.

Messages have a sender principal (referred to as 'from') and a receiver principal (referred to as 'to'). These fields are used to route messages to their receiver.

Message types are divided into two main classes: data and commands.  Data messages carry information, typically the output of a device's operation.  For example, a message typed 'image' contains an image url in its body in its 'url' property.

The second class of messages are commands. Command messages are sent from one principal to another to request an operation on the receiving principal.  For example, a message of the type 'cameraCommand' contains a command that directs the operation of a camera principal.