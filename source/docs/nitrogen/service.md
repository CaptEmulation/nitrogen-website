class Service
-------------
**Methods**

Service.authenticate(principal, callback)
-----------------------------------------
Authenticate this principal with the Nitrogen service.  The mechanism used to authenticate
depends on the type of principal. For users, an email and password is used. For other principals
public key encryption is verify a signed nonce value for authentication.



**Parameters**

**principal**:  *Object*,  The principal to authenticate with this service. The principal should include the email/password for a user principal or the private_key for other principal types.

**callback**:  *Function*,  Callback function with signature f(err, session, principal).

Service.create(principal, callback)
-----------------------------------
Creates the principal with this service.



**Parameters**

**principal**:  *Object*,  The principal to create with this service. It should include email/password for user principal types.

**callback**:  *Function*,  Callback function with signature f(err, session, principal).

Service.resume(principal, callback)
-----------------------------------
Attempts to resume a session for this principal using a saved accessToken.



**Parameters**

**principal**:  *Object*,  The principal to resume the session with this service.

**callback**:  *Function*,  Callback function with signature f(err, session, principal).

Service.connect(principal, callback)
------------------------------------
Connect attempts to authenicate the principal with the service. If the principal
isn't provisioned with the service, it automatically creates the principal with the
service.



**Parameters**

**principal**:  *Object*,  The principal to connect with this service.

**callback**:  *Function*,  Callback function with signature f(err, session, principal).

Service.authenticateSession(principal, authOperation, callback)
---------------------------------------------------------------
Internal method to run all the common steps of authentication against a Nitrogen service.



**Parameters**

**principal**:  *Object*,  The principal to connect with this service.

**authOperation**:  *Object*,  The authorization method on the principal that is used to .

**callback**:  *Function*,  Callback function with signature f(err, session, principal).

Service.impersonate(session, principal, callback)
-------------------------------------------------
Impersonate a principal using the passed session



**Parameters**

**session**:  *Object*,  The session to use to authorize this impersonation

**principal**:  *Object*,  The principal to impersonate with this service.

**callback**:  *Function*,  Callback function with signature f(err, session, principal).

Service.configure(config, principal, callback)
----------------------------------------------
Fetch the endpoint configuration for this service for this user. Before authenticating a principal, we first
ask the service to return the set of endpoints that we should for this principal to talk to the Nitrogen service.  Note,
this might actually not be the same service, as Nitrogen may redirect clients to a different service or different endpoints.



**Parameters**

**config**:  *Object*,  The default configuration to use to connect to Nitrogen.

**principal**:  *Object*,  The principal to use configure this service.

**callback**:  *Function*,  Callback function with signature f(err, configuration).

Service.clearCredentials(principal)
-----------------------------------
Clear all of the credentials for a particular principal.



**Parameters**

**principal**:  *Object*,  The principal to clear credentials for.

