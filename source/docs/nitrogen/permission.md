class Permission
----------------
**Methods**

Permission.create(session, callback, callback.err, callback.permission)
-----------------------------------------------------------------------
Create a permission with the Nitrogen service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback for the create.

**callback.err**:  *Object*,  If the create failed, this will contain the error.

**callback.permission**:  *Object*,  The created permission returned by the service.

Permission.find(session, query, options, options.limit, options.sort, options.dir, options.skip, callback, callback.err, callback.permissions)
----------------------------------------------------------------------------------------------------
Find permissions filtered by the passed query and limited to and sorted by the passed options.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query using MongoDB query format.

**options**:  *Object*,  Options for the query.

**options.limit**:  *Number*,  The maximum number to be returned.

**options.sort**:  *String*,  The field that the results should be sorted on.

**options.dir**:  *Number*,  The direction that the results should be sorted.

**options.skip**:  *Object*,  The number of results that should be skipped before pulling results.

**callback**:  *Object*,  Callback at completion of execution.

**callback.err**:  *Object*,  If the find failed, find will callback with the error.

**callback.permissions**:  *Array*,  The set found with this query.

Permission.remove(session, callback, callback.err)
--------------------------------------------------
Delete this permission from the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback for the creation.

**callback.err**:  *Object*,  If the creation failed, this will contain the error.

Permission.save(session, callback, callback.err, callback.permission)
---------------------------------------------------------------------
Save this permission to the service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback for the save.

**callback.err**:  *Object*,  If the save failed, this will contain the error.

**callback.permission**:  *Object*,  The saved permission returned by the service.

