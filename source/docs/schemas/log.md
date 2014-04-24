# log

<b>log</b> messages relay logs from a principal to the service.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

The following properties are used in the body of the message:

* <b>severity</b> (string, required): The severity of this log entry. Must be one of:
    * info
    * warn
    * error
    * debug
* <b>message</b> (string, required): The message to be conveyed in this log entry.