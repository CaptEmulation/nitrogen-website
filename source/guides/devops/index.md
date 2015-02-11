---
title: Nitrogen Dev Ops
---

## Nitrogen Dev Ops

If you want to get a server up and running yourself, it's fairly simple. There are three ways to stand up a Nitrogen server. The first is to manually run the servers yourself. Secondly, we've got a Vagrant script set up that will make this easy. But third, we recommend that you use the Docker deployment to actually run in production.

Before getting started, please run through the [setup of the admin tools](../start/setup.html).


### Manual setup of a server

This is the best option if you are doing back end Nitrogen development as it gives you the most flexibility and you can run everything on your own local machine. 

In short, you'll need to install Node.js, Redis and Mongo then clone the 4 service repositories for Registry, Front Door, Ingest and Consumption, npm install each one and then run them. 


This is the absolute basics that you'll need. There's a lot more detail and troubleshooting on the page called [Manually running Nitrogen Server](manuallyrunserver.html). 

### Running Vagrant

If you are doing device or app development and want a local server, Vagrant is probably your best option. Vagrant is effectively a very robust way of scripting the deployment of a server giving you a very repeatable way of getting things up and going consistently. 

For more information, check out [Deploying with Vagrant](vagrant.html). 

### Deploying with Docker

If you are deploying into production in Azure and really need to be able to scale, the recommendation is to go with a Docker deployment. Docker gives you an app container model. 

For more information check out [Deploying with Docker](docker.html). 