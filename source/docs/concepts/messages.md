---
title: Nitrogen Messages
---

# Messages

Messages are the core of the Nitrogen framework. Nearly everything in Nitrogen uses messages for communication with each other, including most of the parts of the core Nitrogen service platform itself. The Nitrogen service at its core is a messaging broker where [permissions](./permissions.html) define what messages a security [principal](./principals.html) can send, receive, and subscribe to.

## Properties

All messages have the following properties in Nitrogen:

* <b>type</b>: Messages of a given type conform to a particular schema unless they are prefixed with a underscore (eg. "_custom"). This enables principals in the Nitrogen system to communicate with each other using a common schema vocabulary without having to know the details of each other's implementation. Incoming messages are checked for conformance to the schema at creation time unless this is explicitly configured in the service.
* <b>ver</b>: The version of the schema that this message is using. Default: 0.2
* <b>ts</b>: A timestamp that expresses the effective time of this message. If not assigned, it defaults to the timestamp when message is created by the service.
* <b>expires</b>: When this message expires. If not provided, will default to the default message lifetime that the service has configured.
* <b>from</b>: The id of the principal this message is from. This will always be the principal that sent the message.
* <b>to</b>: The id of the principal this message is to (if any).
* <b>response_to</b>: Array of messages this message is in response to. This is typically used to mark that a messages in response to a [command](./commands.html) message.
* <b>link</b>: If this message references external resources, this link will be applied to those resources for cross referencing. An example of this is an image message that references, through a link, a blob that contains the binary image data.
* <b>body</b>: The body of the message.  If the schema is not custom, the body should follow the defined schema in 'type'.

Message types are divided into two main classes: data and commands. The [message schemas](/docs/schemas/cameraCommand.html) section of the documentation defines the full set of project maintained schemas.

## Data Messages

Data messages carry information, typically the output of a device's operation.  For example, a message of type '[image](/docs/schemas/image.html)' contains an image url in its body in its 'url' property.

## Command Messages

The second class of messages are commands. Command messages are sent from one principal to another to request an operation on the receiving principal.  For example, a '[cameraCommand](/docs/schemas/cameraCommand.html)' message contains a command that directs the operation of a camera principal.