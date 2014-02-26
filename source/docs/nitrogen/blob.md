class Blob
----------
**Methods**

Blob.fromFile(path, callback)
-----------------------------
Loads the metadata for a blob from a file: its timestamp, content type, and content length.



**Parameters**

**path**:  *String*,  The path to load this blob from.

**callback**:  *Function*,  Callback function of the form f(err, blob).

Blob.save(session, stream, callback)
------------------------------------
Saves the blob to the Nitrogen service.



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

