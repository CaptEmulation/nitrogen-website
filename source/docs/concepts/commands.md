---
title: Nitrogen Commands
---

# Commands

Message schemas in Nitrogen that end in "Command" are used to control the operation of a [principal](./principals.html) in the system. This is usually a hardware device but Nitrogen also uses it internally, for example, starting and stopping applications within a Nitrogen [Reactor](./reactor.html) using [reactorCommands](/docs/schemas/reactorCommand.html)

## CommandManager

Within the Nitrogen client library, the CommandManager class provides the base infrastructure for command processing within Nitrogen. The CommandManager's role is to watch that principal's message stream and make state changes on the device based on these commands and their context in the stream. CommandManagers are subclassed for specific types of command. This subclass is responsible for providing a set of functions that define how the message stream is interpreted and acted on. In particular, it should implement executeActiveCommands, isRelevant, isCommand, and obsoletes. See the [client documentation](/docs/nitrogen/commandManager.html) for more information on what an implementation of this base class should provide.

As an example, a SwitchManager subclass is used to control a light in a device application like this:

```javascript
service.connect(light, function(err, session, light) {
     if (err) return console.log('failed to connect light: ' + err);

     var switchManager = new nitrogen.SwitchManager(light);
     switchManager.start(session, function(err) {
         if (err) return console.log('switchManager failed to start: ' + err);
     });
});
```