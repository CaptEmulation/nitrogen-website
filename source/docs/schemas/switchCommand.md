# switchCommand

switchCommand messages relay switch control commands to devices with that capability.

## Implementation

Services can add schema support for cameraCommand to a service, device, or application by including the module `nitrogen-switch` via npm:

	npm install nitrogen-switch

## Properties

* on (number, required): The degree that this switch should be open on a scale of 0.0, representing completely closed, and 1.0, representing completely open.