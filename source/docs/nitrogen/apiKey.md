class ApiKey
------------
**Methods**

ApiKey.index(session, query, options, callback)
-----------------------------------------------
Find all the api_keys for the authenticated user.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service. Only user principals will return results.

**query**:  *Object*,  A query filter for the apiKeys defined using MongoDB's query format.  (reserved: currently ignored)

**options**:  *Object*,  Options for the query (reserved, currently ignored):  'limit': maximum number of results to be returned. 'sort': The field that the results should be sorted on, 'dir': The direction that the results  should be sorted. 'skip': The number of results that should be skipped before pulling results.

**callback**:  *Function*,  Callback function of the form f(err, permissions).

