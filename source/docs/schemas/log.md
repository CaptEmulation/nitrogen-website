# log

log messages relay logs from a principal to the service.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

* severity (string, required): The severity of this log entry. Must be one of:
    * info
    * warn
    * error
    * debug
* message (string, required): The message to be conveyed in this log entry.