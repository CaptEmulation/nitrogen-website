# claim

<b>claim</b> messages allow a principal to assert that they should have all permissions for an unclaimed principal in the service by providing a secret code to the service that is shown to the user at startup of that device.

A <b>claim</b> message should be sent from the principal that would like to claim the principal.  The Nitrogen service watches for messages of this type with the [claim application](https://github.com/nitrogenjs/service/blob/master/agents/claim.js) and, if the principal does not have an existing admin, allows the principal to claim it.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

The following properties are used in the body element:

* <b>claim_code</b> (string, required): Claim code asserted by the from principal for the principal that it wants to claim.