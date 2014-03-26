---
title: Nitrogen web admin
---

## Nitrogen Web Admin

You can manage your devices, applications, and users with Nitrogen using either the command line tool or the web admin.  In this section, we're going to use the web admin to control the camera we just connected to the service.

You can reach the web admin by clicking the link in the upper right corner of this page or by navigating to [https://admin.nitrogen.io](https://admin.nitrogen.io).

### Claiming your Camera Device

Login to the web admin using your email and password that you used to create your account.  This will take you to the principals page that will list all of the principals in your cloud. This should include your user principal, and perhaps your camera device, if the service was able to automatically that you were the only principal that was connecting from that IP address.

<img src="/images/admin-new-user.png" style="max-width:100%" />

If your camera device does not appear, you'll need to manually pair your device.  Enter the claim code you received in the previous section in the text box below your principals and then click claim device.  Behind the scenes, Nitrogen checks for a device with this claim code, and if one exists, it deletes its claim code (so nobody else can claim it) and gives you admin permissions for the device.

The device should appear in your principals list.  This includes a delete button for the device if you want to delete it and all of its data at the end of this walkthrough.

<img src="/images/admin-with-camera.png" style="max-width:100%" />

### Taking a Snapshot

With your camera device added to your account, let's send it a command to take a photo of ourselves hard at work.

Click on the row for the camera device.  This should take you to the principal details page that looks something like this.  This details page allows you to rename the device, see when it last connected, and look at its messages.

Click on the 'Command' tab.  This will display a basic user interface (pull requests to improve this gratefully accepted!) for controlling the camera from the web admin.  It also includes a display of the current command queue for what the camera is executing.  Let's give our camera something to execute!

<img src="/images/admin-camera-command.png" style="max-width:100%" />

Press the 'snapshot' button (remember to smile!), which behind the scenes will send a cameraControl message from your user principal to the camera device.   This cameraCommand will look something like this from a logical perspective:

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

Since we have permission to send this device a message, this cameraControl message will be accepted and sent to anyone subscribing to this message stream in real time.  Since our camera device application is running and has such a subscription, it will receive this message and the cameraManager will execute it against the camera device. The web admin should show the command briefly. Once the camera has responded to it with an image message, it should disappear, since it is no longer an active command.

We can see this request / response pattern in detail by clicking on the messages tab.  This should contain the cameraCommand followed by the image that was issued in response. I hope that you were smiling when you pressed 'snapshot'. Here's what my Nitrogen powered selfie looked like:

<img src="/images/admin-camera-messages.png" style="max-width:100%" />

In the real world, devices can live in very unaccessible locations and it might be impossible to shell to them to watch their log output.  For this reason, Nitrogen also sends any log information from the device to the service.  These are just messages like any other message and you can see them in the logs tab in the web admin.  This enables you to remotely diagnose any issues for a device, even if you can't shell to the device.

And that's a wrap.  We've successfully built a device, hooked it up to a Nitrogen service, and controlled it remotely.  We could have done this anywhere in the world, and in fact, I use this same technique to take pictures of my dog when I'm at work.  And all of this privacy sensitive data is only accessible to you.