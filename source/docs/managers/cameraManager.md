# CameraManager

CameraManager is a [CommandManager](../concepts/commands.html) subclass that follows the message stream of a [camera](../devices/camera.html) device, executes [cameraCommands](../schemas/cameraCommand.html) as necessary against that [camera](../devices/camera.html) and emits [images](../schemas/image.html) messages.

## Implementation

CameraManager is included in the module `nitrogen-camera`. You can add camera functionality to any service, device, or application by installing this module via npm:

`npm install nitrogen-camera`

## Example Usage

A CameraManager is typically used within an established session handler for a camera.  Here is an example adapted from the sample [camera](https://github.com/nitrogenjs/camera) device project:

```javascript
var RaspberryPiCamera = require('raspberrypi-camera');

var service = new nitrogen.Service();
var camera = new RaspberryPiCamera();

service.connect(camera, function(err, session, camera) {

    new CameraManager(camera).start(session, function(err, message) {
        // callback each time a relevant message is received. 
    });
});
```