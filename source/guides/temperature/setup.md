---
title: First Steps with Nitrogen
---

## First Steps

This guide will walk you through everything you need to get up and running your first Nitrogen device. We'll start with the simplest possible device, one that only emits telemetry messages: a thermometer.

### Installation

Nitrogen uses node.js for its client SDK. If you don't have node.js already installed, install it from [http://nodejs.org](http://nodejs.org).

<b>WINDOWS USERS</b>: You also need to install [these prerequisites](/guides/thermometer/windows.html) if you haven't already.

Then use npm to install Nitrogen's command line tool:

`> npm install -g nitrogen-cli`

nitrogen-cli is no fun to type, so the command line tool uses the alias `n2` (short for the most common molecule of Nitrogen in our atmosphere).  Let's make sure it all is installed correctly:

`> n2 help`

This will display the top level set of commands that are available from the command line.

### Checking the service

Before we create a user, let's confirm that we are connected to the correct server with the command line tool.

`> n2 service show`

This will show you to which service you are currently connected. By default this is "host: api.nitrogen.io". If you want to change it, use the n2 command to 'set' individual properties or 'use' a separate service profile all together.

`> n2 service help` for more details

We'd recommend that as a starting user that your use the hosted sandbox service to get started.

### Account Creation

Now, let's create a user account with the hosted Nitrogen service:

`> n2 user create`

This will create an account and store away your credentials with the command line tool. Let's run one more command just to make sure it is all up and working correctly by asking for all of the security principals you have view access to from your account:

`> n2 principal ls`

A [security principal in Nitrogen](/docs/concepts/principals.html) is a unit of authenticates with a Nitrogen service and has a set of permissions associated with it. A principal could be a device, user, application, or even the service itself.

You will likely see just one principal at this point, the user you just created, since you haven't added any devices to the service.

Creating devices and other principals in Nitrogen requires an API key to the Nitrogen service you are connecting that device to. You can get your api key using:

`> n2 apikeys ls`

Setting the environmental variable API_KEY is the usual mechanism for passing this API key through to device applications. Do this now before moving on to [create your first Nitrogen device](thermometer.html).