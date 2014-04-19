# Client Module

Nitrogen provides a JavaScript client module to make interacting with the REST and realtime endpoints of the Nitrogen service. This section describes the each of the objects in this module.

## Installation

Installation of nitrogen is via npm for client applications using node.js
For client applications using node.js, install nitrogen is via npm:

`npm install nitrogen`

For browser based applications, the client is also available off any Nitrogen service at `/client/nitrogen-min.js.`  This is the best way to pull in the client library when working with a service because it will automatically track the API of that service.

For example, for the free hosted Nitrogen service, the client library is located here: `https://api.nitrogen.io/client/nitrogen-min.js`