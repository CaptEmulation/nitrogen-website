---
title: First Steps with Nitrogen
---

## First Steps

This guide will walk you through everything you need to do to get setup and running your first Nitrogen device. We'll start with a device that almost everyone has: Let's turn your laptop's camera into an internet controllable camera.

### Installation

Nitrogen uses node.js extensively. If you don't already have node.js installed, install it from [http://nodejs.org](http://nodejs.org). If you are using Windows, please also install the prereqs in the [Running on Windows](https://github.com/nitrogenjs/service) section of the service project's page.

Then use npm to install Nitrogen's command line tool:

`> npm install -g nitrogen-cli`

`nitrogen-cli` is no fun to type, so the command line tool uses the alias `n2`.  Let's make sure it all is installed correctly:

`> n2 help`

This will display the top level set of commands that are available from the command line.

### Account Creation

With the command line tool installed, let's create a user account with the hosted Nitrogen service:

`> n2 user create`

This will create an account for you and store away your credentials with the command line tool. Let's run one more command just to make sure it is all up and working correctly by asking for all of the security principals you have view access to from your account:

`> n2 principal ls`

A [security principal in Nitrogen](/docs/concepts/principals.html) is an entity that authenticates with the service and has a set of permissions associated with it. A principal could be a device, user, application, or even the service itself.

You will likely see just one principal at this point, the user you just created, since you haven't added any devices to the service. Let's make it less lonely in your account by [creating our first device](camera.html).