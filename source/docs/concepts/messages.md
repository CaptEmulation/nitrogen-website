---
title: Nitrogen Messages
---

# Messages

Messages are the core construct of the Nitrogen framework. Nearly everything in Nitrogen use messages to communicate with each other. The Nitrogen service at its core essentially applies a visibility model based, permissioning scheme, and real time and queued subscription model around messages.

## Properties

All messages have the following properties in Nitrogen:

* type: Messages of a given type conform to a particular schema unless they are prefixed with a underscore (eg. "_custom"). This enables principals in the Nitrogen system to communicate with each other using a common vocabulary without having to know intimate details of each other's implementation. Incoming messages are checked for conformance to the schema at creation time.
* ver: The version of the schema that this message is using. Default: 0.1
* ts: A timestamp that expresses when this message took/will take place.  If not assigned, will default to the timestamp when message is created by the service.
* expires: When this message expires. If not provided, will default to the default message lifetime that the service has configured.
* from: The id of the principal this message is from. This will always be the principal that sent the message.
* to: The id of the principal this message is to (if any).
* response_to: Array of messages this message is in response to. This is typically used for messages that are in response to a command message.
* link: If this message references external resources, this link will be applied to those resources for cross referencing. An example of this is an image message that references, through a link, a blob that contains the binary image data.
* body: The body of the message.  If the schema is well known, the body should follow the defined schema.

Message types are divided into two main classes: data and commands. The [message schemas](/docs/schemas/cameraCommand.html) section of the documentation defines the full set of project maintained schemas.

## Data Messages

Data messages carry information, typically the output of a device's operation.  For example, a message of type '[image](/docs/schemas/image.html)' contains an image url in its body in its 'url' property.

## Command Messages

The second class of messages are commands. Command messages are sent from one principal to another to request an operation on the receiving principal.  For example, a '[cameraCommand](/docs/schemas/cameraCommand.html)' message contains a command that directs the operation of a camera principal.