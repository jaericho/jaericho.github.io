---
layout: post
title: "Windows Loses IP After vMotion"
date: 2015-05-11 20:33:36 -0600
categories: [Stupid Bugs]
tags: [IP, vMotion, vmware, Windows]
---

I've been fighting a very annoying bug with a couple of my Windows servers.

They would lose their static IP address after being vmotion'd and go back to DHCP. The easy workaround was to disable DRS on those specific VMs which we did, but that doesn't fix anything.

I thought for sure that the issue was at the VM level, but it turns out that after upgrading from `5.1 Patch 2 (1743533)` to `5.1 Patch 7 (2583090)` the issue has cleared up.

Here is a very [useful list](http://kb.vmware.com/selfservice/microsites/search.do?language=en_US&cmd=displayKC&externalId=1014508#ESX) of all the versions and release dates from VMWare.
