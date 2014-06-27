---
title: Mosaic Web App
---

## Mosaic Web Application

Now that we have our timelapse application running and collecting photos for us, let's combine all of these photos into a web application that displays the last photo for each camera in a mosaic.

First, clone the repo for the mosaic application. The mosaic application is part of the applications Nitrogen maintains. You can clone it with:

`git clone http://github.com/nitrogenjs/apps`

The mosaic application is in the `web/mosaic` directory. Let's first have a look at the server application in `server.js`:

```javascript
function findCameras(session) {
    nitrogen.Principal.find(session, { tags: 'sends:image' }, {}, function(err, principals) {
        if (err) return console.log('principal request failed: ' + err);

        principals.forEach(function(camera) {
           if (!cameras[camera.id]) {
               nitrogen.Message.find(session, { type: 'image' }, { limit: 1, sort: { ts: -1 } }, function(err, messages) {
                   if (err) return session.log.error('message request failed: ' + err);

                   if (messages.length) {
                       session.log.info('last image for camera: ' + JSON.stringify(messages));
                       sendImage(session, messages[0]);
                   }
               });

               sendCamera(camera);
           }
        });
    });
}

service.connect(app, function(err, session, app) {
    if (err) return console.log('airpi: connect failed: ' + err);

    findCameras(session);

    session.onMessage({ type: 'image' }, function(image) {
        sendImage(session, image);
    });

    config.buildAuthorizationUri();

    webapp.get('/', function(req, res) {
        if (req.query.post_authorize)
            findCameras(session);

        res.render('mosaic/index', {
            app_authorization_uri: config.app_authorization_uri
        });
    });

    server.listen(config.port);

    webapp.engine('handlebars', hbs.engine);
    webapp.set('view engine', 'handlebars');

    webapp.use(express.static(path.join(__dirname, '/static')));
});
```

Like the examples that we have seen in the previous guides, it first establishes a session with the service. Once that session is established, it then searches for devices that are have the tag 'sends:image'. In Nitrogen, if a device sends a particular type of message, tagging it with 'sends:<message type>' enables other principals to query for it. In this case, we are using this tag to find all of the cameras. For each of these devices that it finds, it finds the last image it sent, and sends the image to any clients.

Mosaic updates its web clients over socket.io. We next open up a real time subscription on any sent images from the cameras the application has permissions for and fans these messages out to each connected client via the sendImage function.

It next builds an authorization url. Here is the relevant code for that in config.js:

```javascript
config.buildAuthorizationUri = function() {
    config.app_authorization_uri = config.endpoints.users + "/authorize" +
        "?api_key=" + encodeURIComponent(process.env.APP_API_KEY) +
        "&app_id=" + encodeURIComponent(process.env.APP_ID) +
        "&redirect_uri=" + encodeURIComponent(process.env.APP_URL) +
        "&scope=" + encodeURIComponent(JSON.stringify(config.device_scope));
};

config.device_scope = [{
    actions: [ 'view', 'subscribe' ],
    filter: {
        tags: 'sends:image'
    }
}];
```

By default, an application in Nitrogen does not have access to any of your devices. The user of your application must grant the application permissions to their devices. When we make this authorization request, we include a 'scope' specification that provides a filter and the actions we'd like to be granted permissions for these principals. In this case, Mosaic would like to be able to view the principal's details and subscribe to messages for any devices that can send `image` messages. The request also needs to include the 'redirect_uri' that should be called after authorization.

This authorization uri is used by the application to kick off authorization for the user's cameras in `views/mosaic/index.handlebars`:

```html
<a href="{{app_authorization_uri}}" class='btn green'>Add Camera</a>
```

When we deploy an application, we typically want to use a seperate API key for the application to track it seperately from our user account. You can create an API key in Nitrogen's [web admin](http://admin.nitrogen.io/#/apikeys). We then use this API key in place of our user key for the application.

We want to execute this application in the context of its own application security principal that we can grant permissions to. Let's create this principal now using the api key that we just created:

`n2 principal create --type 'app' --name 'Mosaic App' --apiKey '<YOUR APP'S API KEY>'`

The command line tool will create your application principal and display its id and public and private keys.

When we are building a web application with Nitrogen, you typically also want to deploy the same image to multiple frontend servers. For this reason, we use `nitrogen-static-store` instead of the `nitrogen-leveldb-store` store you have seen in previous examples. You can use the static store when the application does not provision its own credentials but instead wants to have them delivered with the application. This means we need configure these credentials as part of the application.

Copy the credentials and edit the file `mosaic` file (Linux and MacOS) or `mosaic.bat` (Windows) and add the newly created app id to `APP_ID`, public key in `APP_PUBLIC_KEY`, private key in `APP_PRIVATE_KEY`, and API api key for the application in `APP_API_KEY`. This script sets up these environmental variables before starting server.js. Alternatively, you can set these environmental variables directly in the OS or cloud PaaS platform during deployment.

You can then start the web app using:

`> ./mosaic` (Linux and MacOSX)

or

`> mosaic.bat` (Windows)

Then navigate to `http://localhost:3010` to start the application!

And that's it:  You've seen how you can build a Nitrogen web application and use Nitrogen's OAuth2 based authorization system to have the user grant the application permissions for their devices and their message streams and then use them to build an web application with them.