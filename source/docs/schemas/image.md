# image

The <b>image</b> schema contains the following fields in its body:

## Implementation

This message schema is built into the Nitrogen service.

## Properties

For an image message, if you use blob storage for the image, you should set the <b>link</b> property of the message to the id of that blob.

The following properties are used in the body element:

* <b>url</b> (string, required): The url to the image.