# Client Module

Nitrogen provides a JavaScript client module to ease interacting with the REST and realtime endpoints of the Nitrogen service. Each class of the client module is documented in this section.

## Installation

For client applications running in node.js, installation is via npm:

`npm install nitrogen`

For browser based applications, the client is available from the Nitrogen service you are interacting at via the endpoint `/client/nitrogen-min.js.`  This is the best way to pull in the client library when working with a service because it will automatically track the API version of that service.

For example, for the project hosted Nitrogen service, the client library is located here: `https://api.nitrogen.io/client/nitrogen-min.js`
