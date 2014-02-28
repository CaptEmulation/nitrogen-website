---
title: Nitrogen Messages
---

# Messages

Messages are the core of the Nitrogen framework.  Applications, devices, and services use Messages to communicate with each other. 

## Properties

All messages have the following properties in Nitrogen:

* type: The type of this message.  Messages of a given type conform to a particular schema unless they are prefixed with a underscore (eg. "_custom"). This enables principals in the Nitrogen system to communicate with each other using a common vocabulary of messages within having to know intimate details of each other. Incoming messages are checked for conformance to the schema at creation time.
* ver: The version of the schema that this message is using.
* ts: A timestamp that expresses when this message took/will take place.  If not assigned, will default to the timestamp when message is received by the service.
* expires: When this message expires.  If not assigned, will default to the default message lifetime that the service has configured.
* from: The id of the principal this message is from.
* to: The id of the principal this message is to (if any).
* response_to: Array of messages this message is in response to.
* link: If this message references external resources, this link will be applied to those resources for cross referencing. Currently used for referencing a blob resource.
* body: The body of the message.  If the schema is well known, the body should follow the schema as defined below.

Message types are divided into two main classes: data and commands.  

## Data Messages

Data messages carry information, typically the output of a device's operation.  For example, a message typed 'image' contains an image url in its body in its 'url' property.

## Command Messages

The second class of messages are commands. Command messages are sent from one principal to another to request an operation on the receiving principal.  For example, a message of the type 'cameraCommand' contains a command that directs the operation of a camera principal.