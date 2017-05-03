---
layout: post
title: "Installing a Centos6 VM for HDP or CDH"
categories: Systems
tags: [intro]
image:
  feature: macNnotebook-1920.jpg
  teaser: macNnotebook-1920.jpg
  credit: Death to Stock Photo
  creditlink: ""
---

This post will get you started on installing Centos 6 on your VM.  At the time of this writing, most companies are using either RHEL6/Centos6 or RHEL7/Centos7 for their data clusters with the majority still on version 6 to stay with the older more stable version.

### Get Centos
Go ahead and download the Centos image from one of the mirrors found on the [Centos site](http://isoredirect.centos.org/centos/6/isos/x86_64/).  I prefer the DVD version over minimal as it will come with the desktop and saves you from installing a few applications later.

### VM Configuration
General purpose configuration per node:  

* 4 cores   
* 6GB RAM  
* 50GB Hard disk for root and home partitions  
* 100GB Minimum Hard disk for data partition (optional)

Note: For networking, I generally choose a *bridged* adaptor.  By default this will use DHCP and that can cause issues since the host IP has to be static.  You can set this in the linux config files after your servers have started.

<img src="/images/Bridged.png">

### Install Centos
There\'s not much to the install once the VM has been configured.  It does ask a few questions about storage options.  Since we are installing on a new VM, this makes configuring easier.  Simply choose to overwrite the full partition. 

One option to enable is the NTP service.  Many of the hadoop services need the times to be synchronized across nodes and will fail if it notices a time drift.

<img src="/images/CentosInstall.png">  

### Networking
For basic purposes, set the VMs to have a *bridged* network interface.  Upon startup, the OS will get a dynamic IP address and you will need to run *ifconfig* through the terminal to get it.  

<img src="/images/ifconfig.png">

I will write an article that covers setting a static IP, for now let\'s keep it simple and let the DHCP handle the network configuration.

### Clone
Once the OS has been installed, make sure to clone the VM at least once if you would like a 2-node setup.  It is also a good practice to take an extra clone in case something goes wrong and you need to roll back to an earlier version.

### Questions or Comments?
If there is a step that I should cover in more detail or for any comments send me an email at [boxcardata@gmail.com](mailto:boxcardata@gmail.com)
