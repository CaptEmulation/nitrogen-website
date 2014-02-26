class Service
-------------
**Methods**

Service.authenticate(principal, callback, callback.err, callback.session, callback.principal)
---------------------------------------------------------------------------------------------
Authenticate this principal with the Nitrogen service.  The mechanism used to authenticate depends on the type of principal.
For users, an email and password is used, otherwise the secret generated during creation is used.



**Parameters**

**principal**:  *Object*,  The principal to authenticate with this service. The principal should include the email/password for a user principal or the secret for other principal types.

**callback**:  *Object*,  Callback for the authentication.

**callback.err**:  *Object*,  If the authenication of this principal failed, this will contain the error.

**callback.session**:  *Object*,  The session for this principal with this service.

**callback.principal**:  *Object*,  The authenticated principal.

Service.create(principal, callback, callback.err, callback.session, callback.principal)
---------------------------------------------------------------------------------------
Create the principal with this service.



**Parameters**

**principal**:  *Object*,  The principal to create with this service. It should include email/password for user principal types.

**callback**:  *Object*,  Callback for the create.

**callback.err**:  *Object*,  If the creation of this principal failed, this will contain the error.

**callback.session**:  *Object*,  The session for this principal with this service.

**callback.principal**:  *Object*,  The created principal.

Service.resume(principal, callback, callback.err, callback.session, callback.principal)
---------------------------------------------------------------------------------------
Attempts to resume a session for this principal using a saved accessToken.



**Parameters**

**principal**:  *Object*,  The principal to resume the session with this service.

**callback**:  *Object*,  Callback for the resume.

**callback.err**:  *Object*,  If the resumption of this session failed, this will contain the error.

**callback.session**:  *Object*,  The session for this principal with this service.

**callback.principal**:  *Object*,  The principal used to resume the session.

Service.connect(principal, callback, callback.err, callback.session, callback.principal)
----------------------------------------------------------------------------------------
Connect attempts to authenicate the principal with the service. If the principal
isn't provisioned with the service, it automatically creates the principal with the
service.



**Parameters**

**principal**:  *Object*,  The principal to connect with this service.

**callback**:  *Object*,  Callback for the connect.

**callback.err**:  *Object*,  If the authentication or create of this session failed, this will contain the error.

**callback.session**:  *Object*,  The session for this principal with this service.

**callback.principal**:  *Object*,  The principal used to connect the session.

Service.authenticateSession(principal, authOperation, callback, callback.err, callback.session, callback.principal)
----------------------------------------------------------------------------------------------------
Internal method to run all the common steps of authentication against a Nitrogen service.



**Parameters**

**principal**:  *Object*,  The principal to connect with this service.

**authOperation**:  *Object*,  The authorization method on the principal that is used to .

**callback**:  *Object*,  Callback for the connect.

**callback.err**:  *Object*,  If the authentication operation failed, this will contain the error.

**callback.session**:  *Object*,  The session for this principal with this service.

**callback.principal**:  *Object*,  The principal used to connect the session.

Service.impersonate(session, principal, callback, callback.err, callback.session, callback.principal)
----------------------------------------------------------------------------------------------------
Impersonate a principal using the passed session



**Parameters**

**session**:  *Object*,  The session to use to authorize this impersonation

**principal**:  *Object*,  The principal to impersonate with this service.

**callback**:  *Object*,  Callback for the impersonation.

**callback.err**:  *Object*,  If the impersonation failed, this will contain the error.

**callback.session**:  *Object*,  The session for the impersonated principal with this service.

**callback.principal**:  *Object*,  The impersonated principal.

Service.configure(config, principal, callback, callback.err, callback.config)
-----------------------------------------------------------------------------
Fetch the endpoint configuration for this service for this user. Before authenticating a principal, we first
ask the service to return the set of endpoints that we should for this principal to talk to the Nitrogen service.  Note,
this might actually not be the same service, as Nitrogen may redirect clients to a different service or different endpoints.



**Parameters**

**config**:  *Object*,  The default configuration to use to connect to Nitrogen.

**principal**:  *Object*,  The principal to configure for this service.

**callback**:  *Object*,  Callback for the impersonation.

**callback.err**:  *Object*,  If the impersonation failed, this will contain the error.

**callback.config**:  *Object*,  The configuration for this service with this principal.

Service.clearCredentials(principal)
-----------------------------------
Clear all of the credentials for a particular principal.



**Parameters**

**principal**:  *Object*,  The principal to clear credentials for.

