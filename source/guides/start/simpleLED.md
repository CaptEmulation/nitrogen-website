---
title: Writing your first device
---

## Writing your first device

Now that you've [setup Nitrogen](/guides/start/setup.html), it's time to start writing some code. We're going to work against the public gateway but with just a configuration change, you can run the same device against your own instance of Nitrogen.

This "device" is a node.js application that can run anywhere that node.js can run. For this exercise we'll be running it from the command line but you can run this same code on an Arduino Yun or a Raspberry Pi.

For simplicity sake, we're going to write this all in one JavaScript file with a package.json that pulls in all of our dependencies. When your devices get more sophisticated, it will make sense to split them up into separate files and possibly even separate NPM packages.

First, create a folder called simpleLED:

`> mkdir simpleLED`

Change to that directory:

`> cd simpleLED`

### Setting up the NPM packages

There are 2 NPM packages that we need. The first is the LevelDB based Nitrogen store. This is the library that handles storing your credentials and remembering who this device is for the next time that you connect to the service. The second is the Nitrogen client library that we'll use to interact with the Nitrogen service.

We'll install these via NPM. To do this, we'll need a package.json.

Create a new file in your favorite text editor and save it in this new folder under the file name `package.json`.

Fill out the package.json as follows.

```
{
  "name": "simpleLED",
  "repository": {
    "type": "git",
    "url": ""
  },
  "version": "0.1.0",
  "private": "true",
  "dependencies": {
    "nitrogen": "~0.2.0",
    "nitrogen-leveldb-store": "~0.1.201"
  },
  "devDependencies": {
    "mocha": "1.x"
  }
}
```

Now that your package.json is in place, we can install the packages with the following command from your terminal or command prompt.

`> npm install`

This will create a folder called node_modules and download the required npm libraries into it. If you're not familiar with node.js, this is how you install dependencies. Spend some time looking through this folder and seeing what it downloaded.

### Writing the device.

Now we're ready to write some code. Create a file in your favorite text editor and save it as simpleLED.js.

First let's 'require' all of the modules we are going to use. This is the equivalent of includes or references in many other programming languages.

```
var Store = require('nitrogen-leveldb-store'),
    nitrogen = require('nitrogen');
```

The next bit here is your configuration. Once you start writing real devices, it's highly recommended that you split this out into a separately maintained file so that you can keep it more private. We'll show how to do this in future walkthroughs but we wanted to get the simplest version out possible first.

To get your api_key which you'll need below, go back to the terminal and use the following command.

`> n2 apikeys ls`

The result should look as follows where the Xs are replaced with your apikey and your principal id.

```
> n2 apikeys ls
service: configured.
KEY                               NAME           OWNER
XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX  User           XXXXXXXXXXXXXXXXXXXXX
```

Alternatively you can log into the web admin and see your apikey listed on the API Keys tab.

Now fill in the configuration section of your app as follows.

```
var config = {
    host: process.env.HOST_NAME || 'api.nitrogen.io',
    http_port: process.env.PORT || 443,
    protocol: process.env.PROTOCOL || 'https',
    api_key: "XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX"
};

config.store = new Store(config);
```

Now that we have things configured, it's time to create the device with a few parameters to the constructor:

```
var simpleLED = new nitrogen.Device({
    nickname: 'simpleLED',
    name: 'My LED',
    tags: ['sends:_isOn', 'executes:_lightOn'],
    api_key: config.api_key
});

```
The tags that we're sending in are important in that they tell the Nitrogen server that this device sends an _isOn message and receives/executes _lightOn messages. The "_" is important in that there are some predefined commands in Nitrogen that tell Nitrogen to act on the message in a certain way. An example of that is the cameraCommand message which we'll see in one of the following guides that the CameraManager module knows how to interpret to control an attached camera. However, if you don't want Nitrogen to verify the schema of the message you can just pass it pass it through as a custom message, and "_" is the convention to do so.

Now it's time to connect to the service with your device.

```
var service = new nitrogen.Service(config);

service.connect(simpleLED, function(err, session, simpleLED) {
    if (err) return console.log('failed to connect simpleLED: ' + err);
});
```

And with that, you have a nitrogen device connect to the service. However, this is not an interesting device as it doesn't send any telemetry and doesn't receive any commands.

What we'll do is send a message as soon as the device connects to the service to let the world know that we're here and we're on.

Alter the service.connect call as follows.

```
service.connect(simpleLED, function(err, session, simpleLED) {
    if (err) return console.log('failed to connect simpleLED: ' + err);

    var message = new nitrogen.Message({
        type: '_isOn',
        body: {
            command: {
                message: "Light (" + simpleLED.id + ") is On at " + Date.now()
            }
        }
    });

    message.send(session);
});
```

That's all there is to a telemetry only device.

### Running the device for the first time.

Let's run it and see if you see your messages show up.

From the terminal or node.js command prompt, use run your app as follows.

`> node simpleLED.js`

It should look similar to this with your current date time and your device's principal id.

```
> node simpleLED.js
10/2/2014 22:05:28: XXXXXXXXXXXXXXXXXXXXXXXX: debug: session: created.
```

Hit `control-c` to kill that process.

Now look to see if the message went through.

`> n2 message ls`

You should see a list of your recent messages. That might include some log messages and the like but it will also include your _isOn message.

And as simple as that you've connected to Nitrogen and started sending data. But there's a little magic that needs to be explained first. Remember that we included the nitrogen-leveldb-store at the top. On the first connection, Nitrogen looks to see if there's any credentials for this device.  If not, it passes in the apikey and creates a public/private key pairing that the device will use to identify itself in the future. This key can also be pre-shared and flashed into the firmware of a physical device in the factory. But at the moment we're using the ssh style handshake that asks for the key, gets it and stores it.

If you take a look at the directory that your code is in, there's a new folder called <hostname>_<portname> or in our case `api.nitrogen.io_443`. Look in this folder and take a look at the files in there. The CURRENT points to the current manifest file. The MANIFEST-XXXXXX file contains your newly minted credentials.

At this point you have a device that is authenticated and send telemetry data up to Nitrogen's public gateway.

### Receiving commands.

The next thing to do is to start receiving commands from the server. The way that Nitrogen does this is with a CommandManager. This is slightly more complicated that the device but not tremendously. It's a prototyped object based on the nitrogen.CommandManager.prototype.

Let's create that first. Between where you created your device and where you called the service.connect, add the following code.

```
function SimpleLEDManager() {
    nitrogen.CommandManager.apply(this, arguments);
}

SimpleLEDManager.prototype = Object.create(nitrogen.CommandManager.prototype);
SimpleLEDManager.prototype.constructor = SimpleLEDManager;
```

At this point you have a CommandManager but it's not very useful.

The next step is to override a few methods from the base prototype that will help you process your messages.

The first is "isRelevant". This gets messages in and allows you to, on the client, do fairly complex filtering on the list of messages as to which ones are interesting to your device. There's a simple filter that we'll look at in a moment that opts your device into certain messages on the server side.

```
SimpleLEDManager.prototype.isRelevant = function(message) {
    var relevant = ( (message.is('_lightOn') || message.is('_isOn')) &&
                     (!this.device || message.from === this.device.id || message.to == this.device.id));

    return relevant;
};
```

The next one is to see if it's actually a command that you're going to execute on. It could be a log message or a command that you don't actually know how to execute.

```
SimpleLEDManager.prototype.isCommand = function(message) {
    return message.is('_lightOn');
};
```

The next method is a little trickier. Messages that you have already processed or are no longer interesting to you, such as something that expired, can be filtered out in the "obsoletes" method. It's important to do this correctly or you will keep getting the same queue of messages over and over.

If you return true, the upstreamMsg will be expired. If you return false, it will be added to the queue to get executed next. You always want to make sure that the base CommandManager has a crack at these first as that will manage things such as expired messages and such for you.

```
SimpleLEDManager.prototype.obsoletes = function(downstreamMsg, upstreamMsg) {
    if (nitrogen.CommandManager.obsoletes(downstreamMsg, upstreamMsg))
        return true;

    var value = downstreamMsg.is("_isOn") &&
                downstreamMsg.isResponseTo(upstreamMsg) &&
                upstreamMsg.is("_lightOn");

    return value;
};
```

Now that we've figured out that it's a message that we're actually interested in and that is still relevant, we'll get a queue of these message that we need to execute look through and execute commands based on. In our case, we're just going to send a message back to the server stating that the message was received and that the light is either in the on or off state now. It's an exercise to the reader to get it to actually turn on and off a light on your platform but there are lots of tutorials for those type of exercises.

```
SimpleLEDManager.prototype.executeQueue = function(callback) {
    var self = this;

    if (!this.device) return callback(new Error('no device attached to control manager.'));

    // This looks at the list of active commands and returns if there's no commands to process.
    var activeCommands = this.activeCommands();
    if (activeCommands.length === 0) {
        this.session.log.warn('SimpleLEDManager::executeQueue: no active commands to execute.');
        return callback();
    }

    var lightOn;
    var commandIds = [];

    // Here we are going to find the final state and but collect all the active command ids because we'll use them in a moment.
    activeCommands.forEach(function(activeCommand) {
        lightOn = activeCommand.body.value;
        commandIds.push(activeCommand.id);
    });

    // This is the response to the _lightOn command.
    // Notice the response_to is the array of command ids from above. This is used in the obsoletes method above as well.
    var message = new nitrogen.Message({
        type: '_isOn',
        tags: nitrogen.CommandManager.commandTag(self.device.id),
        body: {
            command: {
                message: "Light (" + simpleLED.id + ") is " + JSON.stringify(lightOn) + " at " + Date.now()
            }
        },
        response_to: commandIds
    });

    message.send(this.session, function(err, message) {
        if (err) return callback(err);

        // let the command manager know we processed this _lightOn message by passing it the _isOn message.
        self.process(new nitrogen.Message(message));

        // need to callback if there aren't any issues so commandManager can proceed.
        return callback();
    });
}
```

This filter in this method is very important. It opts you into messages that you care about on the server side. If your filter is not broad enough, your device will never see messages that it wants to see and you'll drive yourself nuts trying to figure out why your isRelevant and isCommand aren't working. Notice below that we're simply using the device.id (wrapped in the commandTag call) as our filter. What this means is that we want to receive anything that is addressed to us that is tagged with this command tag. You could filter it further than that and get only messages of a certain type that are addressed to us. If you remove this filter, you'll get a lot of log messages and other things from this device before they leave the device and go to the server. There are times that's useful but most of the time it's a tremendous amount of noise you don't want to deal with.

```
SimpleLEDManager.prototype.start = function(session, callback) {

    var filter = {
        tags: nitrogen.CommandManager.commandTag(this.device.id)
    };

    return nitrogen.CommandManager.prototype.start.call(this, session, filter, callback);
};
```

The only code left to write is to alter the service.connect to start our new CommandManager so that it can start listening.

```
service.connect(simpleLED, function(err, session, simpleLED) {
    if (err) return console.log('failed to connect simpleLED: ' + err);

    new SimpleLEDManager(simpleLED).start(session, function(err, message) {
        if (err) return session.log.error(JSON.stringify(err));
    });

});
```

And we're done writing your first device that has command and control as well as telemetry data.

### Running the device with command and control

Now if you run your app, you'll see the see that it authenticates does some plumbing and then goes into a ready state.

```
> node simpleLED.js
principal: authenticated.
10/3/2014 15:59:23: XXXXXXXXXXXXXXXXXXXXXXXX: debug: session: created.
10/3/2014 15:59:24: XXXXXXXXXXXXXXXXXXXXXXXX: debug: CommandManager::execute: empty command queue.
10/3/2014 15:59:24: XXXXXXXXXXXXXXXXXXXXXXXX: debug: starting heartbeat interval
10/3/2014 15:59:24: XXXXXXXXXXXXXXXXXXXXXXXX: info: commandManager: started.
10/3/2014 15:59:26: XXXXXXXXXXXXXXXXXXXXXXXX: debug: session: socket.io connected
```

Now switch to separate terminal/node.js command prompt and run this n2 command replacing the X's with your device id, your principal id and your device id respectively.

`n2 message send '{"type": "_lightOn", "tags":["command:XXXXXXXXXXXXXXXXXXXXXXXX"], `
`   "body": {"value": "false"}, "from":"XXXXXXXXXXXXXXXXXXXXXXXX", "to":"XXXXXXXXXXXXXXXXXXXXXXXX"}'`

Now you can either run the `> n2 message ls` command or log into the admin portal and see your new messages being passed back and forth.

With this guide you've built the simplest full round trip device. In a more real scenario, we'd break this up into separate libraries and separate out the configuration. Let us know about any issues or improvements by filing bugs on this and any other part of the documentation in the [website github repository](https://github.com/nitrogenjs/website).
