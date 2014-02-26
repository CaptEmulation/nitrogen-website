Message(session, query, options, options.limit, options.sort, options.dir, options.skip, callback, callback.err, callback.messages, type, principal, type, principal, session, query, callback, callback.err, callback.removed, session, callback, callback.err, callback.removed, session, callback, callback.err, callback.message, session, messages, callback, callback.err, callback.messages)
----------------------------------------------------------------------------------------------------
{
class: "Message",
namespace: "nitrogen",
description: "The Message object is the core of the Nitrogen framework.  Applications, devices, and
services use Messages to communicate with and issue commands to each other. All messages that don't
begin with an unscore are checked against a schema chosen by the messages 'type' and 'schema_version'
fields such that a message of a given type is known to conform to a particular structure.   This enables
sharing between differing devices and applications.  For custom message types, an application
may use an unscore prefix (eg. '_myMessage') with any schema that they'd like.  This supports communication
between principals of the same organization over a private schema.  That said, it is strongly encouraged
to use standard schemas wherever possible.

Messages have a sender principal (referred to as 'from') and a receiver principal (referred to as
'to'). These fields are used to route messages to their receiver.

Message types are divided into two main classes: data and commands.  Data messages carry information,
typically the output of a device's operation.  For example, a message typed 'image' contains an image
url in its body in its 'url' property.

The second class of messages are commands. Command messages are sent from one principal to another to
request an operation on the receiving principal.  For example, a message of the type 'cameraCommand' contains
a command that directs the operation of a camera principal."
}


**Parameters**

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query filter for the messages you want to find defined using MongoDB query format.

**options**:  *Object*,  Options for the query.

**options.limit**:  *Number*,  The maximum number of results to be returned.

**options.sort**:  *String*,  The field that the results should be sorted on.

**options.dir**:  *Number*,  The direction that the results should be sorted.

**options.skip**:  *Object*,  The number of results that should be skipped before pulling results.

**callback**:  *Object*,  Callback for the find's execution

**callback.err**:  *Object*,  If the find failed, find will callback with the error.

**callback.messages**:  *Array*,  The set of messages found with this query.

**type**:  *String*,  Message type to compare against.

**principal**:  *String*,  Principal to compare against.

**type**:  *String*,  Message to compare against.

**principal**:  *String*,  Principal to compare against.

**session**:  *Object*,  An open session with a Nitrogen service.

**query**:  *Object*,  A query filter for the messages you want to remove.

**callback**:  *Object*,  Callback to receive the results of the remove operation

**callback.err**:  *Object*,  If the operation failed, the error that caused failure, else undefined.

**callback.removed**:  *Object*,  The count of messages removed with this operation.

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback to receive the results of the remove operation

**callback.err**:  *Object*,  If the operation failed, the error that caused failure, else undefined.

**callback.removed**:  *Object*,  The count of messages removed with this operation.

**session**:  *Object*,  An open session with a Nitrogen service.

**callback**:  *Object*,  Callback at completion of operation

**callback.err**:  *Object*,  If the operation failed, the error that caused failure, else null.

**callback.message**:  *Object*,  If successful, the sent message.

**session**:  *Object*,  An open session with a Nitrogen service.

**messages**:  *Array*,  An array of messages to send.

**callback**:  *Object*,  Callback at completion of operation

**callback.err**:  *Object*,  If the operation failed, the error that caused failure, else null.

**callback.messages**:  *Object*,  If successful, the array of sent message.

