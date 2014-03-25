---
title: Nitrogen Permissions
---

# Permissions

A permission in Nitrogen describes actions that principal(s) can or cannot take on principal(s).
 
## Properties 

* issued\_to: The principal id that this permission is granted to. If missing, this permission applies to all principals.

* principal\_for: The principal this permission is for. For instance, if you were granting subscription access for a lamp to a user, the lamp would be the principal_for. If missing, this permission applies to all principals.

* action: The action that this permission is relevant for. Valid values include:

    * (empty): issued\_to is authorized to perform all actions on principal_for
    * 'admin': issued\_to is authorized to perform administrative operations on principal_for.
    * 'send': issued\_to is authorized to send messages to principal_for.
    * 'subscribe': issued\_to is authorized to subscribe to messages from principal_for.
    * 'view': issued\_to is authorized to see principal_for in searches.

* authorized: Boolean declaring if matches to this permission authorizes or forbids the action. Default: true

* priority: The priority this principal has in relation to other permissions.

* filter: An object that specifies additional filters that should be applied to a relevant object at authorization time.  For example, { type: "ip" } would be used to limit matches with this permission to only messages with the type 'ip'.

* expires: An expiration date for this permission. After this expiration date, the permission will be disregarded and removed from the system.

## Evaluation Order

Active permissions for a principal are examined in priority order and the first match is used to determine if the action is authorized. Lower numbers are higher priority.