# heartbeat

A heartbeat message relays status about a principal to the service. The principal is in control of sending heartbeat messages for itself to the service. The JavaScript client module automatically does this for clients on a time interval.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

The following properties are used in the body element of a heartbeat message:

* error (boolean, required): Is the device is in an error condition. The optional status field may contain more information.
* status (object, optional): An optional and schema-less status object that contains more information about the current state of the device.