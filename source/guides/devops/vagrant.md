---
title: Vagrant Instructions
---

# Vagrant Instructions

The easiest way to stand up your own dev environment for Nitrogen is to use the Vagrant scripts written by [Ivan Judson](http://irjudson.org). 

Vagrant is a tool for building complete environments. It starts by downloading a virtual machine and then runs scripts to download and setup the rest of the environment.

Before you get started, you'll need either [VirtualBox](https://www.virtualbox.org/) or [Parallels](http://www.parallels.com/) installed.  

At present, the Vagrant scripts for Nitrogen start with a base image of Ubuntu 14.04 and starts layering the other bits on top of it. It will install Redis, Mongo, Ruby, Node.js, Grunt, Bower, Compass and all of the other prerequisites. Then it clones the repositories required from the [NitrogenJS Github](https://github.com/nitrogenjs), installs all the dependencies and then starts those services. 

At the end of the script, you'll have a VM with Nitrogen up and running listening on at localhost:9000 for the web portal and at localhost:3030 for the api. 

Prior to running the steps below, make sure to have VirtualBox installed. 

```
# Clone the rep
> git clone https://github.com/ivanjudson/vagrant-vms.git
# Get into the code
> cd vagrant-vms/nitrogen
```

The next step depends on if you are running VirtualBox (the default) or Parallels. 

For VirtualBox: 

```
# create the vm
> vagrant up
```

For Parallels

```
# Install the Parallels plugin 
> vagrant plugin install vagrant-parallels
# create the vm
> vagrant up --provider parallels --provision
```