class Session
-------------
**Methods**

Session.stop()
--------------
Stop the session with the service.



Session.clearCredentials(principal)
-----------------------------------
Clear all of the credentials for a particular principal.



**Parameters**

**principal**:  *Object*,  The principal to clear credentials for.

Session.connectSocket(principal, accessToken)
---------------------------------------------
Connect subscription socket for principal with this accessToken to the service.



**Parameters**

**principal**:  *Object*,  The principal to open a subscription socket for.

**accessToken**:  *Object*,  The accessToken to open a subscription socket for.

Session.disconnectSubscription()
--------------------------------
Disconnect the current subscription connection with the service.



Session.disconnectSubscription()
--------------------------------
Connect a subscription with the service.



Session.restartSubscriptions()
------------------------------
Restart all subscriptions with the service.  Used after a connection disruption.



Session.impersonate(principal, callback, callback.err, callback.session, callback.principal)
--------------------------------------------------------------------------------------------
Impersonate the principal with the authorization context of this session.  Used by the Nitrogen service to impersonate principals for agent setup.



**Parameters**

**principal**:  *Object*,  The principal to impersonate with this session.

**callback**:  *Object*,  Callback for the impersonation.

**callback.err**:  *Object*,  If the impersonation failed, this will contain the error.

**callback.session**:  *Object*,  The session for the impersonated principal with this service.

**callback.principal**:  *Object*,  The impersonated principal.

Session.onAuthFailure(principal, callback, callback.err, callback.session, callback.principal)
----------------------------------------------------------------------------------------------
Provide a callback function on authentication failure.



**Parameters**

**principal**:  *Object*,  The principal to impersonate with this session.

**callback**:  *Object*,  Callback for the authentication failure.

**callback.err**:  *Object*,  If the impersonation failed, this will contain the error.

**callback.session**:  *Object*,  The session for the impersonated principal with this service.

**callback.principal**:  *Object*,  The impersonated principal.

Session.on(options, options.type, options.filter, callback, callback.object)
----------------------------------------------------------------------------
Core subscription event method. Primarily used to subscribe for changes to principals and new messages.



**Parameters**

**options**:  *Object*,  Options for what this subscription would like to receive.

**options.type**:  *String*,  The type this subscription should receive.  One of 'message' or 'principal'.

**options.filter**:  *Object*,  The filter to apply to the objects returned from this subscription.  For example { from: '51f2735fda5fcca439000001' } will restrict messages received to only those from this particular principal id.

**callback**:  *Object*,  Callback for event.

**callback.object**:  *Object*,  The received event.  Is either a principal or message object depending on the type of the subscription requested.

Session.onMessage(options.filter, callback, callback.message)
-------------------------------------------------------------
Syntax sugar to setup a message subscription.



**Parameters**

**options.filter**:  *Object*,  The filter to apply to the objects returned from this subscription.  For example { from: '51f2735fda5fcca439000001' } will restrict messages received to only those from this particular principal id.

**callback**:  *Object*,  Callback for event.

**callback.message**:  *Object*,  The message received as part of the subscription.

Session.onPrincipal(options.filter, callback, callback.principal)
-----------------------------------------------------------------
Syntax sugar to setup a principal subscription.



**Parameters**

**options.filter**:  *Object*,  The filter to apply to the objects returned from this subscription.  For example { id: '51f2735fda5fcca439000001' } will restrict messages received to only those for this particular principal id.

**callback**:  *Object*,  Callback for event.

**callback.principal**:  *Object*,  The principal received as part of this subscription.

