---
title: Nitrogen Service
---

# Service

A service is a principal and messaging hub in Nitrogen. It authenticates and authorizes principals, manages messaging between principals, and provides real time message subscriptions. A typical device application using the JavaScript library looks like this:

```javascript

var config = {
  host: 'api.nitrogen.io',
  http_port: 443,
  protocol: 'https'  
};

var service = new nitrogen.Service(config);

service.connect(light, function(err, session, light) {
    if (err) return console.log('Failed to authenticate: ' + err);

    // your application here
});
```

When you use the Nitrogen client library, the service class manages authentication and session management for you. You provide it a callback function that describes the work you'd like it perform after a session is established.  Its possible that your session will fail.  The service class handles reconnection / reauthorization transparently for you and will call you back again when a connection is re-established with the new session.

## Sessions

When a principal authenticates with the service, it is provided an access token for subsequent service requests in the form of a session object. All of the client functions that interact with the service in the context of a principal take a session to use in that operation:

```javascript
nitrogen.Message.find(session, { to: camera.id }, function(err, messages) {
    // ...
});
```

The service can automatically renew a session as it nears the end of the AccessToken's lifetime. This renewal is automatically handled for you by the Session class of the client library.