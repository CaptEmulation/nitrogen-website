class CommandManager
--------------------
**Methods**

CommandManager.activeCommands()
-------------------------------
Returns the array of commands that are currently active for this manager.



**Returns**

*Array of Messages*,  Array of active command messages.

CommandManager.collapse()
-------------------------
Reduce the current message queue to the set of active commands by obsoleting completed and
expired commands.



CommandManager.execute()
------------------------
Executes the currently active command queue.  If the next command's timestamp occurs in the future,
setup a timeout to retry then.



CommandManager.executeQueue()
-----------------------------
Executes the active commands in the message queue. Should be implemented by subclasses of CommandManager.



CommandManager.isRelevant(message)
----------------------------------
Return true if this message is relevant to the CommandManager. Should be implemented by subclasses of CommandManager.



**Parameters**

**message**:  *Object*,  The message to test for relevance.

CommandManager.isCommand(message)
---------------------------------
Return true if this message is a command that this CommandManager can process. Should be implemented by subclasses of CommandManager.



**Parameters**

**message**:  *Object*,  The message to test to see if it is a relevant command.

CommandManager.lastActiveCommand()
----------------------------------
Return the last active command in the message queue as ordered by timestamp.



CommandManager.obsoletes(downstreamMsg, upstreamMsg)
----------------------------------------------------
Returns true if the given message upstream in time of the given downstream message is obsoleted by
the downstream message. Should be overridden by subclasses to provide command type specific
obsoletion logic.  Overrides should start their implementation by calling this function for base
functionality.



**Parameters**

**downstreamMsg**:  *Object*,  The downstream message that potentially obsoletes the upstream message.

**upstreamMsg**:  *Object*,  The upstream message that is potentially obsoleted by the downstream message.

CommandManager.process(message)
-------------------------------
Process new message in this principal's message stream:  adds it to the messageQueue, collapses the
current message stream, and sets up timeout to handle expiration of this message and the subsequent
collapse that should occur.



**Parameters**

**message**:  *Object*,  The new message to process.

CommandManager.start(session, filter, callback)
-----------------------------------------------
Starts command processing on the message stream using the principal's session. It fetches all the
current messages, processes them, and then starts execution. It also establishes a subscription to
handle new messages and automatically executes them as they are received.



**Parameters**

**session**:  *Object*,  Session this CommandManager should operate under.

**filter**:  *Object*,  Filter for relevant messages for this CommandManager.  This is usually specified by the CommandManager subclass.

**callback**:  *Object*,  Callback of the form f(err, message).  Called after each new message received.

