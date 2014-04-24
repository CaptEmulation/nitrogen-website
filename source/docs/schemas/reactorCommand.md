# reactorCommand

reactorCommand messages relay reactor control commands to reactors.

A reactor in Nitrogen is a device (perhaps virtual) that can execute one or more Nitrogen applications. See [the concepts](../reactor.html) section of the documentation for a complete overview.

## Implementation

Services can add schema support for <b>reactorCommand</b> to a service, device, or application by including the module `nitrogen-reactor` in the project via npm:

    npm install nitrogen-reactor

## Properties

The following properties are used in the body element:

* command (string, required): The command that the reactor should execute. Should be one of:

    * <b>install</b>: Installs an application as an instance on the reactor. Properties `instance_id, `app`, and `config` are also required. If the application is currently running it will be stopped before installation commences.

    * <b>start</b>: Starts an application instance. Property `instance_id` is also required.

    * <b>stop</b>: Stops an application instance. Property `instance_id` is also required.

    * <b>uninstall</b>: Uninstall an application instance on the reactor. Property <b>instance_id<b> is also required.

* <b>app</b> (object, required for 'install' command): The application to install, this object has two properties that follow the form package.json uses for both of them.

    * <b>module</b> (string, required): Name of the npm module.  (eg. 'nitrogen-test-app')

    * <b>version</b> (string, required): Version using the npm version specification. (eg. '~0.1.5')

* <b>params</b> (object, optional): The parameters information for a specific instance of an application. This is typically the principals that it operates on or specific configuration parameters. The object literal is free form and opaque to the reactor itself -- it is passed to the application for interpretation.

* <b>instance\_id</b> (string, required): Since the same application could be installed multiple times on a reactor, Nitrogen identifies specific instances of them using an instance\_id.