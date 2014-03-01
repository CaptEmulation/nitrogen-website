# Camera

A camera device can take snapshots and optionally detect motion in response to [cameraCommand](../schemas/cameraCommand.html) messages.  A camera's operation is typically controlled via a [CameraManager](../managers/cameraManager.html).

## Interface

A camera device implements the following interface:

* snapshot(options, callback): Take a snapshot.
    * options: An object literal that can contain the following options:
        * width
        * height
        * path: Where the image should be stored on the device.

    * callback(err, options): Callback with any error and the options used during the shot.

* status(callback): Return the status of the camera device. Called before heartbeat operations on the device.
    * callback(error, status): 
        * error: True if there is an error with the camera device.
        * status: A free form object with the current status of the camera device. 

## Implementations

* [raspberrypi-camera](https://github.com/nitrogenjs/devices/tree/master/raspberrypi-camera)
* [nitrogen-imagesnap](https://github.com/nitrogenjs/devices/tree/master/imagesnap)
* [fswebcam](https://github.com/nitrogenjs/devices/tree/master/fswebcam)
* [nitrogen-foscam](https://github.com/nitrogenjs/devices/tree/master/foscam)

(Send a pull request to have yours added)