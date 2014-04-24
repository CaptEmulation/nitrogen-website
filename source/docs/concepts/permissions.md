---
title: Nitrogen Permissions
---

# Permissions

A permission in Nitrogen describes actions that principal(s) can or cannot take on principal(s). The service uses permissions to determine if a particular action is authorized for a particular security principal.
 
## Properties 

* <b>issued\_to</b>: The principal id that this permission is granted to. If missing, this permission applies to all principals.

* <b>principal\_for</b>: The principal this permission is for. For instance, if you were granting subscription access for a lamp to a user, the lamp would be the principal_for. If missing, this permission applies to all principals.

* <b>action</b>: The action that this permission is relevant for. Valid values include:

    * (empty): issued\_to is authorized to perform all actions on principal_for
    * <b>admin</b>: issued\_to is authorized to perform administrative operations on principal_for.
    * <b>send</b>: issued\_to is authorized to send messages to principal_for.
    * <b>subscribe</b>: issued\_to is authorized to subscribe to messages from principal_for.
    * <b>view</b>: issued\_to is authorized to see principal_for in searches.

* <b>authorized</b>: Boolean declaring if matches to this permission authorize or forbid the action. Default: true

* <b>priority</b>: The priority this principal has in relation to other permissions.

* <b>filter</b>: An object that specifies additional filters that should be applied to a relevant object at authorization time.  For example, { type: "ip" } would be used to limit matches with this permission to only messages with the type 'ip'.

* <b>expires</b>: An expiration date for this permission. After this expiration date, the permission will be disregarded and removed from the system.

## Evaluation Order

Active permissions for a principal are examined in priority order and the first match is used to determine if the action is authorized. Lower numbers are higher priority.