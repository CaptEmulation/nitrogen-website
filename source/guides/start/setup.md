---
title: First Steps with Nitrogen
---

## First Steps

This guide will walk you through everything you need to do to get up and running your first Nitrogen device. We'll start with a device that almost everyone has: Let's turn your laptop's camera into an internet controllable camera.

### Installation

Nitrogen uses node.js extensively. If you don't already have node.js installed, install it from [http://nodejs.org](http://nodejs.org).

<b>WINDOWS USERS</b>: You also need to install [these prerequisites](/guides/start/windows.html) if you haven't already.

Then use npm to install Nitrogen's command line tool:

`> npm install -g nitrogen-cli`

nitrogen-cli is no fun to type, so the command line tool uses the alias `n2`.  Let's make sure it all is installed correctly:

`> n2 help`

This will display the top level set of commands that are available from the command line.

### Checking the service

Before we create a user, let's make sure that we are connected to the correct server with the command line tool. 

`> n2 service show` 

This will show you which service you are connected to currently. By default this is "host: api.nitrogen.io". If you want to change it, use the n2 command to 'set' individual properties or 'use' a seperate service profile all together.

`> n2 service help` for more details 

### Account Creation

Now, let's create a user account with the hosted Nitrogen service:

`> n2 user create`

This will create an account for you and store away your credentials with the command line tool. Let's run one more command just to make sure it is all up and working correctly by asking for all of the security principals you have view access to from your account:

`> n2 principal ls`

A [security principal in Nitrogen](/docs/concepts/principals.html) is an entity that authenticates with the service and has a set of permissions associated with it. A principal could be a device, user, application, or even the service itself.

You will likely see just one principal at this point, the user you just created, since you haven't added any devices to the service. Let's [create our first device](camera.html).