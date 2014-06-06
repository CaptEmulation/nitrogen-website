# ip

<b>ip</b> messages relay the current ip address for the principal from the service's perspective. The service uses these messages for attemping to match principals with users automatically when possible.

## Implementation

This message schema is included with the Nitrogen service.

## Properties

The following properties are used in the body element:

* <b>ip_address</b> (string, required): IPv4 or IPv6 ip address in conventional string format.