# switchCommand

<b>switchCommand</b> messages relay switch control commands to devices with that capability.

## Implementation

Services can add schema support for <b>switchCommand</b> messages to a service, device, or application by including the module `nitrogen-switch` via npm:

	npm install nitrogen-switch

## Properties

* <b>on</b> (number, required): The degree that this switch should be open on a scale of 0.0, representing completely closed, and 1.0, representing completely open.