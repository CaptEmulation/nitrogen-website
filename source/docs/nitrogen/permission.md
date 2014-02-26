class Permission
----------------
**Methods**

Permission.create(session, callback)
------------------------------------
Creates a permission with the Nitrogen service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, permission).

Permission.find(session, query, options, callback)
--------------------------------------------------
Find permissions filtered by the passed query and limited to and sorted by the
passed options.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query using MongoDB query format.

**options**:  *Object*,  Options for the query:  'limit': maximum number of results to be returned. 'sort': The field that the results should be sorted on, 'dir': The direction that the results  should be sorted. 'skip': The number of results that should be skipped before pulling results.

**callback**:  *Function*,  Callback function of the form f(err, permissions).

Permission.remove(session, callback)
------------------------------------
Delete this permission from the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err).

Permission.save(session, callback)
----------------------------------
Save this permission to the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, permission).

