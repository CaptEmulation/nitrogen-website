# humidity

<b>humidity</b> messages relay the humidity sensed at the timestamp specified.

## Implementation

The <b>humidity</b> schema is included in the module `nitrogen-sensor`. You can add pressure functionality to any service, device, or application by adding this module as a dependency via npm or in package.json:

`npm install nitrogen-sensor`

## Properties

The following properties are used in the body element the message:

* <b>humidity</b> (number, required): The relative humidity in %.