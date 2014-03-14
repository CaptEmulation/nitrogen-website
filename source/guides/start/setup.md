---
title: First Steps with Nitrogen
---

## First Steps

This guide will walk you through everything you need to do to get you quickly setup and running your first device. We'll start simple and with a device that almost everyone has for simplicity's sake: Let's turn your laptop's camera into an internet controllable camera.

### Installation

Nitrogen is built on JavaScript and node.js. If you don't have node.js installed already, install it from [http://nodejs.org](http://nodejs.org).

Then use npm to install Nitrogen's command line tool:

`> npm install -g nitrogen-cli`

nitrogen-cli is no fun to type, so the command line tool uses the alias n2.  Let's make sure it all is installed correctly by asking for some help:

`> n2 help`

This should display of the top level commands available to you with the command line tool.  If you need help on any command at any stage, you can always suffix that command with the keyword help to get more information.

### Account Creation
Next, let's create a user account with the hosted Nitrogen service.  To do that, click on "Web Admin" in the top navigation bar or go to [https://admin.nitrogen.io](https://admin.nitrogen.io).  This will take you to the web admin tool for the hosted service and ask you to create an account.  Create an account with your email, password, and name and then come back here.

Now that you have an account, let's get the command line tool set up to use it with the service:

`> n2 user use <your-email>`

Your user credentials are now associated with the command line tool. If you ever want to change the account you use when working with a service when using the command line tool, you can run this command again. Let's run one more command just to make sure it is all up and working correctly:

`> n2 principal ls`

A [principal in Nitrogen](/docs/concepts/principals.html) is an entity that authenticates with the service. It could be a device, user, or even the service itself.

You should see just one principal at this point, the user you just created, since you haven't added any devices to the service.  Let's rectify that situation by [creating our first device](camera.html)