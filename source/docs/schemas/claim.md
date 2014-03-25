# claim

Claim messages are the mechanism for a principal to assert that they should have all permissions for an unclaimed principal in the service by providing a secret code to the service.

A claim message should be sent from the principal that would like to claim the principal.  The Nitrogen service watches for messages of this type with the [claim application](https://github.com/nitrogenjs/service/blob/master/agents/claim.js) and, if the principal does not have an existing admin, allows the principal to claim it.

## Implementation

This message schema is built into the Nitrogen service.

## Properties

The following properties are used in the body element of a claim message:

* claim_code (string, required): String that contains the claim code for the principal.