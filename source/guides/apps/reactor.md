---
title: Nitrogen Reactor
---

## Nitrogen Applications

As you've seen in the previous two guides, there were a lot of repeated steps in setting up the typical device application. In this guide, we'll see how we can reduce this and at the same time be able to share device applications with each other using the [Nitrogen Reactor](/docs/concepts/reactor.md).

This guide builds on the [hardware device guide](/guides/device/setup.md) and assumes you have already have a Raspberry Pi device up and running. If you don't, jump back to the previous guide and complete that first.

The [Reactor](/docs/concepts/reactor.md) is Nitrogen's application execution environment. Applications in Nitrogen are simply JavaScript objects that are passed a sessions and parameters at creation.

In this guide, we'll see how we can use the Reactor for both device and cloud applications.

Let's start with setting up a Reactor on the Raspberry Pi to execute the camera device application.

You can do this by cloning the Reactor project into its own directory on your device:

`git clone https://github.com/nitrogenjs/reactor reactor`

Navigate into the reactor directory and start the reactor:

`node server.js`

This will start the reactor, and like any device, will provide you with a claim code:

`This principal (533edfae242d25eab7ff036f) can be claimed using code: FBSC-7703`

Copy this claim code and claim the reactor as your own using the Nitrogen command line tool:

`> n2 principal claim FBSC-7703`

Your reactor should now be visible and running in your Nitrogen cloud.  Let's check on its state to be sure:

`> n2 reactor state 'Reactor'`

This