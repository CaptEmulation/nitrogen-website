class Message
-------------
**Methods**

Message.find(session, query, options, callback)
-----------------------------------------------
Find messages filtered by the passed query and limited to and sorted by the passed options.



**Parameters**

**session**:  *Object*,  The session with a Nitrogen service to make this request under.

**query**:  *Object*,  A query filter for the messages you want to find defined using MongoDB query format. This query must include an indexed field on the Nitrogen service for this session or the request will be rejected by the service.

**options**:  *Object*,  Options for the query:  'limit': maximum number of results to be returned. 'sort': The field that the results should be sorted on, 'dir': The direction that the results  should be sorted. 'skip': The number of results that should be skipped before pulling results.

**callback**:  *Function*,  Callback function of the form f(err, messages).

Message.is(type)
----------------
Returns true if the message is of the passed type.



**Parameters**

**type**:  *String*,  Message type to compare against.

**Returns**

*Boolean*,  Returns true if the message is of the passed type.

Message.isFrom(principalId)
---------------------------
Returns true if the message is from the passed principal.



**Parameters**

**principalId**:  *String*,  Principal id to compare against.

**Returns**

*Boolean*,  Returns true if the message is from the passed principal id.

Message.isResponseTo(type)
--------------------------
Returns true if the message is in response to the passed message.



**Parameters**

**type**:  *String*,  Message to compare against.

**Returns**

*Boolean*,  Returns true if the message is in response to the passed message.

Message.isTo(principalId)
-------------------------
Returns true if the message is of the passed type.



**Parameters**

**principalId**:  *String*,  Principal id to compare against.

**Returns**

*Boolean*,  Returns true if the message is of the passed type.

Message.remove(session, query, callback)
----------------------------------------
Removes a set of messages specified by passed filter. Used by the internal service principal to
to cleanup expired messages etc.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query filter for the messages you want to remove.

**callback**:  *Function*,  Callback function of the form f(err, removedCount).

Message.remove(session, callback)
---------------------------------
Remove this message. Used by the internal service principal for cleanup.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, removedCount).

Message.send(session, callback)
-------------------------------
Send this message.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Function*,  Callback function of the form f(err, sentMessages).

Message.sendMany(session, messages, callback)
---------------------------------------------
Send multiple messages.



**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**messages**:  *Array*,  An array of messages to send.

**callback**:  *Function*,  Callback function of the form f(err, sentMessages).

Message.expired()
-----------------
Returns true if the message expired.



**Returns**

*Boolean*,  Returns true if the message is expired.

Message.millisToExpiration()
----------------------------
Returns the number of milliseconds before this message expires.



**Returns**

*Number*,  Number of milliseconds before this message expires.

Message.millisToTimestamp()
---------------------------
Returns the number of milliseconds before the timestamp for this message.  Used to calculate
time to execution for command messages.



**Returns**

*Number*,  Number of milliseconds before the timestamp for this message.

