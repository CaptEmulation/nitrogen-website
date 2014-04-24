# heartbeat

A <b>heartbeat</b> message relays status about a principal to the service. The Nitrogen clicent manages these messages and their frequency.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

The following properties are used in the body element of a heartbeat message:

* <b>error</b> (boolean, required): True if the device is in an error condition. The optional status field may contain more information.
* <b>status</b> (object, optional): An optional and schema-less status object that contains more information about the current state of the device. This status is fetched from the principal by calling it's method of the same name.