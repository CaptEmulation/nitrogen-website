---
title: Nitrogen Web Admin
---

## Nitrogen Web Admin

With Nitrogen, you can manage your devices, applications, and users using either the [command line interface](/docs/tools/cli.html) or the [web admin](https://admin.nitrogen.io). In this section, we're going to use the web admin to view the data from the thermometer we just connected to the service.

You can reach the web admin by clicking the link in the upper right corner of this page or by navigating to [https://admin.nitrogen.io](https://admin.nitrogen.io).

### Viewing Data

Once you have logged in, click on the devices tab and then on the thermometer device. This should take you to the principal details page where you can rename the device, see when it last connected, and look at its messages.

In our case, you should see that the Thermometer has been emitting data with the schema 'temperature'. The body of those messages, in this case the temperature, is displayed on the right. As messages arrive they are displayed in real time so that you can monitor the operation of your sensors in real time.

In the real world, devices can live in very unaccessible locations where it might be impossible (and probably inconvenient) to connect to them to watch their log output. The Nitrogen client automatically transports logs from the device to the service. These are just messages like any other message and you can see them in the logs tab in the web admin. This enables you to remotely diagnose issues for a device by clicking on the 'Logs' tab in this view. Finally, you can see who has permissions for any principal by clicking on its "Permissions" tab.

And that's it. We've successfully built a device, hooked it up to a Nitrogen service, and managed and viewed its telemetry remotely. We could have done this anywhere in the world, on any network, and the Nitrogen service would have routed these messages from our thermometer. And all of the potentially sensitive data this camera is collecting is only accessible to you because of the permissions that the Nitrogen service enforces.

The next guide will walk you through building your [a controllable camera device](/guides/camera/camera.html)