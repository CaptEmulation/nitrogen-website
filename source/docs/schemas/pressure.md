# pressure

<b>pressure</b> messages relay the pressure sensed by the device sensor at the timestamp of the message.

## Implementation

The <b>pressure</b> schema is included in the module `nitrogen-sensor`. You can add pressure functionality to any service, device, or application by adding this module as a dependency via npm or in package.json:

`npm install nitrogen-sensor`

## Properties

The following properties are used in the body of the message:

* <b>pressure</b> (number, required): The pressure in Pascals (standard SI units).