---
title: Nitrogen Commands
---

# Commands

Messages in Nitrogen that are suffixed with "Command" are used to control the operation of a particular Principal in the system. Commands are messages that are issued with the intent of changing the state of a principal in the system.

[TODO: Define Commands]

## CommandManager

Within the client library, the CommandManager class provides infrastructure for command processing within Nitrogen. The CommandManager's role is to watch that principal's message stream and effect state changes on the device it is managing based on these commands and their context in the stream. CommandManagers are subclassed for specific types of command. This subclass is responsible for providing a set of functions that define how the message stream is interpreted and acted on: executeActiveCommands, isRelevant, isCommand, obsoletes. See each function in this class for more information on what an implementation of these functions should provide.
 
An example of how a SwitchManager subclass is used to control a light in a device application looks like this:

```javascript
service.connect(light, function(err, session, light) {
     if (err) return console.log('failed to connect light: ' + err);
 
     var switchManager = new n2.SwitchManager(light);
     switchManager.start(session, { $or: [ { to: light.id }, { from: light.id } ] }, function(err) {
         if (err) return console.log('switchManager failed to start: ' + err);
     });
});
```