---
title: Running the Nitrogen Services Manually
---

## Running the Nitrogen Services Manually

There's a lot of reasons to run the server manually but most of them have to do with you doing back end development. However, if you are looking at running this in production, we recommend that you use one of the more automated deployments. This includes both Vagrant and Docker. For more details check out the [overview](index.html).

1. Install Node.js
2. Install Redis
3. Install MongoDB
4. Clone the 4 github repositories for the services required for the server

    ```
	> git clone https://github.com/nitrogenjs/registry.git
	> git clone https://github.com/nitrogenjs/frontdoor.git
	> git clone https://github.com/nitrogenjs/consumption.git
	> git clone https://github.com/nitrogenjs/ingest.git
	```

5. Use NPM in each of the created directories to install the dependencies for the services


	```
	> cd <name of directory>
	> npm install
	```

6. Run each of the servers

    ```
	> cd <name of directory>
	> node server.js
	```

	At this point you have a server up and running and can start doing development against it. The only admin access you'll have is via the <a href="../tools/cli.html">Nitrogen CLI (Command Line Interface)</a> so if you want to have a GUI interface, you'll need get the Web Admin portal running as well.

7. (Optionally) run the Web Admin portal locally:

	```
	> github clone https://github.com/nitrogenjs/admin.git
	> cd admin
	> npm install
	> node server.js

	```