# heartbeat

A heartbeat message relays status about a principal to the service. A principal manages the frequency of heartbeat messages for itself with the service. The Nitrogen client automatically manages this for clients.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

The following properties are used in the body element of a heartbeat message:

* error (boolean, required): True if the device is in an error condition. The optional status field may contain more information.
* status (object, optional): An optional and schema-less status object that contains more information about the current state of the device. This status is fetched from the principal by calling it's method of the same name.