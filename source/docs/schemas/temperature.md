# temperature

<b>temperature</b> messages relay the temperature sensed by a device sensor at the timestamp specified.

## Implementation

The <b>temperature</b> schema is included in the module `nitrogen-sensor`. You can add pressure functionality to any service, device, or application by adding this module as a dependency via npm or in package.json:

`npm install nitrogen-sensor`

## Properties

The following properties are used in the body element the message:

* <b>temperature</b> (number, required): The pressure in C (standard SI units).