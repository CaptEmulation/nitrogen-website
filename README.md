# Nitrogen Project Website

This repo houses the Nitrogen Project website. It is built using middleman.

## Installation

You need to have Ruby and RubyGems working on your machine, then:

`> bundle install`
`> bundle exec middleman`

## Nitrogen Project

The Nitrogen project is housed in a set of GitHub projects:

Server side main projects
1. [frontdoor](http://github.com/nitrogenjs/frontdoor): Service front end for Nitrogen
2. [ingest](http://github.com/nitrogenjs/ingest): Ingest services for Nitrogen
3. [registry](http://github.com/nitrogenjs/registry): Registry services for Nitrogen
4. [consumption](http://github.com/nitrogenjs/consumption): Egress services for Nitrogen
5. [admin](https://github.com/nitrogenjs/admin): Web admin tool for working with the Nitrogen service.

Client side main projects
1. [client](https://github.com/nitrogenjs/client): JavaScript client library for building Nitrogen devices and applications.
2. [cli](https://github.com/nitrogenjs/cli): Command line interface for working with the Nitrogen service.


Helpers
1. [service](https://github.com/nitrogenjs/service): Core platform responsible for managing principals, security, and messaging.
2. [device](https://github.com/nitrogenjs/devices): Device principals for common pieces of hardware.
3. [commands](https://github.com/nitrogenjs/commands): CommandManagers and schemas for well known command types.
4. [reactor](https://github.com/nitrogenjs/reactor): Always-on hosted application execution platform.
5. [apps](https://github.com/nitrogenjs/apps): Project maintained Nitrogen applications.