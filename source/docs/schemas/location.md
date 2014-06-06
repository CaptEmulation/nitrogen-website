# location

<b>location</b> messages relay the location for the principal at the timestamp specfied.

## Implementation

This message schema is included with the Nitrogen service.

## Properties

The following properties are used in the body element:

* <b>accuracy</b> (number): Approximate bound on error of latitude, longitude in meters.
* <b>altitude</b> (number): Altitude in meters.
* <b>altitudeAccuracy</b> (number): Approximate bound on error of altitude in meters.
* <b>heading</b> (number): Heading in decimal degrees.
* <b>latitude</b> (number, required): Latitude in decimal degrees.
* <b>longitude</b> (number, required): Longitude in decimal degrees.
* <b>speed</b> (number): Speed in meters per second.