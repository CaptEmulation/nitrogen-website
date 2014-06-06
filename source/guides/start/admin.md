---
title: Nitrogen web admin
---

## Nitrogen Web Admin

You can manage your devices, applications, and users with Nitrogen using either the command line tool or the web admin.  In this section, we're going to use the web admin to control the camera we just connected to the service.

You can reach the web admin by clicking the link in the upper right corner of this page or by navigating to [https://admin.nitrogen.io](https://admin.nitrogen.io).

### Taking a Snapshot

With your camera device connected and added to your account, let's send it a command to take a photo of ourselves hard at work.

Click on the devices tab and then on the camera device. This should take you to the principal details page where you can rename the device, see when it last connected, and look at its messages.

Click on the 'Command' tab. This will display a very basic user interface (pull requests to improve this gratefully accepted!) for controlling the camera from the web admin. It also includes a display of the current command queue for what the camera is executing. Let's send our camera something to execute!

<img src="/images/admin-camera-command.png" style="max-width:100%" />

Press the 'snapshot' button (remember to smile!), which behind the scenes will send a cameraControl message to the camera device that logically looks something like this:

```object
{
    from: '5321e2debe46b41671000016'
    to: '5321e2debe46b41671000662',
    ts: 1394732368660,
    type: 'cameraCommand'
    body: {
        command: 'snapshot'
    }
}
```

We have permission to send this camera device a message because it is using our API key (and therefore we have wildcard permissions for it) so this cameraControl message will be accepted and sent to anyone subscribing to this message stream in real time. Since our camera device application is running and has a subscription, it will receive this message and the cameraManager will take a snapshot with the camera.

The web admin's command tab shows the currently active commands. In our case, it should show the command briefly, but once the camera has responded to it with an image message, it will disappear, since it is no longer an active command.

This is a common pattern for commandManagers working with devices. We can see this request / response pattern in detail by clicking on the messages tab.  This should contain the cameraCommand followed by the image that was issued in response. I hope that you were smiling when you pressed 'snapshot'. Here's what my Nitrogen selfie looked like:

<img src="/images/admin-camera-messages.png" style="max-width:100%" />

In the real world, devices can live in very unaccessible locations where it might be impossible (and probably inconvenient) to connect to them to watch their log output. The Nitrogen client provides automatic transport for logs from the device to the service. These are just messages like any other message and you can see them in the logs tab in the web admin. This enables you to remotely diagnose any issues for a device by clicking on the 'Logs' tab in this view. Finally, you can see who has permissions for any principal by clicking on its "Permissions" tab.

And that's it. We've successfully built a device, hooked it up to a Nitrogen service, and controlled it remotely. We could have done this anywhere in the world, on any network, and the Nitrogen service would have routed these messages back to our camera. And all of the potentially sensitive data this camera is collecting is only accessible to you because of the permissions that the Nitrogen service enforces.

The next guide will walk you through building your [first hardware camera using a Raspberry Pi](/guides/device/setup.html)