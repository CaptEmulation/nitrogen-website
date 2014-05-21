# light

<b>light</b> messages relay the light sensed at the timestamp of the message.

## Implementation

The <b>light</b> schema is included in the module `nitrogen-sensor`. You can add light functionality to any service, device, or application by adding this module as a dependency via npm or in package.json:

`npm install nitrogen-sensor`

## Properties

The following properties are used in the body of the message:

* <b>lux</b> (number, required): The light value in lux (standard SI units).