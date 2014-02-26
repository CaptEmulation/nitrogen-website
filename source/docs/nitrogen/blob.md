class Blob
----------
**Methods**

Blob.fromFile(path, callback, callback.err, callback.blob)
----------------------------------------------------------
This method loads the metadata for a blob from a file: its timestamp, content type, and content length.



**Parameters**

**path**:  *String*,  The path to load this blob from.

**callback**:  *Object*,  Callback with the blob.

**callback.err**:  *Object*,  If the load of the blob fails, this contains the error.

**callback.blob**:  *Object*,  The blob metadata from the passed file.

Blob.fromFile(session, stream, callback, callback.err, callback.blob)
---------------------------------------------------------------------
Saves the blob stream with the Nitrogen service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**stream**:  *Object*,  A stream with the contents of the blob.

**callback**:  *Object*,  


**callback.err**:  *Object*,  If the load of the blob fails, this contains the error.

**callback.blob**:  *Object*,  The updated blob metadata.

Blob.fromFile(session, url, callback, callback.err, callback.resp, callback.blobData)
-------------------------------------------------------------------------------------
Fetches a blob from the Nitrogen service.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**url**:  *Object*,  The url for the blob.

**callback**:  *Object*,  


**callback.err**:  *Object*,  If the load of the blob fails, this contains the error.

**callback.resp**:  *Object*,  The response object from the request.

**callback.blobData**:  *Object*,  The blob's data.

