class CommandManager
--------------------
**Methods**

CommandManager.activeCommands()
-------------------------------
Returns the array of commands that are currently active for this manager.  This is typically used to execute them during executeQueue.



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

Commands that have reached this point have been passed the start filter (see the CommandManager.start() method details),
had a "true" result out of the CommandManager.isRelevant and CommandManager.isCommand methods and finally has recieved a "false"
to the CommandManager.obsoletes method.

An example use of this from the Simple Device guide:

SimpleLEDManager.prototype.executeQueue = function(callback) {
var self = this;

// If you don't have a device, throw an error.
if (!this.device) return callback(new Error('no device attached to control manager.'));

var activeCommands = this.activeCommands();
if (activeCommands.length === 0) {
this.session.log.warn('SimpleLEDManager::executeQueue: no active commands to execute.');
return callback();
}

// We will take all of the activeCommand's ids and use pass them to the "response_to".
// This is important for the "obsoletes" method.
var commandIds = [];
activeCommands.forEach(function(activeCommand) {
commandIds.push(activeCommand.id);
});

// Create the status response
var message = new nitrogen.Message({
type: '_myStatusResponse',
tags: nitrogen.CommandManager.commandTag(self.device.id),
body: {
command: {
message: "My status is good"
}
},
response_to: commandIds
});

message.send(_session, function(err, message) {
if (err) return callback(err);

// Let the command manager know we processed this _lightOn message by passing it the _isOn message.
self.process(new nitrogen.Message(message));

// Need to callback if there aren't any issues so commandManager can proceed.
return callback();
});
}



CommandManager.isRelevant(message)
----------------------------------
Return true if this message is relevant to the CommandManager. Should be implemented by subclasses of CommandManager.

This works in concert with the filter passed into the server in the start method. It enables more intricate processing and
filtering than the simple filter. It is also possible that you could just return true on the method if your filter is correct and you
don't want to filter out additional messages. For example:

MyCommandManager.prototype.isRelevant = function(message) {
return (message.body.property === "value I'm looking for");
};



**Parameters**

**message**:  *Object*,  The message to test for relevance.

CommandManager.isCommand(message)
---------------------------------
Return true if this message is a command that this CommandManager can process. Should be implemented by subclasses of CommandManager.

For example:

MyCommandManager.prototype.isCommand = function(message) {
return message.is('_myCommandName');
};



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

For example:

MyCommandManager.prototype.obsoletes = function(downstreamMsg, upstreamMsg) {
if (nitrogen.CommandManager.obsoletes(downstreamMsg, upstreamMsg))
return true;

var value = downstreamMsg.is("_myStatusResponse") &&
downstreamMsg.isResponseTo(upstreamMsg) &&
upstreamMsg.is("_myStatusRequest");

return value;
};



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

The filter specified is passed to the service as both a query and subscription and should specify a bound on the messages you'd like
to receive.  By default, it uses a commandFilter (as defined in commandFilter) which is a tag applied to messages that are "command relevant"
for this device. and is an opt in model for messages that you want to recieve. You can further filter out messages if you like but this can handle
nearly all cases. In the case that you can't specify a perfect filter, you can further filter the message stream by subclassing the
"isRelevant" function.

In the most common case, your implementation of start in your CommandManager subclass should look like this:

MyCommandManager.prototype.start = function(session, callback) {
return nitrogen.CommandManager.prototype.start.call(this, session, null, callback);
};



**Parameters**

**session**:  *Object*,  Session this CommandManager should operate under.

**filter**:  *Object*,  Filter for relevant messages for this CommandManager.  This is usually specified by the CommandManager subclass.

**callback**:  *Object*,  Callback of the form f(err, message).  Called after each new message received.

