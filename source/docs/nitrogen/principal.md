class Principal
---------------
**Methods**

Principal.authenticate(config, callback)
----------------------------------------
Authenticate this principal with the service.  The mechanism used to authenticate depends on
the type of principal. For users, an email and password is used.  For all other principals,
public key auth will be used.



**Parameters**

**config**:  *Object*,  The config for the Nitrogen service to auth against.

**callback**:  *Function*,  Callback function of the form f(err, principal, accessToken).

Principal.create(config, callback)
----------------------------------
Create a new principal with the service.  For user principal types, this principal must have a email, password, and
name.



**Parameters**

**config**:  *Object*,  The config data for the Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, principal, accessToken).

Principal.find(session, query, options, callback)
-------------------------------------------------
Find principals filtered by the passed query and limited to and sorted by the passed options.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query filter for the principals defined using MongoDB's query format.

**options**:  *Object*,  Options for the query:  'limit': maximum number of results to be returned. 'sort': The field that the results should be sorted on, 'dir': The direction that the results  should be sorted. 'skip': The number of results that should be skipped before pulling results.

**callback**:  *Function*,  Callback function of the form f(err, principals).

Principal.findById(session, principalId, callback)
--------------------------------------------------
Find a principal by id.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**principalId**:  *String*,  The principal id to search for.

**callback**:  *Function*,  Callback function of the form f(err, principal, accessToken).

Principal.impersonate(session, principalId, callback)
-----------------------------------------------------
Impersonate a principal using another principal's session.  This is used by the service to
impersonate a particular principal for application execution.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**principalId**:  *String*,  The principal id to impersonate.

**callback**:  *Function*,  Callback function of the form f(err, principal, accessToken).

Principal.remove(session, callback)
-----------------------------------
Delete this principal from the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err).

Principal.resume(session, callback)
-----------------------------------
Resume a session using a stored accessToken (attached to this principal).



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, principal, accessToken).

Principal.save(session, callback)
---------------------------------
Save this principal to the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, principal).

Principal.status(callback)
--------------------------
Report the status of this principal.  Principal subclasses should override this method if there
is meaningful status that they can provide.  This status is included in the principal's heartbeat
to the Nitrogen service.

By default this implementation simply makes a no status callback.



**Parameters**

**callback**:  *Function*,  Callback function of the form f(err, status).

