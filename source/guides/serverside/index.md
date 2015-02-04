--- 
title: Nitrogen Server Side Development
---

## Nitrogen Server Side Development

Nitrogen's server side is Node.js and released under an MIT license. We don't say it often enough but we're always looking for contributors and help so don't be bashful. 

### Nitrogen Architecture

The core Nitrogen architecture is divided into 4 services including: 

 - Front Door
 	- A service veneer that all of the incoming devices attach to. This includes the MQTT protocol adapter, the Rest interface and any other protocol adapters. 
 - Registry
 	- The central service that stores and allows queries on all of the principals in the system. All of the services use this Registry for doing authentication and authorization. 
 - Ingress
 	- A service that checks the authentication of the incoming messages and then pushes those into the message routing. 
 - Consumption
 	- A services that does the outbound communications, egress, including the mail boxing for semi-connected devices. 

Each of these services rely on various parts of the Nitrogen core and other services. 


Main main projects
[frontdoor](http://github.com/nitrogenjs/frontdoor): Service front end for Nitrogen
[ingest](http://github.com/nitrogenjs/ingest): Ingest services for Nitrogen
[registry](http://github.com/nitrogenjs/registry): Registry services for Nitrogen
[consumption](http://github.com/nitrogenjs/consumption): Egress services for Nitrogen
<li><a href="https://github.com/nitrogenjs/admin">admin</a>: Web admin tool for working with the Nitrogen service.
</ol>

Helpers
<ol>
<li><a href="https://github.com/nitrogenjs/service">service</a>: Core platform responsible for managing principals, security, and messaging.</li>
<li><a href="https://github.com/nitrogenjs/devices">devices</a>: Device principals for common pieces of hardware.</li>
<li><a href="https://github.com/nitrogenjs/commands">commands</a>: CommandManagers and schemas for well known command types.</li>
<li><a href="https://github.com/nitrogenjs/reactor">reactor</a>: Always-on hosted application execution platform.</li>
<li><a href="https://github.com/nitrogenjs/apps">apps</a>: Project maintained Nitrogen applications.</li>
</ol>
</div>