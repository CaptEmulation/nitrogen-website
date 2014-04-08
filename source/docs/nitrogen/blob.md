class Blob
----------
**Methods**

Blob.save(session, stream, callback)
------------------------------------
Saves a blob via streaming to the Nitrogen service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**stream**:  *Object*,  A stream with the contents of the blob.

**callback**:  *Function*,  Callback function of the form f(err, blob).

Blob.get(session, url, callback)
--------------------------------
Fetches a blob from the Nitrogen service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**url**:  *Object*,  The url for the blob.

**callback**:  *Function*,  Callback function of the form f(err, httpResponse, blobData).

