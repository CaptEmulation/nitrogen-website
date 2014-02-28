---
title: Nitrogen Permissions
---

# Permissions

A permission in Nitrogen describes actions that a set of Principals can or cannot take on another set of Principals.
 
## Properties 

* issued\_to: The principal id that this permission is granted to.  If missing, this permission applies to all principals.

* principal\_for: The principal this permission is for.  For instance, if you were granting subscription access for a lamp to a user, in this scenario the lamp would be the principal_for.  If missing, this permission applies to all principals.

* action: The action that this permission is relevant for.  Valid values include:

    * 'admin': issued\_to is authorized to perform administrative operations on principal_for.
    * 'send': issued\_to is authorized to send messages to principal_for.
    * 'subscribe': issued\_to is authorized to subscribe to messages from principal_for.
    * 'view': issued\_to is authorized to see principal_for in searches.

* authorized: Boolean declaring if matches to this permission authorizes or forbids the action.

* priority: The priority this principal has in relation to other permissions.  Permissions are walked in priority order and the first match is used to determine if the action is authorized.  Lower numbers are higher priority.

* filter: An object that specifies additional filters that should be applied to a relevant object at authorization time.  For example, { type: "ip" } would be used to limit matches with this permission to only messages with the type 'ip'.

* expires: An expiration date for this permission. After this expiration date, the permission will be disregarded and eventually removed from the system.

## Access Control List (ACL)

Permissions within Nitrogen are evaluated in a first-match manner via priority. When a principal requests an action, its list of permissions are pulled and walked from highest to lowest priority. The first matching permission is used to determine if the action is allowed.
