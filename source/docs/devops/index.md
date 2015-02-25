---
title: Nitrogen DevOps
---

## Nitrogen DevOps

This section describes the various ways that you can stand up a Nitrogen service. Running a scaled Nitrogen service is necessarily a complicated affair given the scale involved in the Internet of Things. Given that, you should first consider if you need to run a service locally at all. For small scale sandbox style experiments, you should consider using the <a href="https://admin.nitrogen.io">project maintained hosted service</a>.

When you decide that you need to run your own service, there are three approaches that you can follow: manually run the service yourself, use the project maintained Vagrant scripts to standup a dev or test environment, or use the tooling we've developed around Docker to stand up a scaled projection service.

This overview gives you an overview of the three options and how to choose between them.

### Manual setup of a server

This is the best option if you are doing back end Nitrogen development as it gives you the most flexibility and you can run everything on your own local machine. If this fits your usage profile, you can find more details in the [manual Nitrogen Server](manual.html) section.

### Running Vagrant

If you are doing device or app development and want a local single server and don't want to make frequent changes to the Nitrogen service, Vagrant is probably your best option. Vagrant is effectively a very robust way of scripting the deployment of a server giving you a very repeatable way of getting things up and going consistently.

For more information, read tbe [deploying with Vagrant](vagrant.html) section.

<!--
### Deploying with Docker

If you are deploying into production in Azure and really need to be able to scale, the recommendation is to go with a Docker deployment. Docker gives you an app container model.

For more information, read the [deploying with Docker](docker.html) section.
-->