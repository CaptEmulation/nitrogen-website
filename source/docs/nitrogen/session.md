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

Session.connectSocket()
-----------------------
Connect subscription socket for principal with this accessToken to the service.



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

Session.onAuthFailure(principal, callback)
------------------------------------------
Provide a callback function on authentication failure.



**Parameters**

**principal**:  *Object*,  The principal to impersonate with this session.

**callback**:  *Function*,  Callback function with signature f(err).

Session.on(options, callback)
-----------------------------
Core subscription event method. Primarily used to subscribe for changes to principals and new messages.



**Parameters**

**options**:  *Object*,  Options for the filter of the messages this subscription should receive: 'type': The type this subscription should receive.  Only 'message' is currently supported. 'filter': The filter to apply to the objects returned from this subscription.  For example { from: '51f2735fda5fcca439000001' } will restrict messages received to only those from this particular principal id.

**callback**:  *Function*,  Callback function with signature f(objectReceived).

Session.onMessage(filter, callback)
-----------------------------------
Syntax sugar to setup a message subscription.



**Parameters**

**filter**:  *Object*,  The filter to apply to the objects returned from this subscription.  For example { from: '51f2735fda5fcca439000001' } will restrict messages received to only those from this particular principal id.

**callback**:  *Function*,  Callback function with signature f(messageReceived).

