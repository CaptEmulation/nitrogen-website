# ultraviolet

<b>ultraviolet</b> messages relay the ultraviolet sensed at the timestamp specified.

## Implementation

The <b>ultraviolet</b> schema is included in the module `nitrogen-sensor`. You can add this schema to any service, device, or application by adding this module as a dependency via npm or in package.json:

`npm install nitrogen-sensor`

## Properties

The following properties are used in the body element the message:

* <b>ultraviolet</b> (number, required): The ultraviolet measurement in UVI (ultraviolet index).