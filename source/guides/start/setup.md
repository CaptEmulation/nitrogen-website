---
title: First Steps with Nitrogen
---

## First Steps

This guide will walk you through everything you need to do to get you setup and running your first device. We'll start with a device that almost everyone has: Let's turn your laptop's camera into an internet controllable camera (for simplicity sake).

### Installation

Nitrogen is uses node.js extensively. If you don't already have node.js installed, install it from [http://nodejs.org](http://nodejs.org).

Then use npm to install Nitrogen's command line tool:

`> npm install -g nitrogen-cli`

nitrogen-cli is no fun to type, so the command line tool uses the alias n2.  Let's make sure it all is installed correctly by asking for help:

`> n2 help`

This should display of the top level commands available to you with the command line tool.  If you need help on any command at any stage, you can always suffix that command with the keyword help to get more information.

### Account Creation

With the command line tool installed, let's create a user account with the hosted Nitrogen service:

`> n2 user create <your-email>`

This will ask you for a password and your real time, create an account for you, and store away your credentials for use with the command line tool. Let's run one more command just to make sure it is all up and working correctly:

`> n2 principal ls`

A [principal in Nitrogen](/docs/concepts/principals.html) is an entity that authenticates with the service. It could be a device, user, or even the service itself.

You should see just one principal at this point, the user you just created, since you haven't added any devices to the service.  Let's rectify that situation by [creating our first device](camera.html)